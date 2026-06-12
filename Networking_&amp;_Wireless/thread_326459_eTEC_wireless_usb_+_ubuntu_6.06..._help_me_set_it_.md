---
title: "eTEC wireless usb + ubuntu 6.06... help me set it up please!"
date: 2006-12-27
forum: Networking &amp; Wireless
---

### Post by tom1979 on 2006-12-27
Hello, firstly id like to thank you all for making intresting reading and convincing me to make the switch to linux! ive successfully duel booted XP and ubuntu, i bought the book ubuntu unleashed to aid the instalation, and so far im doing ok!

One major issue was my intel pro wireless card appeared imposible to set up, so ive bought the eTEC XG-762N usb wifi adapter, as on the box is says linux kernel 2.4 & 2.6 supported.As of yet ive been unable to set it up. I can run a lan cable and happily go online in ubuntu, but im really lost as the how to install it. ive tried loading the .inf file through ubuntus windows driver loading tool, but thats about all im capable of at the mo. Can somebody please give me some very simple installation instructions for this device, or for the intel pro wireless pcmcia? and once its working id like to know why and how you come to make it work!

Thanks in advance.
Tom

---

### Post by Floppyjoe on 2006-12-27
Do you mean you tried it with Ndiswrapper?

I looked for your device on the hardware compatibility list here:
[http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)

and could not find it there. It may still work with ndiswrapper.

---

### Post by tom1979 on 2006-12-27
yes i think the wrapper program is what i used, it asks for the .inf file from the cd... so i loaded it in then the pc appeared to do nothing with it!am i missing something?

edit:

after looking on that list..
Intel  	802.11b  	WPC2011BWW  	PCMCIA  	Symbol  	
	
	uses proprietary firmware

is the pcmcia card i use... would it being there suggest i can use this card afterall?

---

### Post by Floppyjoe on 2006-12-27
What is the output of:
```
ndiswrapper -l
```
when entered into the terminal?
Can you post this?

---

### Post by tom1979 on 2006-12-27
ahhh my bad i used "windows wireless drivers" and the result of that command says no drivers installed...

so what do i do?! cheers for the quick replies ;)

---

### Post by Floppyjoe on 2006-12-27
Copy the driver files from the cd that came with the device to your home folder. There should be a driver.inf and a driver.sys and possibly a .bin file that needs to be copied to your home folder

Then make sure ndiswrapper-utils version 1.8 is installed on your computer using Synaptic Package Manager via System/Administration/Synaptic Package Manager

Then open a terminal and enter the command:
```
sudo ndiswrapper -i driver.inf
```
where driver is the name of the driver you copied from the cd. It is case sensitive so make sure you spell it right.

Then enter this:
```
ndiswrapper -l
```

If it says the driver is installed and hardware present then enter this:
```
sudo modprobe ndiswrapper
```
The light on the usb device may or may not come on.

Then try this:
```
iwconfig
```
and post the results here

---

### Post by tom1979 on 2006-12-27
ok im failing miserably. cd driver folder contains : wlanUZ2K.sys, wlanUZ64.sys, wlanUZ98.sys, wlanuzg.cat, wlanUZG.inf, wlanUZME.sys, wlanUZXP.sys .

ive tried installing several, but assume the only possible good files are the .inf and wlanUZ64.sys.

heres an extract from terminal
laptop:~$ sudo ndiswrapper -i WlanUZG.inf
wlanuzg is already installed. Use -e to remove it
laptop:~$ ndiswrapper -l
Installed ndis drivers:
wlanuz64.sys    invalid driver!
wlanuz98.sys    invalid driver!
wlanuzg invalid driver!
wlanuzxp.sys    invalid driver!

edit: opening the inf file i find a script...

; WlanUZG.INF

;

;   This installation script supports Windows 98SE, ME, 2000, XP for the

;   Wireless LAN Adapters.

so im guessing this dosent infact support linux as the box suggests :S

is there anyway you could edit the script to make it work?

---

### Post by Floppyjoe on 2006-12-27
Ok slow down a bit.

You can only have one .sys and one .inf file in your home folder when you do the sudo ndswrapper -i command.

First you need to delete all those invalid drivers using:
```
sudo ndiswrapper -e driver
```
Where driver is the driver listed in the ndiswrapper -l command.
So I would do the sudo ndiswrapper -e command for each of the invalid drivers.

Then you need to install only one of these drivers. Im trying to figure out which one here. You might have to just have the wlanUZG.inf file in your home folder and the wlanUZXP.sys file.
usually these files have the same name so if it deoesn't give you a valid driver when you install the wlanUZG.inf driver using sudo ndiswrapper -i wlanUZG.inf then delete it using the sudo ndiswrapper -e driver command. and change the name of wlanUZXP.sys to sudo wlanUZG.sys and try it again.

I hope this works.

(I'm headed off for Wednesday prayer meeting. Will be back in about 1 1/2 to 2 hours if you would like to continue later)

---

### Post by tom1979 on 2006-12-27
yes i tried the inf file first on its own and then the 64.sys ive now tried each one at a time and always invalid drivers. can u recomend a pcmcia card i can buy tomorow?! cheers for trying :(

---

### Post by Floppyjoe on 2006-12-27
I believe you need to have both the .inf file and the .sys file present in the folder where your are installing the driver from but only one of each. You need to make sure the that the terminal is in right directory. The terminal opens up in your home folder. This is not the Desktop. If you click on Places/Home Folder, that is where the files need to be. If you try to install a driver that is on the Desktop but the terminal is on the home folder it will result in an invalid driver. I hope you understand this.  You can change to the desktop directory in the terminal from the home folder directory by using the cd command:

```
cd /home/username/Desktop
``` 
and then install drivers that are on the Desktop.

Also you never  install the .sys file only the .inf file but the .sys file needs to be present.

---

### Post by tom1979 on 2006-12-28
Ok well i gave up on this usb dongle, and bought a linksys wpc54g v3 pcmcia card, and got it up and running through the ubuntu's menus, bassicly wrapping the .inf file as u described originally, and then setting it up with wireless connection manager! so now i just have to destroy the unoperatable first install of ubunto and i have a fully functional and usable pc again! go me!cheers for your help ;)

---

