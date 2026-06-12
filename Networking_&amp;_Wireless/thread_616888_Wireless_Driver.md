---
title: "Wireless Driver"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by djm5091 on 2007-11-18
My laptop's wireless does not work on Ubuntu.  The wired connection worked out of the box though.

There is no driver loaded and assigned to the device.  At this point, I believe I have two options

1.  Find a driver

2.  Use ndiswrapper

I'd like to just find an Ubuntu driver first if at all possible, but I don't know where to look.  I have a Lenovo Thinkpad R60e.  The wireless card is from Atheros Communications, Inc.  AR5212 802.11abg NIC
The pciid is 168c:1014

---

### Post by djm5091 on 2007-11-18
I just looked through the list of ndiswrapper supported cards and my pciid did not show up.  Does that mean I can't use ndiswrapper?

---

### Post by kevdog on 2007-11-18
ndiswrapper should work not all cards are listed

---

### Post by djm5091 on 2007-11-18
I went to use ndiswrapper and I got an error.  The following is straight from the terminal.

dave@Tweak:~$ sudo ndiswrapper -i ~/7kwc27ww.exe
installing 7kwc27ww.exe ...
couldn't get manfacturer section - installation may be incomplete

I downloaded and used the XP version of the wireless driver.  The ndiswrapper troubleshooter for Ubuntu said I should put all the files from the driver download in a common directory, but I only had one file...a .exe file, which is what I specified in the code above.  Why isn't this working?

---

### Post by kevdog on 2007-11-18
The exe file contains the .sys and .inf files.  What I would do, would be to open this exe in Windows and then extract out only the .inf and .sys WinXP drivers (should be a folder containing these files).  Bring these two files over to linux.

---

### Post by djm5091 on 2007-11-18
I've made some progress.

I did what you said, and used the same code but with a bunch of different .inf files till I got one of them to install.

When I ran ndiswrapper -l, I got a message that said I had a bunch of invalid drivers, and one driver installed. Which I assume means that that one driver works.

Now, the next part of the trouble shooting instructions didn't work.

heres the terminal

dave@Tweak:~$ sudo depmod -a
dave@Tweak:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-29-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

---

### Post by kevdog on 2007-11-18
Can you list 

ndiswrapper -l

You can only have one driver listed here, not a bunch of wrong drivers and then one correct driver.

---

### Post by kevdog on 2007-11-18
So just to summarize to start over:

