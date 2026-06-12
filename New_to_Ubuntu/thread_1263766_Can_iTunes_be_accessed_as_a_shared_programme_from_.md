---
title: "Can iTunes be accessed as a shared programme from XP"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by Scunnered on 2009-09-11
I have been looking at iTunes via Wine but having difficulty in making things work.  Various suggestions have been made for music players however these do not offer what I am looking for.

I am now wondering if it would be possible to make iTunes a shared programme on an XP laptop which I could access via a wireless broadband connection using Jaunty?  Would I then be able to load audio books and sync them to an iPod using this method?

If this is possible I would imagine that I could access the programme as and when I like and not have to plead with my friend for use of the XP laptop.

Is this a feasible option?   I hope so as I am getting so frustrated in wanting to work totally from Ubuntu.

---

### Post by Penguin Guy on 2009-09-11
It may be possible, but is completely crazy - why don't you just use a Linux music player such as [Rhythmbox]("http://www.swansonblog.com/geekspeak/wp-content/uploads/2009/01/rhythmbox-ipod1.png")?

---

### Post by Excedio on 2009-09-11
> **Penguin Guy said:**
> It may be possible, but is completely crazy - why don't you just use a Linux music player such as [Rhythmbox]("http://www.swansonblog.com/geekspeak/wp-content/uploads/2009/01/rhythmbox-ipod1.png")?
 
Or [Songbird]("http://getsongbird.com")

---

### Post by Scunnered on 2009-09-11
My thanks to you both for your reply.

It may be *completely crazy* ! **but will it work**?

I have been up hill and down dale seeking a solution to my problem but as I stated earlier music players do not meet my needs.

I do not want to listen to music I want to listen to **audio books** commencing at CD1 track 1 and finishing on CD11 track 25. Each time I stop listening it must be possible to recommence listening from the point where the recording was stopped. Itunes lets one join each track on a CD to form one complete track and that is why I am looking at some means of working from Ubuntu into iTunes.

If I can obtain this functionality in Linux then please tell me.  If not will I be able to share iTunes from XP and have things work?

It appears from what I have seen and been advised that the function for Audio Books in iTunes is not well known. Asking specifically on music player sites for it does not give me any encouragement.

---

### Post by Scunnered on 2009-09-13
Can anyone please confirm that it is possible to work with a shared programme in XP from Ubuntu.

I am desperate to keep Windows off my system and as it appears that no Linux programme exists that provides the functionality that I require this could be my last hope.

Thanking you for your assistance

---

### Post by tacantara on 2009-09-13
Are you talking "shared program" as in located on a server?  That, I can't answer (although it sounds really good, and I may have to experiment with that).  Right now, I use iTunes on XP running in a virtual machine (Sun's VirtualBox program).  Based on the specs of your computer in your signature, you should have no problem building a virtual machine and running it efficiently.  In the past, I've used Banshee, and found it to be quite good at handling iPod stuff...until I switched from a Classic to a Touch.

---

### Post by Scunnered on 2009-09-13
**tacantara**

Many thanks for your reply.

Please correct me if I am wrong.  Am I right in thinking that if I install Virtualbox on my laptop that I would then be able to download iTunes and work with it without having to get involved with Windows or Wine?

If this can be done without involving anyone else then that is exactly what I want.

I can ask my friends to let me use their systems but copying books on to iTunes and transfering them over to the iPod for playing is a rather lengthy process. It is for this reason that I wish to be self sufficient and work within Ubuntu.

If my reading of things is correct can you please confirm so and if possible guidance on the best way to set this up.  Up until now the light in the tunnel has been the train coming in the oposite direction.

Once again many thanks for your assistance.

---

### Post by tacantara on 2009-09-13
VirtualBox allows you to install an operating system.  After that, you can install programs that are compatible with the OS.  For instance, my virtual machine is Windows XP.  I installed XP as my virtual OS (essentially a guest OS on my Linux host), then I installed XP compatible programs, such as iTunes.  If you have a valid copy of XP or other Windows OS available, then you can create the virtual machine in VirtualBox.

