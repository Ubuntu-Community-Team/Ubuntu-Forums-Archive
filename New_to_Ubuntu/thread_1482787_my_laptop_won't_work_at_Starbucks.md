---
title: "my laptop won't work at Starbucks"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by cetacean on 2010-05-13
I have posted at least a dozen questions here, and elsewhere, about  getting a wireless signal on my clean new Acer/AMD/Atheros laptop, in  various ways, under various user names.

I can boot into Windows and connect via ethernet or wireless, no problem  at all, and via ethernet under Ubuntu - but try to connect wirelessly -  dead meat.

Quite a few people on this forum have been wonderfully helpful to give  me numerous methodologies to fix this - all failed. I have downloaded  and installed loads of crap, done Madwifi, I run update manager, sudo  apt-get update, Synaptic - pure nada.

I am a newbie here with decades of Microsoft experience. I really like  like the Ubuntu concept and just about everything I have tried has  worked - sometimes immediately - sometimes after several convoluted  iterations. 

I have to admit, I don't really "get it" yet, but this seems to be a  gaping chasm that a whole lot of users have fallen into.

"lspci" reports that this situation involves an Atheros AR928X wireless  network adapter although other sources name slightly different flavors  of hardware.

This is obviously a massively widespread problem since there have been  dozens of posts every day with "wireless" and "10.04" in the subject  line since April 29.

I am serious about migrating from Windows to Ubuntu but this kind of  stumbling block is close to a deal-killer. 

Realistically, what can I expect to happen in the near future?

---

### Post by ronlayt on 2010-05-14
I'm in the same boat as Cetacean. What can we do to fix this? Don't let this miniscule problem make me give up on using UBUNTU. I hate Microsoft and thats the reason I went toUBUNTU after much discussion with many users. HELP!!!:confused:

---

### Post by Ozymandias_117 on 2010-05-14
@cetacean Unfortunately, the problem is with the hardware manufacturers. FOSS programmers try their best, and do a wonderful job, at supporting as many devices as they can. On some devices, they run into problems because the hardware manufacturer doesn't release the specs or details about how the device is supposed to work, which makes it incredibly difficult on FOSS programmers. Since they also don't release drivers for Linux users, some devices are just screwed.

Note: Have you tried ndiswrapper?

---

### Post by uRock on 2010-05-14
Which version of ubuntu are you using?

---

### Post by qwerty2009 on 2010-05-14
try and install linux-backports-modules-wireless-lucid-generic from synaptic and restart

---

### Post by cetacean on 2010-05-14
Ozymandis - 

I have installed ndiswrapper via Syanptic and attempted to run it, but maybe I did it wrong. 

Of all the hints I have gotten, that seems promising.

What do I type in the terminal to make it happen?

thanks

---

### Post by qwerty2009 on 2010-05-14
copy and past this into terminal...

sudo apt-get install linux-backports-modules-wireless-lucid-generic

you need to restart after :D hope it works

---

### Post by cetacean on 2010-05-14
Qwerty - 

I have been there and done that on the backports business. 

Not only does it not work, it kills the ethernet connection as well !

but thanks for trying, anyway !

---

### Post by uRock on 2010-05-14
To use ndiswrapper, you need to download the Windows driver for your Atheros card and install it.

Depending on which version of Ubunt you are using, installing backports may be helpful, too.

---

### Post by qwerty2009 on 2010-05-14
ok it usually is the first thing that works when wireless is not working, might be usefull to ronlayt anyway :P

---

### Post by uRock on 2010-05-14
> **qwerty2009 said:**
> ok it usually is the first thing that works when wireless is not working, might be usefull to ronlayt anyway :P
?

---

### Post by cetacean on 2010-05-14
the laptop connects instantly and automatically and blazingly fast under Windows.

are you saying that I have to go somewhere and find a driver of some sort?

---

