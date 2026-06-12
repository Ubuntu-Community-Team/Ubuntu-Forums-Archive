---
title: "Some questions about Xubuntu"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by GSI on 2009-11-15
Hello.I'm planning to install Xubuntu 9.04 onto an old machine and I have some questions :) 

1.The PC is old and the audo card is on ISA slot.Does Xubuntu support ISA slots?
2.Will 192mb ram and 400mb swap be enough for Xubuntu?
3.Does Xubuntu has Automatic codec and drivers dowlnoad or I will have to search for drivers manualy?

Thanks in advance ! :)

---

### Post by Paqman on 2009-11-15
> **GSI said:**
> 
1.The PC is old and the audo card is on ISA slot.Does Xubuntu support ISA slots?


Good question, I have no idea.
> 
2.Will 192mb ram and 400mb swap be enough for Xubuntu?

Only just. That's a pretty slow machine, how much fun it will be to use is up to how patient you are.

One option you could try if Xubuntu is not good: there's an even lighter (unoffical) version of Ubuntu called Crunchbang Linux

> 
3.Does Xubuntu has Automatic codec and drivers dowlnoad or I will have to search for drivers manualy?


Xubuntu will take care of this for you. Or you can force it to download and install all the codecs by installing the package xubuntu-restricted-extras from the package manager.

---

### Post by GSI on 2009-11-15
This PC is like my experimental PC :D I just try out different OS it had 98SE and now has XP and I wanna try Xubuntu or any older version of ubuntu :)

---

### Post by zeroseven0183 on 2009-11-15
I agree with Paqman, you should try [Crunchbang Linux]("http://crunchbanglinux.org/").

---

### Post by Paqman on 2009-11-15
Well, if you're just playing around, another excellent option is building your own custom lightweight version of Ubuntu. It's actually surprisingly easy, as Linux is so modular.

[Ubuntu Minimal Howto]("http://andyduffell.com/techblog/?p=361")

---

### Post by GSI on 2009-11-15
Thanks for the answers guys! I'm half way through the installation of Xubuntu now.I'll report here when its installed and how it runs :)

---

### Post by GSI on 2009-11-15
Alright,I got the system installed and the speed is better than I expected.But I dont have sound :(

---

### Post by halitech on 2009-11-15
Glad to hear you are pleased with the speed :)

is the system a homebuilt or a storemade like dell,hp, etc?

Open a terminal and run lspci (lowercase L) and post the results here

---

### Post by GSI on 2009-11-15
I dont  know is the system home made or not but on the case it says 'Debis systemhaus'

---

