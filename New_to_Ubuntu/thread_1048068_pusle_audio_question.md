---
title: "pusle audio question"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by 5dollafootlong on 2009-01-23
im thinking of unistalling pulse audio because some wine apps 
dont play nice with it like out going mic functions in vent. I have
unistalled it in the past and that fixed my problems. But my question
is if I remove it will I be losing audio quality or functionality im 
confused as to what it actually does.

thanks

---

### Post by halovivek on 2009-01-23
You can use Alsa instead of the pulse audio. I had the same problem with the computer and i have removed the pulse audio and installed ALSA. it is working fine now and sound also really good.

---

### Post by Hoaxe on 2009-01-23
hi,

please don't un-install pulse audio. if you do something ELSE might not work. To address your specific problem, I suggest using these commands:

```
killall pulseaudio
```

this will kill pulse audio and from there you will have to pipe your sound through alsa.

when you're done, you can re start pulse audio with this command:

```
pulseaudio
```

further more, 
use skype or teamspeak since they have extremely well performing native binaries/packages for ubuntu.

I suggest you write 2 bash scripts for your kill and start commands, so you don't have to remember them, and so you can engage the commands with a click by putting the scripts in your applications menu or even in straight in your quick bar. This is also a good chance to learn bash scripting and experience the better and more refined features of a linux system

good luck and
kthxbai:KS

---

