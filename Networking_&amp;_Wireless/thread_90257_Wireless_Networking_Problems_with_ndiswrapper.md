---
title: "Wireless Networking Problems with ndiswrapper"
date: 2005-11-14
forum: Networking &amp; Wireless
---

### Post by technophreak on 2005-11-14
Hi,

I've read through the threads on here about wireless networking and installed ndiswrapper for my wireless network card in my laptop. The card is the Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01) and I have got the right drivers from the ndiswrapper site. It's all installed properly and everything looks the same as in the guide. I removed the prism54 drivers before I installed ndiswrapper.

When I run iwconfig, eth1 doesn't show up at all anymore and it isnt present in the networking tool. If i do sudo modprobe ndiswrapper and then dmesg, I get this:

```

[4297544.107000] eth1: resetting device...
[4297544.107000] eth1: uploading firmware...
[4297544.222000] prism54: request_firmware() failed for 'isl3886'
[4297544.222000] eth1: could not upload firmware ('isl3886')
[4297544.222000] eth1: islpci_reset: failure
[4297547.767000] eth1: resetting device...
[4297547.767000] eth1: uploading firmware...
[4297547.859000] prism54: request_firmware() failed for 'isl3886'
[4297547.859000] eth1: could not upload firmware ('isl3886')
[4297547.859000] eth1: islpci_reset: failure
[4297547.909000] eth1: resetting device...
[4297547.909000] eth1: uploading firmware...
[4297548.001000] prism54: request_firmware() failed for 'isl3886'
[4297548.001000] eth1: could not upload firmware ('isl3886')
[4297548.001000] eth1: islpci_reset: failure

```

Can anyone help?

Thanks

---

### Post by MightyMouse on 2005-11-14
Check my thread, I posted how I did it (same Insel chipset you have)

