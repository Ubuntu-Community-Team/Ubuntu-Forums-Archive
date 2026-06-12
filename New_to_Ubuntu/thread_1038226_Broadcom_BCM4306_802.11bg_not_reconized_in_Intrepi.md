---
title: "Broadcom BCM4306 802.11b/g not reconized in Intrepid 8.10"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Kevide on 2009-01-12
I'll apologize upfront for the redundancy of this topic. I've read many threads with like issues concerning Broadcom, but so far I’ve been unable to properly utilize their advice. I’ll say now that I’m a novice with Linux (which I suspect is painfully obvious), and I can only get online wirelessly, via my Windows XP partition, which I am running an older Gateway 7324gz notebook.

lspci yielded this: Network controller: Broadcom Corporation BCM4306 802.11b/g

Any suggestions would be greatly appreciated.

---

### Post by anewguy on 2009-01-12
Do you have, or can you download, a Windows driver for your card (non-Vista)?  If so, we should be able to get it working with ndiswrapper.  You may also want to try the new b43 restricted driver and it's fwcutter - I just don't know if that driver supports the 4306 or not, as it supports some but not all of the bcm43xx series.

If you get the Windows (non-Vista) driver, post back and I can walk you through using ndiswrapper.

Dave :)

EDIT:  According to [http://linuxwireless.org/en/users/Drivers/b43#supported]("http://linuxwireless.org/en/users/Drivers/b43#supported") the 4306 is supported by b43legacy for rev 2 and b43 for rev 3.

---

### Post by Kevide on 2009-01-12
I have the XP driver for my wireless. (I re-install this machine quite frequently; hence the move to linux. ;) )

---

### Post by anewguy on 2009-01-12
okay, if you have the XP driver, let's make this as easy as possible.

(1) create a new folder in your home folder:

- open a terminal window (applications/accessories/terminal

- mkdir wireless_driver <enter> creates a folder named wireless_driver

- cd wireless_driver <enter> changes your terminal session so that you are working in the wireless_driver folder

-copy your Windows wireless driver files (.inf and .sys) to this folder.

(2) leave the terminal session window open, but start up synaptic package manager (system/administration/synaptic)

- look for ndis* via the search
- if ndiswrapper (and possibly the utilites if present) do not have a green box in front of them indicating they are installed, check each of the boxes and click apply.  Wait for this to all finish, then close out of synaptic package manager.

(3) back to the terminal window:

- sudo ndiswrapper -i xxxxx.inf <enter> Where it's a lower case "I" for install, and replace xxxxx.inf with the name of your driver .inf files

- sudo ndiswrapper -l <enter> That's a lower case "L" for list.

your device should show as installed.  If there is any type of error message stop here and post back with it.

- sudo depmod -a <enter> set up the dependency

- sudo ndiswrapper -m <enter> This is supposed to force the system to load ndiswrapper at boot, but doesn't always work so we also do the following:

- sudo gedit /etc/modules <enter> This calls up a GUI'd editor and will open the file /etc/modules in it.  Go to the very bottom of that file and add this line to the end:

ndiswrapper

- now save the file and exit the editor. This file tells the system of extra kernel modules to load at boot.

- sudo gedit /etc/modprobe.d/blacklist <enter>  This will open the /etc/modprobe.d/blacklist file in the same editor.  Go to the very end of this file and add the following lines:

blacklist bcm43xx
blacklist b43

- now save the file and exit.  The blacklist file(s) tells the system which kernel modules not to load at boot.  BCM43xx was the first attempt at a driver structure for the bcm43xx series of adapters, but was only really a skeleton.  B43 is the newer driver.  We must stop both of these from being loaded so that ndiswrapper can do it's thing.

Now reboot.  When the system comes back up, go to system/administration/network and be sure roaming mode is enabled.

Now check to see if your wireless is working by clicking on the network manager icon (2 little computers/terminals on your upper status bar) and see if networks show up.

Any problems or questions just post back!

dave :)

---

### Post by Kevide on 2009-01-12
[quote=anewguy]- look for ndis* via the search [/quote]

Nothing shows up at all. Scrolling down revealed there is no program on that list.

