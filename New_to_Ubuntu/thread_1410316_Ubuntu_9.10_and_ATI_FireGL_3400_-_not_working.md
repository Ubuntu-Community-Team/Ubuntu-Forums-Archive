---
title: "Ubuntu 9.10 and ATI FireGL 3400 - not working"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by anigodin on 2010-02-18
Hello people,

I have a dual core 1.6 with an onboard graphic card of intel (the board is Intel).
Untill a couple of weeks ago I was working on ubuntu 8.04 LTS. after some problems with the avanat dock after one upgrade, I decided to updrage the all system to the latest version. so I upgraded to ubuntu 9.10. 
Then I found out, that for some reason, the special visual effects wont work no matter what I do. after reading about it abit here I understood the my OB graphic card cant show effects when running 9.10. (which is funny becuse on 8.04 LTS I had mac4lin with compiz and all)
So I decided to upgrade my graphic card. a friend gave me am ATI FireGL v3400 (with dual dvi connections). when I restarted the computer I got many messages and finally 'done' and that's it. 
I also have windows on this computer and it works fine with this card. 
I tried several things that might solve this problem. most of it from a root shell since linux just wont start the X session.
Today I took out the ATI card in order to try and install the ATI drivers from the x-session.
synaptic told me I have two borken ati drivers and removed them. then I tried to install the fglrx driver from synaptic. after it was installed I pluged the ATI card back again but still nothing..

I tried to use ati linux driver versions 9.10 and 9.12

Any idea how can I solve this or should I just toss this card away and get an nVidia card (which I have on my Mythbuntu machine and works great)?

---

### Post by markbuntu on 2010-02-18
Try this, the latest driver for that card is 9.4 which you can get from the ati web site which there is a link to in here and directions for properly removing old drivers and getting back to square one to try again.

[http://ubuntuforums.org/showthread.php?t=1409467](http://ubuntuforums.org/showthread.php?t=1409467)

---

### Post by halitech on 2010-02-18
actually the last ATI driver that ATI provided was 8.583 which does not work with 9.04 so installing the driver will more then likely break your system. Either drop back to 8.04 where ATI support is better or go for an Nvidia

---

### Post by anigodin on 2010-02-19
> **markbuntu said:**
> Try this, the latest driver for that card is 9.4 which you can get from the ati web site which there is a link to in here and directions for properly removing old drivers and getting back to square one to try again.

[http://ubuntuforums.org/showthread.php?t=1409467](http://ubuntuforums.org/showthread.php?t=1409467)


I tried what you suggested but it didnt work.
I keep getting the same blank screen with lots of text on it.

I'm going to toss this card away and get something else.

Thank you anyway. :-)

---