### Post by ronlayt on 2010-05-14
This simple fix by kerry_s worked for me. Heres the link: [http://ubuntuforums.org/showthread.php?t=1482795](http://ubuntuforums.org/showthread.php?t=1482795)

I hope this will help you with your problem.

---

### Post by uRock on 2010-05-14
> **cetacean said:**
> the laptop connects instantly and automatically and blazingly fast under Windows.

are you saying that I have to go somewhere and find a driver of some sort?
The ndiswrapper is for installing your products Windows drivers. That is what the info in Synaptic and Ubuntu Software Center are implying.

---

### Post by uRock on 2010-05-14
[http://www.atheros.cz/](http://www.atheros.cz/)

---

### Post by henry cow on 2010-05-25
Thanks for your help. I must just be too old or dense to understand. I have "downloaded" and attempted to "install" all of these things - please forgive my Microsoft terminology but that's all I know.

According to Synaptic and/or Update Manager and/or Ubuntu Software Center this stuff is all resident on disc but what do I do to make it "take" or "run" it?

It's just like it's sitting there waiting on ME to tell it to do something.

Is this me or what?

---

### Post by anewguy on 2010-05-25
A short background:  not all wireless works with Linux.  Some adapters have native (Linux) drivers.  Others rely on the Windows drivers running in Linux via ndiswrapper.

If you have installed ndiswrapper and the utilities, the next thing to do is install the ndisgtk package.  Ndisgtk is a GUI'd based front-end to ndiswrapper and eliminates typing in a bunch of things on the command line.  Once you have ndiswrapper, the ndiswrapper utilities and ndisgtk installed, then you need to make the .sys and .inf files for your Windows driver available to Linux.  The easiest way to do this is just to copy them to the desktop.

Now, with everything in place, just click on System/Administration/Windows Wireless Drivers.  The GUI for ndisgtk will start up.  You want to "add" and point it to the driver files on your desktop.  Once finished, your wireless should work (though this isn't a 100% - realize you are running non-native drivers).

Also, if you can tell us a distinct example of what you have tried and where it failed, perhaps we could help you through that.

Dave ;)

---

### Post by Talon2 on 2010-05-25
[QUOTE=henry cow;9360643
According to Synaptic and/or Update Manager and/or Ubuntu Software Center this stuff is all resident on disc but what do I do to make it "take" or "run" it?

It's just like it's sitting there waiting on ME to tell it to do something.

[/QUOTE]

The "stuff" that Synaptic, Ubuntu Software Center and Update Manager make available to you is available on servers.  You select what you want and tell Synaptic, Ubuntu Software Center or Update Manager to download and install.  If you do not have an internet connection this will not work well.  If wifi is the problem then find a ethernet cable to connect to the internet.  With a connect then Synaptic, Ubuntu Software Center and Update Manager will work as advertized.

If you have questions about Synaptic, Ubuntu Software Center or Update Manager please be specific with the questions.

---

### Post by anewguy on 2010-05-26
Maybe I misunderstood what you meant by > waiting on ME to tell it to do something

I *thought* you meant that you had installed these things via Synaptic Package Manager, but don't know how to actually start them running.  If, instead, you meant that you have downloaded package files, such as .deb, .gz, etc., then things are a little different.

For such tools as ndiswrapper, ndisgtk, etc., and anything else for that matter, check to see if they are available in Synaptic Package Manager first.  If so, and if the box at the front if the line is not solid, click on the item and choose mark for installation.  When you have selected all of the packages you want, then click on "Apply" and, as long as you have your ethernet cable connected [considering you don't have wireless yet], it should download the packages and install them.

The next step is to actually run them.  If the package you installed is a system package, look under the system menu at either preferences or administration for an entry. For other non-system packages, you need to check the entire menu structure to locate it, if available. If you don't see an entry, then open a terminal window (Applications/Accessories/Terminal) and type "sudo" followed by a space followed by the name of the command (and any parameters it may require) EDIT:  Please note that you should try without sudo first - sudo is only used when super user (root) access is needed.  For example, if you installed ndiswrapper but didn't install ndisgtk, then you would open a terminal window and do something like the following:

sudo ndiswrapper -l <press enter> That's a lower case "L", and is asking ndiswrapper to list any active devices and their drivers that it is controlling.

As I mentioned in a previous post, I highly recommend using ndisgtk as it eliminates the headache of typing in all of the commands in the terminal window.  Just to give you an idea:

- running ndisgtk via System/Administration/Windows Wireless Drivers and doing an add, takes the place of all of these command line items if only using ndiswrapper:

Type:

sudo ndiswrapper -l <press enter>

- if any items are returned above, do:

sudo ndiswrapper -e xxxx <press enter> where xxxx is the name of the driver the list showed.  Continue this until the list is empty.

cd <path to windows driver files> <press enter>

sudo ndiswrapper -i xxxxx <press enter> Where it's a lower case "I" for install, and xxxxx is the name of your Windows driver file

sudo depmod -a <press enter>

sudo modprobe ndiswrapper <press enter> Load the ndiswrapper kernel module

sudo ndiswrapper -m <press enter> Request ndiswrapper to include itself in the modules to load at boot

The above "-m" normally doesn't seem to do anything anymore, so:

sudo gedit /etc/modules <press enter> This will call up an editor and open the modules file (the list of extra kernel modules Linux should load at boot).  Go to the end of the file and add the following line:

ndiswrapper

Now save the file and close the editor.

Also, with some wireless chipsets, it is necessary to disable the driver module included with Linux.  A particular case (but not limited to) are many of the Broadcom wireless adapters.  In those instances you must edit another file - /etc/modprobe.d/blacklist.conf - and add "blacklist xxx" lines for each of the modules you need to disable.


So, as you can see, using ndisgtk can help eliminate a lot of typing at the command line if you are using ndiswrapper.

I don't know if that helps answer your question or not.  If not, could you explain a little more about what you are doing (wanting to install or wanting to run something)?  >deb, .tgz, .gz, etc., files require a little more so let us know if you are trying to work with one of them.

Dave ;)

---

### Post by Stigmata13 on 2010-05-26
I'll vouch for ndiswrapper. I have an acer aspire 5515 and I am currently using Ubuntu 8.04, the wireless didn't work correctly out of the box. After installing the backports, the wireless worked, although I would get random bits of lag every 30 seconds or so (I do light gaming, Diablo 2 under Wine.)
After downloading the wrapper and windows xp drivers for my wireless chip, it has been working perfectly, on par with windows, that is for sure.

---

### Post by henry cow on 2010-05-26
Dave - 

Thanks a lot, really, I appreciate your help.

But it still is not working. I did what you said, and it all seemed like it worked, up until the very end.

(when I searched Windows drivers *.inf I got almost 1900 hits!)

I combed through them and found what might be the right ones "netrtx64.inf" and "rt64win7.sys" and I used System/Administration/Windows Wireless Drivers to install them and got a "hardware present" message.

So I'm really close, right?

I shut down and did a cold hard boot with the ethernet cable unplugged to give it a clean shot.

But everything returns an empty box, such as System/Preferences/Network Connections/Wireless and none of the "Add" options are live (ie the "Apply" buttons are grayed out).

The laptop has a push-button for the wireless "antenna" with an LED but it has never lit up except under Windows, does that indicate anything else?

Thank you so much for hanging with me on this.

Oh yes, and by the way, Chili555 had me try that backports thing a couple of weeks ago and that also killed my ethernet connection.

---

### Post by anewguy on 2010-05-27
I found mention of something on the net I thought I'd pass along in case you haven't seen/tried it yet.

There is a file in the /etc/modprobe.d folder called "blacklist.conf".  This file contains statements that request that certain kernel modules not be loaded at boot, and are in the form of "blacklist xxxxx".

On several posts I saw on the net, they have blacklisted IPv6.  If you want to try this to see if it helps, do the following:

- open a terminal windows (Applications/Accessories/Terminal

- type:

sudo gedit /etc/modprobe.d/blacklist.conf <press enter>  This will call up a GUI based editor with the blacklist.conf file.  You have to use the "sudo" since the file is owned by root, so your normal userid would not be able to access it.  

- scroll to the end of the file and add this line:

blacklist IPv6

- save the file and exit the editor

- reboot

Try your wireless again - I have no idea if this will help or not.  If it makes no difference, please reverse the edit above:

sudo gedit /etc/modprobe.d/blacklist.conf

scroll to the bottom and remove the following line:

blacklist IPv6

save the file and reboot.

I always do this when attempting a change - 1 thing at a time, and reverse it if it doesn't work before moving on to the next thing.  This accomplishes 2 things - you don't end up with a mish-mash that doesn't work together, and you can identify the step that did help.

Let me know how that turns out.  In the mean time, I'm going to search to see if there is something that must be done to physically enable the device (so the light is on).

Dave ;)

---

### Post by anewguy on 2010-05-27
Just thought of something - you're using the Windows 7 drivers from the way it looks, and I'm not sure if ndiswrapper supports them.  We may need to locate Windows XP drivers for your wireless adapter.

Also, I found [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/557414?comments=all") which suggests it is a bug in the kernel, the status of which I don't know.  If you have the grub menu at boot check to see if the 2.6.32-18 kernel normal mode is an option and chose it if it is, then check to see if it helped your wireless or not.

I'll try to search for some Windows XP drivers for your adapter.

Dave ;)

EDIT:  For the wireless button and light, have you tried booting Windows, enabling the device, then reboot to Ubuntu without a power off?  I seem to remember some sequence like that in other posts I have read for a similar type of problem.

---

### Post by uRock on 2010-05-27
If it is for the Atheros card. The link I posted above has both, XP and newer drivers.

---

### Post by Matt__ on 2010-05-27
A quick question to those having atheros problems...do you have to manually turn on your wireless in windows with a FN key combo?

---

### Post by uRock on 2010-05-27
> **Matt__ said:**
> A quick question to those having atheros problems...do you have to manually turn on your wireless in windows with a FN key combo?

Mine turns itself on in Windows.

---

### Post by Matt__ on 2010-05-27
Ah ok Urock, its just that Ive come across this on the fujitsu-siemens amilo 2727li (atheros AR5001 rev0.4 [168c:001c])where the card  is automatically disabled at boot to conform to US use of wireless on  aeroplanes regulations and you have to FN + F1 to start it up.
The only way i got it to work was a hardware hack to disable the off  signal as the soft keys wouldnt work in Ubuntu.

---

### Post by cetacean on 2010-05-27
urock - the site you listed replied as bad

matt - my laptop has a real hard dedicated button that never responds under Ubuntu

any other ideas? a lot of other people seem to be having the same problem

---

### Post by anewguy on 2010-05-28
Back to the original poster - henry cow:

When I look on the net, the Windows XP drivers (albeit 32-bit, I haven't downloaded the 64-bit to look at them yet) are named athw.sys and netathw.sys.  This is different from the names you found and are trying to use.  Perhaps you should search your Windows stuff again and see if you have files named similarly to these 2 and try them instead.

EDIT:  Indeed, I just did a web search on your netrtx64.inf file and it is for your internal realtek ethernet adapter.  You need to locate the wireless driver files as I named above, then try it again!

Dave ;)

---

### Post by Eva-Suki on 2010-05-28
> **anewguy said:**
> Now, with everything in place, just click on System/Administration/Windows Wireless Drivers.  The GUI for ndisgtk will start up.  You want to "add" and point it to the driver files on your desktop.  Once finished, your wireless should work (though this isn't a 100% - realize you are running non-native drivers).
Dave ;)

I have tried this for my atheros AR5001A chip. I installed the netathw.inf and wifi is still disabled. I made a thread but no one will respond. Can someone *help*?

Thanks

---

### Post by henry cow on 2010-05-30
[SIZE=3]OK folks, I have spent many many hours doing a complete and meticulous re-install of Lucid on my[/SIZE] [SIZE=3]Laptop - I will not bore you with the details of my tribulations.

After running the Update Manager and getting ndisgtk, finding the Windows directory that has the wireless drivers and copying it into the Ubuntu realm, then doing System/Administration/Windows Wireless Drivers/Install New Driver, and installing "netathrx.inf" I get a cheerful "Hardware Present" message.

- HOWEVER -

Going to System/Preferences/Network Connections, shows that I am still nowhere. In the "Wireless" tab, I have never seen any entry since I have owned this computer, never.

And although "Connect Automatically" is checked, it seems to be asking me for SSID, Mode, BSSID, and MAC Address.

I feel certain that this is the problem area, but have nothing to work with there.

Lastly, and this is interesting, I have a hardware button with an LED for my wireless antenna. As soon as I re-installed 10.04 fresh, that LED came on, and I could turn the switch off and on, even though I had no actual connection.

After doing the updates and running ndisgtk, the button seems dead.

Since I know that this is a gargantuan nightmare, I am not planning on doing anything else to this install until I get my wireless working, or give up utterly and permanently.

Dave, Chili, any of you guys got any new ideas on how I should proceed (as long as they don't involve any of that dreadful "backports" nightmare) I will try them?
[/SIZE]

---

### Post by anewguy on 2010-05-30
What happens when you open up network manager?  Does it show any wireless networks?  Is "Enable Wireless" checked?  Have you tried connecting via network manager instead of trying to set up a connection in System/Preferences/Network Connections?  Also, since the system is "clean" now, could you re-post the outputs from:

lspci (just the lines referring to your wireless adapter

lshw -C network (again, just the group for your wireless)

lsmod

sudo ndiswrapper -l

Wooppsss - I mis-spoke here originally here.  Text removed!


Sorry for all the questions, some of which seem like dups, but want to know the complete status now that everything is clean again.

Hang in there!

Dave ;)

p.s. - just thought of something - may need to execute the script to bring up wireless -  try  sudo ifup wlan0 in a terminal window and see if that helps.

---

### Post by henry cow on 2010-05-30
I desperately appreciate your help. It should not be this hard.
 
I am in my hotel room with 2 laptops, so I am looking and typing, not pasting:
 
from lspci - I get:
 
02:00.0 Network Controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
 
 
from lshw -C - I got:
 
*-network UNCLAIMED
       description: Network controller
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: [EMAIL="pci@0000:02:00.0"]pci@0000:02:00.0[/EMAIL]
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f1100000- f110ffff
 
 
from lsmod - get a big long return, can you get by with:
 
ndiswrapper              244768 0
 
I did not see the "ath" character string anywhere in there
 
 
sudo ndiswrapper -l returned nothing at all
 
Good news or bad?
 
thanks

---

### Post by kaldor on 2010-05-30
I think it's a well-known fact that you must have a MacBook Air to connect to the internet in Starbucks.

Realistically, it sounds like your laptop's wireless isn't supported by Ubuntu. Does it work at home?

---

### Post by henry cow on 2010-05-30
I haven't been to a Starbucks in months, I just needed a humorous title to get people to notice me - it worked.
 
The ethernet plug has always worked perfectly, except for the 3 times I have allowed something with "backports" in it to be installed, which killed the wire as well, and was a nightmare to get back.
 
I have never connected wirelessly for even a second under Ubuntu in the 2 months I have had this laptop, although the wireless connection under Windows is breathtakingly clean and fast - I am constantly amazed at how much better it is than my DSL on my big computer at home.
 
The "Wireless" tab under "Network Connections" has always stayed empty no matter what I have done, and the antenna button near the keyboard seems dead as well.

---

### Post by chili555 on 2010-05-30
> product: AR928X Wireless Network Adapter (PCI-Express)This is supposed to work with the module ath9k. Find out if it's on your system:```
modinfo ath9k
```It will either say 'not found' or it will say something like:> $ modinfo ath9k
filename:       /lib/modules/2.6.32-22-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
etc., etc.If it is on your system, please do:```
sudo modprobe ath9k
sudo lshw -C network
```Is it still unclaimed? Can you disconnect the ethernet cable, click the Network Manager icon and connect?

If the module is not on your system, please do:```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```Modprobe and check as above.

---

### Post by chili555 on 2010-05-30
> The ethernet plug has always worked perfectly, except for the 3 times I have allowed something with "backports" in it to be installed, which killed the wire as well, and was a nightmare to get back.I don't believe backports-*wireless* will have any effect on your wired ethernet.

---

### Post by henry cow on 2010-05-30
I had the ath9k module
 
When I did sudo modprobe ath9k I quickly got a black retangular dialog box in the upper right saying that a wireless connection was available.
 
However, when the mouse touched it blurred and grayed and would not take. As soon as the mouse moved away, it became clear and sharp again.
 
What the heck is that all about?
 
I am deathly afraid of that linux-backports thing. I have done it twice for you and once for somebody else, and each time it killed my ethernet connection and it took me a lot of work to get back. 
 
Also, I went to a lot of work to do this clean install and I do not want a single byte of junk leftover if I can help it. Whenever you tell me to do something and it does not work, can you also tell me how to totally clean it up afterwards?
 
Thank you so much.

---

### Post by henry cow on 2010-05-30
Oh yes, to answer your other questions, it DOES seem to be claimed now.
 
And no, I have tried literally hundreds of times to make a wireless connection from every which way that I can get there and never succeded. 
 
The "Connect Automatically" box is checked, but it still looks like it wants that SSID and BSSID information.
 
At this point I have 2 laptops in front of me (one belongs to work) and I do not have the computer in question online at this time, but I can plug it in if I need to.

---

### Post by henry cow on 2010-05-30
HELP - guys please don't give up on me.

I know this is obviously a hard one but can you give it one more shot?

Is there any other way to get a driver besides using my Windows driver?

Please don't leave me again.

---

### Post by anewguy on 2010-05-31
Since your lshw -C network only shows latency on the configuration line, then it isn't showing a driver loaded.  See my example below to see how the driver shows for my device:

```
dave@dave-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 7
       bus info: pci@0000:00:07.0
       logical name: wlan0
       version: 03
       serial: 00:1e:2a:46:a8:b4
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wg311v3 driverversion=1.55+NETGEAR,12/30/2005,3.2.3.2 ip=10.0.0.3 latency=32 multicast=yes wireless=IEEE 802.11g
       resources: irq:18 memory:cffe0000-cffeffff memory:cffb0000-cffbffff

```

sudo ndiswrapper -l <press enter>

If ndiswrapper -l returned nothing, not a single line, then the driver is not loaded, no matter what ndisgtk thinks (it does show the driver there when you go back into it, right?).  This would lead me to think we need to try something involving a little more typing than ndisgtk.  Hope you're ready!

- start up ndisgtk (system/administrative/windows wireless drivers) and remove any known drivers

- open a terminal window (applications/accessories/terminal)

- type:

sudo ndiswrapper -l <press enter>  It should return absolutely nothing.

Assuming your wireless driver files are on your desktop:

cd Desktop

sudo ndiswrapper -i netathrx.inf <press enter>

Did it return any errors?

sudo ndiswrapper -l <press enter> Obviously it will be different for your adapter, but it should return something like this:

 ```
dave@dave-desktop:~$ sudo ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
wg311v3 : driver installed
	device (11AB:1FAA) present
dave@dave-desktop:~$ 

```

It's important that it show both the device and the driver.  If it doesn't, stop there and post back.

sudo ndiswrapper -m <press enter>

sudo depmod -a <press enter>

sudo modprobe ndiswrapper <press enter>

sudo ifup wlan0 <press enter>

If at this point your wireless indicator is not lit, you can't check "Enable Wireless" in Network Manager, and you don't see any networks, stop and post back.

sudo gedit /etc/modules <press enter>

go to the end of the file and add:

ndiswrapper

save the file, close the editor, and reboot.  

Is the wireless indicator lit?  Is "Enable Wireless" in Network Manager already checked (or it is "checkable")?  Are there any wireless networks showing?

If not, try:

sudo ifup wlan0 <press enter>

If none of that works, also post back the output of:

iwconfig <press enter>

iwlist scan <press enter>


I know some of these outputs get long, but it is important to see all of the text.  You could try redirecting the output of the various "ls" and "iwconfig" commands to a file (follow the command by a space, the ">" sign, another space and the name of a file to store the output text in. ">" means to overwrite the file, ">>" appends to the file if you want to put all of the text in a single file). That way you could copy the file via a flash drive or CD to the machine you are using to get to the net and post it all back here.

Dave ;)

EDIT:  My suspicion:  ndiswrapper doesn't support Windows 7 drivers, at least as far as I know.  I think we may need to get you copies of the Windows XP drivers, keeping mind that if you have installed 64-bit Ubuntu we will need the 64-bit drivers, or if you have installed "normal" (32-bit) Ubuntu we will need the 32-bit drivers.  The drivers are easy enough to get so don't worry about that!

---

### Post by henry cow on 2010-05-31
Dave - 

thank you.

the device and driver appeared to already be installed.

sudo ndiswrapper -m returned :

module configuration already contains alias directive (about 100 times)

sudo depmod -a blinked for a few seconds and returned nothing

harry@hubuntu:~$ sudo depmod -a
harry@hubuntu:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
harry@hubuntu:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.

* * * * * * * * * *
everything still off and dead. I am still very curious why my switch and indicator light were live after the fresh install but died when we started mucking with these drivers.
* * * * * * * * * *

to save time, since your reply came after I went to bed, here is that last bit:

harry@hubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

harry@hubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

harry@hubuntu:~$ 

The laptop came with Windows 7 preinstalled, so I don't have a proper disc anyway.

---

### Post by anewguy on 2010-05-31
What did the ndiswrapper -l return?

Also, post back the output of:

lsmod | grep ath*


For now, it might be best if we also "undo" what we've done so far so we are back to a clean slate before moving on:

- in ndisgtk, remove all known devices/drivers

- sudo ndiswrapper -l

if anything is returned:

- sudo ndiswrapper -e <drivername>

until nothing is returned

- sudo gedit /etc/modules

go to the end and remove the line that says:

ndiswrapper

Save the file and exit the editor

sudo rmmod ndiswrapper

Now, reboot.

Since we removed the driver, does your wireless indicator light up again?

do the:

lsmod | grep ath*

lshw -C network

again and post here noting it is after the removal so I can tell them apart.

I have the Windows XP 32-bit and 64-bit drivers downloaded to my machine, so when we are ready to try those (I want the above finished and a chance to look at the output first) I can send them to you.

I was hoping by now that someone who had the exact adapter, etc., that you have would have "chimed in" but I guess nobody out there reading must have it working yet.  In that regard, I'm going to suggest you change the title of the thread to "10.04 - Atheros AR928x driver help needed" and see if someone else comes up with anything.  In the mean time, if you want to try the Windows XP drivers let me know.

Dave ;)

---

### Post by henry cow on 2010-05-31
harry@hubuntu:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netathrx : driver installed
    device (168C:002A) present (alternate driver: ath9k)
harry@hubuntu:~$ 

harry@hubuntu:~$ lsmod | grep ath*
vgastate                9857  1 vga16fb
v4l1_compat            15495  1 videodev
v4l2_compat_ioctl32    12020  1 videodev
pata_atiixp             4209  0 
harry@hubuntu:~$

* * * * * * 
after your housecleaning nothing turned up, and gedit/etc/modules returned nothing
* * * * * * 

harry@hubuntu:~$ ndiswrapper
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
harry@hubuntu:~$ 

* * * * * * 
harry@hubuntu:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
harry@hubuntu:~$ 

* * * * * * 

I don't really know what you mean by save the file and reboot, I don't see anything to save, but here goes with the reboot ......

---

### Post by henry cow on 2010-05-31
Dave - 

The reboot did not bring the antenna switch back to life.

Also, I now find that there are 2 ethernet connections that seem to be almost identical.

harry@hubuntu:~$ lsmod | grep ath*
vgastate                9857  1 vga16fb
v4l1_compat            15495  1 videodev
v4l2_compat_ioctl32    12020  1 videodev
pata_atiixp             4209  0 
harry@hubuntu:~$

harry@hubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f1100000-f110ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:26:22:51:d6:00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=172.16.0.15 latency=0 multicast=yes
       resources: irq:27 ioport:2000(size=256) memory:f1010000-f1010fff(prefetchable) memory:f1000000-f100ffff(prefetchable) memory:f1020000-f102ffff(prefetchable)
harry@hubuntu:~$

* * * * * * * * 

I will post a new thread as you suggest in Wireless & Networking

I came back to beginners because there seem to be a lot more people who are a lot more friendly and helpful here.

I have seen literally dozens if not hundreds of similar threads, sometimes different things work, for some people, like backports, madwifi, etc, but I don't think any of them have worked for me.

I am ready to try the Windows drivers.

Thank you so much, I really appreciate your help.

Chili555 spent a couple of days with me a few weeks ago, but gave up after a half a dozen or so attempts.

If you solve this, I know that there are lot of people out there who want to hear about it.

---

### Post by henry cow on 2010-05-31
Hey folks - 

I am typing this via a wireless connection on my Atheros AR928X via  Lucid!

Can you believe it, I can't.

NUB had the answer, (so did Dave) the Windows XP driver worked like a  charm. Obviously, the later stuff just hasn't caught up yet.

If any of you are reading this because your Atheros AR928X wireless card  will not work under Lucid, get the Windows XP driver and run that. One  of these days there may be a better choice, but this worked for me when  everything else failed. I wish I had tried it first instead of 15th.

There are a few strange anomalies, for example the switch button for the  antenna seems to work now, but not the LED. It stayed on solid after  the latest clean install of Lucid, even though not connected, but  installing the wireless driver seems to have turned it off permanently.  Mildly annoying, but no biggie.

Whether ethernet or wireless, it seems that whenever I make any  connection change such as unplugging the ethernet or switching the  button off or on, I am dead until I reboot. Is there not "hot switching"  in Linux? In Windows I can go back and forth at will.

All-in-all, this has been quite a learning experience for me, and an  acid test of my dedication to my migration from Micro$oft. If I had not  been trapped in a hotel room out of town for weeks on end I am not sure  if I could have pulled through.

Meanwhile, if anybody else has an Atheros wireless card under Windows 7  that will not run under Lucid, don't waste countless hours trying  convoluted fixes, get the XP driver below and be online in minutes. 

Trust me, that is the way to go.

---

### Post by anewguy on 2010-05-31
I just got back on so I didn't get a chance to reply to your request for the drivers before.  I'm glad that worked - I suspected ndiswrapper/ndisgtk wouldn't work with the Windows 7 drivers - I'm just sorry I didn't get you to the Windows XP drivers earlier!

Glad it's going!

Dave ;)

---

