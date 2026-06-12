---
title: "Wireless and wired not working for 10.04.4"
date: 2013-11-01
forum: Networking &amp; Wireless
---

### Post by hoangtu69 on 2013-11-01
I'm new to Ubuntu. I installed Ubuntu 10.04.4 on my HP Pavilion ZT3000 laptop.  Wireless and wired do not work.  I used to have Win XP on it and both wired and wireless worked fine.  

I installed Ubuntu using the USB stick method.

1) How do I install all the networking drivers (wired and wireless) when I don't have internet connection?
2) What drivers should I install?

Thanks

---

### Post by Hadaka on 2013-11-01
Hi, Ubuntu 10.4 is no longer supported, you might want to
consider loading Ubuntu 12.04..supported untill 2017.
good luck.

---

### Post by hoangtu69 on 2013-11-01
When I installed 12.04, it couldn't boot up from the USB because of the [COLOR=#444444][FONT=arial]**Physical Address Extension**[/FONT][/COLOR][COLOR=#444444][FONT=arial] ([/FONT][/COLOR][COLOR=#444444][FONT=arial]**PAE**[/FONT][/COLOR][COLOR=#444444][FONT=arial]) error.  I did some research and it said to install previous versions and then update it using the normal way after installation.


[/FONT][/COLOR]

---

### Post by Hadaka on 2013-11-01
please post the output of..
```
lspci -nn | egrep '0200|0280'
```
all you need to post is the [14e4:XXXX] numbers.
also..just to see if it might activate your wireless
please do..
```
sudo modprobe -v ipw2200
```
thanks

---

### Post by mörgæs on 2013-11-01
A fresh install of 12.04 is still your best option, but go for Xubuntu and not Ubuntu.

---

### Post by hoangtu69 on 2013-11-01
It looks like the modprobe command works.  Thanks.  Wireless is working now.

I'll install 12.04 on a dell latitude D610 next. The dell did not have issue with PAE so I can use 12.04.   The last time I did it , wireless did not work either. 

Do I issue the same modprobe command on the dell?

---

### Post by Hadaka on 2013-11-01
Hi,glad the wireles side is working ! You may want to
consider reloading that machine with Xubuntu as mortgaes suggested.
and no, it wont be the same command for the dell 610, more than likely
the dell will have broadcom cards. Post back if you have any problems
and we will guide you through,
thanks.

---

### Post by hoangtu69 on 2013-11-02
Ok. I'll reinstall the HP machine using 12.04 xubuntu.  Thanks

Can I ask why xubuntu instead of Ubuntu?  Is it because of the networking and PAE issues I had with the HP machine?

---

### Post by Hadaka on 2013-11-02
Yes, the PAE issue. I have not delt with pae issues before,
perhaps Morgaes will jump in and offer a better explination than
I would be abe to give.

---

### Post by mörgæs on 2013-11-02
Here's a guide I wrote on [PAE]("https://help.ubuntu.com/community/PAE") which might come in handy if one wants to get Lubuntu 13.10.

Ubuntu requires PAE capability from 12.04 but Xubuntu from 12.10 meaning that Xubuntu 12.04 LTS is an option through april 2015. 

Bodhi Linux is also worth considering.

---

### Post by hoangtu69 on 2013-11-02
Thanks for the explanation. The dell latitude D610 is the main computer that I want to install on and it does not have issue with PAE. I only use the HP pavilion machine to test it out first.

The last time I installed Ubuntu 12.04 on the dell, I did not have wireless either. What command should I run after I install Ubuntu to find out the correct networking card please?  I'll post back the result so you can tell me the correct command to activate wireless like you did with the HP machine.

---

### Post by Hadaka on 2013-11-02
Hi, Dell uses several different wireless cards, The wired
ethernet however "should" just work. To determine what
driver you need. Please post the output of..
```
lspci -nnk | grep -iA3 net
```
thanks.

---

### Post by hoangtu69 on 2013-11-03
Thanks. I'll post back the result.  One question,  Below is what I'm using the computer for

1) Watch movies online with firefox and flash
2) Play video using VLC

So speed and performance are what's important to me.  My dell laptop is very old (2005), max 2Gig of RAM. Do you still recommend me to install the latest 12.04 ubuntu release or if there's a smaller footprint ubuntu derivative that i can install?

---

### Post by mörgæs on 2013-11-03
I would not call a 610 very old. It will be fine with Lubuntu 13.10.

---

### Post by hoangtu69 on 2013-11-03
Ok thanks.  I'll install Lubuntu 13.10 instead of Ubuntu 12.04.

---

### Post by mörgæs on 2013-11-03
If this solves your problem(s) please mark the thread so.

---

### Post by hoangtu69 on 2013-11-03
I opened a new thread called [Unable to upgrade from 10.10 to 13.10]("http://ubuntuforums.org/showthread.php?t=2185663") for lubuntu under installation and upgrade.  After I solve that issue then I'll come back here and post the result of the wireless issue I'm having.

---

