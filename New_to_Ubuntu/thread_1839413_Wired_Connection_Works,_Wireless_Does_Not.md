---
title: "Wired Connection Works, Wireless Does Not"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by ricarpe on 2011-09-05
Good afternoon!

I decided to make the lengthy upgrade to Ubuntu 11.04 over the Labor Day weekend.  Almost everything is working well.  

A personal complaint I have with 11.04 is that it's a little too much technically.  I don't like the sidebar that autohides, and I don't like the layout where I now have to hunt for 'Applications' and 'Folder', etc.  Maybe I'll get used to it... maybe not.

The complaint I do have is that my wireless card does not work.  I can plug in to my router with an ethernet cable and everything works fine, but my laptop isn't my home machine so wireless is a necessity.

I have an old Dell Inspiron 1501 with an AMD chipset.  I would get you more information on the computer itself, but I'm having trouble navigating the UI.

I have run the Ubuntu Help using nm-tool and iwconfig, etc., but no joy there either.  The driver is present and, again, the laptop works fine when plugged in via ethernet cable.  When I click on the 'Network' icon at the top I get no wireless network to connect to.  The other wireless devices in the house -- my wife's laptop and my B&N Nook Color -- are actively connected to the network as I type.

Any assistance is greatly appreciated.

Rich

PS: As a back up, I have the CD for 10.04... I have thought about "downgrading" since that is an LTS version and I have used it before/am comfortable with it.

---

### Post by ricarpe on 2011-09-05
As a follow up:

I did search the forums and tried several of the tips and how-to's there.  

1. I've used Synaptic Package Manager to search for 'bcm' and then download the bcm43 packages. 

2. When I use the terminal window and type in 'lspci', I get the following return:

05:00.0 Network controller: Broadcom Corporation BCM4311 802.11 a/b/g (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

3. When I type in sudo iwconfig, I get the following return:

lo     no wireless extensions

eth0     no wireless extensions

4.  I did follow the Ubuntu Help guide, but nothing came of that.  I know that the ethernet card is present; and, that it works when physically plugged in to the router.

---

### Post by Ad1217 on 2011-09-05
have you tried jockey-gtk? that has worked for finding the drivers for my two computers with broadcom cards.

---

### Post by ricarpe on 2011-09-05
@ Ad1217:

No, I haven't tried anything for finding drivers.  I've been reading a few sites and others with similar problems (older ethernet adaptors, some with Broadcom) have had no luck with add-on programs that search for drivers or assist with detecting their networks.  I just skipped that as an option.

I'll give that a try and see if I can find a fix for it.  

The thing is, I need this computer running immediately.  I use it to do my homework assignments for my econ grad program.  I think I may end up downgrading back to 10.04.

---

### Post by gandaran on 2011-09-05
> 05:00.0 Network controller: Broadcom Corporation BCM4311 802.11 a/b/g (rev 01)
connect with wired internet and wait a few minutes to update software package list then look in additional drivers to enable the broadcom driver.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by ricarpe on 2011-09-05
@ gandaran:

Thank you for the link.  I tried something similar earlier, but I read the instructions in that post.  I'm going to try them now and see what happens.

---

### Post by ricarpe on 2011-09-05
"firmware-b43-installer version 4.150.10.5-5 failed to install/upgrade."  I submitted the trouble report, but than got an error message that the crash report could not go through becuase... well, because I now have no internet connection whatsoever, wired or wireless.

This is becoming more trouble than it's worth.  Now, even when I click on "Enable Network" I get the message that I'm disconnected and offline.

I followed the instructions from the link gandaran gave, including the more "advanced" stuff... no luck there, either.

I've been reading threads on these forums of people with similar  problems with various model laptops with mixed reports of success.  It's 4:46PM on the east coast of the US... I would honestly love to sit and play around with this, but I can't.  I need this laptop for my classes.

Thanks for the help.

I'm going to have to downgrade to 10.04 because I know that it works.

---

### Post by garvinrick4 on 2011-09-05
Your wireless card works with these two installed (type bcm in the search window of synaptics and remove all but these two) Wired should work out of box as it was. Will
have to have these 2 installed if you go back to 10.04. Use wired connection to install
these 2 packages and then remove wire and reboot.

---

### Post by ricarpe on 2011-09-05
@ garvinrick4:

Yeah, that was in the instructions that gandaran sent, as well as a few other threads in this forum.

I followed the instructions, used the terminal window, enabled and disabled, removed and installed, etc.  No luck on getting it to work.

I'm not worried about it anymore.  I've already got 10.04 LTS back on the laptop.

As I said, I need this laptop for my grad program so immediacy trumps novelty.

Again, I'd like to thank everyone for the help.  I'm going to stay with 10.04 LTS for the foreseeable future.

Rich

---

