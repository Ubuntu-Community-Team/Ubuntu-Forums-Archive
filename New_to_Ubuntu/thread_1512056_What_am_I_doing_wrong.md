---
title: "What am I doing wrong?"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by fcruz2489 on 2010-06-17
so i have been using ubuntu for a few months on my desktop in a vm as an ssh server and to expand my knowledge of OSs. i have done alot of reading and learned alot of stuff online but thats besides the point. as i said i was using ubuntu in a vm on my i7 860 with 1 cpu core with 2 threads and 2gb of memory dedicated to it. but it wastes too much power so i decided to get a net top.

i purcahse a foxconn nettop with a intel attom a330 dual core 1.6ghz processor, nvidia ion gpu (256mb shared mem), and 1gb ddr2 667 (256mb going to vid card) 

i installed ubuntu 10.04 32bit on it and it seems sooooo slow. it takes AT LEAST 5 seconds to open up a simple program like firefox. and when i click on the menus it takes time for the little icons to show up. i know my desktop is faster than the net top but i didnt think it'd be like this. i installed the "restricted" nvidia drivers and i have all the latest updates installed and there are no startup programs other than docky. does anyone have a similar setup? is it slow as hell? 

my question is did i somehow do something wrong, in the system monitor 850mb of memory is being used as soon as i start up the computer with nothing running! should i install that netbook remix version?

thanks in advance for any information and or suggestions

---

### Post by wojox on 2010-06-17
Did you install the nvidia driver?

System > Admin > Hardware Drivers

---

### Post by HomeSlixe on 2010-06-17
[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)


known bugs and solutions... maybe you can find a workaround here?

---

### Post by bodhi.zazen on 2010-06-17
> **fcruz2489 said:**
> so i have been using ubuntu for a few months on my desktop in a vm as an ssh server and to expand my knowledge of OSs. i have done alot of reading and learned alot of stuff online but thats besides the point. as i said i was using ubuntu in a vm on my i7 860 with 1 cpu core with 2 threads and 2gb of memory dedicated to it. but it wastes too much power so i decided to get a net top.

i purcahse a foxconn nettop with a intel attom a330 dual core 1.6ghz processor, nvidia ion gpu (256mb shared mem), and 1gb ddr2 667 (256mb going to vid card) 

i installed ubuntu 10.04 32bit on it and it seems sooooo slow. it takes AT LEAST 5 seconds to open up a simple program like firefox. and when i click on the menus it takes time for the little icons to show up. i know my desktop is faster than the net top but i didnt think it'd be like this. i installed the "restricted" nvidia drivers and i have all the latest updates installed and there are no startup programs other than docky. does anyone have a similar setup? is it slow as hell? 

my question is did i somehow do something wrong, in the system monitor 850mb of memory is being used as soon as i start up the computer with nothing running! should i install that netbook remix version?

thanks in advance for any information and or suggestions

Linux does not use RAM the same way as Windows, and the saying goes unused ram is wasted RAM.

See : 

