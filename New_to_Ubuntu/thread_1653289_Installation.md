---
title: "Installation"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by RKulasiewicz on 2010-12-26
I downloaded and successfully installed Ubuntu 10.4. It ran for a couple of days and then I accepted an upgrade to 10.10 which was the begining of the end.
 
After installation I lost the graphic interface and instead I got a text only interface. Being new to Linux and Ubuntu this was of little use so I tried to reinstall Ubuntu 10.4. I initially received errors relating to drives which informed me that there were no disks in six drives. I have two hard drives and a single CD drive so I assumed the others related to a multi card reader. I tried the windows installer and live CD options with exactly the same results.
 
I dowloaded Ubuntu 10.10 and tried to install that. The installation halted with a message 'can not mount / dev/ loop0 (cdrom/ casper/ filesystem.squashfs) on// filesystem.squashfs'  When I try to install from windows I get an error message which reads 'permission denied' and a reference to wubi-10.10-rev197.log, which is a very long document.
 
I have tried Ubuntu 9.10 and 8.04.4 which result in pop up windows informing me that there is a boot CD error and the computer locks. No matter what boot options I have tried in all the versions of Ubuntu I receive errors.
 
I really do want to migrate to Ubuntu partly because my son came home from University with Ubuntu installed on his laptop so that he can easily commnicate with a mainframe and partly to get away from the clutches of Microsoft. Is there anyone who can help me resolve the installation issue. It can't have been a mistake that allowed me to install and run Ubuntu 10.4. 
 
There does not appear to be any self help that I can follow. This cannot be the only instance where Ubunt has not installed on a computer and there has to be a solution
Please help.

---

### Post by Runckle on 2010-12-26
Are you trying to install the correct version?
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) 
Are you trying to install on the correct drive and the correct partition? 
Pre format the drive before installation.
Then that should work. Use 10.10 Meerkat version then come back to us!

---

### Post by RKulasiewicz on 2010-12-27
I am trying to install Ubuntu on c: drive which is now empty and formatted. The d: drive contains a working Windows OS. Other than versions 9.10 and 10.10 I do not get as far as the options of where to install. Wouldn't the live cd installation work regardless of the state of the hard drives?

---

### Post by amjjawad on 2010-12-27
Hello and welcome :)

I guess you did all that while you have a Wubi Installation.

Anyway, that's exactly why I have a link in my signature saying : HOWTO Avoid Wubi.

Anyway, please follow the instructions in this link and "post" back the result here: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Please, once you post the result, highlight the text (yeah, I know it's long) and click "#".

Don't panic.

---

### Post by sailor2001 on 2010-12-27
when dual booting with windows, I've always found it is easier to format the partitions from windows. ie: rt. click "my computer" and then "properties" " manage" "disk managment" or wording close to that.

---

### Post by amjjawad on 2010-12-27
> **sailor2001 said:**
> when dual booting with windows, I've always found it **[COLOR=Red]is easier to format the partitions from windows[/COLOR]**. ie: rt. click "my computer" and then "properties" " manage" "disk managment" or wording close to that.

How is that possible? Windows, by default, can't deal with ext4 file system!

Windows for Windows. Linux for Linux. GParted comes with the LiveCD for a reason ;)

---

### Post by RKulasiewicz on 2010-12-27
I'm a bit lost with what the correct version is. I downloaded the differenr releases of Ubuntu for the intel 386 chip from the Ubuntu website. None correspond with the MD5 hash listed on the link. What does this mean and if this is stopping installation how is it cured?

---

### Post by RKulasiewicz on 2010-12-27
I do not have any kind of installation although the computer does default to a terminal when the installation fails which allows me to enter help for a list of commands. I have downloaded the boot info script but where do I put it and how do I access it from the terminal as none of the drives appear to be recognised by the dos name c: d: etc

---

### Post by amjjawad on 2010-12-27
> **RKulasiewicz said:**
> I'm a bit lost with what the correct version is. I downloaded the differenr releases of Ubuntu for the intel 386 chip from the Ubuntu website. None correspond with the MD5 hash listed on the link. What does this mean and if this is stopping installation how is it cured?

