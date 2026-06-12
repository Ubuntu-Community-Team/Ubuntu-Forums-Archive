---
title: "Sound Card Problem"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by PR_FM on 2009-06-02
Hi,
I've got "hp pavilion dv4-1070" & i have a problem with my sound card , when ubuntu boots & i want to login , there's some noise & it continues about 2 or 3 min after logging in , then i don't have any sound in ubuntu :(
please help me ,

---

### Post by khelben1979 on 2009-06-02
```
sudo apt-get install alsamixergui
```
installs [AlsaMixer]("http://en.wikipedia.org/wiki/Alsamixer")GUI where you have the possibility to check your sound channels. Then raise the volume meters if they aren't already on top.

---

### Post by PR_FM on 2009-06-03
> **khelben1979 said:**
> ```
sudo apt-get install alsamixergui
```installs [AlsaMixer]("http://en.wikipedia.org/wiki/Alsamixer")GUI where you have the possibility to check your sound channels. Then raise the volume meters if they aren't already on top.
i think i have the alsamixer , & the sounds are at top but i still don't have any sound !
some of my friend said that the noise in the login zone is the sound of ubuntu but for me that sound repeats & hangs even after i logged in !
maybe ubuntu douse'nt recognize my sound card !! how should i check that !?

---

### Post by PR_FM on 2009-06-03
> **khelben1979 said:**
> ```
sudo apt-get install alsamixergui
```installs [AlsaMixer]("http://en.wikipedia.org/wiki/Alsamixer")GUI where you have the possibility to check your sound channels. Then raise the volume meters if they aren't already on top.
during the installation :
dpkg: status database area is locked by another process
E: Sub-process /usr/bin/dpkg returned an error code

---

### Post by khelben1979 on 2009-06-03
> **PR_FM said:**
> during the installation :
dpkg: status database area is locked by another process
E: Sub-process /usr/bin/dpkg returned an error code

That would indicate that you have a install program active already. It could be synaptic or some other installer application. Close it first before you proceed.

Have you tried with mute/unmute the sound inside the sound settings application?

---

### Post by PR_FM on 2009-06-04
> **khelben1979 said:**
> That would indicate that you have a install program active already. It could be synaptic or some other installer application. Close it first before you proceed.

Have you tried with mute/unmute the sound inside the sound settings application?
yes , that does'nt work too :(
maybe my problem related with hp !?!? because my friend who has hp tablet had this problem , he said i should export my sound card but he did'nt remember how ! you have any idea what's he talking about !?

---

### Post by Favux on 2009-06-04
Hi PR_FM,

The following in a terminal:
```
aplay -l
```
should tell you what sound card you have.

---

### Post by PR_FM on 2009-06-04
> **Favux said:**
> Hi PR_FM,

The following in a terminal:
```
aplay -l
```should tell you what sound card you have.
the result:
```
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
Subdevice : 0/1
Subdevice #0: subdevice #0
```

now what should i do !?

---

### Post by Favux on 2009-06-04
Hi PR_FM,

I forgot to ask what version of Ubuntu you're using.  Is it Jaunty (9.04)?  I'm not a sound guru so I'm hoping someone with your card and version of Ubuntu can help you.  There are a few things we could try that are "straightforward".  But after that it can get complicated and you'd have to be pretty persistent to figure things out from the info. dump I would end up delivering.  So I'd rather try to avoid that.

---

### Post by PR_FM on 2009-06-05
> **Favux said:**
> Hi PR_FM,

I forgot to ask what version of Ubuntu you're using.  Is it Jaunty (9.04)?  I'm not a sound guru so I'm hoping someone with your card and version of Ubuntu can help you.  There are a few things we could try that are "straightforward".  But after that it can get complicated and you'd have to be pretty persistent to figure things out from the info. dump I would end up delivering.  So I'd rather try to avoid that.
thanks , yes i'm using jaunty

---

