<a href= "https://prototypefund.de/project/voice-ql-datentabellen-mit-gesprochener-sprache-barrierefrei-erkunden/"><img src="./images/assets/voice-ql-ring.png" width="40%" height="40%" align="right"></a>

# Model Linter for Jovo V4

## Overview

Small flaws in your voice model can cause serious malfunctions at runtime. 

A concept frequently used in software development is called "[linting](https://en.wikipedia.org/wiki/Lint_(software))". Linting refers to the process of static code analysis and is used to flag programming errors, bugs, stylistic errors and suspicious constructs.

Surprisingly I don't see this concept being used often with voice model files though I see a big potential here.
 
This is why I collected some of my voice model test scripts and bundled them together as a Jovo extension. This hook for the [Jovo V4 Framework](https://github.com/jovotech/jovo-framework) will auto check your model files against a number of rules when you run the build process.

You can easily integrate this "hook" into your build process by following this documentation.

## Voice model maintenance is hard

Maintaining voice model files is hard especially when they grow and get bigger. So easily you add duplicate contents without notice or use same utterances for different intents which may later lead to strange behaviour of your application at runtime.

## How can Model Linter help?

The **Model Linter** will auto check your voice model files against a number of rules when you run the Jovo build process. While doing this the policy is to **never break a build** but to print *meaningful warnings* on the console in case something seems odd.

You may know why your are doing things as they are, so technically you can simply ignore the warnings. It is a good idea though to double check what **Model Linter** is complaining about.

## How does Model Linter look like?

**Model Linter** hooks into the build process. It remains silent if there is nothing to say. In case some rule is violated then you will see a warning message on the console. The message is intended to support you with information about where the problem is and how to maybe fix it.

An example may look as follows:

![Model Linter example output on console](https://github.com/fboerncke/jovo-v4-community-hook-model-linter/blob/main/images/model-linter-screenshot.png?raw=true)

## Why should I use the Model Linter?

It costs nothing and may save you a lot of time! For sure you have better things to do 🙂

## Is Model Linter complete?

**Definitely not**: up to now there are about ten different warning messages. Obviously you could do more. But you have to start somewhere with a project and if you like **Model Linter** then tell me and I might add more rules to the list.

## Install

The hook can be installed as a package via **[npmjs](https://www.npmjs.com/)**. For more information see here:

[![NPM](https://nodei.co/npm/jovo-v4-community-hook-model-linter.png)](https://nodei.co/npm/jovo-v4-community-hook-model-linter/)

From the console you may install the hook right into your Jovo project and save the dependency in your **package.json**:

`npm install jovo-v4-community-hook-model-linter --save`

Register the hook in:

`jovo.project.js`:

```javascript
const { ModelLinterHook } = require("jovo-v4-community-hook-model-linter");

const project = new ProjectConfig({
  hooks: {
    'before.build:platform': [ModelLinterHook],
  }, // [...]

```

`jovo.project.ts`:

```typescript
import { ModelLinterHook } from "jovo-v4-community-hook-model-linter";

const project = new ProjectConfig({
  hooks: {
    'before.build:platform': [ModelLinterHook],
  }, // [...]
```

## Further reading

When defining your voice model it is important to know and respect the rules and limitations from a target platform. Therefore the following might be wort a read:

- Alexa platform: "Rules for sample utterances":

  https://developer.amazon.com/en-US/docs/alexa/custom-skills/create-intents-utterances-and-slots.html#h3_intentref_rules



## License

Apache V2

## Acknowledgements

The code published here is part of the project "[Voice QL](https://prototypefund.de/project/voice-ql-datentabellen-mit-gesprochener-sprache-barrierefrei-erkunden/)" which receives funding from the [German Federal Ministry of Education and Research](https://www.bmbf.de/) (FKZ 01IS22S30)

[![Logo Bundesministerium für Bildung und Forschung](./images/assets/logo-bmbf.svg)](https://www.bmbf.de/)
&nbsp; &nbsp;
[![Logo Open Knowledge Foundation](./images/assets/logo-okfn.svg)](https://okfn.de)
&nbsp; &nbsp;
[![Logo Prototype Fund](./images/assets/PrototypeFund_Logo_smallest.svg)](https://prototypefund.de/)

The Prototype Fund is a project of the Open Knowledge Foundation Germany, funded by the German Federal Ministry of Education and Research (BMBF).
