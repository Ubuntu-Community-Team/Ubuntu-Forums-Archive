---
title: "nube"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by rockinroll on 2010-03-20
linux has always been a nightmare and it wont change till its user friendly. most people aren't interested in learning Klingon just to connect to the internet. i have been around it, i've installed it and wiped the drive shortly thereafter. i assume it has not changed much over the years because ppl don't want it to. maybe they like walking to the beat of a different drum or something. idk but i hope to get this thing running so i can make it into a ras server or something useful other wise i scrap it again.  anyways if anyone has a dell demesion 2350 and can possibly walk me though connecting to the internet that would be wonderful. apparently just doing the install does not set any of that up for you also my resolution is so low i cant see the buttons so its a blast.

---

### Post by Ozymandias_117 on 2010-03-20
System -> Preferences -> Display should let you change your resolution.

Need more information about your network... Wired or wireless? Do you have DHCP or does it need to be manually configured?

---

### Post by rockinroll on 2010-03-20
nothing in drop down menu for resolution just 640x480 as for the other i did if config and got and error message  error fetching info device not found

---

### Post by synicalx on 2010-03-20
Install some drivers for your GPU, seems to fix most resolution problems.

---

### Post by Ozymandias_117 on 2010-03-20
> **synicalx said:**
> Install some drivers for your GPU, seems to fix most resolution problems.

For most GPUs you can do this by going to System -> Administration -> Hardware Drivers

---

### Post by 3rdalbum on 2010-03-20
You're going to have to give us some information about HOW you are connected to the internet. 

If you connect your computer to your ADSL/cable router via an Ethernet cable, your computer should automatically connect to the router. If it's connected via a USB cable, then forget it - hook up via Ethernet.

Linux is more user-friendly than Windows. But it's very, very different to Windows, and as with any operating system you may need to choose your computer hardware carefully to avoid hardware compatibility issues.

---

### Post by egalvan on 2010-03-20
Personally, I find that Linux is Not Windows. ;)

I had as much trouble learning Klingon as I did learning Microsofteese.
The difference is that I *remember* the time and trouble I spent to learn Microsofteeese (for example... press "start" to "stop" :confused:)... which most all MS-users seem to quickly forget... :(
they like to pretend that humans are born with Windows-on-the-Brain.  :p

To further muddy the waters, most of 90% of MS users have never installed Windows in their lives...
it's quite a revelation to watch someone do their first XP install...
and quite a riot to have them try to install Windows 3.x or DOS. (not that I would recommend *anyone* use those systems)


Just One Example (does not a movement make)

Using a Genuine Dell Windows XP Install CD, on a Genuine Dell Computer (Optiplex 270), I found that
the video was limited to 800x400,
the audio was DOA
the network (wired LAN) was DOA
the modem was DOA
(further hardware "issues" that I cannot recall, sorry)

no network, so no connection to download the missing drivers...
(used another machine to finish)

So I installed Hardy... everything worked, video maxed at 1280x1024, sound, network, modem...

same for Intrepid, 
same for Jaunty
same for Puppy
same for PartedMagic LiveCD
same for Knoppix
same for TinyCore
same for Mandriva

Your Mileage Will Vary.


P.S.
Set two Ferengi down in front of a Windows 7 machine and a Lucid machine, and see which is the "winner" :lolflag:

---

### Post by HermanAB on 2010-03-20
Hmm, some people just like to complain I guess.

There are various Linux distributions and there should be one for every taste and need.  If you want a super easy to use Linux suitable for your Grandma or grandchild, then use Puppy Linux.  If you want something like Windows with wizards for everything, where you can go click crazy, use Suse or Mandriva. If you want something intermediate between Mandriva and Slackware, then use Ubuntu.

..and for heaven's sake, please use [http://google.com/linux](http://google.com/linux) to resolve basic problems.

---

### Post by andrew.46 on 2010-03-22
Hmmm..... it is actually *n00b*, not* nube* :).

Andrew

---

### Post by readycarpenter on 2010-03-22
> Using a Genuine Dell Windows XP Install CD, on a Genuine Dell Computer (Optiplex 270), I found that
the video was limited to 800x400,
the audio was DOA
the network (wired LAN) was DOA
the modem was DOA
(further hardware "issues" that I cannot recall, sorry)

no network, so no connection to download the missing drivers...
(used another machine to finish)


I just worked on the same model dell, and same thing, trying to narrow the problem I've found most everything dead, I think dell puts a time bomb inside, so they just expire after 2 or 4 years

---

### Post by rockinroll on 2010-03-22
ok well i took one of the comedians suggestion and made a mandriva from their web site unfortunately it doesn't boot.   for those who asked i have a dell dimension 2350 it has 512 megs of ram 200 gb hd i connect to the internet with Ethernet.  im looking for a linux boot disk. also is there a way of deleting smart *** responses?

---

### Post by linuxman94 on 2010-03-22
> **rockinroll said:**
> ok well i took one of the comedians suggestion and made a mandriva from their web site unfortunately it doesn't boot.