I hope my answer wasn't too verbose, I'm just trying to cover all my bases in describing this.  You won't be completely free of Windows, but if all you're using the virtual machine for is syncing your iPod, then you won't be using it enough to really notice.  I only open my virtual machine for iTunes tasks, and use of the U.S. Army's website (requires use of my ID card, which has smart card technology, to log in - and the smart card reader software is only written in Windows).  I also used it the other day to open up IE8 to view a website that was Java intensive (FF and Opera in Linux couldn't open the documents in the Java viewer).

If you decide to go the VB route, I'll be more than glad to offer you advice based on my experience with it.

---

### Post by SuperSonic4 on 2009-09-13
You will still have to install a copy of windows inside the virtualbox. The virtualbox is essentially like a partition inside your current OS. You'd have to install windows inside it

If you want to combine a load of mp3 files you can use the cat command ```
cat file1.mp3 file2.mp3 file3.mp3 > file.mp3
```

---

### Post by Scunnered on 2009-09-13
**tacantara**

I knew it was too good to be true. I found an old XP CD and SP2 which I had used on my old desktop so at least I am not having to splash out on new software.

If I go down this road how do I tackle it.  Would I be right in thinking that I start with Virtualbox and then add the XP to that?  Will I have to arm wrestle Microsoft as this is ancient software previously installed on another system?

My concern is that I do not want any problems with Microsoft wanting to take over my world.  I am prepared to compromise provided Ubuntu Rules and I am able to keep XP well apart from Jaunty.

I will be pleased to accept your guidance in this matter as I am finding my way in Ubuntu slowly.  It appears to be a new experience every time I think that it would be good to this or that. I find it interesting but am very reliant on the kind assistance freely offered via the forum.

**SuperSonic4**

Your suggestion will work well in music playing however I dont think it is suited to audio books.  To give you an idea of what I am looking at I have just listened to an audio book comprising 5 CDs. I was able to join all the tracks on each CD to form one continuous play and within that can start and stop at will without loss of my place.

It is this facility in iTunes that I seek and so far have been unable to find in Linux software.

My sincere thanks to you both for your kind assistance. Things are looking up by the minute.

---

### Post by tacantara on 2009-09-13
Sorry for the delay in responding.  I'm in the hospital with my daughter.  We're both recovering from injuries received in an accident two weeks ago today.

With the virtual machine, you're running the two OSes independently.  As I mentioned earlier, Windows only receives about 5% or less of my total computing time.  Like you, I prefer Ubuntu as my main OS. The steps involved in setting up the virtual machine are:

1.  Install VirtualBox (you can download the software package at the Sun website link I sent in an earlier post).  The package is a ".deb" so installation is easy.

2.  Open the program and start setting the parameters for your virtual machine by selecting Machine > New or by clicking the NEW icon.  You will set it up as a Windows XP machine.  During setup you will be able to assign RAM allocation, sound info, network info, etc.

3.  Install XP off the CD/DVD into your virtual machine.

4.  Boot up the XP virtual machine.  Before you install iTunes or any other software, install the VB Guest Additions.  These additions will allow you to utilize the USB ports (which you'll need to sync your iPod) and a bunch of other neat things. To install the guest additions for XP, select Devices > Mount CD/DVD-ROM > CD/DVD-ROM Image.  From the list, select the VBoxGuestAdditions.iso file.

5.  Install iTunes and any other Windows-compatible software you wish to add to your new virtual machine.

**NOTE**  When you plug in your iPod (or any USB device), both Ubuntu and VB will try to mount the device plugged in.  This creates a conflict.  Simply to to your Ubuntu desktop and unmount the USB device, then go back to your VB screen.  Right-click the USB icon on the bottom right of the screen, and make sure your device is recognized and selected (black X next to it indicates that it is active).

I could go on ad infinitum about running VB, but the Help feature that comes with it is quite detailed.  If you run into a snag, there's a whole forum dedicated to virtualization.  Of course, I'm usually on line so just drop me a line if I can be of further assistance.

---

### Post by Scunnered on 2009-09-14
**tacantara**

Many thanks for your reply.  I appreciate your kind assistance with this problem.

I will now set to installing and report back once things have been completed.

I hope that both you and your daughter make a quick recovery and wish you well.

My sincere thanks

---

### Post by NexusZA on 2009-09-14
I just thought I would pip in here with a little comment to make understanding what you're doing easier. Virtualbox is really a machine emulator. It creates a software environment that pretty much pretends to be a full machine. When you create a "machine" with Virtualbox you specify how much of your RAM that fake machine will use while it is "turned on". If you have the XP disc mounted inside Virtualbox, for example, and startup the machine, it will boot from the disk and XP doesn't know that it is actually running inside a pretend machine.

Kind of like how The Matrix was made to fool people into thinking they were living in a real world, just in this case we are fooling an OS and the software that runs on it :D

---

### Post by Scunnered on 2009-09-15
**NexusZA**

Thanks for your reply.  I have got the understanding of the process OK it is the implementation that I am having problems with.  I was following the idiots guide provided by **tacantara** and hit a problem.

Having got to the length of item 3 and installed XP when I opened up the VirtualBox the XP screen displayed and immediately asked that I install SP2.  This was a bit strange as my XP Home Edition disk clearly states on it "***includes service pack 2***" so why am I being asked for it.  I also have a seperate SP2 CD so I loaded it up and so far it has been running for near enough an hour without no visable activity.  There is also no drive activity evident (total silence from the CD drive).

I will give this another hour and if nothing appears to happen by then I will shut down and start praying for assistance.

So far the only one that appears to be fooled is me.  Yours in frustration.

---

### Post by Scunnered on 2009-09-16
Ok I have now managed to wrestle my way through installing VirtualBox and have managed to load iTunes on to the system.

It however comes up with an error message advising that iTunes was not properly installed.  This is a complete pain as it would appear that either the system is reading earlier attempts to load iTunes or Apple is giving me a copy of what it gave me earlier including the problem.

I still have Wine loaded and wonder if the iTunes loaded there is being read and not a new clean installation?

I think that I will mark this as resolved and seek guidance by asking specifically about this difficulty

My thanks to all who assisted.

---

