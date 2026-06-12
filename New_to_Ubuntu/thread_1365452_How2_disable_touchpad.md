---
title: "How2 disable touchpad"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by webwiller on 2009-12-27
Hi there!
I'm running Ubuntu 9.10 Karmic Koala and I need to disable my touchpad which annoyes me badly while typing.

I tried SYSTEM>PREFERENCIES>MOUSE>Disable touchpad while typing

but it doesnt work properly. How is it supposed to understand I'm typing? I normally mix typing and mouse use...as everybody else I guess. MAh...

I would like to COMPLETELY disable touchpad.

Any clue geeks?

Thx in advance for your kind help and Happy New Year!

---

### Post by webwiller on 2010-01-07
bump!

---

### Post by drs305 on 2010-01-07
I have used this link to *restore* my touchpad. If you have a synaptics touchpad you may be able use the commands to *disable* it as well.

[https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig]("https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig")

---

### Post by rexh on 2010-01-07
Two things that helped me in the same situation were:
1. turn the sensitivity of the touchpad way down
2. there is program in the software center called touchfreeze that allows you to set a delay for the touchpad.

---

### Post by sandyd on 2010-01-07
gsynaptics

---

### Post by webwiller on 2010-02-03
> **carlee said:**
> gsynaptics

This is THE answer!

You could put it down a bit more described as I'm newby...but by luck I'm not so much newby...

Thx anyway!

---

### Post by Silvernail on 2010-02-04
Carlee......
You are a treasure trove of knowledge and information. Thank you. Thank you.
If you would just upload your brain, I could dig through it and not have to ask so many questions.

Thank  you
Dave

---

### Post by seaniedee on 2010-02-17
Thanks Carlee. I love simple solutions.

edit: except it seems this is only a temporary fix. Touchpad starts up again a few minutes later. I recall reading a solution a while ago, but I re-installed Ubuntu and lost the fix.

---

### Post by shawnisalk on 2010-02-27
Thank you, God!

---

### Post by rlgribble on 2010-03-16
Same question - I disable the touchpad, but it reenables itself.  I've set up gsynaptics, and run "syndaemon -i 1 -d -t -K", but it insists on being active, and when I touch it with the side of my hand, I end up typing where I don't want to be.  How can I disable this (9.10)?

---

### Post by Bladtman242 on 2010-06-13
I have the same problem as rlgribble. it keeps enabling itself (and i am not sure whether or not the chance is visible with synclient -l) I haven't tried gsynaptics, because i would prefer to use my own scripts instead.
Also it drives me INSANE that it doesn't work when there is no apparent reason why it shouldn't?

---

### Post by naveed@7vals on 2011-02-28
for my machine it  works
synclient TouchpadOff=1

---

### Post by Rodney9 on 2011-06-15
> **naveed@7vals said:**
> for my machine it  works
synclient touchpadoff=1

+1

---

### Post by inameiname on 2011-06-15
I have this in my ~/.bashrc file as a function. Works just fine for the times I need it. Could even be set a keyboard shortcut, if desired:

```

##################################################
# Touchpad stuff                               
##################################################

###### to get information on touchpad
alias touchpad_id='xinput list | grep -i touchpad'



###### to disable touchpad
# using 'touchpad_id', set the number for your touchpad (default is 12)
function touchpad_off()
{
touchpad=12
xinput set-prop $touchpad "Device Enabled" 0
}



###### to enable touchpad
# using 'touchpad_id', set the number for your touchpad (default is 12)
function touchpad_on()
{
touchpad=12
xinput set-prop $touchpad "Device Enabled" 1
}

```

---

