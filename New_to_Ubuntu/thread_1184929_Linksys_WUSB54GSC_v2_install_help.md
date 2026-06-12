---
title: "Linksys WUSB54GSC v2 install help"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by steigerjb on 2009-06-11
:!: 

I fixed an old toshiba laptop and put Ubuntu 8.04 on it. (nevermind, i went ahead and installed 9.04 on it 6/23/09) I have this Linksys WUSB54GSC v2 wireless USB adapter i wanna use with it but I don't know how. All the tutorials online are **SOOOOOOO** confusing. Strange weird codes and stuff.

Please give me exact, step by step. VERY VERY simple instructions. All i know is i need to use ndiswrapper.

The user name for the Ubuntu account is "steiger". So you can give me the exact terminal codes i need, that may help.

I hope someone here can help. I don't wanna have to put Windows back on the thing. ](*,)

I've seen all the tutorial out there so please don't just post a link for a tutorial and say "try this"

Thanks in advance

---

### Post by steigerjb on 2009-06-13
bump

---

### Post by TeoBigusGeekus on 2009-06-13
If you insist on using 8.04 and not 9.04 (the newer the version the better the wireless support) then:
First thing to try is wicd instead of network-manager.
```
sudo apt-get install wicd
```

---

### Post by Mark Phelps on 2009-06-14
When you're here, you're not in one-click-land of MS Windows anymore; you're in a subset of the Linux community -- where some things (like in MS Windows) are really simple, and other things (like forcing Ubuntu to use MS Windows drivers) are really hard.

Installing and using NDISWrapper is one of the harder things to do.

To come here and tell folks NOT to point you to tutorials and then say you want details is a contradiction of terms.  IN Linux land, there are things that you just MUST become familiar (like using Command Line Interface (CLI) mode) in order to do.  If you're basically uncomfortable with command line work, you're in the wrong place.

The tutorial I've linked to below is about as detailed as they get.  If there are things in there you don't understand, you will need to do more background work on understanding Linux in general.

Tutorial:  