[http://www.cyberciti.biz/faq/linux-check-memory-usage/](http://www.cyberciti.biz/faq/linux-check-memory-usage/)

    
    Barn analogy : [http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage](http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage)

    [http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html)

---

### Post by eriktheblu on 2010-06-17
Have you tried disabling desktop effects?

---

### Post by think13 on 2010-06-17
Here's some things to try:

System -> Preferences -> Appearance -> Visual Effects tab. Setting visual effects to 'none' can help with graphics performance.

To see if any programs are using a huge amount of CPU or Memory, you can run ```
top
``` from a command line.

Also, Firefox is not a simple program. It can take 5 seconds or more to start on my 4 year old laptop with more memory than your machine.

If you can't find anything else and are willing to be a little adventurous, you can try [Xubuntu]("http://www.xubuntu.org/") or [Ubuntu Netbook Edition]("http://www.ubuntu.com/netbook/get-ubuntu/download").

---

### Post by pr0t3g3 on 2010-06-17
> **think13 said:**
> Here's some things to try:

System -> Preferences -> Appearance -> Visual Effects tab. Setting visual effects to 'none' can help with graphics performance.

To see if any programs are using a huge amount of CPU or Memory, you can run ```
top
``` from a command line.

Also, Firefox is not a simple program. It can take 5 seconds or more to start on my 4 year old laptop with more memory than your machine.

If you can't find anything else and are willing to be a little adventurous, you can try [Xubuntu]("http://www.xubuntu.org/") or [Ubuntu Netbook Edition]("http://www.ubuntu.com/netbook/get-ubuntu/download").
Netbook edition? and how is that better than the original?

---

### Post by think13 on 2010-06-17
> **pr0t3g3 said:**
> Netbook edition? and how is that better than the original?

I'm not sure-haven't used it myself.
I have however used Xubuntu on an ~6 year old PC sitting in my basement, and it works like a charm. It's snappy even on 512 MB RAM and about 1.5 GHz single core processor.

---

### Post by fcruz2489 on 2010-06-17
ive tried all of that. nvidia drivers are installed. no effects are enabled. no startup programs are enabled other than docky. the only thin i can think of is that i have too little memory i might try to get a 2gb stick. i just didnt think it would run so slow. thanks to everyone who answered i guess ill try the netbook edition and if that doesnt work ill get some more memory. i just dont get why its so slow becausrd people run my exact setup with ubuntu and xbmc on top of it and they say it runs great meanwhile i cant even play a full screen flash video without stuttering.

---

### Post by bodhi.zazen on 2010-06-18
> **fcruz2489 said:**
> ive tried all of that. nvidia drivers are installed. no effects are enabled. no startup programs are enabled other than docky. the only thin i can think of is that i have too little memory i might try to get a 2gb stick. i just didnt think it would run so slow. thanks to everyone who answered i guess ill try the netbook edition and if that doesnt work ill get some more memory. i just dont get why its so slow becausrd people run my exact setup with ubuntu and xbmc on top of it and they say it runs great meanwhile i cant even play a full screen flash video without stuttering.

Linux is not Windows, and your system is not running slow due to a lack of RAM (just trying to save you some $$ ).

---

### Post by fcruz2489 on 2010-06-18
> **bodhi.zazen said:**
> Linux is not Windows, and your system is not running slow due to a lack of RAM (just trying to save you some $$ ).

i understand that. what i dont understand is why its running so poorly when ive never had any previous issues whatsoever with it. ive been using it lightly since 9.04 and i know that old machines are very well capable at running ubuntu very well. 

i installed the netbook edition and not only does it still run slow but im not a huge fan of the layout. i dont want to return the nettop because its working perfect for what i bought it for (ssh server) but i was hoping it would be usable so that i could tinker with it and vnc into it and stuff. thats another thing when i go into the remote desktop settings and i try to change the access password my system locks up. both when i had the desktop version and now with the netbook edition. i swapped out the harddrive for a faster 7200rpm drive that has less storage and its still slow and locking up

---

### Post by bodhi.zazen on 2010-06-18
> **fcruz2489 said:**
> i understand that. what i dont understand is why its running so poorly when ive never had any previous issues whatsoever with it. ive been using it lightly since 9.04 and i know that old machines are very well capable at running ubuntu very well. 

i installed the netbook edition and not only does it still run slow but im not a huge fan of the layout. i dont want to return the nettop because its working perfect for what i bought it for (ssh server) but i was hoping it would be usable so that i could tinker with it and vnc into it and stuff. thats another thing when i go into the remote desktop settings and i try to change the access password my system locks up. both when i had the desktop version and now with the netbook edition. i swapped out the harddrive for a faster 7200rpm drive that has less storage and its still slow and locking up

It is sometimes hard to know what is causing performance issues. It can vary from video drivers to wireless drivers.

You can try starting with a google search on your hardware and see if others have similar problems or solutions.

Ubuntu has a number of likely unnecessary services running, you can stop those services you do not use.

---

### Post by arsenic23 on 2010-06-18
It just sounds like a slow hard disk to me.
Are you 100% that isn't normal behavior for your nettop?  I have a similar machine and it doesn't sound like yours performs much worse then mine.  In fact if I try to open firefox on my netbook it takes much longer then 5 seconds.

---

### Post by fcruz2489 on 2010-06-18
> **arsenic23 said:**
> It just sounds like a slow hard disk to me.
Are you 100% that isn't normal behavior for your nettop?  I have a similar machine and it doesn't sound like yours performs much worse then mine.  In fact if I try to open firefox on my netbook it takes much longer then 5 seconds.

i had a toshiba 5400rpm hard drive in there running desktop edition and swapped it out for a 7200rpm wd black edition now running netbook edition and its still slow as a snail. but im just gonna suck it up and leave it the way it is or maybe try xubuntu but i have no idea what the difference is and if it uses less resources so im gonna have to do some research. 

thanks again for all the replies i really appreciate the help.

---

### Post by Paddy Landau on 2010-06-19
> **think13 said:**
> ... you can try [Xubuntu]("http://www.xubuntu.org/") or [Ubuntu Netbook Edition]("http://www.ubuntu.com/netbook/get-ubuntu/download").
The UNE used to be optimised for the Atom chip, but I'm told that it's no longer the case. The only difference between UNE and the normal one is the layout.

[Xubuntu is no longer better]("http://www.linux-mag.com/cache/7520/1.html") than Ubuntu for lower-end computers. Try [Lubuntu]("http://lubuntu.net/") instead (it works well on my oldest machine).

> **arsenic23 said:**
> Are you 100% that isn't normal behavior for your nettop?
My wife's netbook, too, runs something like yours -- even slower, actually. Netbooks are small machines and take a while to get going.

---

### Post by warfacegod on 2010-06-19
> The UNE used to be optimised for the Atom chip, but I'm told that it's no longer the case.The only difference between UNE and the normal one is the layout.

Xubuntu is no longer better than Ubuntu for lower-end computers. Try Lubuntu instead (it works well on my oldest machine).


This really just meant that it used some minor power saving features. The extra amount of battery life was insignificant. Hence, they stopped bothering. UNE has *slightly* (maybe 2%) higher RAM use in my system. I assume that is due to the "transparencies".

A Lubuntu option would be to use Synaptic and install LXDE into your existing install then changing the Session to LXDE during login (before clicking the Login button).

---

### Post by Paddy Landau on 2010-06-19
> **warfacegod said:**
> A Lubuntu option would be to use Synaptic and install LXDE into your existing install then changing the Session to LXDE during login (before clicking the Login button).
That's part of it. Lubuntu also uses different programs for the browser, terminal, file manager and so forth. I've found it quicker than Xubuntu on my oldest machine.

---

### Post by warfacegod on 2010-06-19
> **Paddy Landau said:**
> That's part of it. Lubuntu also uses different programs for the browser, terminal, file manager and so forth. I've found it quicker than Xubuntu on my oldest machine.

And they get installed with LXDE into Ubuntu.

---

