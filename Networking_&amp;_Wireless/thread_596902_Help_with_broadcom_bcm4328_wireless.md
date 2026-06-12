---
title: "Help with broadcom bcm4328 wireless"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by jader2toesbumpy on 2007-10-30
Yesterday i finally go my first laptop. Its a hp dv6646. The first thing I did when i got home was installed ubuntu. I couldnt get my wireless to work. I have tried at least 5 tutorials multiple times and nothing is working. I really need some help with this. I have a bcm 4328 chipset and 7.10 gusty gibbon 

devin@ubuntu:~$ lspci -nn | grep Network
03:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)

devin@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth13     no wireless extensions.

devin@ubuntu:~$ ndiswrapper -l
bcmwl5 : driver installed

I am by no means an expert but i think that it is not recognizing my built in hardware.
When i plug in a spare usb wireless adapter it works. (linksys wireless-g wusb54gc)

thank you

---

### Post by jader2toesbumpy on 2007-10-31
Ok so after another 10 frustrating hours in addtion to the 8 I had before this post i finally solved it.  I had gusty 7.10 and i tried every tutorial this fourm had to offer.  Finally i just downloaded feisty 7.04 and just used this thread
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

I rebooted and it worked like a charm.

---

### Post by Levo75 on 2007-11-01
Is there no other way? I'm just done configuring everything on Gutsy for gods sake...
The only thing left is the wifi on my mac.

(17" intel c2d 2.0ghz broadcom BCM4328 )

---

### Post by jader2toesbumpy on 2007-11-01
sorry dude, but trust me i tried every tutoiral i could find on these fourms and on others and none of them worked for gusty.  The only advice  have is just downgrade to fiesty.

---

### Post by h4p0 on 2007-11-01
I've got the same problem,
I installed Gutsy on my Desktop server because it solved many problems on my laptop...
And the wireless configuration (10 month of troubles) that finally works on feisty...PUFF!!GONE!!!
I can't understand this!!
If a problem is solved in a older version....why don't leave things just how they are!!??:confused:


grrrrr!!!

---

### Post by Er1ck on 2007-11-11
Hey, I just searched the ubuntu forum for "dv6646" and it brought me to this thread.

I have also purchased the HP Pavilion DV6646US laptop from Circuit city about a couple weeks ago and the first thing I did when I bought was try to install Ubuntu 7.10. I couldn't get the LiveCD to work so I tried the alternate install CD and that barely got through (barely, because it couldn't recognize my wireless device). 

So after reading several threads, I've come to the conclusion to install ubuntu 7.04 feisty to avoid future headaches in attempting to get the wireless card to work.

---

### Post by drinkmocha on 2007-11-12
I have the same problem and I gave up, I bought a linksys USB wireless adapter, now I just need to figure out how to make this work. Good luck to me.

---

### Post by jader2toesbumpy on 2007-11-12
> **drinkmocha said:**
> I have the same problem and I gave up, I bought a linksys USB wireless adapter, now I just need to figure out how to make this work. Good luck to me.

I didn't realize the updates in gusty were worth buying and carrying around a extra usb key with you everywhere but ok man, more power to you.

---

### Post by drinkmocha on 2007-11-12
Guess what, the instructions here for making the USB adapter work ALSO won't work for my laptop. I guess Circuit City will have their Linksys back tomorrow.

---

### Post by Benchrest on 2007-12-05
I also have the DV6646US but your solution leanves me in a quandry. I tried Feisty first because of the graphics problems. I could not get the Nvidia GeForce GO 7150M to work. Found a post where a user got it to work of Gutsy so I went that way. But now the Broadcom BCM4328 doesn't work.

My question, how did you get your graphics card to work with Feisty?

---

### Post by jader2toesbumpy on 2007-12-05
> **Benchrest said:**
> I also have the DV6646US but your solution leanves me in a quandry. I tried Feisty first because of the graphics problems. I could not get the Nvidia GeForce GO 7150M to work. Found a post where a user got it to work of Gutsy so I went that way. But now the Broadcom BCM4328 doesn't work.

My question, how did you get your graphics card to work with Feisty?

use feisty and use this easy to use script [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) 
download envy_0.9.9-0ubuntu1_all.deb unpack it and run it, i used manual and chose the default drivers

hoped that helped :)

---

