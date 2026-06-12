---
title: "New to Ubuntu"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by PhatKat on 2008-03-25
Hi there - yay post #1 :lolflag: So my windows has been crashing a lot this past few days and it could be a HDD problem for all i know but in the meantime i was fiddling with my Ubuntu live CD that i burned off the net and i am seriously of experimenting on one of the family PCs in the house with Ubuntu. I have some questions though:

1) Lets say i have 3 other terminals with windows OS and they are all in a wireless network - can i connect wirelessly with the PC using Ubuntu?

2) I read that list of supported wireless adapters and am pleased to see some Edimax ones cos i use them! Saw that the list is under construction - anyone know if Edimax EW-7318uG is supported?

3) What browsers are available on Ubuntu? Opera available?

4) Can i do anything on the net that i can on Windows on Ubuntu? I.e watch shows online, MSN chat, internet banking, yada yada

5)For hardware: is there a shortage of drivers for linux/Ubuntu?

6) Would you recommend Ubuntu to a non gamer who mostly surfs, does office work and does a lot of movies/music? Oh and is something like Realplayer available for Ubuntu?

Thanks in advance to anyone who could enlighten men on these questions of mine :popcorn:

---

### Post by insineratehymn on 2008-03-25
Wow.

It's almost like you set someone up for a sales pitch for Ubuntu!
I'll just start at the beginning:

1) Yes. Samba is a service that you can run on your Ubuntu machine that will allow all windows computers to see, access, read, write, and execute all of the files (that you let it) on your linux box.

2) I can't speak from experience about the Edimax EW-7318uG... But I can say that I have used some pretty obscure wireless cards (both PCMCIA and USB) and I have never even needed to install a driver; they've always been included in the build on the CD!

3) Opera? Sure. Firefox? Sure. Internet Explorer? Sure. Konquerer? Sure. You name it, Ubuntu has it.

4) You can get an almost unlimited amount of plugins and MIME types for any browser you wish to run on your shiny new Ubuntu box. It will allow you to do everything from watching flash movies, doing a fantasy baseball draft, checking your account balances, ebay, and anything else you use the internet for.

5) Drivers? Lots of them. Between the restricted and universe drivers there are probably thousands. 

6) OpenOffice is the standard for open-source office software, and is quickly making a dent in even the PC world. It is completely free and is 100% compatible with any MSOffice formats (.xls, .doc, .ppt, etc...)

Have fun with it, and just think about this... your days of paying for half-working software are gone!

---

### Post by PhatKat on 2008-03-26
> **insineratehymn said:**
> Wow.

It's almost like you set someone up for a sales pitch for Ubuntu!
I'll just start at the beginning:

1) Yes. Samba is a service that you can run on your Ubuntu machine that will allow all windows computers to see, access, read, write, and execute all of the files (that you let it) on your linux box.

2) I can't speak from experience about the Edimax EW-7318uG... But I can say that I have used some pretty obscure wireless cards (both PCMCIA and USB) and I have never even needed to install a driver; they've always been included in the build on the CD!

3) Opera? Sure. Firefox? Sure. Internet Explorer? Sure. Konquerer? Sure. You name it, Ubuntu has it.

4) You can get an almost unlimited amount of plugins and MIME types for any browser you wish to run on your shiny new Ubuntu box. It will allow you to do everything from watching flash movies, doing a fantasy baseball draft, checking your account balances, ebay, and anything else you use the internet for.

5) Drivers? Lots of them. Between the restricted and universe drivers there are probably thousands. 

6) OpenOffice is the standard for open-source office software, and is quickly making a dent in even the PC world. It is completely free and is 100% compatible with any MSOffice formats (.xls, .doc, .ppt, etc...)

Have fun with it, and just think about this... your days of paying for half-working software are gone!


Wow thanks a lot and that was the kind of information that was most useful for me! So are you saying that drivers for wifi cards/adapters are already on the Ubuntu OS? Which version is that if so? Hmm can i connect to the internet with my live CD if i also burn samba to disc u think? As in not an install just fiddling around? Ok i take it that Linux/Ubuntu would be far safer for I-banking compared to Windows then? Suppose i use Firefox - so all those add ons/extensio would work fine on Ubuntu right? Yes i so agree! 'Big Brother' is slowly over milking us poor sods with Windows and people should at least be open to te idea of an alternative OS. OSX and Hackintosh don't sit well with me so :lolflag: Hmm maybe i start a side project and build a linux box - any recommendation for hardware/configuration by any chance? Maybe under $250 w/o monitor? Ok what u think of this kind of box:

AMD x2 4000+ = $60
ECS 690G = $30
Hitachi 160gb = $49
LiteOn DVD burner = $24
2 x 1gb Value Rams = $40
Cheap casing with 4xxW psu = $25
Total = $230 (all from Newegg.com)

