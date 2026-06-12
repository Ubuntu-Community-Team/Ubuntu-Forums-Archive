---
title: "How to set un usb adsl modem"
date: 2005-06-21
forum: Networking &amp; Wireless
---

### Post by polloz on 2005-06-21
Hello,

I've run the Ubuntu 5.04 Live-CD to see if I can get my internet connection working, since if I can accomplish this then good bye windows and welcome ubuntu. the problem is that I have a adsl conection, and the modem I have is connectet through the usb drive. the brand and model is Huawei SmartAX MT810 ADSL USB Router. the thing is that when I run the live-cd I can't get my internet connection established. I wonder if anyone can help me by telling me if I need to download any drivers or what not.
Thanks a lot and hope I can dump windows ASAP

sergio

---

### Post by tadeuszk on 2005-07-15
Sorry sergio that I can not help you. I myself have exactly the same problem, only different ADSL modem type: Speadtouch 530.
I hope that some Linux expert will give us some clues soon.
After a bit of searching the Net, I thought that I had solution, I went so far as to go to the root in Terminal and run PPPOECONF but unfortunately this program only wants to configure Ethernet and knows nothing about USB connection.
cheers

---

### Post by voromax on 2005-07-18
Sorry... This is Not a Reply too... 
This is a quastion aboun the same... 

The modem Huavei mt810. As many others i would love to escape from M$ OS. Please help us! SOS!!!  ](*,)

well now i am installing PPPoE Client as it is explained in FAQ: [http://ubuntuguide.org/#rp-pppoe](http://ubuntuguide.org/#rp-pppoe)

---

### Post by vreemde eend on 2005-07-18
I also had some trouble configuring my ADSL-USB modem, because there is no Linux driver available from the modem company. But now it's working just fine. Unfortunately I have a different modem and I think the driver I used doesn't support the modems mentioned above. Maybe the reply of Dradul in [this topic](http://ubuntuforums.org/showthread.php?t=45923&page=1&pp=10) can help you.

---

### Post by luca_linux on 2005-07-18
Actually USB Modems are really a pain to get to work under Linux, simply because there aren't so many drivers...so, always the same story.
Anyway, there're some open source project aiming at getting USB to work under Linux.
An example is EciAdsl: [http://eciadsl.flashtux.org/index.php?lang=en](http://eciadsl.flashtux.org/index.php?lang=en)
And here's a list of supported modems: [http://eciadsl.flashtux.org/modems.php?lang=en](http://eciadsl.flashtux.org/modems.php?lang=en)
EciAdsl drivers are available in the Ubuntu repositories, search for them through Synaptic or apt.

---

### Post by voromax on 2005-07-18
Thanx friends!

I guess this will be a difficult road to the Open Source...
But it must be done.  

I will post my Howto after that.

The most interesting fact that at homepage of Huawei company it was said that:
MT810 ADSL USB modem
Windows 98 / 98 SE / ME / XP / 2000, Macintosh OS 8 / 9/ X, Linux OS;
PPPoA / PPPoE;

---

### Post by damonw5 on 2005-07-18
[QUOTE=voromax]Thanx friends!

I guess this will be a difficult road to the Open Source...
But it must be done.  

I will post my Howto after that.

Or not...

 ](*,)[/QUOTE]
 Voromax:

Is USB the only way to connect this modem to the computer, or does it have another way (such as ethernet)?

---

### Post by branco on 2005-07-18
Hi!

I use an ethernet modem-router under Ubuntu and it was unbelievably easy to configure (especially compared to my Intel  dial-up modem). The only tricky part, if  you can call it that, is to have the modem itself set up (you know, the 10.0.0.x address and all).

Once you've got that right, 90% of modems should work without any problem. Of course, there are cases when this doesn't happen, but you can always ask here in the forums for help.  ;-)

---

### Post by voromax on 2005-07-18
well.. the ethernet modem is the last thing i will try. 
If not solve such kind of problems now (mean new hardware drivers) later there will be more difficult. 
The only way the open source can survive - is a Community! 
And a readiness to solve the problem for the others

Well I hope so...


Status: searching.... 6% done  ](*,)

---

### Post by voromax on 2005-07-18
Well.. As I found out the modem Huawei MT810 has to work with a drivers Eagle-usb-2.0.0... It must help... 

Now I am studying the documentation at 
[http://faq.eagle-usb.org/wakka.php?wiki=InfoCMVEn](http://faq.eagle-usb.org/wakka.php?wiki=InfoCMVEn)
[http://packages.debian.org/unstable/net/eagle-usb-utils](http://packages.debian.org/unstable/net/eagle-usb-utils)

Still will be very appreciate for some more or less useful instructions about the installation process.. There is a real problem to stop everything to switch to M$ XP for some additional info from internet every time

Status: searching.... 15% done  ](*,)

---

### Post by voromax on 2005-07-19
there will be some useful info for this subj

[http://forum.eagle-usb.org/viewtopic.php?p=21279#21279](http://forum.eagle-usb.org/viewtopic.php?p=21279#21279)

and updates for the driver requirements: eagle-usb 2.3.2
This problem is NOT solved yet...
People! Lets help each other! We are the newbies... But not in everything!!!

Status: searching.... 19% done  ](*,)

---

### Post by sheepdog on 2005-07-19
Hi,

Here's how I got my Sagem F@st 800 USB modem working using the eagle-usb drivers:

[http://ubuntuforums.org/showthread.php?p=189972#post189972]("http://ubuntuforums.org/showthread.php?p=189972#post189972")

This works for me without any problems, hope it's of some help.

---

### Post by voromax on 2005-07-20
Thanx a lot sheepdog!

I will try this out asap! And then I will post the result here. Well I see again that the community is everything!

---

### Post by wint on 2006-02-12
I saw page where was solution of Install Huawei MT810 but to do that i haven't spme package and i don't know hove i can install it...
This is that packages:
        gcc (C-Compiler) 
        cpp 
        libgcc (C-Bibliotheken) 
        eazy (SUSE Compatibilty Links) 
        lsb (Standard Base Tools) 
        bison (C Parser Generator) 
        libusb (USB-Bibliotheken) 
        usbutils 
        make 
        ncurses 
        ncurses - devel (kernel-menuconfig) 
        rp-pppoe 
        kernel-source 
        dchclient
If SOMEBODY help me to install that packages i'll translate this solution and give it to ALL(solution is in RUSSIAN=))...
Help me and i'll help you....

---

### Post by wint on 2006-02-16
YEAH!:) :) :)  I did IT!
I install my mt810 on my Ubuntu!!!
All i need was 1) eagle-usb-2.3.2 
 //(and all things that need to install  tab of those package i write up) 
2) pppconf - rulezzz... this util help me to configurate my DSL-connection...

p.s. Hockey: Russia - Sweden 5:0 in Torino. YEAH!\\:D/ \\:D/ \\:D/

---

### Post by Rusangl on 2006-03-11
I've just connected!!! If anybody still needs it, I can describe my actions (sure only in MTU-Stream)

---

### Post by meethelemadathil on 2006-11-12
could u type some commands in ur methods to check how the usb modem is working even i  have the same modem in ubuntu it is not working

---

### Post by miloske on 2006-11-15
I have Actiontec modem, anybody has experience with it?

---

