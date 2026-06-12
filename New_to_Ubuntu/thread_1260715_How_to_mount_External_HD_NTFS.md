---
title: "How to mount External HD NTFS"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by locucho on 2009-09-07
Hi! I'm new in Linux and Ubuntu, and I really start to try Ubuntu because I had a serious problem with the Windows Registry. I have Windows XP in a HD with 320Gb. My Pc is a AMD Athlon64 X2 (Dual Core) 5200+ 2.7Ghz (x2); Mother ASUS M2N-VM HDMI and a VIdeo ATI PowerColor HD 4650 (1Gb); and 4Gb RAM.

(Excuse me for my horrible english, I really don't speak very well, I speak spanish because I'm from Argentina)

The problem is this: My computer start to work slowly with XP, and when I reboot, It start with Windows, and in the Desktop reboot automatically, few seconds later. So, I put "not to reboot when there is an error" and it show me the famous blue screen with the explanation of the problem, talking about the Registry Error. So, my brother try to reinstall Windows XP but when he starts I tell him to stop, because the reinstallation don't format the Hard Drive but delete the Desktop and "My Documents" and all our important information, ando the music, and the movies where there, like 200 Gb or more. So, he try to cancel de process (because he put the CD of Windows and boot from there) and he couldn't, so we take the CD and reboot whit the button of the Computer Case. Now, when the computer boot from the Hard Drive, the installation files of Windows XP are there, so it try to restart the installation and ask for the XP CD. 

When that happend, I think in all the information that I want to save, and I think in the Live CD of Ubuntu, because I didn't want to take de HD and read it like an External HD in an other computer and start to save all that in a lot of DVDs; and I try to start the Computer with the Live CD of Ubuntu 9.04. When I did that, I connect an other HD in a Case with USB 2.0 and I start to copy some files from my 320Gb HD to the other (160Gb, external). 

Until that, all was perfect. But when I copied about 250Mbs (nothing) it starts to give me and error (all in the Live Session User) about an invalid file once and once again. I cancel the process and I reboot the computer, without disconect the External HD. When I start the new Live Session (always in the Live CD) and I try to open the External HD, because I had in the Menu "Places" the icon with the picture of USB HD. But there it shows me an error:

[I]**It's not possible to mount the device (No se puede montar el volúmen).**

Details (Detalles): 
**$MTFMirr does not match $MTF (record 0) . Failed to mount '/dev/sdb1': Error de entrada/salida NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows twice**. The usage of the /f parameter is very important! If the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more details.

[/I]I search with Google and a lot of people had some similar problems (like [here]("http://74.125.113.132/search?q=cache:qWIUI52EoF8J:www.ubuntu-es.org/%3Fq%3Dnode/97516+ubuntu+9.04+no+monta+disco+externo&cd=2&hl=es&ct=clnk&gl=ar")) but nothing had the solution. Somebody said me to take the HD and conect it in a XP computer to put "Hardware Safely Remove" and may be take off the lock in the port of the HD that doesn't allow me to mount the HD. I did that and nothing happends, now always give me that error. 

I try to do such of things in the Terminal but I don't understand anything of the comands and lines, so, I really don't know what I really do. I know that I try to install and config NTFS-3g and then I install ntfs-config also; but it didn't change nothing, and being the Live Session, if I reboot again, all of these is gone and I start in zero again (like now in some minutes).

So, I need help to learn how to fix this problem and how to mount the HD (don't thing in change the USB because I try in every ports) and to write OK there, so I can do the backup of important things and format all to put Ubuntu and throw to the trash XP. 

Remember that the External (and the other too) HD is NTFS system, and that I do everything in a Live Session with the Live CD of Ubuntu 9.04. It have to be a way to mount again the HD and make the backup!

Thanks you very much, and help me!

Franco, or "Locucho".

---

### Post by Stebalien on 2009-09-08
Do you have important data on the external hard drive? If not, you can try to reformat it. I would recommend that you try using a different file system because, as far as I know, NTFS is not very reliable in linux. Otherwise, I have no idea of how to fix your external hard drive problem. The errors about bad files when transferring data from the local to the external hard drive could be due to a dying local hard drive. A dying local hard drive would also explain the registry problems.

---

### Post by oboedad55 on 2009-09-08
Pardon my English, I'm American... Okay, joke. Are you trying to recover data from an ntfs partition? You shouldn't need to install anything extra to read the disk. I can read my Windows partitions from Ubuntu with nothing extra installed. The errors you're getting sound like either a hardware failure or your ntfs drive is hosed. I've seen a lot of posts where people have recovered data using Testdisk, which you can download here: 
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk). I've seen a number of success stories with ntfs drives and this bootable CD. If I've misunderstood you please post back and correct me.
Edit: I just looked at Testdisk and it looks like you need to download either the Linux or Windows version and then run it from the OS. I thought it was a bootable CD.
--Jon

---

### Post by egalvan on 2009-09-08
> **Stebalien said:**
> Do you have important data on the external hard drive? If not, you can try to reformat it

Yes the OP has "important information", so a format is not want he needs...

> **locucho said:**
> and all our important information, ando the music, and the movies where there, like 200 Gb or more.



> **Stebalien said:**
> . I would recommend that you try using a different file system because,
** as far as I know, NTFS is not very reliable in linux.** 

NTFS is, and has been, reliable in Linux more than three years now.

---

### Post by Stebalien on 2009-09-08
I know that he has important information on the internal hard drive but I am asking about the external hard drive. One of his problems is that the external hard drive will not mount.

---

### Post by locucho on 2009-09-08
@ oboedad55: May be you're right and I have a hardware failure in the external HD, may be there TestDisk it' the solution, but if the HD is wrong, why I can read and write there with Windows Vista, in my father's Computer? I think the problem ins with Ubuntu and the configuration in NTFS.

@ Stebalien and egalvan: Yes, I have important information in the external HD too, because is from my father, and he use it to work. May be I have to buy another HD and format in FAT32. That's the better file system for Ubuntu? If i do that, can a read and write in the FAT32 HD with Ubuntu and with Windows XP?

---

### Post by oboedad55 on 2009-09-08
> **locucho said:**
> @ oboedad55: May be you're right and I have a hardware failure in the external HD, may be there TestDisk it' the solution, but if the HD is wrong, why I can read and write there with Windows Vista, in my father's Computer? I think the problem ins with Ubuntu and the configuration in NTFS.

@ Stebalien and egalvan: Yes, I have important information in the external HD too, because is from my father, and he use it to work. May be I have to buy another HD and format in FAT32. That's the better file system for Ubuntu? If i do that, can a read and write in the FAT32 HD with Ubuntu and with Windows XP?

Yes, you can read/write FAT32 with Linux. I'm still wondering why you can't access the NTFS in Ubuntu.

---

### Post by locucho on 2009-09-08
Yes, I can't understand, but perhaps the problem is the Live Session, I don't know, may be it's a problem in my USB ports (?) but there always work OK. Well, if somebody knows the answer, tell me!! Meantime I'm thinking in buy another HD. Do you recommend a 500Gb HD? A 1Tb HD? Or 320Gb it's okay? Do you recommend to make partitions there?

Thanks!

---

