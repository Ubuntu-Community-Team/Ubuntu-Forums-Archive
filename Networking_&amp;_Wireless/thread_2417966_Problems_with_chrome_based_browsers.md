---
title: "Problems with chrome based browsers"
date: 2019-04-29
forum: Networking &amp; Wireless
---

### Post by dolios on 2019-04-29
Hi. Chrome based browsers always stops working for me after a while on  ubuntu. The pages takes forever to load and just times out. Other  browsers work just fine though

---

### Post by Rubi1200 on 2019-04-30
Hi,

what version of Ubuntu are you using? What Chrome based browsers are you using? Are you on a wired or wireless connection?

---

### Post by dolios on 2019-04-30
I am using Ubuntu 16 desktop. For chrome I am using: Google Chrome, Opera, Chromium and Blisk. None of them work.

---

### Post by Rubi1200 on 2019-04-30
A couple of things to try:

1. temporarily disable any extensions or addons you are using to see if the problem persists

2. go to Settings and then Advanced >> System and turn off hardware acceleration (this is for Google Chrome but should be fairly similar in the other ones) [https://prnt.sc/nijfka](https://prnt.sc/nijfka)

---

### Post by dolios on 2019-04-30
> **Rubi1200 said:**
> A couple of things to try:

1. temporarily disable any extensions or addons you are using to see if the problem persists

2. go to Settings and then Advanced >> System and turn off hardware acceleration (this is for Google Chrome but should be fairly similar in the other ones) [https://prnt.sc/nijfka](https://prnt.sc/nijfka)

I tried to remove all extensions. And what I meant with when I said that it stops working after a while is that this has happend before on other installations. It is usually fine for a couple of months, and then just like that it becomes extreamly slow like 30seconds per website and then it just breaks. I have tried to clear cache etc with no success.

---

### Post by Rubi1200 on 2019-04-30
I don't use Chrome or Chrome based browsers on Linux so am not sure what you can try next other than perhaps purge and then reinstall one of the browsers and see if that helps.

---

### Post by dolios on 2019-04-30
I did try and reinstall them, nothing. The only thing that does help is to create a new account/user in ubuntu and switch to it.

---

### Post by Rubi1200 on 2019-04-30
That is interesting. It would suggest there is somehow something corrupted in the main account that is slowing the browsers down.

Have you checked or changed DNS settings? Perhaps try another DNS service like Google's 8.8.8.8

---

### Post by dolios on 2019-04-30
The DNS service on both accounts. I am not sure what it is but maybe there is something that is getting corrupted overtime in the usercache?

---

### Post by deadflowr on 2019-04-30
> **dolios said:**
> I did try and reinstall them, nothing. The only thing that does help is to create a new account/user in ubuntu and switch to it.

Removal of programs doesn't remove the user's profile settings for said programs, so the old profile settings remained unless you manually removed those as well.
Chrome's profile settings are in ~/.config/google-chrome. (In Files it's a hidden folder so you need to enable show hidden files/folders; easy with a keyboard shortcut ctrl + H)

What you can also do is rename the current setting folder to something like google-chrome-old, which will force chrome to create a new clean profile setting,
which you can then run to see if the original profile had an issue.

---

### Post by Rubi1200 on 2019-04-30
This is specifically for Google Chrome:
[https://www.bleepingcomputer.com/tutorials/how-to-reset-the-chrome-browser-back-to-its-default-settings/](https://www.bleepingcomputer.com/tutorials/how-to-reset-the-chrome-browser-back-to-its-default-settings/)

Would try this first to see if it helps.

Note: just saw the post from deadflowr and would suggest you try that first.

---

