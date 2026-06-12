---
title: "Vista doesn't' Boot"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by locucho on 2010-06-19
Hi friends, I came here to ask once for a problem with Ubuntu 9.04; it was resolved. Now, I come for another problem, with a notebook, and I need a solution ):P (pleeeease)

(Excuse me for my horrible english, I really don't speak very well, I speak spanish because I'm from Argentina)

Well, I have Windows XP in a 500Gb HD (SATA). My Pc is a AMD Athlon64 X2 (Dual Core) 5200+ 2.7Ghz (x2); Mother ASUS M2N-VM HDMI and a VIdeo ATI PowerColor HD 4650 (1Gb); and 4Gb RAM. The idea was to clean an old 80Gb HD (IDE), so I start to use my brother's notebook to do that with a case.

My brother's notebook is a Dell XPS 1640, T9600 (2.80GHZ) Core 2Duo; don't know the Mother, I think is Intel ;Graphics ATI Mobility Radeon M96XT (1Gb) ;4Gb (DDR3,1067 MHZ 2 Dimm) RAM; 500Gb HD (7200rpm M1640), WIN VISTA SP1 HOME PREM64.

My idea was to connect the 80GbHD (IDE) into a carry disk case and working with USB 2.0 like an external disk, in the Dell notebook (I didn't do it with my PC because the Usb has some problems and it often disconnects), format that external drive and install there Ubuntu 10.04 (32bit, I readed it's recommended), so then I can plug it into my CPU (The Athlon64 and Asus one) and work with my original XP drive (500Gb) and another with Ubuntu (80Gb). 

The problem is that I change boot order in the notebook, was:
1. Hard Drive
2. USB Storage (here I was the 80gb drive, like external device)
3. CD/DVD
4. Removable Devices
5. Network

I change for:
1. CD/DVD
2. USB Storage
3. Hard Drive
...

I boot from the Ubuntu 10.04 Live CD, I set "Install Ubuntu 10.04" and I select the 80Gb External Drive to do it there. Setup formatted that external device and installed there Ubuntu 10.04, like I was thinking to do. When it finished, I took Ubuntu CD and I reboot from the new system, in 80Gb external HD; but it didn't start, and stayed on a black screen like a empty Terminal. 

So, I disconnected the external device (the usb) and I reboot and changed again the boot order to the original: 
1. HD
2. USB storage
3. CD/DVD
...
 
I was expecting to see WIN Vista starting (for the original 500gb HD of the notebook), but it didn't work, because it appeared a black screen, a Terminal, with the text: 

[B]error: no such device: b842ab47-2fc0-4708-9ed4-aab6e8c318aa.
grub rescue>[/B]

I have searched about "grub" on google and here, and I see these possible solutions for recovery the Vista Boot:

