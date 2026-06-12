---
title: "SPSS on lucid lynx 10.04"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by filipe.a.pinto on 2010-07-15
Hi there.
I have Ubuntu Netbook Edition 10.04 on my Acer Aspire One.
I also got SPSS for linux v16.0. I know I'm on a netbook, but SPSS says it meets the requirements..
I've installed it, with no problems at all, but I can't seem to run it.
It asks for this libstdc++.so.5 and I don't seem to have it or to be able to install it.
Anyhow, I have the libstdc++6 installed, so I don't know why it doesn't work..
Was anyone successful in running SPSS16 for Linux?

---

### Post by bodhi.zazen on 2010-07-15
I highly suggest you post on the SPSS mailing list or support forms.

Debian 4.0 and RHEL are listed as supported OS ...

You could try installing Debian Etch (4.0)

[http://www.debian.org/releases/etch/](http://www.debian.org/releases/etch/)

On the support page they claim :

> NOTE: [COLOR=#cc0000]A blank cell below signifies NO support.  In addition, if a certain platform that you are interested in is NOT  listed, then it is NOT supported.[/COLOR][COLOR=#cc0000]

[/COLOR]With that in mind, try Debian Etch ...

---

### Post by filipe.a.pinto on 2010-07-15
Hi bodhi.zazen.
Thanks for the quick reply.
What about running SPSS on Wine or a virtual machine?
BTW - Why not Debian 5.0?

---

### Post by filipe.a.pinto on 2010-07-15
I'll check out those forums and mailing lists..
Moving to Debian is out of the freaking question!!
It's very complicated to install..

---

### Post by k3lt01 on 2010-07-16
Have you thought about using PSPP instead of SPSS? PSPP is in the repositories.

---

### Post by bodhi.zazen on 2010-07-16
> **filipe.a.pinto said:**
> Hi bodhi.zazen.
Thanks for the quick reply.
What about running SPSS on Wine or a virtual machine?
BTW - Why not Debian 5.0?

I tried SPSS in wine many years ago, it did not work.

Wine has come a long ways, it may be worth a try.

Debian 5.0 is not supported (according to the page I looked at).

You may be interested in this :

[http://www.gnu.org/software/pspp/](http://www.gnu.org/software/pspp/)

> PSPP is a program for statistical analysis of sampled data. It is a  Free replacement for the proprietary program SPSS, and appears very  similar to it with a few exceptions.Even better, it is in the repositories

[http://packages.ubuntu.com/lucid/pspp](http://packages.ubuntu.com/lucid/pspp)

Edit: See [k3lt01]("http://ubuntuforums.org/member.php?u=397303") 's post.

Edit 2 : There is also this :

[http://bas-r.nl/?p=10](http://bas-r.nl/?p=10)

Seems it may work in Ubuntu 9.10 (Ah Karmic, my favorite release).

---

### Post by bodhi.zazen on 2010-07-16
> **filipe.a.pinto said:**
> I'll check out those forums and mailing lists..
Moving to Debian is out of the freaking question!!
It's very complicated to install..

def - ***Ubuntu*** : An ancient African word for "can't install Debian".

:lolflag:

If you have been using Ubuntu for a while, Debian is not (usually) too bad. Try one of the Debian Live CD or (personally) I prefer the net install.

---

### Post by filipe.a.pinto on 2010-07-16
I'll have a look at PSPP.
I've tried a netinstall.. I managed, after a long time to create the USB flash drive, remember, I'm on a Aspire One. But then the install didn't recognize either my wlan or my lan connection. I wasn't able to install the firmware, and I don't even know if my ethernet card was supported in the firmware releases..
It was about 5a.m. when I went to bed, and thought OK - if I haven't managed to install Debian than maybe it's not for me..
Anyhow.. I'll keep on trying to install the missing packages to get SPSS running..

---

### Post by filipe.a.pinto on 2010-07-16
I think I solved it..
Thanks for the link bodhi.zazen. The solution was in here [http://bas-r.nl/?p=10](http://bas-r.nl/?p=10)

I justed installed libstdc++5 and it's dependencies and it worked..
Couldn't install it through the console though.. It didn't find the package!
Well.. Time to work now! Thanks guys!!

---

### Post by bodhi.zazen on 2010-07-16
> **filipe.a.pinto said:**
> I think I solved it..
Thanks for the link bodhi.zazen. The solution was in here [http://bas-r.nl/?p=10](http://bas-r.nl/?p=10)

I justed installed libstdc++5 and it's dependencies and it worked..
Couldn't install it through the console though.. It didn't find the package!
Well.. Time to work now! Thanks guys!!

w00t !!!

---

### Post by anthony2010 on 2012-01-01
PSPP does the job for most simple statistical analyses but not more complex ones. Also many educational institutions teach stats on spss and competency on spss is a requirement of examining bodies. 

I for one refuse to allow anything other than Ubuntu or a derivative if Ubuntu on my machines. To do my stats therefore, I have to use Institution computers running windows. It would be useful to a lot of people to crack this problem.

Ant.

---

### Post by Benic on 2012-03-05
> **anthony2010 said:**
> PSPP does the job for most simple statistical analyses but not more complex ones. Also many educational institutions teach stats on spss and competency on spss is a requirement of examining bodies. 

I for one refuse to allow anything other than Ubuntu or a derivative if Ubuntu on my machines. To do my stats therefore, I have to use Institution computers running windows. It would be useful to a lot of people to crack this problem.

Ant.

Even if they are not free, SPSS and Stata have java-based versions that work with Windows, Mac or Linux. I use Stata frequently on my Ubuntu home computer and it's the same old thing as I have back in lab computers. I've tried to migrate to R, but it's like learning a new language. I do some complex things with R, but the learning curve is way too steep for me.

Anyway SPSS is trying to migrate into the business research and puts less and less focus on academic research, so I wouldn't be surprised if universities stop using it at some point in the future.

---

