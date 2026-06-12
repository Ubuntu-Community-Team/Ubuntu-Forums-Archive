---
title: "I have no idea what I am doing .."
date: 2009-01-23
forum: New to Ubuntu
---

### Post by Chainesaw on 2009-01-23
So I decided to install Ubuntu 8.10 on a clean partition (200gb) I installed it from inside windows,(Vista) everything installs fine. I reboot, update the 224 available packages, reboot. Everything is fine. I updated the graphics drivers (Nvidia) to the recommended ones (177 I believe) and now when it boots, it just puts me at a command prompt - Ubuntu login:

I enter my user name and password, and I get Joe@ubuntu: ~$ 

I have no idea what the hell I'm supposed to do now, or why it's not booting into the GUI. 

I've reinstalled it twice now, and I get the same issue. I've gone into the "recovery" mode, and still don't get any different results. 

What am I missing? :(

---

### Post by diablo75 on 2009-01-23
Well for starts I wouldn't have used the Wubi installer to put Ubuntu on a fresh partition.  I would have just booted off that CD and used the native Ubuntu Live CD based installer... but that aside.

Something you can try to do is, at a command prompt type:

sudo dpkg-reconfigure xserver-xorg

Answer all the questions to the best of your ability.  There are many you won't know the answer to (and you can just ignore them/leave their answer's blank).  When you get to the one about using the kernel as a buffer, pick "No".

Then restart the computer from the command prompt by typing "init 6" with no quotes and press enter.

Hopefully that'll clear things up.  If it doesn't, I'd use your Windows Control Panel>Add/Remove Programs to uninstall Ubuntu via Wubi and install using the traditional method.  Here's a video tutorial on how to do that:

[http://video.google.com/videoplay?docid=-2369893842637434537&ei=EWx5SdHdJJTuqAKd3uGrBQ&q=how+to+install+ubuntu+linux+alan+pope&hl=en](http://video.google.com/videoplay?docid=-2369893842637434537&ei=EWx5SdHdJJTuqAKd3uGrBQ&q=how+to+install+ubuntu+linux+alan+pope&hl=en)

---

### Post by hyper_ch on 2009-01-23
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by bailbath on 2009-01-23
Can you tell us your hardware?
Ian

---

