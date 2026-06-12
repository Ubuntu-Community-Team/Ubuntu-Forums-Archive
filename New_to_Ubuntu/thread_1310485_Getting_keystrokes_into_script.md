---
title: "Getting keystrokes into script"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by wideyes on 2009-11-01
Hello all. I'm trying to get the nice little utility 'tilda' to start on my bootup in the background. I've activated it via the gnome startup applications menu, but it's a bit annoying to have the program launch front and center every time I log on. I've tried appending an '&' in the command to run it in the background. The problem here is that, when I do this, it seems to be so 'in the background' that it doesn't respond to my summon key to pull it up. Is there a way I can put a command in a startup script that basically says "run tilda, then hit the F10 key to hide it"? Or is there a better way to do this that I'm missing? Even if there is, I'd be curious to see how one gets an F key or some other cool character into a script :)

---

### Post by peculiar penguin on 2009-11-01
Doesn't it have a command line switch to autohide on startup or something? Check the docs.

Or use Guake instead :P

---

### Post by wideyes on 2009-11-01
Nice one! Missed that option the first time around. It now behaves how I want it to. Thanks for that. I tried using guake, but on my eeepc the text was all @#$%ed up. I actually find tilda to be very well implemented.

My other question still stands, though: how does one get keystrokes into shell script? I've read a bit about ASCII characters and am thoroughly confused. Anybody feel like giving a n00b a clarification?

---

