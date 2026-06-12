---
title: "Is Ubuntu DVD supposed to auto run in MS Vista"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by terryb_au on 2011-01-02
Good day all, ):P
I just want to try out and have a look at Ubuntu without installing it on my computer. Do I have to alter BIOS to boot from cd/dvd drive and thus see Ubuntu come up or is the DVD supposed to auto run whilst I have Vista(Basic) running. It doesn't auto run, is this correct?, I'm thinking it must be :confused: 
I downloaded the DVD iso (about 4.05GB) ver 10.10 from one of the mirror sites, I also downloaded the MD5SUM for the DVD from the same place, I checked my download using.. WinMD5sum.. program from [www.nullriver.com]("http://www.nullriver.com") and all is good. I also did the MD5SUM check on the DVD I burnt and it is also exactly the same; Is this correct?, should  checksum for the iso I downloaded AND the burnt image be the same? I only ask this because obviously I don't know, but also because I saw in one of the posts here somewhere that someone said that an iso is unpacked etc before it is burnt, if that is the case then I'd imagine that the checksum would change, I of course may have misunderstood what the poster was saying or I have burnt the image incorrectly.
I could also download just the CD version and burn it, does this version auto run in Vista or does it have to be booted from, to try it live.
I've been doing my best to find answer myself, but can't :redface:
Thanks,
Terry. ](*,)

---

### Post by stardustdk on 2011-01-02
> **terryb_au said:**
> Good day all, ):P
I just want to try out and have a look at Ubuntu without installing it on my computer. Do I have to alter BIOS to boot from cd/dvd drive and thus see Ubuntu come up or is the DVD supposed to auto run whilst I have Vista(Basic) running. It doesn't auto run, is this correct?, I'm thinking it must be :confused: 
I downloaded the DVD iso (about 4.05GB) ver 10.10 from one of the mirror sites, I also downloaded the MD5SUM for the DVD from the same place, I checked my download using.. WinMD5sum.. program from [www.nullriver.com]("http://www.nullriver.com") and all is good. I also did the MD5SUM check on the DVD I burnt and it is also exactly the same; Is this correct?, should  checksum for the iso I downloaded AND the burnt image be the same? I only ask this because obviously I don't know, but also because I saw in one of the posts here somewhere that someone said that an iso is unpacked etc before it is burnt, if that is the case then I'd imagine that the checksum would change, I of course may have misunderstood what the poster was saying or I have burnt the image incorrectly.
I could also download just the CD version and burn it, does this version auto run in Vista or does it have to be booted from, to try it live.
I've been doing my best to find answer myself, but can't :redface:
Thanks,
Terry. ](*,)

Well make sure that the BIOS makes the DVD boot at first priority. Then boot from the DVD - it is simple as that.

---

### Post by ram2500 on 2011-01-02
By default, CDs with programs will usually engage AutoRun. The Ubuntu CD has a program, named Wubi, which will install Ubuntu "inside" Windows. It's similar to a dual-boot setup, except it's less riskier and much easier. However, there is a slight performance loss, and it would be advisable to create a partition for a Wubi install if you decide to go this route.

---

