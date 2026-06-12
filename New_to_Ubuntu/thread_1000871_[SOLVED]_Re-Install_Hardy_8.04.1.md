---
title: "[SOLVED] Re-Install Hardy 8.04.1 ???"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-12-03
It looks like I may have lost the kernel in the last update which addresses the restricted driver for the wireless connection. Is there a way to re-install 8.04.1 without losing my data files ?

---

### Post by Titan8990 on 2008-12-03
Might be another way but I would recommend backing up and then restoring after the reinstall.

---

### Post by Michael.Godawski on 2008-12-03
Do you have a separate home partition?
Did you make backups?
> 
It looks like I may have lost the kernel in the last update which addresses the restricted driver for the wireless connection.Can you please be more specific? Have you lost your wireless connection. can you login into Ubuntu? Perhaps there is a less-direct intervention possible than a fresh install.

---

### Post by Kobalt on 2008-12-03
> **Michael.Godawski said:**
> Do you have a separate home partition?
If you reinstall then you should really consider [having a separate home partition.]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by CoCoKnots on 2008-12-03
I had an another thread addressing this issue... [http://ubuntuforums.org/showthread.php?t=999731&highlight=CoCoKnots](http://ubuntuforums.org/showthread.php?t=999731&highlight=CoCoKnots) . I'm new to Ubuntu & quite honestly, I feel like I get over my head at times. Last night I thought if I was able to re-install Hardy without loosing my data, I might be able to retrieve the kernal for my wirless & not deal with the updates which I feel may have caused the problem in the first place.

Also, Kobalt... I tried: System > Administration > Partition Editor to see what was involved in setting up a home partition. The 'Partition Editor' is not listed in my Sys>Admin> tab. I believe it states that I need the CD to do this exercise.

---

### Post by stchman on 2008-12-03
> **CoCoKnots said:**
> It looks like I may have lost the kernel in the last update which addresses the restricted driver for the wireless connection. Is there a way to re-install 8.04.1 without losing my data files ?

Did you try selecting one of the older kernels on bootup?  If you are running an Ubuntu only machine pressing ESC at the GRUB screen will give you a list of kernels.

---

### Post by Michael.Godawski on 2008-12-03
Let's see what is left after the battleground has cleared...

In terminal
```
cat /boot/grub/menu.lst
```This will show us what options there are available during the start up.

---

### Post by CoCoKnots on 2008-12-03
Thanks Stchman, Here is a snapshot of the bottom part of the grub menu. As you can see it has 5 different options. How do I know which one I need & how do I activate it as the default for the boot?

---

### Post by CoCoKnots on 2008-12-03
Michael, When I tried to run cat /boot/grup/menu.lst, it came back with no such file or directory.

---

### Post by Michael.Godawski on 2008-12-03
> How do I know which one I need & how do I activate it as the default for the boot? 	

Did you try them out? 
> 
All you have to do is choose the kernel you want to boot at the Grub menu. Or edit menu.lst and change default=0 for the corresponding number keeping in mind that Grub starts to count from 0.Pumalite

---

### Post by ugm6hr on 2008-12-03
> **stchman said:**
> Did you try selecting one of the older kernels on bootup?  If you are running an Ubuntu only machine pressing ESC at the GRUB screen will give you a list of kernels.

Pick the 3rd from top option after pressing Escape at bootup Grub option.

---

### Post by oldos2er on 2008-12-03
> **CoCoKnots said:**
> Michael, When I tried to run cat /boot/grup/menu.lst, it came back with no such file or directory.

 The proper command is

cat /boot/grub/menu.lst

---

### Post by CoCoKnots on 2008-12-03
Ok... I hit esc while re-booting. I was only able to see two of the options available. The 2nd & 4th appear to be restore versions of the 1st & 3rd. I entered the 3rd option as ugm6hr suggested. It didn't make any difference. I'm still in a haze about what you were discussing Michael as to exactly what to change. I did not see any numbers listing t

---

### Post by CoCoKnots on 2008-12-03
Obviously, I am currently hard wired into the internet. When I click on the double monitors, it is showing both the lan & wireless options available. So it's seeing that I have a Linksys router. When I click on the wireless  it will not connect. It just keeps searching. Alos the little light which normally comes on during this process isn't working either, if that means anything at this point.

---

### Post by Michael.Godawski on 2008-12-03
Sorry for the typo. 

I just thought your loosing your wlan connection had something to do with the new kernel. But when you say you booted into the other, older kernel and the wlan did not work either, then I was on the wrong track.

---

### Post by ugm6hr on 2008-12-03
> **CoCoKnots said:**
> Ok... I hit esc while re-booting. I was only able to see two of the options available. The 2nd & 4th appear to be restore versions of the 1st & 3rd. I entered the 3rd option as ugm6hr suggested

Presumably you mean you have 4 (not 2) options then, and you picked the 3rd.

I have just read the other thread you had started (and closed it).

To summarise that thread, and your previous actions:

Intel 3945ABG wifi card
iwl3945 driver correctly installed
Lost wifi after kernel update to 2.6.24-22-generic
Tried to mess around with ndiswrapper (didn't get very far)
Removed kernel 2.6.24-22 related image, headers, modules and restricted modules.

Since then:
Tried kernel 2.6.24-21 and 2.6.24-19 from Grub - still no wifi.

Did a quick search, and discovered that the iwl driver is in the kernel since 2.6.24, so there is no need for Restricted Drivers (Ref: [http://intellinuxwireless.org/?p=iwlwifi](http://intellinuxwireless.org/?p=iwlwifi))

However, further digging does reveal that others have had similar iwl breakages with kernel updates; problems are also reported with 2.6.24-21 (which presumably did work for you before).

I'm afraid I don't have an Intel card to try and confirm the problems you've been having.  But hopefully this summary will help you search more efficiently, and allow others to offer useful advice.

---

### Post by CoCoKnots on 2008-12-03
Could I be going down the wrong path here. Could there be a short of some kind which only effected part of my wireless system allowing it to detect the Linksys router but not able to connect. I know it's unlikely & for all of this to happen after downloading an update sure is strange... It just sounds like a driver problem... or hardware ???

---

### Post by CoCoKnots on 2008-12-03
Great Job ugm6hr. It looks like you have it in a nutshell. Do you have a thought one way or another about this may be a strange hardware porblem?

---

### Post by Michael.Godawski on 2008-12-03
I think it is unlikely that it is a hardware issue, since the intel wlan chipsets used to work with Linux very well. 

But when you look in launchpad for bugs related with your card you get a bunch of answers:


[LIST]
[*][https://launchpad.net/+search?field.text=Intel+3945ABG](https://launchpad.net/+search?field.text=Intel+3945ABG)
[/LIST]
So perhaps it is just a temporally issue, till the next kernel update.

---

### Post by CoCoKnots on 2008-12-03
I hope you're right Michael. I may just live with a lan cable for a while & give Hardy a chance to catch up with the bug.

---

### Post by CoCoKnots on 2008-12-05
Here's a twist for you... It now looks like possibly when I downloaded the update a few days ago, it may have altered the soft settings in the Linksys router. Here is a recap of the conversation with the customer service department at Linksys. I found I could get a wireless connection at the local library... But was still unable to connect on the wireless at home. Here are step by step instructions for those of you who have had the same experience... Hope it helps. 
 
[I]
1. Open a new Internet Explorer window, type "192.168.1.1" in the Address bar and press Enter.

2. When it asks for a User name and Password, just leave the User name field blank and type the password you set for the router. If you didn't set a password, the default is "admin".

3. On the setup page, please click on the Wireless tab, and tell me the settings there.

Cal: Mixed linksys 6-2.437Ghz Enable

August: Thank you. Please choose a new name for your wireless network and enter it in the Wireless Network Name (SSID) box, replacing "linksys", then click Save Settings.
August.Okay, please click on the Wireless Security sub tab.
August: Is the Security Mode set to Disabled? 
Cal: Settings are Successful.... Continue

August: Nice. Please click the "Wireless Security" sub tab.
August: Is the Security Mode there set to WEP?
August: click on "Wireless Security" below it.
Cal: WPA Personal. Should that be WEP ?

August: No, leave the Security Mode as is.
August: Choose a password for your wireless network and enter it in the WPA Shared Key box. This can be any word or phrase at least 8 characters long.
August: Okay, lastly, click on the Status tab.
August: Under Status, what's the Login Type and Internet IP Address?
Cal: Login Type: Automatic Configuration - DHCP
IP Address: 169.254.1.2

August: Thank you. Let's try connecting the laptop to your new wireless network.
August: Is it an XP or Vista laptop?
Cal: Ubuntu Linux 8.04.1
Cal: I am Hardwired now... Do you want me to simply disconnect ?

August: No, not yet.
August: Try connecting the laptop to your wireless network, and enter the wireless password when prompted.
Cal: Do I stay hardwired ?

August: Yes, for now.
August: Were you able to connect to the wireless network?
Cal: yes

August: Okay, please unplug this laptop from the router, and check if you can now go online wirelessly.
Cal: It looks like it's working
August: Yes.
Cal: Thank you very much... Great Support[/I]
):P

---

### Post by P235 on 2008-12-09
For what it is worth, I share the same situation as CoCo with my Atheros card immediately after I installed the kernal update.  I recently set my laptop to dual boot with Vista and 8.04, and ndiswrapper worked quite well up until I ran synaptic and restarted.  Now the wireless works on some reboots and not on others.  

When I thought between setting my laptop for dual boot or full linux I was on the fence, but these tricky updates suggest that the dual boot choice was a good idea.  I hope the next update will come quick.

---

