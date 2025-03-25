---
theme: ./theme
title: "Prompting is the New Scripting: Meet GenAIScript"
# apply unocss classes
class: text-center
transition: fade
mdc: true
selectable: true
fonts:
  sans: Noto Sans
  serif: Noto Sans
  mono: Incosolata
colorSchema: dark
background: /images/bg.png
zoom: 2.3
---

```js
$('#hello').text('DotJS');
```

<!-- 
jQuery once simplified web development by abstracting away complexities — and I think AI needs the same today.

Nearly 20 years ago, jQuery changed the way we build web applications. It made it easier to manipulate the DOM, handle events, and create animations. It was a game-changer, allowing developers like me and you to focus on what we wanted to achieve. Again, GenAI needs the same today.
-->

---
title: jQuery for GenAI?
layout: cover
background: /images/bg2.png
class: text-center
zoom: 2.3
---

````md magic-move
```js
$`Create an haiku about why JS is awesome`
```

```js
$`Create an haiku about why JS is awesome`

Logic flows like streams,
Dynamic, boundless, it adapts—
JavaScript creates.
```
````

<!-- 
I'm sure you can spot something familiar.

[click] This code here is valid JS that makes use of GenAI.
And you'll see that it's way more than just a fancy wrapper for prompts.
-->

---
layout: cover
# background: 'linear-gradient(#0000, #0008, #0000), url(images/bg5.png)'
background: 'linear-gradient(#0003, #000a, #0005), url(/images/bg2.png)'
class: text-left
zoom: .99
---

# Prompting is the New Scripting

<Me class="animate-keyframes-fade-in animate-duration-1000 animate-ease-in-out animate-fill-mode-forwards animate-delay-2000 op-0"/>

## ![](/images/genaiscript.svg){.inline-block .w-15 .m-r-4} Meet GenAIScript{.font-size-8}

<!--
Hey folks, I'm Yohan Lasorsa, and I work as Developer Advocate at Microsoft.
I maintain many open source projects on my free time, and I'm always looking for ways to make it more manageable.
-->

---
title: Issue without context
layout: center
---
![](/images/not-working.png){.inline-block .border-rounded-xl}

<!-- 
Answering issues like these to explain that you need some context to be able to help, 
-->

---
title: PR without details
layout: center
---
![](/images/pr-details.png){.inline-block .border-rounded-xl}

<!--
Or looking through all the changes in a PR trying to understand it - takes time. And it's not the really the fun part.

And since I've been working with GenAI for a while now, I thought that it could actually be useful for stuff like this, if I could make it work without too much effort!

That's how I started looking into GenAIScript.
-->

---
zoom: 1.4
layout: center
---

![](/images/genaiscript.svg){.inline-block .w-20 .m-r-4 .float-left}
# GenAIScript
[aka.ms/genaiscript](https://aka.ms/genaiscript)

<br>

- Use with CLI, VS Code or GitHub Copilot
- Works with GitHub Models, OpenAI, Anthropic, Ollama...
- Built-in prompts, tools, agents and helpers

<!--
GenAIScript is a Open Source JS toolbox for GenAI that helps you get productive with it, allowing you to create even agents to do complex tasks for you, as simple as writing a script. 

It's really meant to be a developer tool and works best when it's used within a project repository.

But really instead of telling you about its extensive set of features, let's see it in action.

## PR reviewer: 5min
- Open `pr-describe.genai.js`
  * Here I've created a new GenAIScript.
  * The first thing you may have noticed is this `.genai.js` extension:
  * This is what enables the GenAIScript environment. It works with TS and you can use ES Modules.
  * Now let's start with the prompt: I want to build a script that will help me review PRs, by describing what's in the PR.
  * `pr_prompt` explain the prompt
  * `pr_def` to define the GIT_DIFF
  * `pr_changes` to get the git changes

- Test it: stage some changes
  * Explain how to run or debug the script
  * Show the chat panel

- Now, we want this script to run on my GH repo, so I created a GH Action.
  * I won't dive too much into the details, but the important parts here are:
    - The action is triggered on PR events
    - It runs the script using `npx` and the genaiscript CLI
    - It uses the `GITHUB_TOKEN` and the permissions to update the PR
  * Open the PR in the repo and show the results

## Issue reviewer: 3min
- Open `issue-review.genai.js`
  * `issue_prompt` explain the prompt
  * `issue_def` to define the title/body
  * `issue_github` to get the issue
  * `issue_script` to set the meta

- What other meta and config settings can be useful?

- Run the script
  * Show the extension panel
  * Add title/description meta
  * Change the model to "ollama:phi4"

## Copilot: Gen background: 4min
- Open `background.genai.js`
  * `bg_prompt` explain the prompt
  * `bg_def` to define the question
  * `bg_tool` to define the tool => tool+prompt=agent
  * `bg_script` to set the meta

- @genaiscript /run background geometric gradients blue

## Agent: Git changelog generator: 3min
- Open `changelog.genai.js`
  * `ch_prompt` explain the prompt
  * `ch_def_agent` explain agent
-->

---
layout: left
hide: true
---

# Syntax recap

```ts
// Prompt templates
$`Say hello to ${name}`

// Set context
def(README, 'README.md')
defImage(PICTURE, 'https://http.cat/403')

// Create tools
defTool(
  'random',
  'Generate a random number',
  async () => Math.random(),
)

// Create agents
defAgent(
  'math',
  'Agent that does math operations',
  `You're a math expert. Answer the question using provided tools.`,
  { system: 'python', tools: ['random'] },
)
```

---
title: Automated refactoring, anyone?
layout: cover
class: text-left
background: /images/bg2.png
zoom: 2.4
---

<div class="text-center font-size-9">
  <span v-click.hide>🤔</span><span v-after>✨</span>
</div>

<v-after>

```js
$`Refactor all components to use the new
template syntax introduced in Angular 17`

