---
title: "Ripping a DVD"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2010-05-17
Okay, I've never gotten straight advice on this.  I have Ubuntu on this laptop (9.10), and I have a copy of Avatar on DVD right next to me.  How do I get my digital copy stored on my hard drive so I can watch whenever?  It would be great if someone could give me step-by-step advice.  I have VLC if that helps anyone...

---

### Post by lisati on 2010-05-17
You might want to start by reading this: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by TriBlox6432 on 2010-05-17
I've already installed all the media/restricted formats.  :)

But it won't play for me...  When I open "movie player" it closes instantly.  And when I open it with VLC it doesn't do ANYTHING, not even closing.  And the disc tray wont open unless I restart my laptop.

---

### Post by Ozymandias_117 on 2010-05-17
Do you have libdvdcss2?

---

### Post by alphacrucis2 on 2010-05-18
Add the medibuntu repo and install libdvdcss2

---

### Post by 4Orbs on 2010-05-18
You might want to follow the steps in [this How-To.]("http://ubuntuforums.org/showthread.php?t=766683") It has always worked for me through numerous installs of Ubuntu and Xubuntu.

If your DVD is a Blueray disc, I doubt you'll ever get it to even play, much less ripped.

---

### Post by baddnady23 on 2010-05-18
Check out this site using k9copy:

