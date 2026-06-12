---
title: "Ati Radeon Driver 9.3 in Ubuntu 9.04"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by Duskao on 2009-04-25
Hey guys, since Ati has stopped supporting my video card (Radeon X1950 Pro) I was trying to install the old 9.3 driver with the "ati-driver-installer-9-3-x86.x86_64.run. it was working fine untill it says
"Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.ODaSCp"

Not sure why this is happening. Is there something I am missing? It would be nice to use my video card in 9.04 till I get a chance to pick up my new one.

---

### Post by kwacka on 2009-04-25
Use Synaptic to install 'xserver-xorg-video-radeonhd' the information provided states that this is amongst the cards supported.

---

### Post by Duskao on 2009-04-25
I tried that before and it messed up my system because it seems to want to install the newest ati driver which doesn't suppory my video card. I ended up having to reinstall Ubuntu. Perhaps I will try to be patient until I get my new video card... :(

Oh wait I think I may have misunderstood. That is not what I tried last time, I tried X.org through add/remove last time, this isn't the same thing is it?

---

### Post by kwacka on 2009-04-25
As I understand it these aren't ATI drivers, but developed by Xorg developers.

Can you install via 'hardware drivers' (under System - Administration)?

If there are problems open a virtual console (e.g. press ALt, Control and F3) and use apt-get remove to get rid of that driver

---

### Post by Duskao on 2009-04-25
No I can't install using "hardware drivers". Not since upgrading to 9.04. But I'm quite sure it is because the support has been dropped for my card so I cannot use the newest fglrx drivers.

---

### Post by Mark Phelps on 2009-04-27
> **Duskao said:**
> No I can't install using "hardware drivers". Not since upgrading to 9.04. But I'm quite sure it is because the support has been dropped for my card so I cannot use the newest fglrx drivers.

That's correct, support for X1950 has been dropped.  Plus, AFAIK, you won't be able to get Catalyst 9.3 to work in 9.04 because the Xorg has changed to v1.6.

---

### Post by kwacka on 2009-04-29
Drivers are available at the AMD site, they have been moved from the main section to 'Legacy'.

See [http://preview.tinyurl.com/d64lfc](http://preview.tinyurl.com/d64lfc)

Installation instructions for Open Source & restricted drivers are at: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

---

### Post by yperiard on 2009-05-14
> **Duskao said:**
> 
"Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.ODaSCp"


64 bits, 9.04
ATI Radeon x1950 pro

Same error here, no joy with any of the proposed solutions. Apart from buying a newer video card? is there anything I can try?

I tried installing the open source ones from synaptic but how can I make sure these are the running ones? Is there anything else to do after installing?


P.S. I also tried envyng, did not work.

thanks

---

### Post by razor7 on 2009-07-07
Hello...anyone tried the legacy 9.3 driver in Ubuntu 9.04¿? I installed them by generating the deb packages but no luck, i had to go back to the free drivers

---

### Post by jimsheep on 2009-07-07
> **razor7 said:**
> Hello...anyone tried the legacy 9.3 driver in Ubuntu 9.04¿? I installed them by generating the deb packages but no luck, i had to go back to the free drivers
i tried using the 9.3 drivers on a Dell Inspiron E1505, with no dice.

---

### Post by Newbie_777 on 2009-10-29
Howdy guys:DI am using Ubuntu Linux for several years now.Currently I am running under Ubuntu Linux 9.04 Jaunty,GNOME 2.26.1. I need to install a video/graphic driver for my system.I actully dont remember which graphic card is in my PC,but I have the installation CD which I got when I bought the graphic card." I have been trying to install Civilization 4,but I am having some severe issues with it. ***When I go to my System>Hardware Drivers there are none listed!:(*** "**The CD that I got with my graphic card** : Graphics by *ATI, Drivers ATI 8.273, Supported OS Win98SE,ME,2000,XP,XP 64 bit." **How can I install the driver and which one do I need ****for playing CIV4?***

---

### Post by halitech on 2009-10-29
> **Newbie_777 said:**
> Howdy guys:DI am using Ubuntu Linux for several years now.Currently I am running under Ubuntu Linux 9.04 Jaunty,GNOME 2.26.1. I need to install a video/graphic driver for my system.I actully dont remember which graphic card is in my PC,but I have the installation CD which I got when I bought the graphic card." I have been trying to install Civilization 4,but I am having some severe issues with it. ***When I go to my System>Hardware Drivers there are none listed!:(*** "**The CD that I got with my graphic card** : Graphics by *ATI, Drivers ATI 8.273, Supported OS Win98SE,ME,2000,XP,XP 64 bit." **How can I install the driver and which one do I need ****for playing CIV4?***

you should have started a new thread instead of reviving such an old thread :)

to answer your question though, chances are the card is no longer supported by ati so whatever drivers are installed are what you have to live with. To find out what card you have, open a terminal and run
```
lspci
```and paste the output here.

---

### Post by Newbie_777 on 2009-10-29
Thanks for a quick reply.***Here is the output:***
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:09.0 Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
01:00.1 Display controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series] (Secondary)

---

### Post by halitech on 2009-10-29
[color="red"]01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series][/color]

here is your video card and it is not supported by the ati drivers so the open source drivers are the only ones that will work.

---

### Post by ssri on 2009-10-29
at the risk of sounding like a broken record, here are the instructions on how to get Catalyst 9.3 to work in Jaunty.

[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

---

### Post by halitech on 2009-10-29
Just to note, while some have had success following those instructions, there is potential for breakage of your system so hold no one responsible if you decide to follow them and your system because unstable or unusable.

---

### Post by Newbie_777 on 2009-10-29
I decided to upgrade my Ubuntu to 9.10 Karmic Koala.I was searching for the driver only because I was trying to install Civilization 4.I just quit trying:(.Thank you halitech and also to you ssri.I very much appreciate your help.I hope that the possibilities with the new Ubuntu will be much greater.And that it will provide more of a gaming spirit than before.:D

---