They forgot to post this: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by amjjawad on 2010-12-27
> **RKulasiewicz said:**
> I do not have any kind of installation although the computer does default to a terminal when the installation fails which allows me to enter help for a list of commands. I have downloaded the boot info script but where do I put it and how do I access it from the terminal as none of the drives appear to be recognised by the dos name c: d: etc

Everything is inside this link: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
I mean all the instructions!


All what I need is to post the result here in this forum. That's all.

---

### Post by RKulasiewicz on 2010-12-27
I was able to run winMD5Sum exactly as instructed but nothing I have downloaded corresponds to the hash list. I don't understand why or the significance.
 
I'm probably still suffering the effects of Christmas so please bear with me. The instructions for the boot info script link are clear enough but I downloaded the script using windows as I cannot install Ubuntu. The download is in a specific directory in a windows folder. The instructions tell me to include the path to the download but where can I put a copy of the downlaod so that my very limited access to Ubuntu terminal can find it?
 
I'm probably appearing very stupid but I do have some knowledge of dos and in my very early days I tried a hand at machine code which I do not intend to persue again.

---

### Post by amjjawad on 2010-12-27
> **RKulasiewicz said:**
> I was able to run winMD5Sum exactly as instructed but nothing I have downloaded corresponds to the hash list. I don't understand why or the significance.
 
What is the name of the file you downloaded? From where did you get it? how did you download it?


> The instructions for the boot info script link are clear enough but I downloaded the script using windows as I cannot install Ubuntu. 

No one asked you to install Ubuntu :)

1) You need to download Ubuntu from here: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

What kind of CPU do you have? if it's Intel and 32bit then install the default one.

2) Check MD5SUM as per the instructions you already have now.

3) Once the MD5SUM is equal then go ahead and burn the image to a CD. The instructions yet again are given ([http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)).
Try not to use high speed, try to burn using 16x for example.

4) Once the LiveCD is ready, please, put that CD into your CD-Drive

5) Reboot your machine

6) Make sure your machine set to boot first from CD-ROM - Check your motherboard manual if you don't know how.

7) Once you see a dark purple screen with a small icon for a man with opened arms, press any key.

8 ) Choose the first option which is "TRY"

9) Once you get the desktop, run the script as per the instructions given here: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) 

10) Make sure to download that script on your Desktop.

11) You'll get RESULTS.txt on your desktop.

12) Open it, select all, copy, paste it here, highlight the whole thing and click "#" on the top of the Window that you're posting inside. Do you see where is "**B**" "***I***" and "_**U**_"? it's on the opposite side.

13) Once we see the boot script, we'll be able to help you much better.

14) Done.


> I'm probably appearing very stupid.
No body is stupid so stop saying that ;)

---

### Post by RKulasiewicz on 2010-12-27
You're very kind and I appreciate your help. I have already downloaded Ubuntu 10.10 and 10.4 from the link you provided. The file name is ubuntu-10.10-desktop-i386.iso and ubuntu-10.4.1-desktop-i386.iso. They were downloaded by broadband connection. I have checked them using winMD5Sum and the check sums are not the same as from the table provided.
 
My computer runs a 32-bit version of windows but it can run a 64-bit version. I know that not all device drivers were supported by the 64-bit version of windows. Would this be a problem with Ubuntu and is it likely that a 64-bit version would install any better

---

### Post by RKulasiewicz on 2010-12-27
I've probably not made myself very clear. The first installation of Ubuntu 10.4 worked as it should have and for a couple of days I had Ubuntu up and running. Since then I cannot install any releases that I have downloaded. I cannot install using windows installer wubi. I cannot install from the boot cd which in addition will not even run the live cd and give me the option to try.
I get an error 
 
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs)
on //filesystem.squashfs
 
I then get a flashing cursor after (intramfs) prompt which allows me to open the help command facility. Is this of any help?

---

### Post by RKulasiewicz on 2011-01-03
I managed to solve the problem myself and I can tell you I am really chuffed. I downloaded the alternate installation torrent and installed Ubuntu 10.10 to my c: drive. Windows boot manager didn't recognise Ubuntu and visa versa so I changed connections to the hard drives making Windows the c: drive. I can now boot from either hard drive using the computer bios. It may not be a sleek solution but it works and I have a dual boot system on two hard drives which is what I wanted.

---

