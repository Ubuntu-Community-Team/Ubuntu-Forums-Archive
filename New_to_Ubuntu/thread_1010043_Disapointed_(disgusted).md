---
title: "Disapointed (disgusted)"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by cypher000 on 2008-12-13
Hi Guy's. Got my free Ubuntu 8.10 CD a couple of weeks ago and ever since then, in spite of hoping upon hope, the thing aint booted yet.

Hoped it would boot the live CD but all I get is the following.

ISOLINUX 3.65. Debian-2008-07-15.Copyright 1994-2008. H.Peter. Anvin.
Loading.......

Here it all ends untill I eventually stop the whole thing and try another reboot and another and another............Well where do I go from here?:lolflag:

---

### Post by jakupl on 2008-12-13
what are your computer specs? What computer are you on?

---

### Post by jakupl on 2008-12-13
I read your other posts and figured that you are running a Dell Optiplex 260.

this is probably your solution:
[https://bugs.launchpad.net/ubuntu/+bug/293747](https://bugs.launchpad.net/ubuntu/+bug/293747)

> boot in rescue mode
select root shell prompt
```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
```
resume normal boot

[And a link to boot in rescue mode]("http://psychocats.net/ubuntu/fixsudo#recoverymode")

---

### Post by jakupl on 2008-12-13
This will only be helpful if you allready installed ubuntu. If you cannot even install it, goto [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") and download the alternate install disc.

---

### Post by cypher000 on 2008-12-13
Many thanks Jacup for the help given. At last I can get to grips with Ubuntu. What a great forum and what super members. Thanks again. Walt

---

### Post by jakupl on 2008-12-13
> **cypher000 said:**
> Many thanks Jacup for the help given. At last I can get to grips with Ubuntu. What a great forum and what super members. Thanks again. Walt

Yeah, I love these forums also, I have gotten unbelievably much help here. As you see. I have more thanks than thanked. I know of no forum with so much activity.
Please tell us if it worked or not. If it did, then please mark the thread as solved. (you will find it under "thread tools" at the top), All the best. jakupl

---

### Post by Kellemora on 2008-12-13
Hi Cypher000

My son picked up a used DellOptiPlexGX270 a couple of days ago and we installed the latest stable LTS version of Ubuntu called Hardy on it no sweat, including installing Compiz-Fusion.
Since then he's installed all kinds of things and (knock on simulated woodgrain) has not found a single problem yet.  (Wish I could say the same for my installations, hi hi).

I have no idea what the difference between a GX260 and GX270 is as I've never owned either.

But I was thinking, if you are having problems with 8.10, you may want to give the stable LTS 8.04 version a try.  Besides, it will still be supported for at least 6 months after 8.10 dies.

Good Luck

TTUL
Gary

---

### Post by sneeks on 2008-12-13
> **Kellemora said:**
> Hi Cypher000

My son picked up a used DellOptiPlexGX270 a couple of days ago and we installed the latest stable LTS version of Ubuntu called Hardy on it no sweat, including installing Compiz-Fusion.
Since then he's installed all kinds of things and (knock on simulated woodgrain) has not found a single problem yet.  (Wish I could say the same for my installations, hi hi).

I have no idea what the difference between a GX260 and GX270 is as I've never owned either.

But I was thinking, if you are having problems with 8.10, you may want to give the stable LTS 8.04 version a try.  Besides, it will still be supported for at least 6 months after 8.10 dies.

Good Luck

TTUL
Gary

as above,try the stable version first..

---

