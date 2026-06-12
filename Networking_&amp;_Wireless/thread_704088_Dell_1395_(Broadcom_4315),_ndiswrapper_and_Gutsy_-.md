---
title: "Dell 1395 (Broadcom 4315), ndiswrapper and Gutsy - success!"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by elektropod on 2008-02-22
There have been a couple of threads that touched on some of these elements, but nothing that gave a complete walkthrough, so here it is. I have a Dell Vostro 1500 with the Dell TrueMobile 1395 wireless card, one that has given many Linux users big headaches.

After trying many different approaches suggested all over the web, and gathering clues in many Ubuntu forum posts, I finally worked out this solution:

1. blacklist bcm43xx

	echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

2. install ndiswrapper and related files

	sudo apt-get install ndiswrapper-common ndisgtk

	(this should also pull in the 'utils' package)
	when I was all said and done, I had
		ndiswrapper 1.45
		ndiswrapper-utils 1.9
		ndisgtk   (you don't really need this, and my instructions don't make use of it)

3. download and extract [http://ftp.us.dell.com/network/R174291.exe](http://ftp.us.dell.com/network/R174291.exe)

	this is a ridiculous bit of bloat, but the most complete INF for 43xx devices

4. go into folder DRIVER_US inside the result of what you did above

5. use ndiswrapper to install bcmwl5.inf

	sudo ndiswrapper -i bcmwl5.inf
	sudo ndiswrapper -m	(this one will give you a bunch of warnings - ignore)
	sudo ndiswrapper -ma
	sudo ndiswrapper -mi

	(I don't honestly know if the last three steps are necessary, but can't hurt)

6. reboot your machine

After I did the above and rebooted, the little blue Wi-Fi light on the right side of my Vostro came on, and it grabbed an IP via DHCP without any additional fuss. :KS

---

### Post by Mizai on 2008-02-23
Thanks for this. Just bought a Dell Inspiron 1720 with the same card, and after hours of struggle, these instructions worked perfectly.

---

### Post by JayBachatero on 2008-02-25
Man you don't know how much I love you right now.  I tried everything trying to get wireless to work with this laptop.  After a few days I gave up and sticked with Vista.  I did a search today and came across this.  You just made my day.  THANKS.

---

### Post by elaurent on 2008-03-01
Thanks a lot! I have been struggling with my new inspiron 1720 T8100 and gutsy for hours before I found your post.
I had followed almost the same procedure but was using driver bcmwl6 delivered with my laptop instead of the one you pointed to...
After being able to activate the wlan0 card I faced the following problem:
It seems impossible to enter a 128 bit WEP key with the gnome network settings (max number of characters in the caption windows for the key?).
I had to use KDE interface to enter my key and now every thing works fine.

thanks again.

---

### Post by ubonetu on 2008-03-15
Wow,

I've been looking for an answer to this problem for days.  BTW it works on the Inspiron 1521 in Fedora as well.  Trick is, you have to use the driver you suggested and not the current one:  bcmwl6.inf = bad.

Thanks so much,

ubonetu 8) 8) 8)  <-- Three cools for you, Sir.

---

### Post by swat253 on 2008-03-15
I'm having the same problem with a BCM43xx card. Problem is, I have no clue as to what the original poste, and the following success story posters, did to make theirs work!

Could someone dumb this down for me a bit? 

Are the following commands being entered on a terminal screen after, in my case, **"swa@swa-laptop: - $"** ?

> 1. blacklist bcm43xx

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

2. install ndiswrapper and related files

sudo apt-get install ndiswrapper-common ndisgtk

(this should also pull in the 'utils' package)
when I was all said and done, I had
ndiswrapper 1.45
ndiswrapper-utils 1.9
ndisgtk (you don't really need this, and my instructions don't make use of it)

