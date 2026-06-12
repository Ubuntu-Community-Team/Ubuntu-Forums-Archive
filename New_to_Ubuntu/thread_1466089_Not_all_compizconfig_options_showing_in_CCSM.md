---
title: "Not all compizconfig options showing in CCSM"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by thejakeman on 2010-04-30
When I fresh installed 10.04 today and installed CompizConfig Settings Manager I noticed that I was missing a lot of options such as Animations Add-on and 3D windows (the thing that makes the windows elevated when you go into the cube mode). How can I get these settings back?

Thanks in advance!

---

### Post by akand074 on 2010-04-30
```
sudo apt-get install compiz-fusion-plugins-extra
```

Problem solved =)

---

### Post by thejakeman on 2010-04-30
You... are a god. How do people learn these things??

---

### Post by akand074 on 2010-04-30
> **thejakeman said:**
> You... are a god. How do people learn these things??

By accident. You learn as you go, I had the same issue one time and searched through the software in the repositories to find it. Generally, in these forums people can only answer what they've experienced themselves. You'll get the hang of everything soon and will be able to quickly troubleshoot yourself knowing where to look.

Good luck !

---

### Post by banyanbraid on 2010-07-31
hey i'm having this same problem. except when i type in the code u gave me in the terminal and press enter, it prompts me for my password as usual, but my keyboard becomes unresponsive. I installed these extra plugins through synaptic package manager, but it doesnt seem like my problem is fixed. any thoughts?

---

### Post by Nick_Jinn on 2010-07-31
Subscribes.

---

### Post by thejakeman on 2010-07-31
> **banyanbraid said:**
> hey i'm having this same problem. except when i type in the code u gave me in the terminal and press enter, it prompts me for my password as usual, but my keyboard becomes unresponsive. I installed these extra plugins through synaptic package manager, but it doesnt seem like my problem is fixed. any thoughts?

The reason your password isn't showing up when you type it is because it's not echoing. It's simply a security measure, instead of showing asterisks it simply doesn't display anything. It's still accepting the keystrokes but they're hidden.

---

