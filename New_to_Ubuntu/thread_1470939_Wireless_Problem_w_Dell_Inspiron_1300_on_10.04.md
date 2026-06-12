---
title: "Wireless Problem w/ Dell Inspiron 1300 on 10.04"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by Tobin-Tobin on 2010-05-03
This is my first post on here and i have only installed ubuntu yesterday having used Windows my entire life - so please go easy. I am struggling with even basic tasks so you'll have to talk me through EVERYTHING, sorry :)
 
PROBLEM: I have installed ubuntu 10.04 on my Dell Inspiron 1300 laptop. I cannot seem to connect to any wireless networks now. It does not even seem to see any networks. I presume that ubuntu has found my wireless controller since there is no warning message or icon or anything. There is an exclamation mark over the wireless symbol though.
 
I do not have a wireless button on the laptop so i dont think that is the problem. I should have good signal. Is there a way to do some sort of diagnostic? I ran the 'System Testing' application and it found the wireless controller and said everything was ok. It says my controller is a:
 
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g.
 
Any help would be apprecaited, i appologise if this is a stupid question, i have searched already but couldn't find anything.
 
Cheers,
 
Toby

---

### Post by theotherotherguy on 2010-05-03
I'm also looking for help on a broadcom 43xx card, if someone posts a fix to my thread I'll see if I can spread it over, I know there's a workthrough for my e1505 for older ubuntu versions using ndiswrapper on the forum, and I would guess that it would also work for you if you used the drivers from your specific hardware.

I'm jumping the gun asking for it, but would you post the output of 
```
 lspci -nn 
```it might help diagnose the issue more specifically.

---

### Post by Tobin-Tobin on 2010-05-03
I would love to post the output of that command on here except that i cannot connect that laptop to the internet. I might be able to save it to a file and use a USB key to transfer it to this computer that is on the internet?

---

### Post by Tobin-Tobin on 2010-05-03
That was easier than i thought! Here it is:
 
[SIZE=2]00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]00:1c.3 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 [8086:2666] (rev 03)[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)[/SIZE]
 
Thank you in advance for any help, if you do find a solution be sure to let me know.
 
Toby

---

### Post by theotherotherguy on 2010-05-03
My problems were resolved by this post in my thread

"To solve it I simply went to Synaptic Package Manager

Typed “broadcom”

Right clicked on “bcmwl-kernel-source” and marked it for re-installation

Then went back to the hardware drivers where I could now activate the  broadcom driver without any problems!"

I did similar but in Kubuntu, I hope that this or something like it fixes things for you, I think this is a common issue

---

### Post by spiky001 on 2010-05-03
Tobin  I would get on net 1st Use a wired connection do updates and check for drivers (system admin hard ware drivers)

---

### Post by Tobin-Tobin on 2010-05-03
I have followed your suggestion but cannot find "bcmwl-kernel-source" only "bcmwl-modaliases". And i cannot mark it for reinstallation as the option is greyed out so i cannot click it.
 
Any more ideas would be much appreciated.
 
Toby

---

### Post by Tobin-Tobin on 2010-05-03
> **spiky001 said:**
> Tobin I would get on net 1st Use a wired connection do updates and check for drivers (system admin hard ware drivers)
 
I thought the very same thing but i will not have access to a wired network for 3 or 4 weeks. I was wondering if it was possible to download a driver on this computer and transfer it across to the ubuntu laptop in the same way i would using windows?
 
Thanks again guys,
 
Toby

---

### Post by spiky001 on 2010-05-03
i take it you are using another laptop now? can you not put the internet connection straight in to your laptop use net that way

---

### Post by Tobin-Tobin on 2010-05-03
Unfortunately not, i am at uni so i can either connect to an unsecured wireless network on my ubuntu laptop (which does not work) , or use one of the uni PC's. You cannot plug the LAN cable from the uni PC into the laptop as you have to log in to the server etc.
 
Keep the ideas coming though!

---

### Post by spiky001 on 2010-05-03
installing drivers is not straight forward can you not borrow a lead share connection with the windows box, it will save a lot of trouble sorry cant be more positive, Maybe another forum member has better solution

---

### Post by xifer on 2010-05-03
> **Tobin-Tobin said:**
>  I was wondering if it was possible to download a driver on this computer and transfer it across to the ubuntu laptop in the same way i would using windows?
 

Toby

