---
title: "Still no wireless"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by Bikinguy on 2011-05-03
Hi All,

I have had 10.04 up and running fine for several weeks and like it enough to have replaced my xp pro on an older Dell lat.

I downloaded 11.04 and put it in a small partition to tinker around with it. Very nice interface except no luck with wireless.

Copied down all the broadcom packages i used to get the 10.04 going and still no luck. I have a broadcomm 4311 wireless card.

I have installed and uninstalled over a 10 or so packages trying to get this to work. My 10.04 took over a day to get it up but now it works great.

Ok now a bit of a rant but I just dont understand why ubuntu has so many probs with wireless esp common cards. This in not cutting edge tech here at all. My kindle hooked up to my wireless in about 2o seconds. My Roku box in a few minutes and several other divices no problem at all.

---

### Post by natehall on 2011-05-03
The page link below will tell you what you need. 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)

I know it works for 10.10. Of course my problem is trying to get it to work in Debian. If anybody knows how to do that without internet access on the computer I'm trying to do this with chime in!

---

### Post by 5149.5 on 2011-05-03
The problems are with hardware that uses proprietary drivers. When the hardware vendors don't cooperate with the free software community, that is what happens. If you look around at all of the posts with wireless problems, the vast majority of them are for users with Broadcom adapters. There is a reason for that.

---

### Post by Bikinguy on 2011-05-03
Thanks for the replies.

I have tired those install several times but will follow that script again..may just have missed something.

I figured it was a pissing match between vendors but hey in all these years seems something a bit more elegant could have been figured out for broadcom.

Why did I not have t enter all those sudo apt gets for my 10.04 install to get wireless

---

### Post by BertN45 on 2011-05-03
It is simple you do noy have to enter any apt-get. Just make sure that you remove all drivers you have tried. Make sure that the Broadcom STA driver is de-activated, go to menu/dash "additional drivers".

Go to the synaptic package manager and type b43 in the filter box and mark the next two package for installation:
- firmware-b43-installer
- b43-fwcutter

That should solve your problem, since I did the same and have the same wifi.

---

### Post by Bikinguy on 2011-05-03
Thanks guys,, appreciate the prompt replies.

Will try out the suggestions right away. I think I will with Burts as it seems a bit simpler.

---

### Post by Bikinguy on 2011-05-07
Hi all,

Finally got wireless in Natty. I deleted Natty from the second partition. Did a upgrade in stall over the remaining 10.04.

Then as told before in here I deactivated the wireless driver that ubuntu suggests.

Opened up the Synaptic package manager and entered B43 in the search engine. Installed the firmware b43 installer  and the b43 fwcutter rebooted and wireless is up and running. I have a broadcom wireless setup. The entire process including complete upgrade to getting wireless up took less than 30 minutes.

So far Loving Natty...thanks again guys for all the helpful input.

---

