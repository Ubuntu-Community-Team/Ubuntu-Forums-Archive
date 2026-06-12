---
title: "D link dwp 157 datacard"
date: 2014-09-29
forum: Networking &amp; Wireless
---

### Post by sadasivam on 2014-09-29
Recently I bought a new 3g datacard. It is Dlink dwp 157 3g wireless data modem usb card. It does not work with Ubuntu 14.04. Even it cannot be recognized as a cdrom. I cannot access it either as a storage medium or a data card. But lsusb results Dcorp something. Please help me to use the datacard in Ubuntu 14.04.

---

### Post by varunendra on 2014-10-01
Welcome to the forums Sadasivam!

While the modem is plugged-in, please open a terminal (Ctrl-Alt-T) and post back the outputs of following commands -
```
lsusb
dmesg | tail -20
```
Preferably run the above commands 30-40 seconds AFTER plugging in.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by Bucky Ball on 2014-10-01
*Thread moved to **Networking & Wireless**.*

Welcome. Better luck here. ;)

---

### Post by Bucky Ball on 2014-10-01
@sadasivam: I have sent your last four posts to jail. We don't delete them. Please provide relevant links which don't require a login or take a screen shot and attach it to your post using Adv. Reply or Go Advanced in your next post and clicking the paperclip icon>attach pic. I realise you probably weren't looking to cause any harm. Thanks.

---

### Post by sadasivam on 2014-10-01
Sir,
  Here is the attachment of a png file.

---

### Post by Bucky Ball on 2014-10-01
Hmm. Appears to be picked up just fine there, but Varun possibly knows more about this stuff. When you open a file manager, Nautilus for instance, it doesn't appear there in the left column?

Could you remove the card and all other USB devices and anything else (dongles, not mice, etc.) restart the machine, plug in the datacard and then give the readout of 'dmesg' varunendra's two commands about half a minute later? I know this sounds like a repeat, but just to make sure. ;)

---

### Post by sadasivam on 2014-10-01
Yes, Sir. It does not appear.

---

### Post by Bucky Ball on 2014-10-01
Hmm.

---

### Post by varunendra on 2014-10-01
Thanks for the backup BB!

It is detected, but didn't change its mode from storage to modem as per dmesg. The device ID looks too new for modeswitch.

If you open Disk Utility program, does it appear as a mounted CDrom? We may need the contents in its storage area, hoping for a linux configuration or at least clues for modeswitching.

---

### Post by sadasivam on 2014-10-01
Yes, Sir. It can be detected as hspa_usb scsi cd-rom in disk utility program with 101 MB.
I cannot read the contents in linux. 
But,
The contents says to type "sudo modprobe usbserial vendor=0x2001 product=0x7d0c" in terminal.
(It is /dev/sr1)(Read Only)
How to eject it, as a storage medium?(But there is no cdrom in file manager nautilus)
I think I have to install another file manager and that file manager may detect it as a cdrom. Then I can eject it as a storage medium. Automatically it can be converted into data card. Then there is a possibility of using it...

---

### Post by varunendra on 2014-10-01
> **sadasivam said:**
> Yes, Sir. It can be detected as hspa_usb scsi cd-rom in disk utility program with 101 MB.
I cannot read the contents in linux. 
But,
The contents says to type "sudo modprobe usbserial vendor=0x2001 product=0x7d0c" in terminal.

Where did you read the contents? From Windows? Could you post the entire contents of the linux driver directory?

If the disk utility shows its size, it may be only a matter of mounting it correctly.

It can be ejected from the Disk Utility program, but that would work only when modprobe has done its job. The terminal reference you found is not much useful I'm afraid, it also needs something called "Message Content", a long alphanumeric code. For example "55534243785634120100000080000601000000000000000000000000000000", but this is from a different device's configuration file.

A different file manager or anything else is not going to help until usb_modeswitch does its job, for which it depends on the correct configuration data (the above message content) and the vendor/product IDs (which we already have), nothing else.

---

### Post by sadasivam on 2014-10-17
I have tried with Nemo file manager, the same problem...

I did not notice the second page... Thank you Varun, Sir. Very soon I shall post "message content".

Here is contents of D link dwp 157 datacard contents ....
OMG, File Size Restriction....

[URL="https://drive.google.com/file/d/0BzEgjgeXTetWelpKWENCY1FlcjA/view?usp=sharing"]Here is the contents of D link dwp 157 datacard contents... 

https://drive.google.com/file/d/0BzEgjgeXTetWelpKWENCY1FlcjA/view?usp=sharing[/URL]

---

### Post by varunendra on 2014-10-22
Just looked at the contents, and apparently it is an outdated file with reference to a different device. The kind of ignorance or stupidity that is not new from vendors towards Linux.

The contents mention using "usbserial", which is a much slower and comparatively inefficient driver meant for slower devices. The recommended driver for 3G devices is "option" (it's the name of the driver) as it can easily keep up with the high speeds that a 3G connection offers.

But anyway, since we don't have the "Message Content" for now, please try usbserial as they have suggested in the file, with the **_corrected_** device ID (the command in the pdf is for a device "7d0c", while yours is "a403") -
```
sudo modprobe usbserial vendor=0x2001 product=0xa403
```
..after plugging in the modem. Report back if you see any errors. If not, please check -
```
lsusb
dmesg | tail -20
```
Did the device change its ID from [2001:a403] to something else? You may need to 'Eject' it's virtual CDrom part using "Disk Utility" program to let the modeswitching complete.

**PS:**
I think you should forget the pdf included on the cdrom part now. It is outdated and misleading.

---

### Post by sadasivam on 2014-11-22
modprobe command not found

After installing UBUNTU 14.10, my problem was solved. UBUNTU 14.10 recognize my modem as a CD (Storage medium), so that i can read the contents of it. To recognize it as a modem, I have to eject it. Then it is recognized as a modem not as a CD. Now I can use it as a Modem. My problem Solved. Thanks...

---

### Post by Hemant_Koushik on 2015-02-05
Actually I have managed to work with D-link DWP 157 on Ubuntu 10.10. After inserting the Data Card you will see no cd/dvd entry on Computer but you will find one in System>Administration>Disk Utility ; just eject it from Disk Utility and it will appear again there with similar name but this time you can give sudo modprobe... command in a terminal and wait for 10 seconds. Then you can add a new Mobile Broadband connection with system recognizing your Data Card as "DWP-157". :)

---

### Post by Bucky Ball on 2015-02-05
> **Hemant_Koushik said:**
> Actually I have managed to work with D-link DWP 157 on Ubuntu 10.10. After inserting the Data Card you will see no cd/dvd entry on Computer but you will find one in System>Administration>Disk Utility ; just eject it from Disk Utility and it will appear again there with similar name but this time you can give sudo modprobe... command in a terminal and wait for 10 seconds. Then you can add a new Mobile Broadband connection with system recognizing your Data Card as "DWP-157". :)

Welcome. 10.10 is no longer supported and this thread was solved a couple of months ago (by installing the supported release 14.10), but thanks for sharing. ;)

Best to upgrade to a supported release. See [here]("http://ubuntuforums.org/showthread.php?t=2229730"). Good luck.

---

### Post by Bucky Ball on 2015-09-05
Time for bed.

*Thread closed.*

---

