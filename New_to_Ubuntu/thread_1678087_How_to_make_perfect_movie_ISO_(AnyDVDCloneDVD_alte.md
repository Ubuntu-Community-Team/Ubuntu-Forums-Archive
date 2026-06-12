---
title: "How to make perfect movie ISO? (AnyDVD/CloneDVD alternative)"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by kenny2009 on 2011-01-29
I recently purchased Avatar on DVD. As soon as I got home with it, I put it in my computer to make a full ISO backup of the movie. I used k9copy to create the ISO. When that finished I burned the ISO to a DVD. When I played that DVD in my DVD Player, Computer, Xbox 360, or Wii there was no audio. The video and the menus worked perfectly... but the movie had no sound. I thought it was just a bad burn so I mounted the ISO on my computer and played the movie. No sound. I switched over to Windows 7 and used AnyDVD + CloneDVD to create the ISO and then burned it to a disc using InfraRecorder. That DVD played with no problem.

So, what do I need to do to make backup copies of my movies without using Windows? I would like to do everything in Ubuntu instead.

---

### Post by NightwishFan on 2011-01-29
Well even Brasero can make a copy of a DVD, though it will be a full size (over 7gb) iso for something like Avatar. You might be missing the libdvdcss library which might be needed for such an operation:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by robsoles on 2011-01-29
When I want a strict copy of an optical disc (CD or DVD) I use dd in a terminal, you have to find out where in /dev your disc is referenced - pretty sure I've found them at /dev/dvd and /dev/cdrom but you can use
```
ls /dev/?v*
```in terminal to find it, if you find /dev/dvd and /dev/dvdrw then use /dev/dvd as **i**nput **f**ile. Then you can use dd to make a copy of it
```
dd if=/dev/dvd of=~/whatever-it-is-called.iso
```When that completes open the new iso with a media player that can play DVDs (I prefer VLC) and if it plays back, with all it's trimmings, then brasero should be able to burn you a working copy, provided you have a big enough blank :)

<edited-in>I open VLC and drag and drop the whatever.iso file of valid DVD onto the gui interface of VLC and VLC gets up and plays the video :)</edited-in>

---

### Post by kenny2009 on 2011-01-29
```
kenny@Kenny-Laptop:~$ ls /dev/?v*
/dev/dvd  /dev/dvdrw
kenny@Kenny-Laptop:~$ dd if=/dev/dvd of=/media/SeagateHDD/Avatar.iso
dd: reading `/dev/dvd': Input/output error
59360+0 records in
59360+0 records out
30392320 bytes (30 MB) copied, 11.0262 s, 2.8 MB/s

``` Why does that happen? I have libdvdcss2 installed, if that matters here. Is it because I'm trying to copy it to my external USB hard drive? I don't have any disk space left on my internal hard drive.

---

### Post by NightwishFan on 2011-01-29
The dvd might have bad sectors. In that case I recommend you give DVDisaster a try. It is in the Ubuntu repositories. Though note, to have libdvdcss crack it, its best to "play the movie for about 5 minutes", then try the copy. Else it will say nearly every sector is unreadable. Also your USB drive might have run out of space, a common DVD is dual layer nearly 9gb.

---

### Post by robsoles on 2011-01-29
Have to admit, I haven't done it with a recent release - copy protection of many forms are overcome by taking the raw image, like dd does, but there are copy protection schemes that use relatively clever geometry stuff to make it harder (or at least I think that's what they are doing)

If a 'cloning' program in Windows got it then I sort of expect dd will get it for you but 'AnyDVD + CloneDVD' probably has copy-protection removal stuff and dd can't compete because it doesn't refer to libdvdcss to access the disc (as far as I know).

NightwishFan's suggestion of making sure it can play for more than five minutes, under Ubuntu, with the libdvdcss library installed and then using something that refers to libdvdcss to copy DVDs will be the more likely way.

---

### Post by kenny2009 on 2011-01-29
Okay so I tried to play the DVD like normal using VLC or Movie Player. At first both programs refused to play the movie properly. It had "colored static snow stuff" over the video and the audio was crap. I don't know how to describe it.. I should have taken a screenshot but I didn't think of it at the time. I took the dvd out and made sure it wasn't scratched (and it's not - it's practically brand new still), then I put it back in and it played fine. So I'm using dd to copy it and so far it sounds like it's working. The optical drive sounds like it's working hard and the terminal window looks like it's waiting for the command to be completed. 

I'll post back in about an hour or so if this works. 

Thanks for all the help! :)


Edit: Seems like it's stuck. The ISO is 3.3GB and there is 10GB of free space on my HDD. The DVD drive is not doing anything. No blinking lights or spinning DVD. The Terminal window appears to be waiting for the command to be completed but nothing is happening.

---

### Post by robsoles on 2011-01-29
I imagine lots of people will be grateful to know **if** dd can make a working raw image of a recent DVD, thank you for being responsive.

---

### Post by TeAmigo on 2012-01-20
Here's an outline of how k3b successfully cloned a copy protected dvd.  Documentation seems to be sparse, but k3b has a very clear interface.  This is with Ubuntu 11.10 x86_64 on a Dell Studio laptop. I imagine this  does depend on having installed libdvdcss mentioned above. Once k3b is  installed, go to menu  Tools/Rip Video DVD...  That will create the copy  on hard disk. After it finishes copying(decrypting?), it will ask for a  blank media to write the copy to. Save the project if you're going to  want more copies.

Check out [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

