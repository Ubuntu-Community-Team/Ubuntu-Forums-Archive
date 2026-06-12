---
title: "Download help"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by bazerka on 2010-11-02
Hi, 
I am utterly new to Ubuntu and everything, but i have a question. I am trying to download the windows wubi.exe installer for my comp so i can get dual boot with Ubuntu. But everytime i run the installer it goes for like 2 hours and than says "permission denied check log c:\users\alex\appdata\local\temp\ubuntu...." any idea what tis means? I'm running vista home premium x64 bit. and yes i am on the admin account. Also another question when you download the actual boot from a cd/usb ubuntu can that be used as a dual boot as well? or does that make ubuntu your sole operating system? thanks 
-Baz

---

### Post by Hippytaff on 2010-11-02
you can dual boot by installing from livecd/usb, (read up on the various opyions available to you about this first) but back anything that you want to keep up before doing that just in case...I didn't but it is advisable. wubi installs ubuntu 'inside' windows, so it's not a true dual boot but its good for trying out ubuntu. :-)

you can also just boot from a livecd/usb to try ubuntu, by choosing cd or usb in the bios boot order (ask if you need to)

btw, welcome :-)

---

### Post by bazerka on 2010-11-03
Thank you! That didnt really answer my question about the Wubi installer, but what ever Im just gonna try the usb boot than if it doesnt interfere with the windows aspect (like i totaly dont have to erase it). Thanks :). Also another question when u install ubuntu frm a usb do you always need to have that usb plugged in when using ubuntu? or do u only have to do it once?

---

### Post by Hippytaff on 2010-11-03
If your booting from usb, then you have to have the usb plugged in...if you install ubuntu to the hard drive (as dual boot) you don't. btw sorry I didn't quite answer your question.

---

### Post by sikander3786 on 2010-11-03
If Wubi is unable to download the Ubuntu iso, you can just grab the standard image from

[http://www.ubuntu.com](http://www.ubuntu.com)

and it already contains the Wubi installer. Just mount the image or burn it to disc and use it as an installation media.

The downloaded image can be used for a dual boot setup as well. You can just try it from the CD or USB. If you wan to install it, you can actually install it in dual boot to Windows. Just take care of your Windows partition.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

A dual boot setup is recommended over Wubi. It is much faster, less problematic and you can upgrade the whole OS to the new version when it comes out.

---

### Post by bazerka on 2010-11-04
Thanks for the responses, and np with the wubi i just gave up on it hahas :P. I am currently downloading the 64 bit iso normal ubuntu download. I am gonna try it from a usb so we shall see how it goes :D. I just wanted to know that after you install it if i 1) had to totally erase my windows, and 2) if after i installed it i needed to always keep my usb plugged in, but apparently i dont so thanks :D I look forward to this aloooot :D:D.
 
One last question tho, when im in my ubuntu partition i cant run my windows programs right? But with the partition can i still access my documents and music n what not? or is it totally seperated?

---

### Post by Hippytaff on 2010-11-04
You can run some windows apps with an package called Wine and you can access documents you've got on windows from Ubuntu, but you have to set that up.
 
[http://en.wikipedia.org/wiki/Wine_(software](http://en.wikipedia.org/wiki/Wine_(software))
[http://www.wikihow.com/Access-Windows-Files-in-Ubuntu](http://www.wikihow.com/Access-Windows-Files-in-Ubuntu)

---

### Post by mastablasta on 2010-11-04
> **bazerka said:**
> 1) had to totally erase my windows, ?
 
no you just reduce the size of partition that windows uses. 
 
you can access windows files out of the box as far as i know. and even from liveCd or US you will be able to access them.

---

### Post by Hippytaff on 2010-11-04
> 
access windows files out of the box 

Really? I wish I'd known that two months ago :-)

---

### Post by bazerka on 2010-11-04
Ok one majjjjor question i just realized that i need answered. I live in china and cause its lame n what not my internet is a dial up. Meaning that i have a seperate Pppoe connection that i need to dial up before i connect to the internet (i know stupid, but its suprisingly fast so what ever). On windows its easy to set up, i just type in the username and password that is needed. My big question is if this is avaliable on Ubuntu? Can i still dialup to my internet while running Ubuntu? or does it only support Wifi n what not? 
 
Also! i dont get this step from the "How to access windows files from ubuntu:
 
**Having located the partition, write down the name – it will look something like [COLOR=green]/dev/hda2[/COLOR] or [COLOR=green]/dev/sda2[/COLOR], depending if your drives are PATA, SCSI or SATA**. Do this carefully – this is no time for dyslexia. Now check to see if this is the partition by manually mounting it and looking at the files.
 
Thanks so much!
-Baz

---

### Post by bazerka on 2010-11-04
Ignore that cry for help on the accessing windows from ubuntu, i got it lolz just read it wrong

---

### Post by bazerka on 2010-11-04
> **mastablasta said:**
>  
you can access windows files out of the box as far as i know. and even from liveCd or US you will be able to access them.
 
What does out of the box mean? o.o

---

### Post by Hippytaff on 2010-11-04
> **bazerka said:**
> What does out of the box mean? o.o
 
It means you don't have to configure anything, it just works :-)

---

### Post by bazerka on 2010-11-04
really?!?! well thats handy rofl, well i guess i should wait till i actually get ubuntu up and running hahas :D im so excited i cant wait! XD. this will be awesomeeee been waiting for a while for this :P. i found my answer to the broadband tho. i just need my provider info ubuntu provides the connection (i think rofl)

---

### Post by gneerajg on 2010-11-12
I am new to the forum. I am having trouble downloading Wubi.exe . Got an message download started nothing comes up. then I downloaded the ISO but it does not work without wubi.exe. Pl. guide
My system specs are
Windows XP Pro 2002 SP3
Dell Inspiron 1520
 
Thanks in advance

---

### Post by Hippytaff on 2010-11-12
> **gneerajg said:**
> I am new to the forum. I am having trouble downloading Wubi.exe . Got an message download started nothing comes up. then I downloaded the ISO but it does not work without wubi.exe. Pl. guide
My system specs are
Windows XP Pro 2002 SP3
Dell Inspiron 1520
 
Thanks in advance

Your probably better off starting a new thread. :-)

How we tackle this, depends on what you want to do. If you want to run Wubi, it means that your running Ubunutu, kind of inside windows. If you want to have a dual boot with Ubuntu and windows (ie both operating systems) then you need to nurn the iso to cd and install a dual boot that way. But like I said, post a new thread and you'll get all the help you need :-)

---

