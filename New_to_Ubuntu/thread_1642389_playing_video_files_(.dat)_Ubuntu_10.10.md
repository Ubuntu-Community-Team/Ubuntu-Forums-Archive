---
title: "playing video files (.dat) Ubuntu 10.10"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by lakmalsuranga on 2010-12-10
I m using Ubuntu 10.10. But I cant play VCD (.dat files) with Movie Player.
It search for required plugin, But after searching it says " No packages with requested plugins found. The requested plugins are: VCD protocol source"

Please help me

Thanks

---

### Post by tajiknomi on 2010-12-10
> **lakmalsuranga said:**
> I m using Ubuntu 10.10. But I cant play VCD (.dat files) with Movie Player.
It search for required plugin, But after searching it says " No packages with requested plugins found. The requested plugins are: VCD protocol source"

Please help me

Thanks

[SIZE=2]Try ***VLC*** *player*, mplayer can't handle .dat Extension..
[/SIZE]

---

### Post by germanix on 2010-12-10
Mplayer is a versatile piece of GNU/GPLed video/audio software which supports an astronishing variety of audio and video formats. Here is another tip to help one use mplayer to play a VCD file. As you know a VCD has video files by names avesqrt.dat . To play such files in linux (provided you have mplayer) , do the following :

$ mplayer   vcd://1

If that doesn't work then specify your cdrom (In my case it is /dev/cdrom but it may be different in your case) device as follows:

$ mplayer   -cdrom-device   /dev/cdrom   vcd://1


Note: You should not mount the cdrom for this to work.

To play a DVD

$ mplayer dvd://[title  [start_title]-end_title] [options]

To see a TV channel (Provided you have a TV tuner card)

$ mplayer tv://[channel] [options]

---

### Post by lakmalsuranga on 2010-12-10
Hi, Thank you for both answers. 
It did not work both methods. 
Also no problem with vcd because it works on windows

---

### Post by Spyderkid on 2010-12-10
try installing Ubuntu Restricted extras from the software centre and trying mPlayer again

---

### Post by lakmalsuranga on 2010-12-10
Gstreamer plugins installed. But still not working

---

### Post by Verbeck on 2010-12-10
> **Spyderkid said:**
> try installing Ubuntu Restricted extras from the software centre and trying mPlayer again
have you tried this?

---

### Post by lakmalsuranga on 2010-12-10
Sorry I cant understand "Ubuntu Restricted extras"..... what is it?
pls explain further...

---

### Post by Verbeck on 2010-12-10
open the software center or synaptic
search for *ubuntu restricted extras* and install

alternate method and explanation here: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by lakmalsuranga on 2010-12-11
Hi,
I did everything...... ....
But still it did not play with movie player or VLC.

Thanks for all helps.

---

### Post by timouser on 2010-12-20
I had the same problem with ubuntu 10.10 that some of the vcd and dvd wouldn't play.  After I installed libdvdread4, I can play any vcd or dvd**.  **Refer the link below for more info.


$ sudo /usr/share/doc/libdvdread4/install-css.sh 

[https://help.ubuntu.com/10.10/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/10.10/musicvideophotos/C/video-dvd.html)

---

### Post by Orvar on 2010-12-25
This is really a problem. I have Windows XP on one machine and Ubuntu 10.10 on three others. The Ubuntu computers can´t even read the mpg (or .dat) file when I try to copy it from the CD to the harddrive, there is an "in/out"-problem. I also got a message saying there was a "split" problem or something similar. 
 
But in Windows XP I can both play the movie (using VLC) and copy the .dat- or mpg-file to a USB stick without any problem. And _then_ I can play the file (copied on the Windows machine) from the USB stick on any of my Ubuntu computers. 

All my VCD and SVCD movies were backed-up on a Windows machine, so there is a possibility that there is something missing in Ubuntu (or even the linux kernel) that makes Windows-burned VCD:s unreadable. All of them work perfectly in Windows. So, what I have to do now is to copy from CD to USB stick using my Windows machine, and then copy the mpegs from USB to my Ubuntu hard drive.
It works, but is time consuming. I do have a lot of VCD and SVCD movie backups since the DVD player I used a few years ago was not DivX or Xvid compatible. I also have divX and Xvid movie backups, and they all work and can be copied on my Ubuntu machines.

In short: VCD or SVCD CD:s burned on a Windows XP machine are unreadable directly from the CD:s, but copied (using Windows XP to read the files) can be both read and played. And this only affects VCD and SVCD, not other video formats.

I am no hacker, so I can´t do anything about it, but if this can help someone more skilled to fix the problem it would be very nice. I don´t like having to use Windows, but for now I am happy I kept it on one of my computers. But I would be even more happy if I didn´t have to.

---

### Post by thenamelessone on 2010-12-25
go to system>admin>synaptic package manager. then go to setting>repositories. uncheck ubuntu cd rom. reload repositories. search for vlc and install. once installed right click on file and play with vlc

---

### Post by Orvar on 2010-12-25
Uh???
I already have the Ubuntu CD unchecked in the repositories (and I really don´t understand why it would make a difference), and I already have VLC as well as Totem, SMPlayer, Xine... 
(Double-clicking on the file opens VLC which is my standard player, but it then says the file is unreadable. There is however a way around this that I discovered: Starting VLC, then Open disk and checking SVCD/VCD will PLAY the movie. 

But that is not the most important thing for me. The CD´s are more than five years old now, and some of them are getting unreadable no matter what I do (oxidation from the youtside are eating them up). Before the CD:s get too old I want to COPY the movies to my external harddrive, but  Nautilus just refuses (also when I am root). I am sorry if I was unprecise before, the main problem is copying.
In Windows it is simply drag-and-drop from the CD to the USB-stick. Not in Ubuntu. There I just get a message that the file could not be copied due to "error at splice of file: In/out error".

---