### Post by Benchrest on 2007-12-06
I've lost track of how much time I've spent on this. Really getting frustrated. I was able to get graphics working on Feisty. I used your method. I had tried Envy before, but realized I was leaving out the final step.

But to the wireless. Only 6 steps in the process and all went well (as far as I can tell) but still no wireless! I have the wireless switch on, it works with vista.

I installed feisty from alternate cd in dual boot. THen updated. I had found before Envy would not install unless I did the updates first. Ran envy, rebooted and graphics worked. 

Went to the link you provided, performed the six easy steps, nothing. reobbted nothing.  

I am going to review this other process, [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

And that may be it. My wireless dowesn't show up in network manager, don't see any other way to activate it.

---

### Post by Lorac1949 on 2007-12-06
> **jader2toesbumpy said:**
> sorry dude, but trust me i tried every tutoiral i could find on these fourms and on others and none of them worked for gusty.  The only advice  have is just downgrade to fiesty.

I think I agree with you.  I've tried 2 "fix it" suggestions.  One finally gave me a glimpse of my network when I opened Network Manager.  But - aside from not being able to connect to it - it either shows 98%, 0% or the network disappears from the list altogether.  I've a dual boot Dell Inspiron 1520.  The wireless works just fine in Windows.  I hope that Heron fixes this problem.  If not, I'm bailing to Feisty and gutting Gutsy.

---

### Post by RobertR on 2007-12-22
I have a broadcom bcm4328 card in my Dell D531 and am using it to post this online now. It works for me? I installed the Windows wireless drivers (ndisgtk) and then downloaded the drivers from Dells web site " R174291.exe" . I extracted it (by right clicking on it) and then used the wireless driver option (in System, Administration) and added the file bcmwl5.inf  (i added it from its directory as there are other files here it may use). 

Tested..works well...Using WPA2 personal...trying to find out how to set it up so I can have WPA2 enterprise as thats what we use at work.....

Plus I'd like to not have to use the ndiswrapper if possible..It doesn't support monitor mode....  hmmm

---

### Post by enderbean on 2008-01-04
> **RobertR said:**
> I have a broadcom bcm4328 card in my Dell D531 and am using it to post this online now. It works for me? I installed the Windows wireless drivers (ndisgtk) and then downloaded the drivers from Dells web site " R174291.exe" . I extracted it (by right clicking on it) and then used the wireless driver option (in System, Administration) and added the file bcmwl5.inf  (i added it from its directory as there are other files here it may use). 

Tested..works well...Using WPA2 personal...trying to find out how to set it up so I can have WPA2 enterprise as thats what we use at work.....

Plus I'd like to not have to use the ndiswrapper if possible..It doesn't support monitor mode....  hmmm


Hi there,

I am a complete noob to Linux but I did get it installed and have tinkered around for a few hours trying different things to get my wireless card to work as well (also have Broadcom4328). I have gotten my drivers (I'm pretty sure.. the .inf and .sys files and a folder from the Windows folder), and I came close to where I need to install ndisgtk on Linux but I can't seem to find it. I'm running 7.10 on an HP dv6500z.

I've got a couple things I'm going to try, I'll post with results later. My main problem is I couldn't find the ndisgtk to install so that I can install my drivers (not to mention I don't know for sure how to install them, but I'll get to that later, I think I found some good guides).

The topics I found and am following are here:
[http://ubuntuforums.org/showthread.php?t=411456](http://ubuntuforums.org/showthread.php?t=411456)
[http://ubuntuforums.org/showthread.php?t=98655](http://ubuntuforums.org/showthread.php?t=98655)

The second one seems a little more noob friendly but I've got them both copied and pasted into a little txt and I'm switching over now and going to try them. Sadly I have to go to work pretty much as soon as I get done so I probably won't be able to post soon, but it looks like this thread is a little old so whatever.

Yes I know I type too much. Sorry :)

---

### Post by nimbledinosaur on 2008-01-05
I have a bcm4328 and this worked for me (ndiswrapper solution): [http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html#4](http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html#4)

---

### Post by jader2toesbumpy on 2008-04-25
Good news guys, I can confirm are chipset, BCM4328 working in Hardy with WPA, WEP, and no encryption with this method.

[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

No confirmed cases with WPA2 as far as I know but at least we can do WPA. 


:):):)

---