[http://linuxowns.wordpress.com/2008/10/07/how-to-rip-a-dvd-in-ubuntu-to-avi-the-easy-way/]("http://linuxowns.wordpress.com/2008/10/07/how-to-rip-a-dvd-in-ubuntu-to-avi-the-easy-way/")

---

### Post by hannaman on 2010-05-18
I have used brasero to create an iso from movies and just opened the iso with totem (right click on iso, select "Open With").  That works if the DVD isn't laden with DRM.  It takes up more space, but the quality is great.  Otherwise, I use Handbrake ([http://handbrake.fr](http://handbrake.fr)) to create mp4's.  As others have pointed out, make sure you have libdvdcss2 installed from Medibuntu ([http://www.medibuntu.org](http://www.medibuntu.org)) for Handbrake to work.

---

### Post by cascade9 on 2010-05-18
> **4Orbs said:**
> You might want to follow the steps in [this How-To.]("http://ubuntuforums.org/showthread.php?t=766683") It has always worked for me through numerous installs of Ubuntu and Xubuntu.

If your DVD is a Blueray disc, I doubt you'll ever get it to even play, much less ripped.

Its do-able, from what I've seen on the net. Not that I've tried it. 

[http://www.recipester.org/Recipe:Play_Blu-ray_Movie_in_Linux_19689877](http://www.recipester.org/Recipe:Play_Blu-ray_Movie_in_Linux_19689877)

---

### Post by TriBlox6432 on 2010-05-18
No, it's a normal DVD.  I've gotten all the codecs and K9 installed, so tonight I will try it,.

---

### Post by 3rdalbum on 2010-05-18
> **cascade9 said:**
> Its do-able, from what I've seen on the net. Not that I've tried it. 

[http://www.recipester.org/Recipe:Play_Blu-ray_Movie_in_Linux_19689877](http://www.recipester.org/Recipe:Play_Blu-ray_Movie_in_Linux_19689877)

Firstly, this is an ancient HOWTO and you probably shouldn't link to it anymore. A much better page is: [https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

I wrote part of it and some kind soul has cleaned it up a little for me.

Secondly, Avatar is one of the latest Bluray discs, presumably with the latest MKB. Last time I checked, the hackers were 9-12 months behind on MKB, so you'd have to try using MakeMKV, not DumpHD. Even then, little chance of success.

To the OP: You don't just need the codecs and K9Copy. You need the libdvdcss2 decryption library. You can install it through the procedure in the Ubuntu help program, or by adding the Medibuntu repository. If VLC can't play your DVD, then K9 will not be able to copy it.

Also, K9 is probably better suited to copying and shrinking video DVDs rather than ripping them to disk (although it can do that). A simpler program for ripping DVDs and compressing them is Ogmrip, it's an excellent program. Some people swear by Handbrake but I've never tried it.

---

### Post by cascade9 on 2010-05-18
> **3rdalbum said:**
> Firstly, this is an ancient HOWTO and you probably shouldn't link to it anymore. A much better page is: [https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

I wrote part of it and some kind soul has cleaned it up a little for me.

Secondly, Avatar is one of the latest Bluray discs, presumably with the latest MKB. Last time I checked, the hackers were 9-12 months behind on MKB, so you'd have to try using MakeMKV, not DumpHD. Even then, little chance of success.


Fair enough. Like I said, I've never even tried to rip a bluray disc, I dont even have a bluray drive ;) 

I was just posting that to show that it is possible to play bluray on linux (but yes, you are probably correct, I doubt that avatar will work, for now anyway).

---

### Post by Boondock5 on 2010-06-22
This is Absolute Beginner Talk, so be gentle.
I can't seem to get anything to work when attempting to rip DVD's to my Hard Drive. I've exhausted all efforts, to no avail. 
I have Acidrip, brasero, WinFF, avidemux, VLC, AcetoneISO, dvd::rip, libdvdcss2... I did manage to get an ISO file onto the HD.  ****! What does a guy have to do to rip a dvd to his hard drive? 
I'm running 10.04 LTS i386

---

### Post by Arla on 2010-06-22
> **Boondock5 said:**
> This is Absolute Beginner Talk, so be gentle.
I can't seem to get anything to work when attempting to rip DVD's to my Hard Drive. I've exhausted all efforts, to no avail. 
I have Acidrip, brasero, WinFF, avidemux, VLC, AcetoneISO, dvd::rip, libdvdcss2... I did manage to get an ISO file onto the HD.  ****! What does a guy have to do to rip a dvd to his hard drive? 
I'm running 10.04 LTS i386

Have you tried k9copy? That (for me) has been the best so far, it's not perfect, and some DVD's just refuse to work with it.

---

### Post by NewDisciple on 2010-06-22
**Another vote for OGMRip, it is easy to use.**

---

### Post by MrWES on 2010-06-22
Open up a terminal (command line) and type

```
vobcopy -l
``` (small case L)

That'll rip the DVD into one large .vob file. Playable via VLC or Mplayer.


Bill

---

### Post by foxmulder881 on 2010-06-22
MrWES. I thought I was the only one who still used vobcopy.

It's awesome and works on anything you throw at it.

---

### Post by slooksterpsv on 2010-06-22
Here's how I had to get to the point where I could rip dvds:
1. Install all codecs - e.g. Restricted Extras, libdvdcss2, libdvdread4, etc.

2. I tried with various applications, but the only one that worked, for me, and I had to install other pieces of software after #1, was DVD::RIP, if you go under Debug -> Check Dependancies - it will show you what you're missing.

I was missing a xvid4conf and some others which it was trying to use initially to encode the DVD. So look there. Afterwards, you may need to change your settings for how it rips and how to encode the DVD.

---

### Post by yahoo on 2010-06-22
MrWes, vobcopy is just the bees knees.
Never tried it before, but soooo simple.
Thanks

---

### Post by mc4man on 2010-06-22
If the disk doesn't contain structure protection then vobcopy works fine either as suggested or to create   a VIDEO_TS  whole disk rip (movie,  menus, extras, chapter navigation, ect,) then
```
vobcopy -v -m -F 16
```
Above assumes dvd is on default drive, if you have more than one then read vobcopy --help.

If the title has structure protection then try K9 or one can mis-use dvdisaster to dump to an iso (only good for playback, not backing up or further processing. Works with most structure protections - limited only by number of unreadable sectors/time to rip

---

### Post by Boondock5 on 2010-06-23
> **MrWES said:**
> Open up a terminal (command line) and type

```
vobcopy -l
``` (small case L)

That'll rip the DVD into one large .vob file. Playable via VLC or Mplayer.


Bill


MrWES, Thank you! All I ever wanted was something to easily rip movies over to my hard drive.
vobcopy -l , works like a dream. 
It's how I have imagined Ubuntu being with every application, just a few clicks and its done. Thank you again. ):P

---

### Post by yahoo on 2010-06-23
MrWes, your next challenge :)
vobcopy errored riping a disk, saying the file was too large, but was successful when I removed the -l option.
This created 4 vob files - how do I join these together?

edit: I've tried: cat file1.vob file2.vob > output file, but error is:

3644MB of 5013MB written (73 %)
[Error] Write() error
[Error] It's possible that you try to write files
[Error] greater than 2GB to filesystem which
[Error] doesn't support it? (try without -l)
[Error] Error: Bad address

---

### Post by Boondock5 on 2010-06-24
> **yahoo said:**
> MrWes, your next challenge :)
vobcopy errored riping a disk, saying the file was too large, but was successful when I removed the -l option.
This created 4 vob files - how do I join these together?

edit: I've tried: cat file1.vob file2.vob > output file, but error is:

3644MB of 5013MB written (73 %)
[Error] Write() error
[Error] It's possible that you try to write files
[Error] greater than 2GB to filesystem which
[Error] doesn't support it? (try without -l)
[Error] Error: Bad address

It sounds like you may have your Hard Drive formatted in the wrong format like fat32 which sometimes only allows files under a certain size to be loaded onto it. I use NTFS file type, it allows me to load any size file onto it.

---

### Post by MrWES on 2010-06-24
That would be my guess; FAT32 4GB limit.

Bill

---

### Post by MrWES on 2010-06-24
> **Boondock5 said:**
> MrWES, Thank you! All I ever wanted was something to easily rip movies over to my hard drive.
vobcopy -l , works like a dream. 
It's how I have imagined Ubuntu being with every application, just a few clicks and its done. Thank you again. ):P

Glad I could help. Now lets get into vamps to shrink it all down to a DVD5! woowooo!

---

### Post by xmx on 2010-06-26
Handbrake easy to use, 
Works with 9.04 and 9.10

later versions see bottom

get:[http://sourceforge.net/projects/handbrake/files/0.9.4/HandBrake-0.9.4.tar.bz2]("http://sourceforge.net/projects/handbrake/files/0.9.4/HandBrake-0.9.4.tar.bz2")
Get this to your desktop.  Once on your desktop open terminal.
```
cd ~/Desktop
```
then:```
tar xjvf HandBrake-0.9.4.tar.bz2
```
Extract to desktop 
Then:```
sudo mv ~/Desktop/HandBrake-0.9.4 ~/hb
```
Then for required pack:```
sudo apt-get install yasm build-essential \
autoconf libtool zlib1g-dev libbz2-dev intltool libglib2.0-dev \
libdbus-glib-1-dev libgtk2.0-dev libhal-dev libhal-storage-dev \
libwebkit-dev libnotify-dev libgstreamer0.10-dev \
libgstreamer-plugins-base0.10-dev

```
```
cd ~/hb 
```
```
./configure
```
```
cd build 
```
```
sudo make 
```
That might take a while
```
sudo make install
```
Then ```
sudo apt-get install libdvdread4
```
followed by ```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

REBOOT  ```
sudo shutdown -r now
``` 

Then goto Applications > sound and video > HandBrake 

To use: put dvd in drive wait to mount 
file > source (dvd's name should show)
wait for it to load then click on the video tab *you can pick target size 700 MB, then click start, making sure the name and output dir is video and the correct. There is many things you can change around but this usually work for those who just want to put video on external and to play on your ps3 or pc.  

disclaimer:not intended for copyright infringement 
:guitar:

For versions 10.04 and 10.10 goto 

[http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/pool/main/h/handbrake/?C=M;O=A]("http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/pool/main/h/handbrake/?C=M;O=A")


sort by "date modifed" and select your current version (.deb package easy install)

---

### Post by Boondock5 on 2010-07-01
Ok, now for the next trek into the vobcopy world. 
Is there a method to changing the copy destination for DVD's, from the home folder straight to an external drive?](*,)](*,)](*,)

---

### Post by yetiman64 on 2010-07-01
> **Boondock5 said:**
> Ok, now for the next trek into the vobcopy world. 
Is there a method to changing the copy destination for DVD's, from the home folder straight to an external drive?](*,)](*,)](*,)

Try 
```
vobcopy --help
```It shows a "-o /path/to/output-dir/" option you can use to send to a folder (imagine the path being /media/<external drive name>/ in your case). This should override the standard output directory and write to a usb stick or such - haven't tried it yet, but am just starting to experiment with this myself as it looks quite promising.
Let us know if it works OK as I'll end up using this one myself :).

---

### Post by Boondock5 on 2010-07-01
I'm not sure what I did wrong.
"/media" is the only address I could find for my external drive. I named it media, as it's just for movies.
 Here's what I typed;
boondock5@boondock5-laptop:~$ vobcopy -o /path/to/output-dir/media


[Info] Outputting to /path/to/output-dir/media/AVATAR1-1.vob
[Error] Error opening file /path/to/output-dir/media/AVATAR1-1.vob.partial

 Forgive me if it was something stupid, I'm new to code.

---

### Post by yetiman64 on 2010-07-01
> **Boondock5 said:**
> I'm not sure what I did wrong.
"/media" is the only address I could find for my external drive. I named it media, as it's just for movies.
 Here's what I typed;
boondock5@boondock5-laptop:~$ vobcopy -o /path/to/output-dir/media


[Info] Outputting to /path/to/output-dir/media/AVATAR1-1.vob
[Error] Error opening file /path/to/output-dir/media/AVATAR1-1.vob.partial

 Forgive me if it was something stupid, I'm new to code.

/media is a system folder in which subfolders are held for mounted media. 

For example I have plugged in an 8GB usb stick with a label "Cruzer". So the system mounts it to /media/Cruzer.

I have just finished a dvd mirror directly to the usb stick from a commercial dvd (as per your output question) and it works great using vlc. The command I used is based on that from mc4man.

```
vobcopy -v -m -F 16 -o /media/<your foldername>
```<your foldername> in my case is "Cruzer" (without the quotes) and will be different for you. 

You can define a path in your system other than external media, I just assumed you were sending it to another media type.

Try and copy and paste in the above command then replace /media/<your foldername> with the actual path to the folder in which you want the dvd stored. Cheers yetiman64.

---

### Post by mc4man on 2010-07-01
Hey guys - just a small note about vobcopy - 

By default if vobcopy comes upon unreadable sectors it will retry up to 9 times before skipping. In the case of a smudge, scratch ect. that is a good thing, many times it can recover the data.

If you happen to try to rip a disk with intentional unreadable sectors due to structure protection then generally vobcopy may not be the best choice for a couple of reasons.

One is the time involved which depends on the # of unreadable sectors, the other is the rip, even if successful, may have navigation/playability issues.

It will be pretty obvious if structure protection is present.

(- it is possible to use vobcopy on sp titles, but it's not completely straightforward and can benefit from a rebuilt vobcopy that only reads once per block of 16 sectors (-F 16),  - better alternatives are available.
Fortunately sp is being used less and less, particularly in region 1

---

### Post by yetiman64 on 2010-07-01
@mc4man. Thanks for the extra info, I'll keep my eye out for such discs (and keep your comments in mind). 

My first attempt with it ran completely smoothly only about half an hour ago and I'm currently viewing the vid off a usb stick with vlc (no terminal errors at all showed up :D).

k9copy has always been my staple ripping program in the past, but I do like the simplicity of this one in terminal. Btw, region 4 discs in use here - any known problems ?

Thanks again for the mirror commands and comments etc., cheers yetiman64.

---

### Post by Boondock5 on 2010-07-01
You nailed it Yetiman64 !

Just type in "vobcopy -o /media/Media"

 and away it went copying directly into the external drive.
Hopefully this can help out other people that are as mouse impaired as me.

Thank you.

---

### Post by Boondock5 on 2010-07-01
I guess when I come upon a "secured" disc, I'll be back at square one with K9 copy. but, we'll jump that fence when we get there.

---

### Post by yetiman64 on 2010-07-01
> **Boondock5 said:**
> ... other people that are as mouse impaired as me.

Thank you.

:biggrin: only just past that stage myself, but learning quite fast thanks mainly to this forum.

You're welcome. Just take note of mc4man's comments above if any errors occur. Cheers yetiman64

---

### Post by yahoo on 2010-07-03
I though of the Fat32 4GB limit too, so tried ripping to an ext3 partition, but got the same error message.
I think perhaps it is more to do wtih the comment from mc4man about intentional unreadable sectore on a 'secure disc'.

I'm going to install handbrake as posted by xmx and give it a try .

Not giving up on vobcopy though, it's so easy.
Yahoo

---