1. [http://www.uluga.ubuntuforums.org/showthread.php?t=1450189&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=1450189&page=2) Do what they said there with the **Vista CD**, or try with the **Ubuntu Live CD** to do what there said on Terminal. 
2. Do this: [http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)
3. Use (like said here in spanish another user: [http://www.configurarequipos.com/foro-ayuda/2688084/48/0/error-no-such-device-al-iniciar-ordenador.html](http://www.configurarequipos.com/foro-ayuda/2688084/48/0/error-no-such-device-al-iniciar-ordenador.html)) the **Super Grub Disk**.

I really don't understand so much of Ubuntu, because I am "Absolutly Begginer", and then I will try to understand what happened with the 80Gb HD that didn't work with that installation. But also I dind't understand the diference of "Grub" and "Grub2" and I really don't understand WTF is "Grub" :lolflag: so, I need help to recover my brother's Dell notebook with his Win Vista and all his files, or he will kill me (he doesn't know it yet).

Thanks you very much, and help me!

Franco, or "Locucho".

---

### Post by garvinrick4 on 2010-06-19
This was copied from earlier post in Ubuntu forums
and will get you Vista boot loader back





Vista and 7 fix boot 
How to restore the Windows install grub / Vista or 7 bootloader To restore the Windows install grub bootloader, you must first boot off your Windows install grub Vista/7 installation DVD. If you have one of the many OEM computers that didnt come with a Vista/7 installation disk, you can get the same effect with a Vista recovery disk, which you can download for Vista or Win 7. When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer." On the next page, if it finds your Windows install grub Vista/7 installation, make sure it is UNSELECTED before clicking next. Then click on "Command prompt". From there, type in the following: 

Code: bootrec.exe /fixboot 

Code: bootrec.exe /fixmbr 

and click "Restart."

---

### Post by locucho on 2010-06-19
Oh yeah! :guitar:

I love you, yo're a genius. 

Now I have to know why Ubuntu 10.04 32bit didn't work in the external device, because when I tried to boot from there, it showed me a black screen like a Terminal, and nothing more. 

I have these theories:

1. I have installed 32bit version (wrong?) and I have to install 64bit; but I don't understand, so, how did work the Live CD there.

2. Incompatibilities with the Dell notebook? How did it work with the Live CD?

3. Ubuntu doesn't work in a external device working by USB? or that version is incompatible with IDE system?

I really don't know. Please help me with that. Thanks!

---

### Post by spiky001 on 2010-06-19
I think that there was no problem with the 32bit but 64bit makes better use of your system,
It will work on 2nd drive but I think you had a grub problem which needed to be sorted, when you loaded it up on laptop then put it as 2nd drive grub did'nt know what it was doing

---

### Post by garvinrick4 on 2010-06-19
When you installed Ubuntu on the USB drive did you on last page of install hit the advanced tab in lower right hand corner and put the grub in sdb.  Not sda or sdb1 or sda5 or anything else just sdb when installing to HDD which is sda you install grub to sda.
 When through installing Ubuntu take CD out boot into ubuntu and run in terminal.
```
sudo update-grub
```There is a section just for Dells. Dell has there own drivers and a recovery partition that they use
that is a little different than the norm. And there are a lot of users in these forums with plenty of knowledge
in Linux use.
 Do you still have the Ubuntu install on the USB drive?

---

### Post by locucho on 2010-06-19
I understand, so, to sort that perhaps I have to plug the 80GB IDE HD on my CPU (The AMD64 and Asus one) and connect it like a normal drive, and try to solve the problem of the Ubuntu grub on that disk, booting from there, like a normal primary device?

I'm scared by It can happend the same thing that happend on the Dell notebook (Vista OS), but on the Asus/AMD PC (XP OS), and there is not a recovery disk for repair the grub thing for that, or may be I can do it from the Ubuntu Live CD; but I want to take careful of the 500Gb HD with XP OS, and to avoid this problem again.

edit: sorry, I din't read that answer, garvinrick4. I already have the Ubuntu on that USB drive, but it doesn't boot, so I cant do nothing on Terminal. But if I reinstall, I can do this that you say: "When you installed Ubuntu on the USB drive did you on last page of install hit the advanced tab in lower right hand corner and put the grub in sdb. Not sda or sdb1 or sda5 or anything else just sdb when installing to HDD which is sda you install grub to sda.", if you explain me very slowly because I don't understand =?

I don't know what is sda, sdb, sdb1, etc.

---

### Post by spiky001 on 2010-06-19
Have a read through here
[http://ubuntuforums.org/showthread.php?t=1487211](http://ubuntuforums.org/showthread.php?t=1487211)

it has been done before

---

### Post by garvinrick4 on 2010-06-19
> **locucho said:**
> I understand, so, to sort that perhaps I have to plug the 80GB IDE HD on my CPU (The AMD64 and Asus one) and connect it like a normal drive, and try to solve the problem of the Ubuntu grub on that disk, booting from there, like a normal primary device?

I'm scared by It can happend the same thing that happend on the Dell notebook (Vista OS), but on the Asus/AMD PC (XP OS), and there is not a recovery disk for repair the grub thing for that, or may be I can do it from the Ubuntu Live CD; but I want to take careful of the 500Gb HD with XP OS, and to avoid this problem again.

edit: sorry, I din't read that answer, garvinrick4. I already have the Ubuntu on that USB drive, but it doesn't boot, so I cant do nothing on Terminal. But if I reinstall, I can do this that you say: "When you installed Ubuntu on the USB drive did you on last page of install hit the advanced tab in lower right hand corner and put the grub in sdb. Not sda or sdb1 or sda5 or anything else just sdb when installing to HDD which is sda you install grub to sda.", if you explain me very slowly because I don't understand =?

I don't know what is sda, sdb, sdb1, etc.
You know how Windows gives your drives letters like C: drive  and then D: for recovery and maybe J: drive for external. Well Linux names them sda for internal and sdb for external and sdc for next drive.  
And then inside of sda drive you have partitions called sda1, sda2 sda3 and so on.
sdb has same thing with partitions and so on down the line.
 Linux will see your Windows install as one of those partitions like sda1 or sda2 and so on.

---

### Post by garvinrick4 on 2010-06-19
If you want to use the USB drive with Ubuntu 10.04 installed there are plenty of people
in these forums that can help you get it to boot with a couple of commands. I will be on line
in about 3 hours or so after the United States Open Golf tournament and well check this thread.
 Also I do not know how to install a Windows boot manager without the XP or Vista or 7 recovery disk. Some know how to do it with Ubuntu disk I here but I do not. But I can install grub2 to make Linux boot. You will find a lot of users do. Good luck and have a nice day. Am glad you got your Vista going I could tell you were freaking incase your brother came in and his computer was on the fritz.

---

### Post by locucho on 2010-06-19
Loool! Well, Vista works, now I am connected into Ubuntu, because I just did it, and it works perfect on the external device.

Now, I must know why nothing happends when I write "sudo update-grub" on Terminal. If I don't do this, I think I can start the PC from one or the other disk (so, one of the other Operating System) changing boot options always I need, or may be not, because I din't do this part of installation (what you said about sdb on the last part of installation) with the PC, I did it with the Dell notebook. That means that I can use the external device with Ubuntu on notebook but I can't do that on the PC until I do the same process about Sdb on the installation?

Thanks a lot, you're helping to introduce in Ubuntu to a young argentinian boy on the other side of the globe, or at least on the other side of the continent. I love internet.

Locucho

edit: I said nothing, it works! now, I will try to use the external device with Ubuntu 10.04 with my PC with Win XP, so I'll see if this works everywhere or only on the Dell notebook after this process. Thanks a lot again!

---