// Built-in: ast-grep, fs, agent_fs...
```

</v-after>

<!-- 
You might still wonder how far this can be useful in your projects.

[click] Then what about automated refactoring of your code?
For example, Angular introduced a new template syntax, it can be a pain to update all your components manually, or write a proper migration script to do it.

GenAIScript provides built-in support for navigating the file system, and even for AST manipulation, so hard scripts like this can become a breeze.
-->

---
title: There's more
layout: cover
background: 'linear-gradient(#0005, #000a, #0008), url(/images/bg2.png)'
class: align-middle, font-size-4, more-slide
zoom: 1.4
---

<style>
.more-slide span {
  opacity: 0;
  @apply animate-keyframes-fade-in animate-duration-1000 animate-ease-in-out animate-fill-mode-forwards;
  animation-delay: calc(var(--o) * 300ms + 2s);
}
.no-anim {
  opacity: 1 !important;
  animation: none !important;
}
</style>

[MCP tools]{.font-size-5.animate-delay-1000 style="--o: 1"} &nbsp;&nbsp;&nbsp;&nbsp; [Audio Transcription]{.text-gray-3 style="--o: 17"} &nbsp;&nbsp;&nbsp;&nbsp; Image & Video Input{.font-size-5 style="--o: 8"}

[RAG]{style="--o: 21"} &nbsp;&nbsp;&nbsp;&nbsp; [Structured Outputs]{.font-size-5 style="--o: 4"} &nbsp;&nbsp;&nbsp;&nbsp; [@agentic tools]{.text-gray-3 style="--o: 16"} &nbsp;&nbsp;&nbsp;&nbsp; [Browser control]{style="--o: 9"}

[Multi-Agents]{.font-size-6 style="--o: 0.1"} &nbsp;&nbsp;&nbsp;&nbsp; [🤩]{.font-size-16 .m-4 .inline-block .align-middle .no-anim} &nbsp;&nbsp;&nbsp;&nbsp; [Jupyter Notebooks]{style="--o: 11"}

[PromptFoo evals]{style="--o: 12"} &nbsp;&nbsp;&nbsp; [Office, PDF, XML, CSV, HTML...]{.text-gray-3.font-size-3 style="--o: 6"} &nbsp;&nbsp;&nbsp; [Agent Memory]{.font-size-5 style="--o: 2"} &nbsp;&nbsp; [TypeScript]{.font-size-4 style="--o: 18"}

[Teams Integration]{.text-gray-3 style="--o: 15"} &nbsp;&nbsp;&nbsp;&nbsp; [User Input]{.font-size-5 style="--o: 20"} &nbsp;&nbsp;&nbsp;&nbsp; [Vector Search]{.font-size-3 style="--o: 5"} &nbsp;&nbsp;&nbsp;&nbsp; [Semantic Caching]{style="--o: 13"}

[Containers]{.font-size-5 style="--o: 3"} &nbsp;&nbsp;&nbsp;&nbsp; [JSON schema]{style="--o: 14"} &nbsp;&nbsp;&nbsp;&nbsp; [Jinja Templates]{.text-gray-3 style="--o: 7"} &nbsp;&nbsp;&nbsp;&nbsp; [Zod]{style="--o: 19"}

<!--
There's way more to GenAIScript that what I can show you in 20min, and if there's a fancy new AI tool or pattern that you've heard about, there are good chances that GenAIScript already has it or will have it soon.

But to my regret there's still one thing to keep in mind...
-->

---
title: It's only a developer tool
layout: center
---

<style>
.slidev-vclick-target {
  opacity: 1;
  transition: all 1s ease;
}

.slidev-vclick-hidden {
  opacity: 0;
  font-size: 0;
}
</style>

# It's<span v-click class="font-size-6 color-white align-middle">&nbsp;(only)</span> a developer tool

<!-- 
Right now, it's build as tool for you to use rather than a framework to build applications. 

[click] Though I should note that it can run as an MCP server, exposing your scripts as tools to be used by your regular GenAI apps and workflows. If you've never heard of MCP, it's an open protocol that allows you to expose your GenAI tools and resources for models to use.

Now what I hope is that we'll get GenAI frameworks in the future that gets inspired by the simplicity of GenAIScript.
-->

---
title: Conclusion
layout: center
class: font-size-6 w-2/3
---

# Links{.font-size-10}<br>

- [bit.ly/genaiscript-talk](https://bit.ly/genaiscript-talk)
- [aka.ms/genaiscript](https://aka.ms/genaiscript)
- [aka.ms/genaiscript/samples](https://aka.ms/genaiscript/samples)

![qrcode](/images/qrcode.png){.w-60 .absolute .right-9em .top-1/2 .transform .-translate-y-1/2}

<Contact/>

<!--
If you feel like GenAI could help you automate some of your tasks, but you don’t know where to start and you don't want to spend too much time on it, I think GenAIScript is a great place to begin.

Thank you!
-->
