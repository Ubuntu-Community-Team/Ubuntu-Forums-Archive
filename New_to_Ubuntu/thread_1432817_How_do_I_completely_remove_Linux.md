---
title: "How do I completely remove Linux?"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by johnpap on 2010-03-18
Ok this is funny and tragic at the same time...
I installed Ubuntu on my pc at work, for obvious reasons.. it's light, fast, solid and virus free... but I have an employer who is a right dick and wants it removed because.... he is a dick... he doesn't even know what an operating system is.. 
So I got XP still on and that's fine... but I need the operating system option to go away when I turn the pc on...  or make it somehow go by default to windows instead of Linux... 
Any ideas how to do that... either completely remove Ubuntu or change the default operating system on start up?

Thanks in advance

John...

---

### Post by philinux on 2010-03-18
Install startupmanger. Run it from sys>admin and choose the default os. Change the timeout to say 3 seconds.

---

### Post by slakkie on 2010-03-18
What Ubuntu version are you running? You can configure grub to load Windows and to hide itself and select the default within 2/3 seconds so most users won't notice it.

For grub-legacy (pre-karmic):

sudo vi /boot/grub/menu.lst

```

# Windows is the default in this example
default         1
timeout         2
hiddenmenu

title Your Linux thing
root (hd0,1)
chainloader +1

title Your Windows thing
root (hd0,2)
chainloader +1

```


The example is making use of chainloading, you might want to change that to your current settings.

---

### Post by johnpap on 2010-03-18
Ok I used the "start up manager"...it's a ridiculously  easy tool and it only took a few seconds... I am actually now on windows.... and it feels wrong.... it's like ... being not at work but in the Alien Queen egg chamber in "Aliens"... and using my computer.... and guess what?.... I just got an error message..... lol...!

---

### Post by Calash on 2010-03-18
I am waiting to get yelled at myself.  Just loaded Ubuntu X64 on my work PC last week.  Setup a virtualbox session to run my Windows Desktop along with a virtual test box.

That should make for an interesting entry in the asset management software :)

---