### Post by GSI on 2009-11-15
Heres the output : 

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:13.0 Mass storage controller: HighPoint Technologies, Inc. HPT366/368/370/370A/372/372N (rev 01)
00:13.1 Mass storage controller: HighPoint Technologies, Inc. HPT366/368/370/370A/372/372N (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

---

### Post by Paqman on 2009-11-15
Just a quick question: have you checked that sound isn't muted? Some people have reported that their sound was on mute after installing Karmic.

---

### Post by GSI on 2009-11-15
No,its not muted.When I click the speaker icon on the top left corner of the screen it says : 

GStreamer was unable to detect any sound devices. Some sound system specific GStreamer packages may be missing. It may also be a permissions problem.

---

### Post by GSI on 2009-11-15
I will try installing Ubuntu 5.10.Its older so it must support ISA slot audio cards and it has less system requirements.

---

### Post by XubuRoxMySox on 2009-11-15
> **GSI said:**
> I will try installing Ubuntu 5.10.Its older so it must support ISA slot audio cards and it has less system requirements.

[SIZE="6"][COLOR="Red"]Yikes!![/COLOR][/SIZE] Why install something that is completely unsupported?? 

I would really have a look at [Puppy Linux]("http://puppylinux.org") or even [Simply Mepis]("http://mepis.org") would run reliably on that hardware despite the KDE desktop.

But I would not advise a newcomer to Linux to use an ancient version that reached the end of its life years ago. Just say'n.

-Robin

---

### Post by Paqman on 2009-11-15
> **GSI said:**
> I will try installing Ubuntu 5.10.

That version is no longer receiving security updates. I wouldn't install it on a machine that's connected to the internet.

---

### Post by GSI on 2009-11-15
Alright than ill try puppy linux

---

### Post by kio_http on 2009-11-15
Use the alternate cd of karmic. If it doesn't work then use puppy linux.

---

### Post by GSI on 2009-11-15
Alternate CD?

---

### Post by halitech on 2009-11-15
I'm not even seeing the sound card listed. I see 2 options at this point. 1. go with pupply or DSL as they use older kernels and should hopefully pick up your ISA sound card. 2. Pick up a cheap PCI sound card and install that and it should work.

---

### Post by GSI on 2009-11-15
> **zeroseven0183 said:**
> I agree with Paqman, you should try [Crunchbang Linux]("http://crunchbanglinux.org/").


I will try this distribution now...

---

### Post by GSI on 2009-11-16
Maybie I should try an older version of ubuntu that still gets updates?

Any suggestions?

---

### Post by halitech on 2009-11-16
8.04 would be the oldest that is still getting updates at this time as it is a LTS version.

---

### Post by GSI on 2009-11-16
But 8.04 requires 256 RAM :( I only have 196...


P.S : Maybie if i try the latest version? It's smaller...

What is the chance to run the ISA card on the latest version?

---

### Post by halitech on 2009-11-16
I've used the minimal install and built up from scratch on machines with only 128meg of ram so it can be done. The live cds require more but you can do it.

Another option would be to install debian and build up from scratch following the instructions here: [http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

---

### Post by GSI on 2009-11-16
Yes i may try this but I'll need both PC's runing at the same time

P.S : Later ill try the latest ubuntu first... If it dosent work ill start building up from scratch :)

---

### Post by GSI on 2009-11-16
The Ubuntu 9.10 option didn't worked :( The PC is too slow.Ill try the minimal install and build up :)

---

### Post by GSI on 2009-11-17
Alright so I installed DebianGNU/Linux 5.0.3 and the system is running great! And I do have sound but only on the left channel....


Any suggestions how to fix the sound problem?

---

### Post by halitech on 2009-11-17
you will probably be directed to the debian forum but something to check is alsamixer to make sure nothing is muted.

---

### Post by GSI on 2009-11-17
Nothing is muted.I had the same problem when I installed Windows XP on this PC

---

### Post by RabbitWho on 2009-11-17
I know this is a little late but: You could try Spri, it's based on Ubuntu and uses Icewrm instead of gnome or any of the others... it's still in Beta though, I have the Alpha on a computer at home with 192 of ram and it works perfectly, very fast, I didn't have any problems. 
Read the forums on the website to get an idea what it's like and what issues people have had with it. 
Also if you can wait another version of it will be released soon enough, as soon as Jaxx has a computer and can work on it! 


[http://www.sprilinux.com/](http://www.sprilinux.com/)


Anyway I don't know why your sound isn't working!

---

### Post by GSI on 2009-11-17
Well I may try this out if I don't get my sound working.Thanks for the tip! : )

---

### Post by halitech on 2009-11-17
> **GSI said:**
> Nothing is muted.I had the same problem when I installed Windows XP on this PC

If you had the same issue with Windows then either its something wrong with the speakers (damaged wire maybe?) or the sound card itself.

---

### Post by GSI on 2009-11-17
I use the same speakers and amplifier on both PC's and the sound card was working excelent under windows 98SE

---

### Post by halitech on 2009-11-17
with it being an ISA sound card it may not have full functionality so I'm not sure where to direct you now. Anytime I've restored systems that had an ISA sound card I found it was easier to toss it out and put a PCI card in.

---

### Post by GSI on 2009-11-17
I know that it's easier just to throw it out but im just playing around with this PC. : )

---