---

### Post by anewguy on 2009-01-12
Okay, let's find out if it is already installed:

- open a terminal window

type:

sudo ndiswrapper -l <enter> That's a lower case "L" for list.

If this returns an empty list, everything is ready, so you can skip the section on using synaptic.

If an error is returned, something like ndiswrapper file or directory not found, then locate your LiveCD that you installed with, put it in the CD drive, and do the following (don't reboot!):

navigate to the /pool/main/n/ or /pool/main/n/ndiswrapper (I forget the exact location right now) folder and double-click on the ndiswrapper things there to install them.

Once you have done that, try another sudo ndiswrapper -l and see if it just returns nothing.  If so, we're all set - you can move on to the next step.  If not, post back again and we'll go from there.

Dave :)

EDIT:  I think I gave the wrong syntax for the synaptic search string, try just ndis

---

### Post by Kevide on 2009-02-23
A first apology if this constitutes a grave-dig, and a second apology for bowing out of my own thread without notice. Life has been rather ... insistent lately.

And thanks to Dave for all of his advice thus far.

sudo ndiswrapper -l (and every variant I can think of) yeilds a no "unknown command" message.

---

### Post by MrWES on 2009-02-23
That card should show up in System | Administration | Hardware Drivers; you should not need to use ndiswrapper. I have a Dell D610 with this card and it worked OTB by enabling the hardware driver.

Bill

---

### Post by Kevide on 2009-02-23
MrWES,

Under System | Administration | Hardware Drivers it reads that I have no propriety hardware. 

(Looking over my posts I think I may have misspoken: My Ubuntu is not a separate partition, but installed within Windows itself. I fear that may have been a bonehead oversight on my part. :/ )

---

### Post by MrWES on 2009-02-24
> **Kevide said:**
> MrWES,

Under System | Administration | Hardware Drivers it reads that I have no propriety hardware. 

(Looking over my posts I think I may have misspoken: My Ubuntu is not a separate partition, but installed within Windows itself. I fear that may have been a bonehead oversight on my part. :/ )

Please goto System | Admin | Software Sources and enable All expect source under the 'Ubuntu' tab, and the the restricted under the 'Third Party' tab. Click reload, and then see if the driver shows under hardware drivers.

Bill

---

### Post by Kevide on 2009-02-24
Okay, I think I've made some progress.

I went to &#8220;System | Administration | Software Sources, and everything under the &#8220;Ubuntu Software&#8221; tab was already checked. Under &#8220;Third-Party Software, I clicked on two canonical partner packages. Under updates, I selected &#8220;Recommended&#8221;, &#8220;Pre-released,&#8221; and &#8220;Unsupported&#8221; (backports). I'm guessing it was that last one I needed. I managed to hook-up my notebook to an Ethernet cable, and after installing updates, my b43 Broadcom card now shows up in &#8220;Hardware Drivers&#8221; with a green light next to it telling me it is in use. (The blue wireless indicator light on my laptop is once more on, though my &#8220;FN Wireless&#8221; key combination no longer has any effect.)

However, my wireless network connection options (from the dropdown icon on the top right), are still grayed out.

---

### Post by MrWES on 2009-02-24
Reboot if you haven't

---

### Post by Kevide on 2009-02-24
rebooted twice, no effect.

EDIT: Strike that. I rebooted again, and this time my card worked perfectly. (I'm posting this through my now wireless Ubuntu install). :)

Thank you very much, MrWES, and anewguy. Your swift, patient and informative responses are further reasons why I am glad that I've made this move. (Will soon be formatting my HDD, and making Ubuntu my primary OS. :) )

Thanks again, everyone.

---

### Post by MrWES on 2009-02-24
Glad to hear! Wireless can be frustrating at times, but generally there is a solution. For the life of me I couldn't get that card to work in 8.04; although many had, so I upgraded to 8.10 and it worked with the restricted driver.

Good Luck,


Bill

---

### Post by process91 on 2009-12-30
This is still a "problem" in Karmic, I figured I would mention that checking the unsupported updates is required to make the restricted driver available. It did work for me, following the instructions in this post. Thank you!

---

