---
title: "Dell Inspiron 1525 wifi issue, Broadcom BCM4312"
date: 2014-04-23
forum: Networking &amp; Wireless
---

### Post by Frank_Cowley on 2014-04-23
Can somebody please help me?
I am a complete novice at computers. my laptop, Dell Inspiron 1525, was running windows Vista which was shocking and kept crashing it. I loaded Zorin onto it in the vein hope of speeding it up, which it looks to have done and also sorted the crashing issues.
Unfortunately, I can no longer get WiFi.
I have tried following a previous thread of loading a 'b43' into the /lib/firmware but this hasn't produced any joy.
I then tried the 'rfkill list' & 'lsmod' which bought up a whole load of jargon (i've absolutely no idea what I was looking at).

Please help as this is driving me mad :(

i'm clearly a simpleton.

---

### Post by Frank_Cowley on 2014-04-23
Can somebody please help me?
I am a complete novice at computers. my laptop, Dell Inspiron 1525, was running windows Vista which was shocking and kept crashing it. I loaded Zorin onto it in the vein hope of speeding it up, which it looks to have done and also sorted the crashing issues.
Unfortunately, I can no longer get WiFi.
I have tried following a previous thread of loading a 'b43' into the /lib/firmware but this hasn't produced any joy.
I then tried the 'rfkill list' & 'lsmod' which bought up a whole load of jargon (i've absolutely no idea what I was looking at).

Please help as this is driving me mad :(

i'm clearly a simpleton.

---

### Post by Double.J on 2014-04-23
Hi there, Welcome to the forums!


This most commonly happens with Broadcom wireless drivers (because ubuntu is open source, it can't distribute some non- open source drivers)
 
If you haven't already, see if ubuntu can resolve it itself with additional drivers. Press the windows key and type additional drivers.




If this doesn't work, let's find out what card you have; Could you open up a terminal and run
```
lspci -vnn | grep Network
```


Jj

---

### Post by mörgæs on 2014-04-23
Please stop multiposting.
Merged.

---

### Post by SeijiSensei on 2014-04-23
Another option is to spend a [few bucks]("http://www.amazon.com/gp/offer-listing/B003CNYG8E/ref=dp_olp_new?ie=UTF8&condition=new") on a well-supported Intel wifi adapter for the Inspiron.  I always choose Intel wifi when the choice is offered, as it was when I ordered an equivalent Dell laptop with this adapter some years back.  Intel's drivers are open-source and included in the Linux kernel by default.

I avoid Broadcoms like the plague given their proprietary nonsense.

---

### Post by Frank_Cowley on 2014-04-23
Hi,
OK, so I've tried the 'lspci -vnn grep Network' as advised.
below is what came out (i've no idea what its telling me?):
alexandra@alexandra-Inspiron-1525:~$ lspci -vnn / grep Network
Usage: lspci [<switches>]


Basic display modes:
-mm		Produce machine-readable output (single -m for an obsolete format)
-t		Show bus tree


Display options:
-v		Be verbose (-vv for very verbose)
-k		Show kernel drivers handling each device
-x		Show hex-dump of the standard part of the config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-b		Bus-centric view (addresses and IRQ's as seen by the bus)
-D		Always show domain numbers


Resolving of device ID's to names:
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-q		Query the PCI ID database for unknown ID's via DNS
-qq		As above, but re-query locally cached entries
-Q		Query the PCI ID database for all ID's via DNS


Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]			Show only devices with specified ID's


Other options:
-i <file>	Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>	Look up kernel modules in a given file instead of default modules.pcimap
-M		Enable `bus mapping' mode (dangerous; root only)


PCI access options:
-A <method>	Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>	Set PCI access parameter (see `-O help' for a list)
-G		Enable PCI access debugging
-H <mode>	Use direct hardware access (<mode> = 1 or 2)
-F <file>	Read PCI configuration dump from a given file
alexandra@alexandra-Inspiron-1525:~$ lspci -vnn grep Network
Usage: lspci [<switches>]


Basic display modes:
-mm		Produce machine-readable output (single -m for an obsolete format)
-t		Show bus tree


Display options:
-v		Be verbose (-vv for very verbose)
-k		Show kernel drivers handling each device
-x		Show hex-dump of the standard part of the config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-b		Bus-centric view (addresses and IRQ's as seen by the bus)
-D		Always show domain numbers


Resolving of device ID's to names:
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-q		Query the PCI ID database for unknown ID's via DNS
-qq		As above, but re-query locally cached entries
-Q		Query the PCI ID database for all ID's via DNS


Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]			Show only devices with specified ID's


Other options:
-i <file>	Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>	Look up kernel modules in a given file instead of default modules.pcimap
-M		Enable `bus mapping' mode (dangerous; root only)


PCI access options:
-A <method>	Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>	Set PCI access parameter (see `-O help' for a list)
-G		Enable PCI access debugging
-H <mode>	Use direct hardware access (<mode> = 1 or 2)
-F <file>	Read PCI configuration dump from a given file
alexandra@alexandra-Inspiron-1525:~$

---

### Post by Frank_Cowley on 2014-04-23
Also, I tried the Windows Key thing.
[I]I kept pressing it but nothing was happening?
Great! I've now managed to type in italic?! how on earth did I do this????
one thinks one's too stupid to own a laptop lol! [/I]

---

### Post by Frank_Cowley on 2014-04-23
Hi Jj, I've posted the Terminal report regarding the wifi card.

Many thanks for your help

---

### Post by SeijiSensei on 2014-04-23
> alexandra@alexandra-Inspiron-1525:~$ lspci -vnn / grep Network

You need to use the vertical bar "|" not the slash "/".  The vertical bar is the "pipe" character.  It tells the shell to take the output of one command and feed it to another program as input.  In this case it tells the shell to run the lspci command ("list pci") with some options and feed the result to a program called "grep" that will extract all lines with the word "Network" in them.  

(By default, grep is case-sensitive; here it will match "Network" but not "network".  You can make grep case-insensitive by including the "-i" option.  Then "grep -i Network" would match all possible mixed-case spellings as would "grep -i network".)

---

### Post by Frank_Cowley on 2014-04-23
Thankyou Sensei, much appreciated.
errrr - where do I find the vertical character?

---

### Post by chili555 on 2014-04-23
Right there. We'd actually rather see:```
lspci -nn | grep 0280
```

---

### Post by Frank_Cowley on 2014-04-23
aha! found it ||| :)

---

### Post by Frank_Cowley on 2014-04-23
alexandra@alexandra-Inspiron-1525:~$ lspci -vnn | grep Network
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
alexandra@alexandra-Inspiron-1525:~$

---

### Post by chili555 on 2014-04-23
Please hook up the ethernet temporarily, open a terminal and do:```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet, reboot and let us have your report.

---

### Post by Frank_Cowley on 2014-04-23
Hi Chili, I entered your code and the below is its prompt. (I think it's the same answer)
alexandra@alexandra-Inspiron-1525:~$ lspci -nn |grep 0280
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
alexandra@alexandra-Inspiron-1525:~$

---

### Post by Frank_Cowley on 2014-04-23
Chili, you're a genius!!!!!!
I am now working wirelessly.
My wifi light still hasn't come on but no bother.
do you still need the report? its very long.

---

### Post by Frank_Cowley on 2014-04-23
A great big thankyou to everyone for their support on this matter, I had lost 8hrs trying to work it out and it was sorted in a few minutes with your help.
it's now nearly 2am so sleep time.
thanks again its much appreciated as my niece now has a working laptop to learn on as of tomorrow ;)

you guys/girls are the best. big love!

---

### Post by chili555 on 2014-04-23
We have all we need!> I am now working wirelessly.Please use thread tools at the top to mark Solved.

---

### Post by Double.J on 2014-04-24
Hi there  Frank_Cowley,

Very glad to hear you have managed to get online! Sorry for not having checked back sooner - real life got in the way. Big thanks to chilli and sensei for picking up the torch

Jj

---

### Post by samad260 on 2014-05-31
> **chili555 said:**
> Please hook up the ethernet temporarily, open a terminal and do:```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet, reboot and let us have your report.


This works like charm :) thanks alot Chill you are gr8...

---

### Post by s9032g@comcast.net on 2014-05-31
On my Dell it is with the hyphen - underscore _ key as a Fn click. 

When you choose your sources for updates are you choosing "third party sources"? You need to do that in order to run your driver. If you have not done so, run an update after choosing third party, then look for additional drivers. It should spot the Broadcom. When you see it click next to it and it will enable. A while back that turned out to be my simple solution after trying all sorts of suggested terminal commands.

I suggest that you try this before preceding with terminal solutions.

---

### Post by chili555 on 2014-05-31
> **s9032g@comcast.net said:**
> On my Dell it is with the hyphen - underscore _ key as a Fn click. 

When you choose your sources for updates are you choosing "third party sources"? You need to do that in order to run your driver. If you have not done so, run an update after choosing third party, then look for additional drivers. It should spot the Broadcom. When you see it click next to it and it will enable. A while back that turned out to be my simple solution after trying all sorts of suggested terminal commands.

I suggest that you try this before preceding with terminal solutions.Unfortunately, the 'Additional Drivers' tool installs the wrong driver in several cases. The only way to be sure to get the correct driver is to consult the Broadcom sticky at the top. Not all Broadcoms use the same driver.

---

### Post by s9032g@comcast.net on 2014-06-19
Isn't it still worth a try simply because it is the easiest solution? I can see online that this solution has worked for many with the problem over several years. My belief is to start with the simple, then move on if necessary. I have been messed up more than once by overly complicated solutions proposed by well-meaning helpers.

I do appreciate the work you have done at this site for a long time.

H.A.N.D.

---

### Post by chili555 on 2014-06-19
> **s9032g@comcast.net said:**
> Isn't it still worth a try simply because it is the easiest solution? I can see online that this solution has worked for many with the problem over several years. My belief is to start with the simple, then move on if necessary. I have been messed up more than once by overly complicated solutions proposed by well-meaning helpers.

I do appreciate the work you have done at this site for a long time.

H.A.N.D.I invite you to go right ahead. Please let us know how you get on.> I can see online that this solution has worked for many with the problem over several years.With your _exact _same device as verified in *lspci*??

---

### Post by furieh on 2014-12-19
Sorry for bumping this, but the @comcast.net guy is right. It's about the third time I try Ubuntu (I settled with 14.04 LTS Gnome) and this solution works every time: 
During install choose both "third party sources" and "download packages during install" then update your system and reboot.
Look for additional drivers, select enable the Broadcomm, done.
Same device as **lspci** chilli, sorry. 
```
Broadcom Corporation BCM4312 802.11b/g LP-PHY
```

---

### Post by jeremy31 on 2014-12-19
> **furieh said:**
> Sorry for bumping this, but the @comcast.net guy is right. It's about the third time I try Ubuntu (I settled with 14.04 LTS Gnome) and this solution works every time: 
During install choose both "third party sources" and "download packages during install" then update your system and reboot.
Look for additional drivers, select enable the Broadcomm, done.
Same device as **lspci** chilli, sorry. 
```
Broadcom Corporation BCM4312 802.11b/g LP-PHY
```

If you have a Broadcom Ethernet chipset that uses the b44 module, I would strongly advise against using the bcmwl-kernel-source, broadcom-sta-common or broadcom-sta-dkms as a first choice and try installing firmware-b43-installer```
sudo apt-get install firmware-b43-installer
``` as the first step because if you install one of the other packages first, it will blacklist the module you need to connect to ethernet and installing firmware-b43-installer blacklists nothing

---

### Post by furieh on 2014-12-20
Yes, that is correct Jeremy. I agree on not touching the kernel and go for the B43 firmware firstly, because it has less potential to do any harm (you can just remove the package if it doesn't work).
If that doesn't work, you can move on to more radical solutions like touching the kernel (my gut tells me it's not going to solve anything the firmware can't).
Leave the kernel for the developers ;)
Cheers, and thanks for the helpful and selfless contributions,
Martin

---

### Post by chili555 on 2014-12-20
If I may, I'd like to expand a bit on my colleague Jeremey's excellent post. If you have this chipset:> Broadcom Corporation [COLOR="#FF0000"]BCM4312[/COLOR] 802.11b/g [COLOR="#FF0000"]LP-PHY[/COLOR]Then you should refrain from using the Broadcom STA driver, also known as bcmwl-kernel-source, because it doesn't work well and, in most cases, it doesn't work *at all*. We spend many hours every day here and at askubuntu undoing the incorrect driver for Broadcom devices. Many of you searchers out there are under the mistaken impression that you may select either the STA driver or b43 and firmware for any Broadcom device.

That is incorrect. It is also the case that the Additional Drivers tool often cheerfully offers to install the *wrong* driver!!! Moreover, Broadcom's own documentation is dead wrong on several devices.

I spent weeks working on the sticky and tried to verify at least three cases confirming the suggested method: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110) While nothing and no-one is perfect, in 98% of cases, the method I propose in the sticky works and is verified by many other identical cases.

---