sudo rm -rf /etc/ndiswrapper/*

Then reinstall the known working driver:
sudo ndiswrapper -i ****.inf

Then try to modprobe ndiswrapper again.

---

### Post by djm5091 on 2007-11-18
I used that command you gave me, and got it to the point where I only have one driver installed.

Modprobe still won't work though.  I still get the same invalid argument error.  

i don't know if this helps, but the trouble shooting guide said I should get the following when I use ndiswrapper -l
  
{name of driver} driver present, hardware present

  or 

  {name of driver} : driver installed
       device ({Chipset ID}) present

what I got was like the second one, but all it said was

netw4x32: driver installed

and made no mention of the device {chipset ID} being present

---

### Post by kevdog on 2007-11-18
Then you do not have the correct windows driver.  That is what that line is telling you.  

Just an update.  Is your card listed on this page??:
[http://madwifi.org/wiki/Compatibility/IBM#ThinkPad11abgWirelessLANMini-PCI](http://madwifi.org/wiki/Compatibility/IBM#ThinkPad11abgWirelessLANMini-PCI)

If it is, you are in luck -- madwifi is the answer for you.  You can install it via Synaptic.  Do a search for linux restricted packages, install, reboot, you should be good to go!!

---

### Post by djm5091 on 2007-11-18
Yes, my driver is listed here.  I found this earlier but didn't know what to make of it.  I'll try this now.

---

### Post by kevdog on 2007-11-18
First find the version of your kernel.  Type at the command line:

uname -r

Then in synaptic do a search for the restricted packages and install the package that corresponds to your kernel version.

---

### Post by djm5091 on 2007-11-18
what is synaptic?

---

### Post by kevdog on 2007-11-18
Its the gui package management system.  Or just do the following

Please post the following:

uname -r
sudo apt-cache search linux-restricted

---

### Post by djm5091 on 2007-11-18
oh, you must think I have the internet on ubuntu through my wired connection right now.  I don't.  I'm using another computer.  Could you give me a hyper link to someplace I could download madwifi, or whatever it is I need.

---

### Post by kevdog on 2007-11-18
Ok, try this.  If you are using Gutsy

Boot into ubuntu, place the gutsy cd rom into the drive, type the following:
sudo apt-cdrom add
sudo aptitude update

Please post the following:
uname -r
sudo apt-cache search linux-restricted

---

### Post by djm5091 on 2007-11-18
I don't know what gutsy is.  Heres the code you asked for though

dave@Tweak:~$ uname -r
2.6.15-29-386
dave@Tweak:~$ sudo apt-cache search linux-restricted
Password:
linux-restricted-modules-2.6.15-23-386 - Non-free Linux 2.6.15 modules on 386
linux-restricted-modules-2.6.15-23-686 - Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII/PIV
linux-restricted-modules-2.6.15-23-k7 - Non-free Linux 2.6.15 modules on AMD K7
linux-restricted-modules-2.6.15-25-386 - Non-free Linux 2.6.15 modules on 386
linux-restricted-modules-2.6.15-25-686 - Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII/PIV
linux-restricted-modules-2.6.15-25-k7 - Non-free Linux 2.6.15 modules on AMD K7
linux-restricted-modules-2.6.15-26-386 - Non-free Linux 2.6.15 modules on 386
linux-restricted-modules-2.6.15-26-686 - Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII/PIV
linux-restricted-modules-2.6.15-26-k7 - Non-free Linux 2.6.15 modules on AMD K7
linux-restricted-modules-2.6.15-27-386 - Non-free Linux 2.6.15 modules on 386
linux-restricted-modules-2.6.15-27-686 - Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII/PIV
linux-restricted-modules-2.6.15-27-k7 - Non-free Linux 2.6.15 modules on AMD K7
linux-restricted-modules-2.6.15-28-386 - Non-free Linux 2.6.15 modules on 386
linux-restricted-modules-2.6.15-28-686 - Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII/PIV
linux-restricted-modules-2.6.15-28-k7 - Non-free Linux 2.6.15 modules on AMD K7
linux-restricted-modules-2.6.15-29-386 - Non-free Linux 2.6.15 modules on 386
linux-restricted-modules-2.6.15-29-686 - Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII/PIV
linux-restricted-modules-2.6.15-29-k7 - Non-free Linux 2.6.15 modules on AMD K7
linux-restricted-modules-386 - Restricted Linux modules on 386.
linux-restricted-modules-686 - Restricted Linux modules on PPro/Celeron/PII/PIII/PIV.
linux-restricted-modules-common - Non-free Linux 2.6.15 modules helper script
linux-restricted-modules-k7 - Restricted Linux modules on AMD K7.

---

### Post by kevdog on 2007-11-18
So these are your choices:

linux-restricted-modules-2.6.15-29-386 - Non-free Linux 2.6.15 modules on 386
linux-restricted-modules-2.6.15-29-686 - Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII/PIV
linux-restricted-modules-2.6.15-29-k7 - Non-free Linux 2.6.15 modules on AMD K7

One of those packages you need to install -- Im guessing it will be the first one, but it depends on your processor.  The syntax to install the package is:

sudo aptitude install linux-restricted-modules-2.6.15-29-386

---

### Post by djm5091 on 2007-11-18
Should I reboot after that?

---

### Post by kevdog on 2007-11-18
Yea sure -- it never hurts, but take the cd out of the drive before you do!!

---

### Post by djm5091 on 2007-11-18
I installed that i386 linux restricted package you told me to, but the wireless option still isn't showing up in network settings.

When I run lshw in a terminal, my wireless card is still showing up as unclaimed, and with no driver attached.

---

### Post by kevdog on 2007-11-18
Ohhhhh, this is making my head hurt.

I guess the madwifi drivers dont support your card!!! 

Back to ndiswrapper. 

Just some background.  Are you using 32 or 64 bit ubuntu?  Where did you get your windows drivers??  Can you find them on the internet for me and post a link??

---

### Post by djm5091 on 2007-11-18
1)[http://www-307.ibm.com/pc/support/site.wss/MIGR-64289.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-64289.html)

this is where I got my drivers.  They are listed under
ThinkPad 802.11a/b/g/n, 802.11b/g/n Wireless LAN Mini PCI Express Adapter

I used the XP version.

2) Where do I check what bit ubuntu I'm using?

3) I just now saw this, but when I ran sudo aptitude install (etc.)
here was my code

dave@Tweak:~$ sudo aptitude install linux-restricted-modules-2.6.15-29-386
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

---

### Post by kevdog on 2007-11-18
It just means that the package was already installed with the installation.  

Ok, I didnt really want to install the drivers on my computer to extract the files, so what files did you get out of the downloaded package???  Can you name the .sys and .inf files?

---

### Post by djm5091 on 2007-11-18
I had a NETw4x32.inf, NETw4x32.sys, NETw4x32.CAT

---

### Post by djm5091 on 2007-11-18
There where a bunch of other ones, like NETw4k32.inf,.cat,.sys, but those where all the ones that didn't install.

There were also some .DLL files, but none of thos had NETw4x32 in the name.

---

### Post by kevdog on 2007-11-18
Can you post the following:

lspci -nn 
(only need part regarding Atheros card)

lshw -C network
(only need part with Atheros card)

---

### Post by kevdog on 2007-11-18
If you type

sudo modprobe ath_pci

Then recheck lshw -C network, does anything change for your atheros statement??
Does checking dmesg give any clues at this stage.

---

### Post by djm5091 on 2007-11-18
lspci -nn
0000.03.00.0 0200: 168c:1014 (rev 01)

lshw -C network
network UNCLAIMED
    description: Ethernet controller
    product: AR5212 802.11abg NIC
    vendor: Atheros Communications, Inc.
    physical id: 0
    bus info: pci@03:00.0
    version: 01
    width: 64 bits
    clock: 33mHz
    capabilities: cap_list
    resources: iomemory:edf00000-edf0ffff irq:66

---

### Post by kevdog on 2007-11-18
If you type

sudo modprobe ath_pci

Then recheck lshw -C network, does anything change for your atheros statement??
Does checking dmesg give any clues at this stage.

---

### Post by kevdog on 2007-11-18
Look what I found:

[http://www.thinkwiki.org/wiki/IBM_11a/b/g_Wireless_LAN_Mini_PCI_Adapter](http://www.thinkwiki.org/wiki/IBM_11a/b/g_Wireless_LAN_Mini_PCI_Adapter)

Madwifi has got to work!!

---

### Post by djm5091 on 2007-11-18
nothing changed for lshw

under dmesg

the only thing I can see is this seciton

[17179594.584000] wlan: 0.8.6.0 (EXPERIMENTAL)
[17179594.584000] ath_rate_sample: 1.2
[17179594.592000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[17179594.592000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 66
[17179594.592000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[17179594.592000] Uhhuh. NMI received. Dazed and confused, but trying to continu e
[17179594.592000] You probably have a hardware problem with your RAM chips
[17179594.640000] ath_attach: unable to attach hardware: 'Hardware didn't respon d as expected' (HAL status 3)

---

### Post by kevdog on 2007-11-18
Two failures -- one with ndiwrapper and the other with madwifi -- Are you sure this card works?

---

### Post by djm5091 on 2007-11-18
yes, it works on vista.  I think i'm just very bad at ubuntu.  I'm going to try some more trouble shooting guides, I really don't want to waste any more of your time.

---

### Post by kevdog on 2007-11-18
Id point you in the right direction, however the only two methods that I know ndiswrapper / madwifi do not seem to work.  Not sure what the problem is.  Good luck since its kind of bumming me out!

---

