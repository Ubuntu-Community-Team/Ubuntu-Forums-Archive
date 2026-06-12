---
title: "Wireless Issue"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by jacksogp on 2008-02-04
I know that this issue seems to have been talked about a lot but I am a newbie to Ubuntu so I thought I'd ask again so perhaps I could receieve some extra help. 

I am having a problem getting either my ethernet card or my wireless card to work with my new installation of Ubuntu 7.10. I installed it last night, and when I started the system up, it claimed I had two restricted drivers. I checked the two listed, and one was for my modem and the other my wireless card. I attempted to tell it to use the firmware for the wireless and it gives me an error message saying that it cannot open it or find it. This makes for a dilemma since i don't have any internet access currently on the computer. 

Info on my system: 

Manufacturer: Dell
Model : Latitude D500 
Wireless Card: Broadcom (43xx Chipset) 
Ubuntu 7.10 
No internet access on the machine. 

Thus, my question is, does anyone have a fairly simple way of helping me get the wireless card working? I really would appreciate any input. 

I tried the post at the top of this forum "easy way to get Broadcom working" or something to that effect, well...it wouldn't work on Ubuntu 7.10 because it says it can't work with that Kernel. 

Again, I appreciate the help. 

Thanks

---

### Post by jan quark on 2008-02-04
that works for me
have also a broadcom
but unfortunately you will have as much fun with them as I have

but this should work

[http://janquark.fatfreehost.com/tutorial1.html](http://janquark.fatfreehost.com/tutorial1.html)

---

### Post by jacksogp on 2008-02-04
Thank you for the help :) 

I will post later to let you know how it works.

---

### Post by sneeks on 2008-02-04
no worries mate.

---

### Post by jacksogp on 2008-02-04
The instructions on the posted site were great but  it didn't work. I tried to install the .deb package and it said error: dependancy resource not found or something to that extent. Any ideas?

---

### Post by jacksogp on 2008-02-04
Actually the message I receieve when I open the deb is as follows : "Error: Dependency is not satisfiable: libc6"

---

### Post by jan quark on 2008-02-04
try to install this
[http://packages.debian.org/etch/i386/bcm43xx-fwcutter/download](http://packages.debian.org/etch/i386/bcm43xx-fwcutter/download)
[http://packages.debian.org/unstable/utils/bcm43xx-fwcutter](http://packages.debian.org/unstable/utils/bcm43xx-fwcutter)

you have to find the right package :)

---

### Post by jacksogp on 2008-02-04
I tried the i386 and it gave me the same error.

---

### Post by rcatman on 2008-02-04
I am on a fresh install of Gutsy. I have a broadcom 4306 wireless card.

I had the same problem. Tried to install the bcm43xx driver from the Restricted Drivers and it wouldn´t install. Found a solution!

[http://ubuntuforums.org/showthread.php?t=197102]("http://ubuntuforums.org/showthread.php?t=197102")

I chose option 1 under the title Feisty and Gutsy.

All I did to get my card working was, download this attachment [http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133]("http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133")

Install the package. Restart.

I logged in and on the toolbar I could see a list of wireless points to connect to.

My Previous experience with broadcom cards is that the gnome network-manager couldnt connect to wireless points where it required a wep or wap key. I havent tried connecting to a secure network yet. My solution was to install wicd (uninstalls gnome network-manager) from [http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/").

Good luck. Let me know how it goes.

---

### Post by jacksogp on 2008-02-04
Well that did help ! :) I now see networks however when I try to connect to one (unsecured) it just trys to connect over and over again with no result. Any ideas?

---

### Post by rcatman on 2008-02-04
Try installing wicd from wicd.sourceforge.net


I had the same problem. Wicd seemed to fix it. If not, then you&#314;l have to uninstall the bcm43xx package and use bcm43-fwcutter to extract the firmware from your card. I followed these steps with my last computer and it worked great......
[http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm43xx-fwcutter]("http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm43xx-fwcutter")

its terminal based. Hows your experience working with the terminal? If you follow the directions exactly it should work, but let me know if you get any error messages.

---

### Post by jacksogp on 2008-02-04
I actually now got connected to an unsecured wireless network, however it runs very very slowly.

---

### Post by jacksogp on 2008-02-05
**I am about to give up on this...**

I have a Dell D500 Latitude and I recently installed 7.10. I had been unable to use my Broadcom 43xx wireless for a few days until last night when I tried using the "Bcm43xxCompWiz" install which seemed to have helped. I can now see wireless networks and even on occasion connect to them, however its extremley slow, something like 24mb/s, I actually tried using the fwcutter and ndiswrapper to install the driver however those worked to no avail, only this compwiz install seemed to have worked , but the internet is just to slow for me to realistically keep this over windows. Does anyone have any ideas on how I could fix this? Help ! :(

---

### Post by bcmiller on 2008-02-05
I had given up on wireless on my daughter's computer using Ubuntu until I found Wicd... 

If you can install that it should solve your problem

There should be a sticky about Wicd in this forum for anyone with wireless issues...

I understand that my solution isn't for everyone and you may have a different problem but it was an instant fix after hours spent in vain using windows .dlls etc...

---

### Post by freeatlast on 2008-02-06
I had a similar problem using 64-bit gutsy on a dell with a broadcom.  Right after the install, if you didn't do it during the install, make sure to install all the updates fomr a wired connection if possible.

Then just go to system->admin-> restricted drivers and install the firmware.

select it to dl form the internet, so you have to be wired, and then it works.  I have done this installation on 3 dells with no worries or future issues.

---

