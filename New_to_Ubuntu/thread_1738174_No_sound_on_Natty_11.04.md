---
title: "No sound on Natty 11.04"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by hunter99507 on 2011-04-24
It seems like 1 out of every 5 times I log into Natty i dont get sound.  My sound is not mutted and it seems its detected.  Also sometimes I have this issue in 10.10 as well but 10.04 and below it works fine.  Any sugesstions on fixing this?


```
ubuntu@Ubuntu1104:~$ sudo aplay -l
[sudo] password for ubuntu: 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ubuntu@Ubuntu1104:~$ 

```

---

### Post by ESDEEM on 2011-04-24
try these following commands on terminal.....
>  sudo apt-get install alsa-oss
>  sudo apt-get install libasound2
>  sudo apt-get install libasound2-plugins
>  sudo apt-get install sysv-rc-conf

---

### Post by Hedgehog1 on 2011-04-24
Are you wanting the sound to be output using the HDMI cable? Or the sound card?

***The Hedge***

:KS

---

### Post by hunter99507 on 2011-04-24
I want the sound from the computers speakers.

---

### Post by hunter99507 on 2011-04-24
Also I did ESDEEM's codes and the sound still doesnt work.  Any other suggestions?

---

### Post by KegHead on 2011-04-24
Hi!

You could try:

system..preferences..sound.

There area number of parameters there.

KegHead

---

### Post by mastablasta on 2011-04-24
use 10.04 then if it works.

---

### Post by hunter99507 on 2011-04-24
I looked into Kegheads suggestion and everything I see looks fine.  It seems weird becuase once i restart the computer it works just fine, and probably after i load ubuntu another 10 times it will happen again.

As far as mastablasta suggestion, with all due respect I dont believe that is a good answer. I think its a bug in ubuntu and should be addressed.  If you search google for this topic their are tons of people having these same issues, although none of those solutions I read on google helped me.  

I guess I hope somebody will help provide a solution.

Thank you

---

### Post by KegHead on 2011-04-24
Hi!

A guess;

Have you installed "extras"?

KegHead

---

