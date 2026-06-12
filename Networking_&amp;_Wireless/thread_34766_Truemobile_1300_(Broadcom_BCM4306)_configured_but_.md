---
title: "Truemobile 1300 (Broadcom BCM4306) configured but not working"
date: 2005-05-16
forum: Networking &amp; Wireless
---

### Post by xsoldier1911 on 2005-05-16
I followed the directions here:
[http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto)
I was able to confugure my wirless card and it shows up under network settings under wireless connection wlan0.  When I was setting up the properties I did not have to type in the name of my SSID because it was already listed, which tells me that the card must be working.  I disabled the ethernet connection and enabled the wlan0.  Network settings says the card is active but I do not see any blinking lights and I cannot connect to the net.  Can someone please advise me on what I have to do to get my wirless lan working, I am trying to get away from Microsoft and have tried fedora, suse, mandrake, and now ubuntu.  Ubuntu was the only distro I was able to actually get my card installed on which is a big plus, so if I can get it working ubuntu will be my distro of choice from now on.

Thanks in advance for any help,
John

---

### Post by xsoldier1911 on 2005-05-16
nevermind, I disabled the encryption and 4x support for my wireless router and rebooted the laptop.  When it started back up everything was working.
Thanks anyway,
John

---

### Post by bowie101 on 2007-05-06
i am having a very similar experience, although, not exactly. 

I set up my truemobile 1300 on my Dell Insipron 5000e by following the directions for NDIS wrapper, and getting the right driver by following the NDIS wrapper direction to a T. 

It worked. I had a wireless internet connection. 

Then I turned the computer off , brought it downstairs, and booted up again .  Now the light is not flickering on and off on the card itself, and there is no internet access. It detects that the card is present, but one thing I noticed when looking at the wireless info within the computer itself via command line, of which I hardly understand or remember yet, is that it said 

"no  access point", 

 which I figured is the root of my problem, as I wonder exactly what an access point is. I thought it was similar to mounting or something. 

So, I'd love to know how to fix this. You said you turned off encryption. Was that with the lap top, or with all your wireless connections? You unencryped your password, or removed password protection entirely, thus making your network, in effect, public? 

If that's the solution, then OK, but I want to be clear of what path I'm following , and with some hope, follow the right one. 

really technical from me today, huh?  maybe more tech info when i get the laptop in front of me.

---

