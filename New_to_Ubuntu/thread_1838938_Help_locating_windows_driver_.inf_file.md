---
title: "Help locating windows driver .inf file??"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by Operator1 on 2011-09-04
Hi,

Apologies if this is a stupid question but Ive just decided to give ubuntu a go instead of vista, I am dual running it, booting from the cd. I cannot get ubuntu to recognise my  Belkin N 2000uk wireless adapter.

I have gone as far as 

[LIST=1]
[*]                     Install **ndisgtk** (System &#8594; Administration &#8594; Synaptic Package Manager).
[*]                     Open **ndisgtk** (System &#8594; Administration &#8594; Windows Wireless Drivers).
[/LIST]
My question is how do I obtain the Windows Driver for your system and locate the file that ends with .inf. ?:confused:

Thanks for your help.

---

### Post by haqking on 2011-09-04
> **Operator1 said:**
> Hi,

Apologies if this is a stupid question but Ive just decided to give ubuntu a go instead of vista, I am dual running it, booting from the cd. I cannot get ubuntu to recognise my  Belkin N 2000uk wireless adapter.

I have gone as far as 

[LIST=1]
[*]                     Install **ndisgtk** (System &#8594; Administration &#8594; Synaptic Package Manager).
[*]                     Open **ndisgtk** (System &#8594; Administration &#8594; Windows Wireless Drivers).
[/LIST]
My question is how do I obtain the Windows Driver for your system and locate the file that ends with .inf. ?:confused:

Thanks for your help.

1. download it from the drivers section for your device from manufacturers website.

or

2. boot into windows and browse to the c:/windows/system32 directory in windows or search for it if in different location

or

 3. browse from Ubuntu to your windows partition if it is available.

---

### Post by spiky001 on 2011-09-04
Drivers are here [http://en-us-support.belkin.com/app/answers/detail/a_id/464/~/f5d8053-n-wireless-usb-adapter---drivers](http://en-us-support.belkin.com/app/answers/detail/a_id/464/~/f5d8053-n-wireless-usb-adapter---drivers)  you might be able to just unzip the file the inf should then be there

---

### Post by Operator1 on 2011-09-04
> **haqking said:**
> download it from the drivers section for your device from manufacturers website.

boot into windows and browse to the c:/windows/system32 directory in windows or search for it if in different location

or browse from Ubuntu to your windows partition if it is available.

Thanks, Iv downloaded the belkin software and driver to a usb stick, Il try your suggestion now

---

### Post by haqking on 2011-09-04
> **Operator1 said:**
> Thanks, Iv downloaded the belkin software and driver to a usb stick, Il try your suggestion now

ok then in which case it should be amongst that package your downloaded.

unpack it and should be there

my above suggestions were 3 different methods by the way

---

### Post by spiky001 on 2011-09-04
Read this [https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053](https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053)

---

### Post by Operator1 on 2011-09-04
I tried saving the software and driver to a usb, when i open the usb in ubunt I have autorun.inf, BOOTEX.LOG AND f5d8051v2_ww_2.02.04.exe. None of which run in the wirless network drivers installation box.

I forgot to say i have no hard connection to the net so I have to reboot to windows get online on the desktop, Im ususing a net book for this.

---

### Post by Operator1 on 2011-09-04
> **spiky001 said:**
> Read this [https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053](https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053)

Just tried this and im rebooting
:)

It definately did something anyway!

---

### Post by Operator1 on 2011-09-04
> **haqking said:**
> ok then in which case it should be amongst that package your downloaded.

unpack it and should be there

my above suggestions were 3 different methods by the way
Apologies, let me rephrase that, im trying your "first" suggestion!

---

### Post by Operator1 on 2011-09-04
No still no good, I guess its on to suggestion 2!

---

### Post by haqking on 2011-09-04
> **Operator1 said:**
> No still no good, I guess its on to suggestion 2!


ok so boot into windows, use device manager to find the wireless adapter and look at properties and it will show the files it is using.

Depending on what you need they are probably in the \system32 or \inf directory

---

### Post by Operator1 on 2011-09-04
Ok in device manager, and I have located the N1 Wireless USB network adapter. What now?

---

### Post by Operator1 on 2011-09-04
I have the NVIDIA nForce Network Controller and the N1 Wireless USB adapter, the closest I can get to a inf file is in NVIDIA GeForce 8300GS.

I wonder if I hooked up to an ethernet connection will Ubuntu remedy the device drivers? It is prompting me when I boot about available unauthorised devise drivers for NVIDIA?

---

### Post by Kreacher on 2011-09-04
Not completely sure one USB devices, however: 

Wireless device driver install. First move:

Look on the menu for the Network manager applet and right click on it  (usually has an up and down arrow icon). Right click and note if the  three "Enable" are checked. If not, check them. 

If the wireless one is not there, look on the menu for  System>Administration>Hardware Drivers and click. Wait a few to  see if your card is detected. If yes, then install. 

This worked for my wireless card.

---

### Post by spiky001 on 2011-09-04
That would be a good idea check for hardware drivers as well as updating, "Applications hardware drivers"

---

### Post by haqking on 2011-09-04
> **Operator1 said:**
> I have the NVIDIA nForce Network Controller and the N1 Wireless USB adapter, the closest I can get to a inf file is in NVIDIA GeForce 8300GS.

I wonder if I hooked up to an ethernet connection will Ubuntu remedy the device drivers? It is prompting me when I boot about available unauthorised devise drivers for NVIDIA?


Well you said in OP you wanted the Belkin one ?

if you look at the properties it should list the files it is using and there locations.

lilke i said usually in \system32 or \inf

it will show some files like xxxxxx.inf

---

### Post by Operator1 on 2011-09-04
When I try to search for drivers I get a "no proprietary drivers are in use on this system" there is an activate button but when I try actvate it comes up Failed to fetch http: etc.

I wonder is it because i have no connection to the net, a ethernet connection might help but I have access to one at the minute

---

### Post by Operator1 on 2011-09-04
> **haqking said:**
> Well you said in OP you wanted the Belkin one ?

if you look at the properties it should list the files it is using and there locations.

lilke i said usually in \system32 or \inf

it will show some files like xxxxxx.inf

Sorry for any confusion, I do want belkin, at the moment vista is running fine of the belkin usb adapter, thats th only connection I have at the minute via wifi

---

### Post by ajgreeny on 2011-09-04
I seem to remember that by default windows will not show the file suffix of a file-type it recognises, ie, in your case the .inf.

I always changed that in my windows setup, when I had one, and things may have changed now, but I am just wondering if this could be the reason for you not finding the .inf file that you need.

PS:  If you have a windows CD for the driver of the wireless adapter, you may find the needed .inf file in that somewhere.  That is how I found the **wg511.inf** file for my Netgear adapter.

---

