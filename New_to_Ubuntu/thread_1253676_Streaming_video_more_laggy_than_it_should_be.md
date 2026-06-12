---
title: "Streaming video more laggy than it should be"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by Nailbunny on 2009-08-30
...be gentle it's my first question...

i'm running Ubuntu 9.04 with some Compiz razzle dazzle, mainly set up with a friend who is much more savvy than i. It seems as though my streaming video is slower and laggier than is should be, hulu or the utube is watchable but annoyingly glitchy, even after being loaded well ahead.

I came from XP with the same set up and had no real problems. What am i missing? whats set up wrong? Video from a drive seems to be fine. 

thanks in advance
Nailbunny

---

### Post by Paqman on 2009-08-30
> **Nailbunny said:**
> hulu or the utube is watchable but annoyingly glitchy

Video from a drive seems to be fine. 


That'll be your Flash then. Are you on 32- or 64-bit, and what Flash plugin did you install? I'm assuming you're running Jaunty?

---

### Post by Nailbunny on 2009-08-30
i wish i could tell you, i know it's Jaunty or at least i remember that term being tossed around quite a bit. Sorry, very new to this... how would i go about figuring out if i'm 32 or 64 and what Flash i have?

---

### Post by Perfect Storm on 2009-08-30
> **Nailbunny said:**
> i wish i could tell you, i know it's Jaunty or at least i remember that term being tossed around quite a bit. Sorry, very new to this... how would i go about figuring out if i'm 32 or 64 and what Flash i have?

```
uname -a
```
In the terminal.

---

### Post by Nailbunny on 2009-08-30
done. what does that mean?

---

### Post by Perfect Storm on 2009-08-30
Please post the output of it. It tells which kernel you're using and if it's 32-bit or 64-bit.

---

### Post by Nailbunny on 2009-08-30
Linux nailbunny-desktop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

---

### Post by Perfect Storm on 2009-08-30
Ok, i686 is 32-bit structure.

The next thing;

In the Browsers adresse box, do;

```
about:plugins
```
Please post the list.

---

### Post by Nailbunny on 2009-08-30
seriously? it's a massive list... heres the first section for the flash

**Shockwave Flash**

 File name:  libflashplayer.so Shockwave Flash 10.0 r32   MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes   application/futuresplash FutureSplash Player spl Yes

---

### Post by Perfect Storm on 2009-08-30
or attache it in a txt file, or use the [code ] [/code ] to use as a  pleasent read. ;)
I was look for if there's any other flash apps interfering.

I read some with similiar problems some days ago. He solved it by starting a new firefox profile to use.


```
firefox -ProfileManager
```

---

### Post by Nailbunny on 2009-08-30
those things are a little past my ability/understanding right now and i am getting yelled at by my wife to get off the tubes... 

thank you for your help thus far, sorry i need to cut and run 

i will run those ideas past my savvy friend in hopes of getting it fixed 

thanks again.

---

### Post by mustava on 2009-09-03
Hi there,
I think i have the same problem a Nailbunny. I am also trying to rid myself of Billies s/w, so installed 9.04 as dual boot.
I hate to say this but youtube streaming is fine on Vista Premium (pre-installed on my Acre 5535 lappy) but is terrible on 9.04.
my s/w is:- Linux stingray 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux

and i notice that I have flash 9.0 r999 installed as an addon, tried to d/l version 10 but it tells me its for the wrong platform.

Also tried the "new profile" bit but it made no difference.

Can anyone offer me (us) some help please.
Thanx in anticipation

---

