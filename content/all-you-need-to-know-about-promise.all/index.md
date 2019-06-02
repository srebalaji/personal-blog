---
title: "All you need to know about Promise.all"
description: "Promise.all is a promise that resolves when all the promises passed as an array get resolves. Implementing Promise.all in JavaScript helps to do concurrent operations. Learn Promise all with example."
date: "2019-04-05T20:47:50.518Z"
categories: 
  - JavaScript
  - Software Development
  - Nodejs
  - Web Development
  - Technology

published: true
canonicalLink: https://medium.com/free-code-camp/promise-all-in-javascript-with-example-6c8c5aea3e32
---

![Promise all in JavaScript](./asset-1.jpeg)

Promises in JavaScript are one of the powerful APIs that help us to do Async operations.

Promise.all takes Async operations to the next new level as it helps you to aggregate a group of promises.

In other words, I can say that it helps you to do concurrent operations (sometimes for free).

#### Prerequisites:

You have to know what is a **Promise** in JavaScript.

#### What is Promise.all?

Promise.all is actually a function that takes an array of promises as an input (an iterable) and returns a Promise. Then it gets resolved when all the promises get resolved or any one of them gets rejected.

For example, assume that you have ten promises (Async operation to perform a network call or a database connection). You have to know when all the promises get resolved or you have to wait till all the promises resolve. So you are passing all ten promises to Promise.all. Then, Promise.all itself as a promise will get resolved once all the ten promises get resolved or any of the ten promises get rejected with an error.

**Let’s see it in code:**

```
Promise.all([Promise1, Promise2, Promise3])
 .then(result) => {
   console.log(result)
 })
 .catch(error => console.log(`Error in promises ${error}`))
```

As you can see, we are passing an array to Promise.all. And when all three promises get resolved, Promise.all resolves and the output is consoled.

**Let’s see an example:**

Simple example explaining how Promise.all works

In the above example, Promise.all resolves after 2000 ms and the output is consoled as an array.

One interesting thing about Promise.all is that the order of the promises is maintained. The first promise in the array will get resolved to the first element of the output array, the second promise will be a second element in the output array and so on.

**Let’s see another example:**

Explaining how an array of promises can be used effectively in Promise.all

From the above example, it’s clear that Promise.all waits till all the promises resolve.

Let’s see what happens if any one of the promises are rejected.

Explains how Promise.all behaves if one of the promises got rejected.

As you can see, if one of the promises fails, then all the rest of the promises fail. Then Promise.all gets rejected.

For some use cases, you don’t need that. You need to execute all the promises even if some have failed, or maybe you can handle the failed promises later.

Let’s see how to handle that.

<Embed src="https://gist.github.com/srebalaji/33dec6051fa03675ef91233a401a6a2f.js" aspectRatio={0.357} />

#### Use cases of Promise.all

Assume that you have to perform a huge number of Async operations like sending bulk marketing emails to thousands of users.

Simple pseudo code would be:

```
for (let i=0;i<50000; i += 1) {
 sendMailForUser(user[i]) // Async operation to send a email
}
```

The above example is straightforward. But it’s not very performant. The stack will become too heavy and at one point of time, JavaScript will have a huge number of open HTTP connection which may kill the server.

A simple performant approach would be to do it in batches. Take first 500 users, trigger the mail and wait till all the HTTP connections are closed. And then take the next batch to process it and so on.

Let’s see an example:

<Embed src="https://gist.github.com/srebalaji/8b3ad7f068ff9771b98d903506649b19.js" aspectRatio={0.357} />

Let’s consider another scenario: You have to build an API that gets information from multiple third-party APIs and aggregates all the responses from the APIs.

Promise.all is the perfect way of doing that. Let’s see how.

<Embed src="https://gist.github.com/srebalaji/d904979f74a933bac189a189a3088dae.js" aspectRatio={0.357} />

To conclude, Promise.all is the best way to aggregate a group of promises to a single promise. This is one of the ways of achieving concurrency in JavaScript.

Hope you liked this article. If you did, please clap and share it.

Even if you didn’t, that’s fine you can do it anyway :P