---

### Post by insineratehymn on 2008-03-26
Most of the drivers are already included in any current version of Ubuntu you wish to install.

The live CD also has the ability to detect, configure, and connect with just about any hardware setup that you already have; no modification of the live CD should be needed.

Samba is a service that your linux box must run in the background. When the live CD is running, the operating system is basically running in memory, so I wouldn't suggest setting up any services to do any real load handling because it would cause your computer to run awfully slow.

About the e-banking... Please remember that information traveling over the internet is only as secure as the internet; which, by design, is not very secure at all. I can say, however, that any information stored on your computer itself is fairly safe from things like malicious trojans or viruses, as not many have been written for Unix (why penetrate 2% of the desktop market with something that takes months to write?) 

Firefox is the standard browser that comes with Ubuntu. There is an option to install Kubuntu, which uses the KDE desktop envirnoment and also uses a browser called Konquerer, which is a very good browser I must say. By default, Ubuntu comes with an environment called Gnome; who, like I said, has a default browser of Firefox. Any add-ons that you were accustomed to using on Windows should be accessable on your shiny new ubuntu box as well (i.e. CSS Validator, Yahoo toolbar, etc...)

I can't say I've ever used OSX for more than a minute, but I do know that it is Unix based, and possibly even Debian based (anyone wanna clarify that?) If the previous two statements are true, the only* thing distinguishing OSX and Ubuntu is the GUI environment.

*only = Assuming there are no kernel modifications. Which Im sure there are thousands.

As far as that hardware configuration? Sounds great. Be sure you install the 64-bit build of whatever version you wish to install so you can use your computer to its fullest capacity (Im assuming that AMD x2 4000+ is a 64bit, right?) 2 gigs of ram is more than enough, and the hard drive space... Plenty.

Sounds like all you need to do is build the box, install Linux, slap some [stickers]("http://www.ubuntu.com/products/merchandise") on the side of it, plug it in, and enjoy.

---

### Post by PhatKat on 2008-03-27
Ok that was a thorough answer and thanks! Now before i build that Ubuntu box:

1) If, l partition a small HDD space off for Ubuntu OS how big would you say is adviseable for the fastest start up time?

2) So i could install Samba via windows and when i use the live Ubuntu cd i could run it? Not too clear here..

3) Hmm can i test drive Konquerer on windows by any chance- sounds interesting!

4)For linux/Ubuntu applications: how far are they optimised for dual/quad core processors compared to Windows?

5) Maybe a silly question: so u guys surf the net on Ubuntu w/o an antivirus, anti spy/adware or software firewall (if not behind a router) ??

---

### Post by insineratehymn on 2008-03-27
I like thorough answers. :)

1) [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements) That is the minimum system requirements. It says that 4 gigs of HD space should be enough to allow for installation, system running, and swap.

2) Samba does not need to be installed on your windows machine. It is a service that runs on your linux box that will allow your windows machines to actually see and share files with your Ubuntu machine. Don't worry, your linux box will see your windows boxs just fine, however it will not be retrospective without Samba.

3) [http://www.nomachine.com/download.php](http://www.nomachine.com/download.php) That link takes you to a piece of software called NoMachine. It allows you to run Konqueror on windows. I have not tested or even heard of that application, but that is what it says it does.

4) As far as optimization... I know that the whole processor access is done at the Kernel level. I know that Ubuntu does have kernels optimized for Dual-core/64-bit processors. So... Sure?

5) Of course some users are going to have some kind of anti-virus. I use avast to check all of my downloads. Spyware? Don't use one. Software firewalls are included in the settings of Ubuntu. As far as viruses... You only really need to worry about them if you have windows machines actually on your network and you transfer files between them.

Elaboration on open-source viruses:
There aren't that many viruses for linux to begin with.

*"There are about 60,000 viruses known for Windows, 40 or so for the Macintosh, about 5 for commercial Unix versions, and perhaps 40 for Linux. Most of the Windows viruses are not important, but many hundreds have caused widespread damage. Two or three of the Macintosh viruses were widespread enough to be of importance. None of the Unix or Linux viruses became widespread - most were confined to the laboratory."*
Source: [http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

In 2005, there were less than a thousand total viruses for linux.

*The number of viruses specifically written for Linux has been on the increase in recent years and more than doubled during 2005 from 422 to 863*
Source: [http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

Even if there isn't many, you should still protect your own data.

*In my opinion, the most valuable resource is your data. Hence, it need to be protected as well. Indeed, I always lock the door before I leave my house.*
Source: [http://vntutor.blogspot.com/2008/02/do-we-need-anti-virus-for-ubuntu.html](http://vntutor.blogspot.com/2008/02/do-we-need-anti-virus-for-ubuntu.html)

---

