---
title: "No internet after clean Heron install."
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by Nathan Otis on 2008-07-27
Greetings all.

Last night I decided to totally wipe out my windows partition, back everything up and do a clean install of H. Heron. The PC was working well before this plan was put into action with the exception of an error on start up that began after my update to Heron from Eft or Fawn (I don't recall which I was running at the time I upgraded).

Install seemed to go flawlessly.

The Heron desktop came up for the first time and I readied myself for the onslaught of updates that I knew was coming... Except they didn't.

I clicked the Firefox icon and it seems I have no internet connectivity.

I've tried to ping my router and Heron can't reach it. This Windows PC that I'm posting from is connected to the same router and is connecting fine.

I've swapped the ethernet cable and tried a different jack on my router. I've connected Heron directly to the modem, power cycled the modem and still no connection.

This tells me it's pretty clearly a Heron issue... And now I'm stuck.

What now?

---

### Post by Kevbert on 2008-07-27
What's the wireless card chipset ?  Please enter
```
lspci
ifconfig
iwconfig
```
in terminal and post the outputs here.
Also go to System-Admin-Software sources and check that all boxes under Ubuntu software are ticked and under the Updates Important, Recommended and Unsupported Update boxes are ticked.

---

### Post by Nathan Otis on 2008-07-27
I'm sorry. It seems my problems run a little deeper than just internet connectivity... The thumbdrive I'm trying to use to copy info back and forth isn't mounting... I'm going to search for how to get that done and hopefully post the results you requested soon.

Thank you.

---

### Post by Nathan Otis on 2008-07-27
> **Kevbert said:**
> What's the wireless card chipset ?  Please enter
```
lspci
ifconfig
iwconfig
```
in terminal and post the outputs here.
Also go to System-Admin-Software sources and check that all boxes under Ubuntu software are ticked and under the Updates Important, Recommended and Unsupported Update boxes are ticked.

Also very important to mention... I'm not trying to connect via wireless.

---

### Post by Kevbert on 2008-07-27
OK. So when you installed Hardy Heron did you have the ethernet cable connected and the router on ?  It should have been detected automatically.  If the Software Sources were not enabled, it suggests no connection was available.
Did you perform a hash check on the downloaded ISO file prior to burning it to CD at the lowest speed available and then checked the CD via the front end (built in) menu ?  If you're having several problems it suggests that you may have a suspect CD.

---

### Post by Nathan Otis on 2008-07-27
> **Kevbert said:**
> OK. So when you installed Hardy Heron did you have the ethernet cable connected and the router on ?  It should have been detected automatically.  If the Software Sources were not enabled, it suggests no connection was available.
Did you perform a hash check on the downloaded ISO file prior to burning it to CD at the lowest speed available and then checked the CD via the front end (built in) menu ?  If you're having several problems it suggests that you may have a suspect CD.


Ethernet cable was connected, router was on. I had googled some info on the machine just before I fired up the install cd. The sources were enabled when I checked.

I burned the CD @ 4x... not as slow as possible, but pretty slow. Before I started the install, I checked the CD from the menu that comes up on the LiveCD.

I'll try burning the CD even slower and reinstall... Hopefully, I will not have to post back here, except to say thanks.

---

### Post by Kevbert on 2008-07-27
Seems like you've done the right things so far and 4x should be slow enough.
The ISO file should be [COLOR="Red"][hash checked]("https://help.ubuntu.com/community/HowToMD5SUM")[/COLOR] before burning.

---

### Post by Nathan Otis on 2008-07-27
I should have stayed with my wonky Heron upgrade cause this 2nd Clean Heron install isn't working either... 

I downloaded the iso (8.04.1) again (no problem there), used WinMd5Sum to check the hash (which matched), burned the disc at **_2x!!_** (no errors there, either).

Install went off w/o a hitch.

Fire it up. No internet.

---

### Post by Nathan Otis on 2008-07-27
Well, something is different. I can ping the router.

Still no internet, though.

---

### Post by Kevbert on 2008-07-28
This is a wild guess.  If you go to System-Admin-Network and display Network Settings, do you have Wired Network Roaming selected.  You may have to unlock the settings with your log-in password.  DNS should be set to your router address (something like 192.168.0.1).
Please take a look at this [post]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/unable-to-connect-to-internet-via-wireless-or-wired-connection-556771/") 
If you right-click on the two display icon in the top right-hand menu bar is networking ticked ?
Other than that I'm not sure what to suggest.

---

### Post by Nathan Otis on 2008-07-28
It was set to roaming! What the heck is that!?

So, I've disabled roaming and set the configuration to "Auto config (DHCP)". I also put my router address in DNS. Now Firefox takes a much longer time to tell me it can't find anything.

I think that's a step in the right direction.

It makes me wonder about the General and Host settings under Network Settings, and also under System/Admin/Network Tools, there are two Ethernet Interfaces, and one device called Loopback.

The mind boggles at all I do not know...

---

### Post by dietkinnie on 2008-07-28
What ips are the default gateway and dns set to ?

you might also need to add your dns server ip or ISP's dns server ip in /etc/resolve.conf

---

### Post by Kevbert on 2008-07-28
> **Nathan Otis said:**
> It was set to roaming! What the heck is that!?

So, I've disabled roaming and set the configuration to "Auto config (DHCP)". I also put my router address in DNS. Now Firefox takes a much longer time to tell me it can't find anything.

I think that's a step in the right direction.

It makes me wonder about the General and Host settings under Network Settings, and also under System/Admin/Network Tools, there are two Ethernet Interfaces, and one device called Loopback.

The mind boggles at all I do not know...


I'm not sure what is meant by roaming on a wired connection but that's what my PCs are set to and they work fine. The only thing I have under the General tab is the host name I've given my PC (so that others can see this name on my network).  Under Host Settings I have such things as 127.0.0 localhost and ::1 ip6-localhost ip6-loopback.  I can connect via ethernet or wireless and everything works fine.  If you still are pulling your hair out you could try asking a question on [[COLOR="Red"]launchpad[/COLOR]]("https://answers.launchpad.net/") where all the experts reside.

---

### Post by Nathan Otis on 2008-07-28
> **dietkinnie said:**
> What ips are the default gateway and dns set to ?

you might also need to add your dns server ip or ISP's dns server ip in /etc/resolve.conf

I'm away from the machine til later, but if I recall correctly, the IP and Gateway were both blank and uneditable. There was an option to set up a static IP, but I don't have one. I set it to "Auto Config DHCP" as stated above, then I set the DNS to my router IP per Kevbert's advice.

---

### Post by Kevbert on 2008-07-28
Hi again.  I've taken some screenshots of my network settings.  The pictures are attached.  Hope this is of use.

---

### Post by Nathan Otis on 2008-07-28
> **Kevbert said:**
> Hi again.  I've taken some screenshots of my network settings.  The pictures are attached.  Hope this is of use.

No luck. My settings are similar to yours in every way. Still no web action.

> **dietkinnie said:**
> What ips are the default gateway and dns set to ?
you might also need to add your dns server ip or ISP's dns server ip in /etc/resolve.conf

That file reads: nameserver 192.168.0.1


Maybe I'll make a Feisty or Gutsy CD... Those worked for me.
Signed, Frustrated and totally lost.

---

### Post by Nathan Otis on 2008-07-28
And I've tried using my windows machine's network settings as a means to set network settings on the Heron machine... no luck.

---

### Post by Nathan Otis on 2008-07-29
> **Kevbert said:**
> ... If you still are pulling your hair out you could try asking a question on [[COLOR="Red"]launchpad[/COLOR]]("https://answers.launchpad.net/") where all the experts reside.

I'm folicly challenged, so there will be no (further) hair loss due to this issue, but I though all the experts were here!?
n.

---

### Post by Nathan Otis on 2008-07-31
If you'd like to follow along with the frustration, join me here...

[https://answers.launchpad.net/ubuntu/+question/40745](https://answers.launchpad.net/ubuntu/+question/40745)

---

### Post by Nathan Otis on 2008-08-02
Just FYI, I figured this one out myself. I was nosing through the BIOS as a last ditch before installing XP on this PC and I disabled the onboard modem. I crossed my fingers, restarted and I had internet access.

Thanks all for trying.
n.

---

