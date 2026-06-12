---
title: "Recommendation: Wicd - The Wireless Solution for Newbies"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by Gias Kay on 2008-05-15
I am a new user to Ubuntu who have just installed 8.04 (Hardy Heron) two days ago. The installation and setup process were all smooth except for one yet major part - the wireless. Since I am using a notebook (HP Compaq nc6000), without wireless means losing the ability to get online for most of the time which would effectively render the notebook half-dead, so I was anxious to solve the problem.

I went onto several forums and saw various suggestions, ranging from asking me to download some third party driver for the wireless card which needed to be further "built up" from the source code on my end, to some crazy command line instructions I can't really tell what the freak that was though the answerer kept guaranteeing that should work. But these were all too intimidating for a Linux newbie like me and I couldn't really have the determination to try out those expert-looking "problem-neutralizing attempts" (didn't even have the confidence to say "yep that looks like a working solution for me").

Eventually, I stumbled upon my savior (on this exact forum) - Wicd:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

According to the explanation I found, the current version of the default network manager in Ubuntu is just *incapable* when it comes to **encrypted wireless connections**, and Wicd, coming with a full-fledged GUI, is a better network managing program that can work correctly with the wireless.

I saw the screenshots in the page and the claim seemed to be reliable enough, and there was no horribly long codes and so on, just like how we do things in Windows - install it, set it, problem solved - so I decided to give it a shot.

The installation is quite simple, just follow the instructions inside the "Download" page, then do some more post-setup inside the "FAQ" page; you may or may not have to reboot to make the new problem work, but for me a reboot was necessary. Once you see the Wicd icon on the tray, right click on it and you'll be able to get into the settings. Now just turn on your wireless, wait a few seconds then reload, you can choose from a list of detected networks and the rest is intuitive. Using Wicd, I can even connect to the encrypted WEP network of my home wireless without the password, so I guess it's really the time for me to switch to WPA2.

Unfortunately this handy software seems to be not known by many users who also have problems in trying to get their encrypted wireless connections to work inside the default network manager, so I am writing this from a newbie perspective as an attempt to offer some experience talk for others who are new to Ubuntu as well and have been frustrated over the wireless issue. I also sincerely hope that Wicd can get some deserved attentions from Ubuntu developers and include it into the software repository if not making it the new network managing default :mrgreen:

---

### Post by rustybronco on 2008-05-20
While I have used wicd in the past, network mananger has come a long way since when I first started with ubuntu.
On the hp/compaq nc6000, of which I have the same machine with a hp-w500 (ar5212/ar5213) wireless card installed and wpa encription.
the way that I get the wireless to work for me is, make sure you turn on your wireless switch when it first boots up (the blue light will be on when grub is starting).
if the switch is off upon startup, the light will be off until gdm starts, then it will turn on.
once the blue light is on, it will stay on and will not go off whether you are connected to an access point or not, regardless of the wireless switch position being on or off. 
if the wireless switch is on when first starting grub, when your desktop is fully up it will show the blue tooth icon and your wireless will then be able to connect.
I can't tell you about the w400 (ar5211), but I suspect it will work the same way also.
just for some additional information, the nc6000 the wireless light is software controlled, where the wireless switch is hard wired.

---

### Post by seantm on 2008-05-20
> **Gias Kay said:**
> I am a new user to Ubuntu who have just installed 8.04 (Hardy Heron) two days ago. The installation and setup process were all smooth except for one yet major part - the wireless. Since I am using a notebook (HP Compaq nc6000), without wireless means losing the ability to get online for most of the time which would effectively render the notebook half-dead, so I was anxious to solve the problem.

I went onto several forums and saw various suggestions, ranging from asking me to download some third party driver for the wireless card which needed to be further "built up" from the source code on my end, to some crazy command line instructions I can't really tell what the freak that was though the answerer kept guaranteeing that should work. But these were all too intimidating for a Linux newbie like me and I couldn't really have the determination to try out those expert-looking "problem-neutralizing attempts" (didn't even have the confidence to say "yep that looks like a working solution for me").

Eventually, I stumbled upon my savior (on this exact forum) - Wicd:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

According to the explanation I found, the current version of the default network manager in Ubuntu is just *incapable* when it comes to **encrypted wireless connections**, and Wicd, coming with a full-fledged GUI, is a better network managing program that can work correctly with the wireless.

I saw the screenshots in the page and the claim seemed to be reliable enough, and there was no horribly long codes and so on, just like how we do things in Windows - install it, set it, problem solved - so I decided to give it a shot.

The installation is quite simple, just follow the instructions inside the "Download" page, then do some more post-setup inside the "FAQ" page; you may or may not have to reboot to make the new problem work, but for me a reboot was necessary. Once you see the Wicd icon on the tray, right click on it and you'll be able to get into the settings. Now just turn on your wireless, wait a few seconds then reload, you can choose from a list of detected networks and the rest is intuitive. Using Wicd, I can even connect to the encrypted WEP network of my home wireless without the password, so I guess it's really the time for me to switch to WPA2.

Unfortunately this handy software seems to be not known by many users who also have problems in trying to get their encrypted wireless connections to work inside the default network manager, so I am writing this from a newbie perspective as an attempt to offer some experience talk for others who are new to Ubuntu as well and have been frustrated over the wireless issue. I also sincerely hope that Wicd can get some deserved attentions from Ubuntu developers and include it into the software repository if not making it the new network managing default :mrgreen:
**I've browesd forums for days... And posted... Tired all kinds of command line alchemy just ot get a aeth0 intel running on my Lenov/IBM thinkpad -nothing obsure --no luck Until now. This littel utility did the trick -and quick -I 'didn't even have to compliie it! Thnaks so much I will share this around the fourms...**

---

### Post by Ayuthia on 2008-05-20
This package is also in the Ubuntu repositories so if you want it, you can install it using Synaptic.  Just look for wicd.

Just as an additional note.  This is more for those who should already be able to see wireless networks but can't connect.  There are wireless cards that do need to have some firmware installed before their wireless can start working.

---

### Post by sirzepp on 2008-05-25
I'm currently using WICD and I like it.  It does give me trouble with wired networks sometimes(switching between wireless and wired seems to require deleting the "wired-settings.config" file...  After figuring out that little problem...it works fine.  At least my wireless works flawlessly...something I was struggling with network manager on.  It'd be great if we could just get net-manager to work perfectly.  It's so well integrated into ubuntu.  WICD is just a bit clunky.

---

### Post by dm6257 on 2008-05-25
I experienced similiar problems with a Thinkpad Z61 after the last Hardy  upgrade.  I reloaded 7.10 from an Acronis image and my wireless problems disappeared.

---

### Post by santhony on 2008-06-01
I've been using WICD now for two days with the Broadcomm BCM4603, so far this has stabalized my wirless Connections...   

Thanks:KS:KS:KS:KS:KS:KS

---

### Post by seantm on 2008-06-01
U r welcome! glad your problem is solved Santhany -such a enthusiastic response! So actually here in the forums if we want to officially thank someone we click on the star medal icon next to the reply button --this is an official thanks! But once again -your welcome!

---

### Post by ezufelt on 2008-06-01
Sounds nice.  Does anyone know if this utility can be accessed by Orca?

---

### Post by seantm on 2008-06-02
> **ezufelt said:**
> Sounds nice.  Does anyone know if this utility can be accessed by Orca?
Hi, I'm not sure if it is workable with Orca because I've just learned about this applicaition. However, I see that skype is configurable and other similiar programs so that's encouraigng... Perhaps you can post the Wicd info and this quesiton on the Orca forum or wiki?

---

### Post by jhoe on 2008-06-02
Wicd is GREAT, VERY EASY/USABLE interface.

I have an HP with Broadcomm 43xx.  Solved my problems after I upgraded to Hardy Heron (8.04)!

Funny post because I was about to make a new post praising Wicd.

---

### Post by MagnusS on 2008-09-09
Being fully ignorant in Linux, but having successfully installed Ububtu on a Compaq nw8000 except for it's HP W500 802.11a/b/g wifi, I wonder if the Wicd would be all it takes to get that wifi going?
Or would I still need some driver for it (windows or other).

Anyone knows?

Kind Regards
MagnusS

---

### Post by seantm on 2008-09-09
Should work just fine for you --wysiwyg gui very institutive the only drawback is that with some systems you have to reconnect each time you start up because it detects multiple options for connecting.... But this is a small inconvenience --try it and see...

---

### Post by imdano on 2008-09-09
Having multiple options shouldn't keep it from autoconnecting.  There are some systems that autoconnect doesn't work with, we're just not exactly sure why.

And MagnusS, wicd will only work for you if the wireless driver for your card works correctly as well.  I don't know enough (anything) about your card, so I don't know if it works out of the box.

---

### Post by huwaw69 on 2008-09-09
Do i nid the CD of the installer or something to install the wicd, because when i hit the "RELOAD" button it fails to download... what seems to be the problem?

---

### Post by gordoarcane on 2008-09-09
just downloaded it, set it up, etc etc, but it does not connect me, neither did the original connection manager, hence my post bit further down, looks pretty nice simple interface, but...*sighs* still no wireless for me...and i need it so...any helpers ? x

---

### Post by gordoarcane on 2008-09-09
> **gordoarcane said:**
> just downloaded it, set it up, etc etc, but it does not connect me, neither did the original connection manager, hence my post bit further down, looks pretty nice simple interface, but...*sighs* still no wireless for me...and i need it so...any helpers ? x

Ok i did it, very simply the wired connection gave me the ip address, thus i copyed this into the ip address on the dropdown for the wireless, disconnected, unplugged cable, clicked connect onto wireless and taa daa. Problem solved...*pats self on back* btw i like Wicd, im gonna keep it so many many many thanks to those who made it as its interface and easy to adjust settings helped me to solve a problem !!! :)

---

### Post by shavano47 on 2008-09-10
I am a Newbie and I recently installed Ubuntu 8.0.4 on a Dell Latitude with a Broadcom BCM4306 Wireless LAN Controller (Rev02). I couldn't get the Wireless to work and had the same experience as Gias Kay. I installed WICD and followed all the instructions on //wicd.sourceforge.net. But when I open the WICD Manager I get the message "No wireless networks found" though I know I had a signal before installing WICD. Not only that but I lost the Wired Connection also! The FAQ's on //wicd.sourceforge.net say that I need to download and install the "deb" files fom packages/ubuntu.com and install them with "gdebi" as they were removed in the installation process. Well I don't know what a "deb" file is and I couldn't find any on packages/ubuntu.com and I don't know what "gedebi" is.

I am at my wits end and if I can't get internet connection I will have to reinstall XP which is a pity as I really like Ubuntu. Could someone please help.

---

### Post by imdano on 2008-09-10
Open the preferences window in wicd and make sure it detected your interface names properly.

Also, if you have an eternet cable plugged in you can probably connect to the internet by opening a console and typing ```
sudo ifconfig eth0 up
sudo dhclient eth0
```

---

