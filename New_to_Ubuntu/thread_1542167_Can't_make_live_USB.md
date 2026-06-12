---
title: "Can't make live USB"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by aidenscool09 on 2010-07-30
I'm having a problem with the live usb creation program installed by default in GNOME. It isn't opening any iso I throw at it. I was originally trying to make a Windows XP USB as my cd drive doesn't work well with live cds (it loads them but gives errors). Then i tried opening a Ubuntu 10.04 iso and then Tiny Core Linux, then Damn Small Linux and then Windows Fundamentals for Legacy PCs. It's really getting on my nerves as well so any help is appreciated.

---

### Post by ronnielsen1 on 2010-07-30
I think the one installed is just for ubuntu. I could be wrong

Try Unetbootin
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by aidenscool09 on 2010-07-30
Well as i said, i used an Ubuntu 10.04 iso and that didn't work either. But yes, I'll give that a look.

---

### Post by aidenscool09 on 2010-07-30
But the Ubuntu 10.04 iso might not work because I'm using Ubuntu 9.10, but i really doubt that should make a difference. And i did put this ABT even though i'm relatively experienced with Ubuntu but it might be able to help alot of newbies.

---

### Post by beew on 2010-07-30
The usb creation program that comes bundled with Ubuntu only creates live usb for Ubuntu versions. You can download unetbootin from the repository to create live usb for other Linux distros but there is no persistence feature (There are rumours that you can create a bootable usb for Windows 7 with unetbootin but it seems that the claim originated from one guy and everyone cites him but most of the people who have tried and posted on his blog reported that it didn't work. I would be very surprised if it did!). 

To create a bootable usb for windows xp you have to use a windows utility called BartPE.  I have never done it so I can't tell you if it works. I can be wrong but it seems that it only works for very particular hardware configurations.

---

### Post by aidenscool09 on 2010-07-30
Oh, UNetbotin looks exactly like FUSBi

---

### Post by tarps87 on 2010-07-30
> **ronnielsen1 said:**
> I think the one installed is just for ubuntu. I could be wrong

Try Unetbootin
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

+1

It hasn't failed me, however I have never tried to create a xp boot USB and I am unaware of any support for it. Still no harm in trying :)

---

### Post by aidenscool09 on 2010-07-30
Oh yeah, i forgot to mention, i borrowed my brother's windows machine and tried WinToFlash and PEToUSB. They just gave "Disk Error. Press any key to restart..."

---

### Post by k3lt01 on 2010-07-30
Hey Aiden, good to see you trying things out but try to keep your cool as there is always a way around things and all you need to do is ask for advice. If w don;t know the answer we can often point you in the right direction.

Now to answer your OP. I haven't been able to get the Live USB maker thing to work either so I went looking around cause I really didn't want to keep burning disks if I didn't need to. You know protect the environment from waste etc. Anyway I found [this]("http://ubuntuforums.org/showthread.php?t=1288604") and it works for me, so I offer it to you as a possible alternative.

Have fun.

---

### Post by beew on 2010-07-30
If you use windows and try to create live usbs for Linux distros the LiLI usb creator seems much better than Unetbootin. 

It supports persistence for many distros and looks a lot prettier.

 Too bad there is no such thing for Linux! I guess we are supposed to use command lines .:p

[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

---

### Post by aidenscool09 on 2010-07-30
Yeah, as i said, my cd drive is a bit dodgy and i have no idea how to replaced it as i use a Sony Vaio VGC-V2M and it's hardware is different to any other computer. Even the power supply is different. It only has one molex and i used a splitter and modded it so i could have 2 Hard Drives and the motherboard power cable is 18-Pin. But anyway, back to topic. I usually use FUSBi for Ubuntu Live USBs but there seems to be no way to have a "working" Windows USB installer. No matter how i try it, in just the the "Disk Error. Press any key to restart..." But thanks anyway for your help. Going to try BartPE on my brother's laptop. By the way, I'm only 13, so don't think I haven't moved out yet and i'm still leeching from my brother (who's younger than me).

---

### Post by aidenscool09 on 2010-07-30
And by the way, the version of Windows I'm trying to install is Windows XP Pro Black Edition, i'm not sure weather that's frowned upon here, but I hate any OS that you have to pay for from Microsoft. Apple OS X is ok but not worth the price.

---

### Post by ronnielsen1 on 2010-07-30
Windows 7 will work, I have done it (Didn't stay long) but I don't know whether xp would work

---

### Post by aidenscool09 on 2010-07-30
And imho, my brother's laptop is branded FAIL, it's clocked at 2.8GHz and it's using a 120nm P4, the darn thing overheats within half an hour and you could make a cuppa on the bottom of where the heatsink is.I'm thinking of at least putting some Arctic Silver 5 on it. And i could do with some of that myself tbh.

---

### Post by aidenscool09 on 2010-07-30
[ronnielsen1]("http://ubuntuforums.org/member.php?u=61926"), what did you use for 7?

---

### Post by Plumtreed on 2010-07-30
The USB Disk Creator in Ubuntu works on Ubuntu products. I haven't heard of burning a Windows ISO let alone a USB drive.
 
Prior to burning a USB dongle I always first format it fat32 in Windows.

---

### Post by k3lt01 on 2010-07-30
> **aidenscool09 said:**
> And by the way, the version of Windows I'm trying to install is Windows XP Pro Black Edition, i'm not sure weather that's frowned upon here, but I hate any OS that you have to pay for from Microsoft. Apple OS X is ok but not worth the price.If it wasn;t paid for and it is a marketable item then yes it is frowned upon and I wouldn't mention it again.

---

### Post by theozzlives on 2010-07-30
> **beew said:**
> If you use windows and try to create live usbs for Linux distros the LiLI usb creator seems much better than Unetbootin. 

It supports persistence for many distros and looks a lot prettier.

 Too bad there is no such thing for Linux! I guess we are supposed to use command lines .:p

[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

There's Portable Linux, that works well and plays nice with Ubuntu.

---

### Post by beew on 2010-07-30
> **ronnielsen1 said:**
> Windows 7 will work, I have done it (Didn't stay long) but I don't know whether xp would work

If you use MicroSoft's tool I think you can only use it on the machine that created it and it is only for booting.
Apparantly M$ only allows you to keep one copy for backup. As I said one guy claimed he was able to creat a bootable usb for windows 7 using Unetbootin, but almost everyone posted on his blog said it didn't work.

---

### Post by aidenscool09 on 2010-07-30
Ah, fair enough, and thanks for letting me know. As far as i know, the mention product was created by someone within Microsoft, but they removed tons of unneeded files etc. As far as i know, it's supposed to be free.

---

### Post by aidenscool09 on 2010-07-30
Anyways, so does anyone have any ideas about installing windows from USB? Also any help with the problem of "Disk Error. Press any key to restart..." Also when i press a key, it doesn't restart, it just loads GRUB.

---

### Post by beew on 2010-07-30
I think BartPE doesn't create a full brown XP on a usb, it is just something for trouble shooting and booting etc. There is a tool created by M$ that does similar thing and I think it is avaliable for free if you buy a CD from them. 

I think M$ would go through great length to prevent people from making a genuine live portable device because they want to charge you a fee for every instance of installation/use. The philosophy is opposite to portability. You can probably create a windows live CD or USB with a lot of hecking, but even then it would probably contingent on very particular hardware configurations which would rule out most common installations. If it is common M$ woluld have closed the loophole long ago.

---

### Post by aidenscool09 on 2010-07-30
Yes, buy a CD from m$... that'll happen when i install windows vista. (NEVER!!!11!!!)

---

### Post by aidenscool09 on 2010-07-30
But thanks for saying, and there probably is a way but it most likely will give me the same error as every other time. And also, Windows Fundamentals For Legacy PCs is basically a stripped down version of Windows XP, which was made by m$, and is actually free*








*not including the cost of your bandwith being wasted due to multiple downloads because you can't install it other than in a VM.

---

### Post by beew on 2010-07-30
> **aidenscool09 said:**
> But thanks for saying, and there probably is a way but it most likely will give me the same error as every other time. And also, Windows Fundamentals For Legacy PCs is basically a stripped down version of Windows XP, which was made by m$, and is actually free*
.


Not only error messages, such hacking is probably illegal.:p

---

### Post by k3lt01 on 2010-07-30
> **aidenscool09 said:**
> But thanks for saying, and there probably is a way but it most likely will give me the same error as every other time. And also, Windows Fundamentals For Legacy PCs is basically a stripped down version of Windows XP, which was made by m$, and is actually free*

*not including the cost of your bandwith being wasted due to multiple downloads because you can't install it other than in a VM.I think you need to be very careful with your interpretation of "free".

"Windows Fundamentals for Legacy PCs is exclusively available to Microsoft Software Assurance customers, as it is designed to be an inexpensive upgrade option for corporations that have a number of Windows 9x computers, but lack the hardware necessary to support the latest Windows. It is not available through retail or OEM channels."

You are 13, you are NOT a corporation, you should not have access to that product. Take this as friendly advice ok, I wouldn't go sprouting that you have it.

---

### Post by aidenscool09 on 2010-07-30
Ah, ok, well i only use it in a VM to test software as i don't want to waste money on the actual version of windows xp, 7 etc. The last time i used it was to test a driver (iZ3D). And that was about a week ago, but does anyone know a way of installing windows without a cd drive or usb (as none of them seem to work for me). I tried just copying the files straight from the iso but it just stayed at a blinking underscorfe as if it were loading, that why i haven't replied for a while.

---

### Post by aidenscool09 on 2010-07-30
And i'm not really bothered about windows FLP, it's windows xp black edition i was asking about, but really it's just windows xp in general.

---

### Post by aidenscool09 on 2010-07-30
Also i don't see the problem with me installing it, many Asus EEE users are installing windows FLP. Heres an example [http://forum.eeeuser.com/viewtopic.php?id=1293](http://forum.eeeuser.com/viewtopic.php?id=1293) .

---

### Post by aidenscool09 on 2010-07-30
As a matter of fact, i might as well go use the guide on [http://www.eeeguides.com](http://www.eeeguides.com)

---

### Post by aidenscool09 on 2010-07-30
Actually no, i just realised i have to use BartPE before i use PeToUSB. Stupid me. But thanks anyway for your help guys. You really are a great forum.

---

### Post by ronnielsen1 on 2010-07-30
> [ronnielsen1]("http://ubuntuforums.org/member.php?u=61926"), what did you use for 7?

If you don't have an iso of windows 7, you have to make one. To find out what your computer calls your cd/dvd device go to the Main Menu, click on System, mouseover Administration and select  System Monitor.  Click the File Systems tab.  The device name will be  listed in the **Device** column)
 Mine is /dev/sr0

Then type in terminal in your home directory (make sure dvd is NOT mounted) type in

cat /dev/sr0 > /home/username/windows7.iso

substituting username for your username. This should create an iso in your home directory named windows7.iso. Unetbootin should have no issues with this file

---

### Post by beew on 2010-07-30
> **ronnielsen1 said:**
>  This should create an iso in your home directory named windows7.iso. Unetbootin should have no issues with this file

Creating an iso is no problem if you have the CD. There are many many ways you can do it in Linux or Windows, also creating a bootable usb with Unetbootin is no big deal, the question is what does it boot into and what happens afterwords.  Did you actually install Windows7 using the usb created by Unetbootin? I would be very surprised if it works and indeed most people who have tried this method and bothered to share their experience on forums said it doesn't.

Take a look at this for example [http://jaxov.com/2009/09/install-windows-7-from-usb-stick-easily-unetbootin]("http://jaxov.com/2009/09/install-windows-7-from-usb-stick-easily-unetbootin/")/

---

### Post by k3lt01 on 2010-07-30
> **aidenscool09 said:**
> And i'm not really bothered about windows FLP, it's windows xp black edition i was asking about, but really it's just windows xp in general.
Aiden your missing the point. If you didn't purchase it legally and you use it then you are breaking the law, sorry but that is the crux of the matter. You go ahead and do what you think it ok but you shouldn't drag a forum of other people into it if it isn't legal.

---

### Post by overdrank on 2010-07-30
This issue is not supported on these forums. Thread closed.

---

