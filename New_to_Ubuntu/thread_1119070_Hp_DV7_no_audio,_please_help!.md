---
title: "Hp DV7 no audio, please help!"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by luckync4841 on 2009-04-07
Ok, so I am very new to all of this, please bear with me. Just bought an HP DV7 laptop and installed Kubuntu on half of the hard drive. I have somehow managed to work my way through some of the setup but I cant get any audio. My audio works in windows but I get nothing on the web or through VLC player. I tried searching for a fix to this, but everything I have found is in "computer talk" and I dont really know what to do. Can anyone please help?

---

### Post by duanedesign on 2009-04-07
first I would check to see if your PCM mixer is muted (this is a bug in Intrepid).

go to the Applications menu at the top of your screen.
go to Accesories
Then Terminal
type in:
```
alsamixer -Dhw
```
Check these and make sure especially that your PCM is not set to 0


EDIT: If you have sound on your desktop but not with VLC  Try playing with the settings in VLC under Settings -> Preferences -> Audio -> Output Modules -> OSS and ALSA. Setting this to OSS has solved the problem for some.

---

### Post by Sykobabul on 2009-06-11
I have an HP DV7-2044ca and I had the same problem.  It's not easy to fix, but it's possible.  I still don't have headphones working yet, but at least I have sound.  With the help of a friend and the instructions found here:  

[https://help.ubuntu.com/community/SoundTroubleshooting#Having%20sound%20issues%20with%20HP%20dvx%20laptop](https://help.ubuntu.com/community/SoundTroubleshooting#Having%20sound%20issues%20with%20HP%20dvx%20laptop)

I was able to get it working.

These instructions worked under Ubuntu 9.04.  I'm assuming that they will work for Kubuntu as well:

1.  Make sure the patch application is installed.  Open a terminal window and type:  

[FONT=Fixedsys]sudo apt-get install patch[/FONT]

2.  Type in the following commands in your terminal window:

[FONT=Fixedsys]cd ~
mkdir src
cd src
mkdir alsa
cd alsa
wget [ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz)
tar -xvpf alsa-driver-snapshot.tar.gz
cd alsa-driver
./configure
sudo make (if you get errors DO NOT TYPE THE NEXT LINE.  Stop here)
sudo make install-modules[/FONT]

3.  The next step is to edit your alsa-base.conf file.  Type into your terminal window:

[FONT=Fixedsys]sudo gedit /etc/modprobe.d/alsa-base.conf[/FONT]

gedit is the text editor I use.  You can substitute in vi, vim or whatever one you prefer to use.  Also, if the file is empty, try using the above command and drop the .conf from the end.

4.  Add the following line to the bottom of the file:

[FONT=Fixedsys]options snd_hda_intel model=dell-m4-1 enable_msi=1[/FONT]

I know the model is wrong (the instructions specify hp-dv5), but it's the only option I found that gives 5.1 sound.

5.  Finally reboot your system and if all goes well, you should have sound, though your headphones most likely will not work.  Anyone know how to fix that problem?

Good luck.

---

### Post by N0L3R on 2009-09-30
Thanks you`re a genius. Thanks for your solution it worked seemlessly. :D

---

### Post by demodokos on 2009-10-13
I have an HP Pavillion dv7 and have just installed Jaunty.  I have no sound.  It recognizes the cards and the sound isn't muted (I dual boot and the sound works fine in Vista).  I've searched the forum all day and am about to punt on this.  I've tried all the code adds I can find list here, and none have worked.  Any suggestions?   Thanks.

---