[http://packages.ubuntu.com/da/karmic/i386/bcmwl-kernel-source/download](http://packages.ubuntu.com/da/karmic/i386/bcmwl-kernel-source/download)

---

### Post by Tobin-Tobin on 2010-05-03
> **xifer said:**
> [http://packages.ubuntu.com/da/karmic/i386/bcmwl-kernel-source/download](http://packages.ubuntu.com/da/karmic/i386/bcmwl-kernel-source/download)
 
I downloaded that file, transfered it over to the ubuntu laptop and clicked on it. A window popped up saying ti was installing something then stopped and gave an error:
 
"Status: Dependency is not satisfiable: dkms"
 
Will that file work with 10.04 when it was designed for 9?
 
Thanks again,
 
Toby

---

### Post by xifer on 2010-05-03
> **Tobin-Tobin said:**
> I downloaded that file, transfered it over to the ubuntu laptop and clicked on it. A window popped up saying ti was installing something then stopped and gave an error:
 
"Status: Dependency is not satisfiable: dkms"
 
Will that file work with 10.04 when it was designed for 9?
 
Thanks again,
 
Toby

Should work fine

try this

apt-get remove dkms

then try to install your package again

 bcmwl-kernel-source


check this thread


[http://ubuntuforums.org/archive/index.php/t-1305296.html](http://ubuntuforums.org/archive/index.php/t-1305296.html)

---

### Post by Tobin-Tobin on 2010-05-03
Please appreciate i am a total beginner here. I went to the console and typed in:
 
apt-get remove dkms
 
And the console gave the following message:
 
E: Could not open lock file var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
 
I apologise again for my lack of knowledge on ubuntu. I read that thread but couldn't really make any sense of it :confused:

---

### Post by 1915flyer on 2010-05-03
Try

sudo apt-get remove dkms

---

### Post by Tobin-Tobin on 2010-05-03
> **1915flyer said:**
> Try
 
sudo apt-get remove dkms
 
I tried that, it asked for my password, then said:
 
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package dkms
 
What is this dkms thing? Whatever it is i don't think i have it.

---

### Post by SFCampbell on 2010-05-03
> **Tobin-Tobin said:**
> It says my controller is a:
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g.


Hey Toby, I've had problems with Broadcom wireless drivers before too.  Please try this:

1) edit your modules list by typing **sudo gedit /etc/modules**
2) add "**wl**" (without quotations, just the letters W+L) to the bottom of the list
3) Save, close, reboot

This has repaid me with a list of wireless networks many times, I hope it does the same for you.

---

### Post by Tobin-Tobin on 2010-05-03
> **SFCampbell said:**
> Hey Toby, I've had problems with Broadcom wireless drivers before too. Please try this:
 
1) edit your modules list by typing **sudo gedit /etc/modules**
2) add "**wl**" (without quotations, just the letters W+L) to the bottom of the list
3) Save, close, reboot
 
This has repaid me with a list of wireless networks many times, I hope it does the same for you.
 
I have done that succesfully. I will try it out in an hour or two when i return home. Fingers crossed!
 
Thanks for the help everyone,
 
Toby

---

### Post by xifer on 2010-05-03
> **SFCampbell said:**
> Hey Toby, I've had problems with Broadcom wireless drivers before too.  Please try this:

1) edit your modules list by typing **sudo gedit /etc/modules**
2) add "**wl**" (without quotations, just the letters W+L) to the bottom of the list
3) Save, close, reboot

This has repaid me with a list of wireless networks many times, I hope it does the same for you.

if that doesn't work then try to install it!  But you'll need to get the package from that other site.  Hopefully you won't need to anyway :-)

sudo apt-get install dkms

---

### Post by Tobin-Tobin on 2010-05-03
So if i do need to isntall it i open the package file, then go to the command prompt and type:
 
sudo apt-get install dkms 
 
Or do i type that first then open the package after?

---

### Post by xifer on 2010-05-03
> **Tobin-Tobin said:**
> So if i do need to isntall it i open the package file, then go to the command prompt and type:
 
sudo apt-get install dkms 
 
Or do i type that first then open the package after?

there are different ways to install packages.  if you get the file from another PC like you've been doing you can open it with default package manager by double clicking it - it should prompt you for authentication and then install it just like apt-get would.  I think you can use apt-get to install from a file using the command line rather than the repositories - check the manual.  At command prompt type:

 man apt-get

otherwise there are other command line packge tools around - dpkg for instance

try man dpkg

Good luck

---

### Post by Tobin-Tobin on 2010-05-04
SORTED! Right this is how it went...
 
Firstly i tried plugging my laptop in to a friends through the LAN, then bridging the connection. This worked and i could connect to the net via his wireless, I then used the Synaptic Package Manager to check for updates which worked but the signal was so bad it couldnt get the data.
 
Then we tried plugging a USB wireless card in to my ubuntu laptop which worked a treat. Why didn't i (or you) think of that? Anyway i downloaded all the updates etc but it still wouldn't work.
 
In the end we deleted every broadcom file we could find through the Synaptic Package Manager then used the Hardware Drivers tool to add the drivers back in - success! I think the problem was the dependencies for the braodcom files (like dkmt and about 3 others) weren't installing so the broadcom drivers wouldn't work.
 
Anyway its sorted now, except that my signal was always marginal on windows and cutting out unless the laptop was in a specific place in the house. It seems to be slightly worse now, as if ubuntu requires a better signal threshold before it will connect to the network.
 
Anyway thankyou everyone for your help, i used pretty much everyones advice at some point so cheers =D>
 
Toby

---

### Post by ninjahippie on 2010-05-17
Easy fix.  Connect to your network with an Ethernet cable.  Let Ubuntu download and process the pending updates.  Reboot.  Then go to System - Administration - Hardware Drivers and let it search.  It will Show "Broadcom B43 wireless driver".  Activate it. 

Thats it.

---

### Post by Tobin-Tobin on 2010-05-18
Thanks for your help but i have it fixed now. I couldn't do what you suggested as i didnt have access to ethernet...

---

### Post by arazaxirelcinellersadolur on 2011-11-13
hi, 
really stupid and annoying thing when u can not establish a connection via wireless on 8.04 waiting a while to get 9.04 and damn - not included wireless connection and after a big while getting 11.04 with no wireless capability - all of these are being at the period the earth going to use not wired connection abroad its parks hotels etc...
i dont know, what does mean this careless work but since the 5.04, i really think to transfer to stupid windoze due to this and some other reasons dont hides itself from ubuntu users since a long time till today...
yes, i becames so big pity :(:confused:
from baku, aze
erebce/gmail.com
tefsir/yahoo.com

---