[http://ubuntuforums.org/showthread.php?t=85835](http://ubuntuforums.org/showthread.php?t=85835)

MightyMouse

---

### Post by technophreak on 2005-11-14
Thanks. Where is the hotplug blacklist?

I see your last post now. Thanks! I'm reinstalling Ubuntu now.

---

### Post by MightyMouse on 2005-11-14
Blacklist is at /etc/hotplug/blacklist

MM

---

### Post by technophreak on 2005-11-14
I reinstalled ubuntu but it still thinks I have prisma00.inf installed and wont let me uninstall it because it then says its not there. ndiswrapper -l gives me an invalid driver installed message.

Also, when i do sudo apt-get install linux-image-686, I get "E: Couldn't find package linux-image-686"

---

### Post by Lambert on 2005-11-14
Make sure you have universe/multiverse repositoreis set up.

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

type

```
ndiswrapper --help
or 
ndiswrapper -h
```

See what other options it gives you. There may be something like -f to force the uninstall.

Sometimes I've found where using just the .inf file isn't enough. You need to create a directory in your home folder and copy the .inf, .dll, and .sys files from the disk to get ndiswrapper to work.

---

### Post by MightyMouse on 2005-11-14
After installing Ubuntu you already had a prisma00.inf somewhere?
Where did it come from? Standard should be prism54, so that is kind of strange. Or did you install it with ndiswrapper -i

Adding the sys file into the directory where your inf file is might help, I think I might have them in the same directory too.

If you change your sources.list then you can also install disgtk (use the Synaptic package manager). You will then have the windows wireless tools (I assume you did install ndiswrapper-utils also)
If the prisma00 driver is installed you can uninstall it with the windows wireless tool.

The tool will also tell you if your hardware is present.

MM

---

### Post by technophreak on 2005-11-14
I installed it with ndiswrapper -i but then I reinstalled Ubuntu. After reinstalling, it was only half there. ndiswrapper saw it when I tried to install it again but didn't see it when I wanted to uninstall it.

I have the sys file on the desktop with the inf file. I cant create any directories anywhere or access any harddrives though.

---

### Post by MightyMouse on 2005-11-14
OK,
after a new installation of Ubuntu you should not have an installed prisma00! It can be in your home directory because Ubuntu is intelligent enough to make a base partition and does not overwrite your data section every time you update.

So if you now type ndiswrapper -l what do you see.
What do you see if you type dmesg | grep prism54?

MM

---

### Post by technophreak on 2005-11-14
ndiswrapper -l : prisma00      invalid driver!

dmesg | grep prism54 : [4294708.982000] Loaded prism54 driver, version 1.2

---

### Post by MightyMouse on 2005-11-14
This is the problem. You first need to uninstall prism54.

Do modprobe -r prism54, then dmesg | grep prism54.
What does it say?

---

### Post by technophreak on 2005-11-14
Loaded prism54 driver, version 1.2
Unloaded prism54 driver

I'm sure I already did that though :S

---

### Post by MightyMouse on 2005-11-14
Yes, but now it's really unloaded.
 Now do the ndiswrapper -i /???/prisma00.inf

What do you get?

---

### Post by technophreak on 2005-11-14
prisma00 is already installed. Use -e to remove it

and when I do -e:

Driver /Desktop/prisma00.inf is not installed. Use -l to list installed drivers

-l:

prisma00            invalid driver!

---

### Post by MightyMouse on 2005-11-14
Where did you get the prisma00 from?

It seems that this one might be corrupt.

MM

---

### Post by technophreak on 2005-11-14
I got it from the ndiswrapper.sourceforge.net list. 

[http://download.fujitsu-siemens.com/Download/ShowDescription.asp?SoftwareGUID=3B928095-EEEE-4194-91A7-E0CBE2D28B56](http://download.fujitsu-siemens.com/Download/ShowDescription.asp?SoftwareGUID=3B928095-EEEE-4194-91A7-E0CBE2D28B56)

I have it on my driver cd too. Should I try using that one instead?

Before I reinstalled Ubuntu, I had ndiswrapper installed with the driver showing as installed correctly but it wouldn't display eth1 in iwconfig or the GUI networking tool.

---

### Post by MightyMouse on 2005-11-14
That sounds good to me.
Use that driver (remove the other on or at least make a new folder for the original driver)

Then try again to install with ndiswrapper -i.

MM

---

### Post by MightyMouse on 2005-11-14
Well it's late, I have to work tomorrow, so I will leave you now.

If it works with the original driver I'll hear from you, if it doesn't I'll hear from you for sure!

I'll be back tomorrow evening,
cheers, MightyMouse

---

### Post by technophreak on 2005-11-14
I got the same error. I'm going to go to bed now and will completely format the drive tomorrow and reinstall Ubuntu. Hopefully I can get it working then. Thanks for you help, I'll keep you updated on my progress :p

---

### Post by sedition on 2005-11-14
Just a note I discovered today (not releative to this particular card): I received the "invalid driver" using ndiswrapper until I dropped in ALL files from the zipped folder into my windows_drivers folder. Namely, I think the .sys had something to do with it. Once I dropped it in the folder, I received a "hardware present".

---

### Post by MightyMouse on 2005-11-15
I agree with sedition, I checked and I have the sys file in the same directory as the inf file!

You should also try modprobe -r prisma00 to remove the entry of previous installs from modprobe if you don't want to re-install ubuntu again. This might also be a way to get rid of the old driver.
Then also make sure prism54 is removed and start again with install of the other (from CD) driver and sys file.

Let us know if this works!

MightyMouse

---

### Post by technophreak on 2005-11-15
My sys file has always been in the same directory as the inf file. modprobe -r prisma00 gives me

FATAL: Module prisma00 not found

---

### Post by Lambert on 2005-11-15
You're actually using ndiswrapper aren't you? If so then 

sudo ndiswrapper -r prisma00 or prisma02

Do a ndiswrapper -l command to see what driver is loaded.

Then dump all the files from the driver folder on the disk into a directory on your pc (.sys and .dll etc). maybe /home/<your_name>/drivers

then cd to that directory and sudo ndiswrapper -i <name>.inf

---

### Post by technophreak on 2005-11-15
I've got a PCMCIA Wifi card that never used to work with linux as it has an atmel chipset. I put it in and it was detected automatically and sudo ifup wlan0 made it work fine. I'm going to use this for now until I can be bothered wrestling with the integrated one.

Thanks for all your help

---