3. download and extract [http://ftp.us.dell.com/network/R174291.exe](http://ftp.us.dell.com/network/R174291.exe)

this is a ridiculous bit of bloat, but the most complete INF for 43xx devices

4. go into folder DRIVER_US inside the result of what you did above

5. use ndiswrapper to install bcmwl5.inf

sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m (this one will give you a bunch of warnings - ignore)
sudo ndiswrapper -ma
sudo ndiswrapper -mi

Thanks! I'd really like to get Ubuntu 7.10 hooked up to the net so I can update and add-on a few packages!

---

### Post by swat253 on 2008-03-15
I'm getting this response;
[B]
tee: /: Is a directory
tee: etc/modprobe.d/blacklist: No such file or directory

__________________________________________________________________________________________________________________________________________

Somehow worked thru all that and now stuck at step 5;

"Package ndiswrapper-utils is not available, but is referred to by another package."  ????

---

### Post by swat253 on 2008-03-15
SUCCESS! 

I was having problems with the last step of the workaround (my attempts wouldn't locate the utils files) so I tried another route.
 
[COLOR="RoyalBlue"][http://ubuntuforums.org/showthread.php?t=405990&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=405990&highlight=ndiswrapper)[/COLOR]

The link above proved to work for a Linux/Ubuntu noob like myself! No disrespect whatsoever for the original instructions; I've never dealt with typing commands in terminals, so I'm sure it was on my end. 

In any case, anyone else having problems with a Broadcom wireless card should have at look at the link.

---

### Post by ubonetu on 2008-03-29
:guitar:

I gotta say, on like three different os's this has worked.... bravo.

Ward

---

### Post by ReddogOne on 2008-03-29
So many thank owed to you. 

Only thing is... 

> **elektropod said:**
> 
3. download and extract [http://ftp.us.dell.com/network/R174291.exe](http://ftp.us.dell.com/network/R174291.exe)


How would you extract this? I used wine (as a guest) and it worked but not sure this is the easiest!

---

### Post by Cap'n Skyler on 2008-03-29
> **ReddogOne said:**
> So many thank owed to you. 

Only thing is... 



How would you extract this? I used wine (as a guest) and it worked but not sure this is the easiest!
i had issues getting the driver INF from an executable as well.
only thing i can add,is if the driver file offers win 98, win millenium and Xp drivers,if one doesnt work, remove it and re start and try another one.i have the win 98 working on my Ubuntu 7.10 just a few days ago.i had trouble getting mine to work,and added the step of removing then re starting then re installing a different INF worked for me on my home  wireless network.
  i am almost sure some drivers are the same for xp/98/ etc  but not always.some drivers are totally not the same. but never be afraid to try the different version in the exe file.
i got my exe opened from my win xp on another comp,i searched for the file and opened it and copied it,wrote it to a cd,and then saved to each comp,and then i open and navigate to the INF i need to install..

---

### Post by artvarck on 2008-04-02
This post was what I needed to get me up and running on an Inspiron 1420 with Gutsy and a Dell wireless 1395 card.  However, I have the following issue which I do not know how to troubleshoot.

After reboot, in order for my wireless card to connect to my AP, I have to open Network Manager and erase the current WPA key, and reinsert the original key.  The key hasn't changed, and I am simply reentering the key that already resides there.  Could anyone provide any clues on what I need to do?

Thanks.

---

### Post by artvarck on 2008-04-04
Replying to my own post with a resolution:
I found that Roaming had to be enabled in the Network Manager properties for the wireless card.  No idea why, but making that change solved my problem.

---

### Post by crimsontime on 2008-04-13
Thank you oh praise thee oh mighty one!!!:)  After about 5 hours of trying to get this to work and endless google and dell searches, this is the one that actually worked for me.  Thank you!!!!!  I am using an Inspiron 1525 with Vista pre-installed.  I created Ubuntu for dual boot configuration.  If anyone encounters the same issues, I hope they can find this.

---

### Post by NastyT23 on 2008-04-16
When i paste step 2 into the terminal
sudo apt-get install ndiswrapper-common ndisgtk
Im getting an error:

terry@terry-laptop:~$ sudo apt-get install ndiswrapper-common ndisgtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-common

why is this?


Nevermind, i figured out what happend, it installed fine

---

### Post by lankforddl on 2008-05-01
I just tried it and it worked. Excellent!

---

### Post by ruffEdgz on 2008-05-02
I had to try it two times but this actually worked for my Dell XPS 1530 laptop with Dell Wireless 1395 inside (I know, I'm stupid for not getting the Intel Wireless Card). 

I'm just happy I found this tutorial.

Thanks again!!

:KS

---

### Post by Shugs81 on 2008-05-25
bah.... don't know what i'm doing wrong....

> sudo apt-get install ndiswrapper-common ndisgtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-common


any clues? bit of a linux noob... usually stuff works but this has me a bit stumped... also noob to debian based stuff... was always fedora based before...

any help would be appreciated....

---

### Post by wendong on 2008-05-26
> **Shugs81 said:**
> bah.... don't know what i'm doing wrong....



any clues? bit of a linux noob... usually stuff works but this has me a bit stumped... also noob to debian based stuff... was always fedora based before...

any help would be appreciated....
Run this first:
sudo apt-get update

---

### Post by wendong on 2008-05-26
> **ReddogOne said:**
> So many thank owed to you. 

Only thing is... 



How would you extract this? I used wine (as a guest) and it worked but not sure this is the easiest!
unzip R174291.exe

---

### Post by Shugs81 on 2008-05-27
cockflaps....

never checked my repositories.... will give it another go....

---

### Post by Shugs81 on 2008-05-27
reet.... just for other peeps info... if you're new to linux make sure you check that you've got more than just the standard repository on your machine!!! works like a charm!!

---

### Post by chrisinspace on 2008-05-31
Thank you so much for this.  I just used it to get my wireless working.  I installed Hardy on a Dell Vostro 1310.  Everything worked out of the box except the Dell 1395 Wireless card, but this solved that problem.

---

### Post by CaseWestern on 2008-06-11
Hi All:

      I am new to this forum and found this particular thread useful to fix the wireless problem on my Laptop.  First of all please tell me how to uninstall the previous wireless driver which I installed?   I didnt do it properly.  I want to uninstall the previous bcmwl5.inf driver which I installed and subsequently install the driver afresh.

      Since I am very new to this Ubuntu services, can someone guide through the network configuration steps.  Because when I previously installed the bcmwl5.inf driver and rebooted the system it didnt automatically detect the wireless networks.

Thanks in advance.

---

### Post by Green_biri on 2008-06-15
D*mn, this should be a stickie! It really works, thanks dude! :D

---

### Post by SimonTheMime on 2008-06-23
this worked thanks

---