### Post by myrtle001 on 2011-01-02
This is how it was when I started using 10.04 (it shouldn't have changed too much between 10.04 and 10.10):

All you need to do is insert the CD/DVD into the drive. When the AutoRun comes up, say no (Unless of course you want to install the Wubi version of Ubuntu). Then restart the computer. Pay attention when your computer boots up again for a button that will bring you to the BIOS screen (go here for a much better explanation of this step: [http://www.hiren.info/pages/bios-boot-cdrom]("http://www.hiren.info/pages/bios-boot-cdrom")). Follow the steps there to boot from your CD/DVD. Then, Ubuntu should boot up from the CD. When the screen comes up, tell it not to install (that is of course you want to). Then, when you shut down, it should tell you that you can eject the disk. Then you boot back into Windows.

If you ever want to install, consider trying out Wubi. I've been using Ubuntu via Wubi for about 6 months now. All it does is creates Ubuntu and all it's files right inside your install of Windows. It's far less as complicating and risky as partitioning you hard drive and install the full form of Ubuntu. With this, everytime you start up your computer, your computer will ask you which operating system you want to boot to.

Hope this helps!:D

---

### Post by IWantFroyo on 2011-01-02
Turn off the computer, then put in the disk when it boots, go into BIOS, select cd/dvd/usb as first priority, then sit back and enjoy the ride :D

---

### Post by terryb_au on 2011-01-02
Good day,
Thanks for replies thus far.

I have set boot sequence to cd/dvd first then harddrive second. When I start computer it has a black screen with blinking cursor  in top left corner but after about maybe 1 minute  the Windows boot up starts and Windows is launched.

So as per my first post is the checksum of the burnt image on the DVD supposed to be the same as the downloaded iso.
The file I see(via windows explorer) on the DVD is called "ubuntu-10.10-dvd-i386.iso" is this what I should see or haven't I burnt it correctly.

In my first post I referred to a post I had read about iso unpacking and here is a link

[http://ubuntuforums.org/showthread.php?t=990127&highlight=dvd+live+Vista](http://ubuntuforums.org/showthread.php?t=990127&highlight=dvd+live+Vista)

The 4 th message is to what I refer, by fiddler616.

Thanks again,
Terry

---

### Post by terryb_au on 2011-01-02
Good day all,
OK I have found more information that I must have missed on my initial searching for info.
I have apparently not burnt the DVD correctly, info is here all along,

[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

Will get back eventually with results

Cheers,
Terry.

---

### Post by Jerry N on 2011-01-02
> **terryb_au said:**
> 
The file I see(via windows explorer) on the DVD is called "ubuntu-10.10-dvd-i386.iso" is this what I should see or haven't I burnt it correctly.



You have put a copy of the downloaded .ISO on your DVD.  What you needed to do is select "Burn Image" in your DVD writer so you will write the bootable "image" to the DVD, not the .ISO file.  You probably can't burn the image to the DVD using the Windows built-in CD/DVD burner.  I use Nero but Ashampoo and Imgburn have free downloadable versions that will burn the image.

Jerry

---

### Post by terryb_au on 2011-01-02
> **Jerry N said:**
> You have put a copy of the downloaded .ISO on your DVD.  What you needed to do is select "Burn Image" in your DVD writer so you will write the bootable "image" to the DVD, not the .ISO file.  You probably can't burn the image to the DVD using the Windows built-in CD/DVD burner.  I use Nero but Ashampoo and Imgburn have free downloadable versions that will burn the image.

Jerry


Thanks Jerry,
I had just found info and just posted when your reply came in.

Thanks

---

### Post by mastablasta on 2011-01-03
> **ram2500 said:**
> By default, CDs with programs will usually engage AutoRun. The Ubuntu CD has a program, named Wubi, which will install Ubuntu "inside" Windows. It's similar to a dual-boot setup, except it's less riskier and much easier. However, there is a slight performance loss, and it would be advisable to create a partition for a Wubi install if you decide to go this route.
 
 
Just some additional info if OP is considering wubi - wubi creates a large file within windows system and everything installs into this "virtual" file. if something goes wrong with the file you can lose all data that was in the file.
 
Also you wont' be able to update or upgrade propperly.
 
but for trying out the system with slight performance loss it will be just fine.
 
another good way to try it out is to use a 1GB USB key and create a LiveUSB. it will boot much faster from it than form CD and the systen can be made persistant. unetbootin or linuxliveusb ([http://www.linuxliveusb.com/en/download](http://www.linuxliveusb.com/en/download)) and similar programms can be used in windows to create it easilly.

---

### Post by terryb_au on 2011-01-03
Good day again me hearties, :p
Thanks for the replies, good work.
Well I burnt another DVD disk and all is well. I fired up Ubuntu live and tried to hook up to the internet via mobile broadband, My service provider in Australia(3 Australia) was on the list, I filled out the necessary connection details that I retrieved from the usb modem previously(retrieved whilst in Vista). Unfortunately I can't get it to connect, I think Ubunti requires drivers. The modem is a Huawei model E1803 and probably doctored to suit 3. Obviously(I suppose  :rolleyes: ) if I'm trying to continue trying Ubuntu from live DVD then I can't install drivers even if available.

SO... am wondering:confused:  if there is a usb mobile broadband modem that's not too expensive that suits Ubuntu live and doesn't need any software from the service provider or drivers that aren't already in Ubuntu. Any body tried this?, or am I just way off course in my thoughts ? :redface:

Oh!, Thanks to those talking about installing to computer. If I was to install Ubuntu, and am seriously considering it, it would only be as a dual boot with Ubuntu on an external USB harddrive,, if that's possible :p

Cheers,
Terry

---

### Post by mastablasta on 2011-01-03
> **terryb_au said:**
> Good day again me hearties, :p
Thanks for the replies, good work.
Well I burnt another DVD disk and all is well. I fired up Ubuntu live and tried to hook up to the internet via mobile broadband, My service provider in Australia(3 Australia) was on the list, I filled out the necessary connection details that I retrieved from the usb modem previously(retrieved whilst in Vista). Unfortunately I can't get it to connect, I think Ubunti requires drivers. The modem is a Huawei model E1803 and probably doctored to suit 3. Obviously(I suppose :rolleyes: ) if I'm trying to continue trying Ubuntu from live DVD then I can't install drivers even if available.
 
SO... am wondering:confused: if there is a usb mobile broadband modem that's not too expensive that suits Ubuntu live and doesn't need any software from the service provider or drivers that aren't already in Ubuntu. Any body tried this?, or am I just way off course in my thoughts ? :redface:
 
 
Have you tried to install the drivers? i think they will install you will just lose them after reboot. hence the persistent USB drive is better for trying out.
 
there are Linux compatible USB modems as well as PCMCIA cards out there.
 
> 
Oh!, Thanks to those talking about installing to computer. If I was to install Ubuntu, and am seriously considering it, it would only be as a dual boot with Ubuntu on an external USB harddrive,, if that's possible :p

yes it is also possible to do that.
 
however it might be easier to put it on the same disk. Ubuntu needs about 20 GB (if you intend to put some data there as well. new installed programmes are not like in windows and they won't increase the used space so much. windows porgrammes usually come with their own libraries so sometimes they duplicate the existing ones. Linux uses just one common library (usually). so you might install quite a few programmes and still have  plenty of of disk space left.

---

### Post by terryb_au on 2011-01-03
Thanks Mastablasta. =D>
I've downloaded the getting started manual and will give it due study.
I found mention in another post that the Huawei E220 is well supported in Ubuntu so I dug out my old E220, shut down Ubuntu, switched power off and plugged in the E220, relaunched Ubuntu and the Three insignia/icon showed up on the desktop so I thought, "it's looking good", I tried to connect to the internet but it wouldn't happen, then realised that I didn't have the simm card in the E220. Shut down out of Ubuntu again, switched power off, swapped simm card into E220 and launched Ubuntu again,,,only trouble is after I pressed the try out Ubuntu bar the loading just didn't complete, I left it for quite a while with the little lights under the Ubuntu name going across as they normally do, only trouble it just didn't complete the launch and the cd/dvd drive light wasn't on so after some time I switched the computer off at the wall. I tried to relaunch Ubuntu again and the "Pheonix" bios page just sat there for a long time until I switched computer off again. I swapped back to the Huawei E1803, I started computer again and went into bios , changed to hard drive boot and let her go to boot windows, the Phoenix bios front page came up again and just sat there for a long time, I thought I'd got myself into deep do do but luckily windows eventually started, phew!!!!!!!!!:biggrin:

Yes I'll sort out a bootable usb memory stick.

I'll study up and get back to it all in due course.

Next time I'm here I hope it's through Ubuntu, if you never hear from me again it's probably 'cause I smashed the computer :lolflag:

Cheers, Terry :popcorn:

---