He didn't suggest you use it, he just was listing options.

---

### Post by Calash on 2010-03-22
> **rockinroll said:**
> ok well i took one of the comedians suggestion and made a mandriva from their web site unfortunately it doesn't boot.   for those who asked i have a dell dimension 2350 it has 512 megs of ram 200 gb hd i connect to the internet with Ethernet.  im looking for a linux boot disk. also is there a way of deleting smart *** responses?

I believe you can go back and edit your own smart *** posts, that would be a good first step.

Need a bit more about your connection mto the internet. I assume you have had a modem of some kind.  Do you have a router in-between the modem and the computer?  It can be ether way, so knowing will make a difference as to what you will need to do for the networking to work.

---

### Post by rockinroll on 2010-03-22
ok i got ubuntu installed and i think it installed the nic card when i click on network it shows a windows netowrk and if i click it it says unable to mount location. firefox doest work either so idk where to go now. the display is g2g.  im going to tool around and see if i can figure out the network issue.

---

### Post by Rex Bouwense on 2010-03-22
I think you ought to tone down your comments a little.  Remember the people who answer your and other people's posts are all volunteers.  There is no pay and the only thing that they get out of it is the satisfaction that they have assisted someone or taught someone a little about linux.
Show a little respect and sure enough you'll get it right back.  You are not the only one with a Dell that cannot connect to the internet.  As a matter of fact, I got one sitting under the bed waiting until I get around to working on it.

---

### Post by TBABill on 2010-03-22
rockinroll, I am unsure which wireless adapter you have (post the output of lspci typed into the terminal so we know what you are working with). Some adapters require use of a proprietary driver, which is why they do not natively install in most Linux distros. But, you are able to download them after install, assuming you can get to the net via hardwire to your router.

If you can post the output here you will get a great deal of assistance getting it running. However, if you just want an easier distribution to use than Ubuntu, try Linux Mint 8. It's based on Ubuntu 9.10 and takes care of many things you will likely need to configure once you get Ubuntu installed (like installing Java, Flash, codecs and other items). It is much easier for a new user and removes some of those initial aggravations.

The key to Ubuntu for me was to first get it installed, then to get online and let the system update. It then prompted me to install the drivers for my hardware (for me it was my nVidia video card on one laptop, now a Broadcom wireless adapter on another). Once you go through those steps your system will likely be operational to the point that you are online and ready to use it.

Although SUSE and Mandriva are easy to use, Mint seems even easier. And being based on Ubuntu you can still come here for general assistance because they function very similarly under the hood. 

Good luck and welcome to Ubuntu. I think you get some of the comments you received when you pose the question more as a complaint, or lead off with the frustration rather than a willingness to get to the answer through learning. Just food for thought to make it easier to adapt to the Ubuntu community. So many great people here with a tremendous amount of knowledge help me all the time and it did take some adjustment at first. 

If you still need help, just post. You can search the forums for people who have had similar experiences or problems as you, and you can even search for your specific model number. It is highly likely others before you faced those same challenges and had to figure out the method needed to resolve the conflict. It's not difficult, but it is different enough that you do have to face a learning curve to adapt.

---

### Post by rockinroll on 2010-03-22
i dont know if everyone is seeing this or just parts of the messages or what. so let me try this again i have a dell dimension 2350.  with a 200 gb hd and 512 mb ram.  im gettin instructions that i just dont understand.  not only from ppl but from the help menu in ubuntu also.  it may say something like click here here and here and when i follow that its not there or its named differently.  i typed ifconfig eth0 and got link encap ethernet inet6 addr fe80::208::74ff febd 638/64 i cannot ping anything and cannot see the linux box from my windows machines.  they are all networked with a linksys router and a dsl connection
when i look at teh network tools it says im receiving packets0 error and 0 collisions

   [FONT=&quot]rob@rob-testbox:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

 [/FONT]

---

### Post by egalvan on 2010-03-23
> **rockinroll said:**
> ok well i took one of the **comedians** suggestion and made a mandriva from their web site unfortunately it doesn't boot.

Checked the posts, and herman seems to be the only one who mentioned Mandriva...

Buddy, herman's written more about the inner workings of Linux than you'll ever have time to forget.
His help on this forum is invaluable.
His website has hundreds of pages of Linux Knowledge.

>  a **dell dimension 2350 **it has 512 megs of ram 200 gb hd i connect to the internet with Ethernet.  im looking for a linux boot disk.
Those model of Dell are trivial to use  with Linux...
Definitely sounds like a Db_BKB error in this case.
Especially since you could not get that Mandriva CD to boot.
As for a Linux boot disk, there are some 800 different ones on the 'net. Pick your poison.
But do beware that Db_BKB error, it can take some work on your part to eradicate.


>  also is there a way of deleting smart *** responses?

No, you can only edit out your smart *** parts, you cannot delete them.


This link may be of help with that Db_BKD error you seem to have...
Eric Steven Raymond is a great writer, and can explain very well...

[http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html)

---