[http://ubuntuforums.org/showthread.php?t=225206&highlight=WUSB54]("http://ubuntuforums.org/showthread.php?t=225206&highlight=WUSB54")

---

### Post by steigerjb on 2009-06-20
I couldn't get past step 1 on that one.

"Step 1 - Install the essentials
If you've never used "make" or compiled something, then you probably don't have the necessary tools to get through this HOWTO. Thankfully, you can easily install them. Run the following command to be sure everything is ready.

Code:

sudo apt-get install cpp gcc build-essential linux-headers-$(uname -r)

If you are not online, apt-get will ask for the disk. Insert your install CD into the drive and hit the ENTER key."

it didn't ask for cd.

---

### Post by steigerjb on 2009-06-20
> **TeoBigusGeekus said:**
> If you insist on using 8.04 and not 9.04 (the newer the version the better the wireless support) then:
First thing to try is wicd instead of network-manager.
```
sudo apt-get install wicd
```

does that require internet?

---

### Post by Mark Phelps on 2009-06-20
> **steigerjb said:**
> does that require internet?

Yes, installing packages requires internet access in order to download the package from one of the repositories.

---

### Post by steigerjb on 2009-06-23
Mark,

I got all the way down to step 6, then realized that link you gave me won't help me:

[http://ubuntuforums.org/showthread.php?t=225206&highlight=WUSB54](http://ubuntuforums.org/showthread.php?t=225206&highlight=WUSB54)

it's for WUSB54GS v1 and v2

I have WUSB54GSC v2 <===note the difference (C)

Probably why the drivers weren't working LOL ("Plug in your device. The Power light will come on, and, after at most 3 seconds, the Link light will blink slowly. If the Link light does blink slowly, sucess!") Nope LOL


Now what?

---

### Post by Mark Phelps on 2009-06-24
Sorry, I didn't notice that distinction.
 
The .inf file tells the installer what drivers to load, so as long as you use the correct .inf file and drivers, the instructions are basically the same.  The .inf file and drivers are typically obtained from a CD that comes with the hardware.  If you don't have that, you will have to download the files from the hardware manufacturer's website.  Sometimes those come in .exe files (which you can't use in Linux), so if that is the case, you will have to run that file in MS Windows.  It will then most probably extract the files to a folder on your C: drive.  Copy the .inf and drivers files to somewhere that can be read when you're in Ubuntu, and you should then be able to redo steps 5 and 6.

---

### Post by steigerjb on 2009-06-24
I have a cd. I don't know what I am looking for here

---

### Post by steigerjb on 2009-06-25
It would probably be best for you to download the drivers:

[http://www.linksysbycisco.com/US/en/support/WUSB54GSC/download](http://www.linksysbycisco.com/US/en/support/WUSB54GSC/download)

I am version 2.0

then tell me what to do with them (make a folder?), what files to use, etc...

then give me the new codes

---

### Post by steigerjb on 2009-06-29
> **steigerjb said:**
> It would probably be best for you to download the drivers:

[http://www.linksysbycisco.com/US/en/support/WUSB54GSC/download](http://www.linksysbycisco.com/US/en/support/WUSB54GSC/download)

I am version 2.0

then tell me what to do with them (make a folder?), what files to use, etc...

then give me the new codes

bump :confused:

---

### Post by LewRockwell on 2009-06-29
> **steigerjb said:**
> bump :confused:



oh maaaarrrrkkkkk

---

### Post by steigerjb on 2009-06-30
> **LewRockwell said:**
> oh maaaarrrrkkkkk

yeah, were'd mark go. He was helping me :(

---

### Post by steigerjb on 2009-07-02
bump

I have installed both inf files (using this:[http://www.alstevens.co.uk/how-to-install-wireless-usb-drivers-for-ubuntu/]("http://www.alstevens.co.uk/how-to-install-wireless-usb-drivers-for-ubuntu/"), still no internet :( ](*,)

---

### Post by ibuclaw on 2009-07-05
When you boot into Linux, open a terminal, insert the WUSB54GSC device, then run:
```
lsusb
```
And make a note of the 8 alphanumeric digit ID that is on the same line as the device.

ie, mine looks like this:
```
...
Bus 007 Device 002: ID **03f0:171d** Hewlett-Packard Wireless (Bluetooth + WLAN) Interface
...

```

Regards
Iain

---

### Post by steigerjb on 2009-07-05
> **tinivole said:**
> When you boot into Linux, open a terminal, insert the WUSB54GSC device, then run:
```
lsusb
```
And make a note of the 8 alphanumeric digit ID that is on the same line as the device.

ie, mine looks like this:
```
...
Bus 007 Device 002: ID **03f0:171d** Hewlett-Packard Wireless (Bluetooth + WLAN) Interface
...

```

Regards
Iain

im outta town but then what

---

### Post by steigerjb on 2009-07-13
> **tinivole said:**
> When you boot into Linux, open a terminal, insert the WUSB54GSC device, then run:
```
lsusb
```
And make a note of the 8 alphanumeric digit ID that is on the same line as the device.

ie, mine looks like this:
```
...
Bus 007 Device 002: ID **03f0:171d** Hewlett-Packard Wireless (Bluetooth + WLAN) Interface
...

```

Regards
Iain

ok Iain, here ya go:

```
steiger@steiger-laptop:~$ lsusb 
Bus 001 Device 002: ID 1737:0075 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
steiger@steiger-laptop:~$ 
```

what do I do now? ):P

---

### Post by LewRockwell on 2009-07-13
might we also see the results of this:

```
sudo lshw -C network
```

and that's "el" "shw"...not a one...

.

---

### Post by 3370318 on 2009-07-13
I struggled for quite some time with this particular usb adapter as well.  Unfortunately, I found that nothing worked (multiple attempts with ndiswrapper across different driver versions, attempts at using the b43 native drivers and associated firmware, etc all failed).  I'd suggest returning the adapter and getting a Belkin FSD7050 adapter if you can.  This adapter seems to offer everything that the WUSB54GSC does and it works out of the box.

---

### Post by steigerjb on 2009-07-15
alright...get ready to pounce on me..........

I think i am going to throw in the towel, install windows. I am tired of trying to get the wireless card to work. it's just a spare computer anyway, I'll never use it.

---

### Post by kditty on 2010-04-24
> **steigerjb said:**
> :!: 

I fixed an old toshiba laptop and put Ubuntu 8.04 on it. (nevermind, i went ahead and installed 9.04 on it 6/23/09) I have this Linksys WUSB54GSC v2 wireless USB adapter i wanna use with it but I don't know how. All the tutorials online are **SOOOOOOO** confusing. Strange weird codes and stuff.

Please give me exact, step by step. VERY VERY simple instructions. All i know is i need to use ndiswrapper.


trust me, its hard and odd, but once you pull even something simple like this off, you will feel better than the one click fix windows crap. it makes you feel so much more confident once you begin to learn...

---

### Post by boom08 on 2010-11-26
I tried using Wireless Windows Drivers tool to install the ndis****.inf driver file from both the Linksys disc and C:\Program Files, and the stupid thing still won't work.
I've exhausted all resources. What do I do?

I have ubuntu 8.10 currently installed. If I need to upgrade, how do I do that without overwriting the system?

---

