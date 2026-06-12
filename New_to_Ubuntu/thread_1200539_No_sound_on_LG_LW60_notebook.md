---
title: "No sound on LG LW60 notebook"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by Linuxson25 on 2009-06-30
Hi everyone!! :)

Would just like to say firstly that I am absolutely ubuntufied with the new release!!!
Looks absolutely stunning!! I recently bought a Xenon AMD monster - Tri-core - and cant wait to take
Ubuntu for a test run on it....Would have wanted to try the 64bit version, but downloaded the 32bit so I could run it on my notebook as well. LOL

Anyway, talking of which....
I just finished installing Ubuntu on my LG notebook, and everything runs fine....including my Vodafone dongle that I had problems with in previous versions....THANK YOU!!!....except my sound doesnt seem to be.

I did a bit of the googling...lol....and came across a page that informs you on installing Debian package on a LG LW60 notebook....ect, ect.....
The guy mentions an alsa driver that you have to download, compile and what not....
He just forgets to add a download link....duh
Anyway, is there something minor that I am missing here?
Could it just be a small setting or something that I over looked?

Would appreciate any kind of input :)

PS:  System specs


00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
06:00.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:00.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:00.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)



Thank you

---

### Post by banoncom on 2009-06-30
Hi Linuxson25

I have just installed ubuntu 9.04 on a LW60 myself for a friend. Everything works great but not too sure about the sound.

Does this model of laptop have inbuilt speakers?

Haven't had a chance to ask him, however the sound works via the headphone socket no problems, I just don't know if it is meant to work on inbuilt speakers????

I am using the HDA Alsa mixer (default) This is via the volume control panel which can be accessed via the top panel on the right.

Also if you go to >System >Preferences >Sound under the Devices tag you should have everything set to Auto.

I have played with these settings to see if I could get the "Speakers" to work, alas no go (headphone socket works though).

Would be good to know if this thing has inbuilt speakers!

---

### Post by toejamfootball on 2009-07-25
It does have Inbuilt speakers, I am having the same problem.

---

### Post by tugalsan on 2009-10-30
Hello guys, I have LG S1 express dual. I have the same problem. 

In ubuntu 9.4 I can only use headphones.

After upgrading 9.10, I lost headphones also.

Then I search internet for forums, (I do not find again sorry); they adviced me to these:

sudo -i
sudo apt-get install libncurses5 libncurses5-dev xmlto patch
mkdir alsa
cd alsa

wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.21.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.21.tar.bz2)
tar -xf alsa-driver-1.0.21.tar.bz2
cd alsa-driver-1.0.21
./configure
make
sudo make install
cd ..

wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.21.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.21.tar.bz2)
tar -xf alsa-lib-1.0.21.tar.bz2
cd alsa-lib-1.0.21
./configure
make
sudo make install
cd ..

wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2)
tar -xf alsa-utils-1.0.20.tar.bz2
cd alsa-utils-1.0.20/
./configure
make
sudo make install
cd ..

sudo alsaconf
sudo echo -e "\noptions snd-hda-intel model=lg" >> /etc/modprobe.d/alsa-base.conf
alsamixer
speaker-test -c2


after doing that sound also did not work! Then in some other forum, some guy adviced me to change config files (which i do not remember where) to change line to sth like [Front] = ignore and some PCM think to ignore also. Then my sound works!!!!! in both, wheheter headphones or not :)

However i lost volume control. The very interesting think is that in gnome in sound harware i see nothing. but when i open a terminal and write "aslamixer" i can tune my sound in dos prompt :) that was very disturbing.

In addition to this, I add the kubuntu-desktop package to my ubuntu, I saw that i can tune my sound from taskbar in KDE, but not in gnome.

I wish someone that understand  these think really solve the problem and it comes with the an update

byz

---

### Post by tugalsan on 2009-10-30
i found some links about the upper stuff i wrote:

ref1: [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)
ref2: [http://ubuntuforums.org/showthread.php?t=1077335](http://ubuntuforums.org/showthread.php?t=1077335)

anyone has a solution. pls give a mail to [email]tugalsan@gmail.com[/email]

---

### Post by hopefulhelper on 2010-03-18
The answer to this thread is contained in it, but I just thought I'd add a simple and easy way for us newbies..

I also have a LG LW60 (using 9.10), this is what I did to get speakers and headphones working:

sudo gedit /etc/modprobe.d/alsa-base.conf

Comment out these two lines:

options snd-hda-intel power_save=10 power_save_controller=N

options snd-hda-intel model=all

And then add this one:

options snd-hda-intel probe_mask=1 model=minimal

Save and close, then:

sudo alsa force-reload

alsamixer 

(make sure everything is unmuted using 'm' hotkey)

speaker-test -c2

Thanks for all the previous posts, this is basically a summary from what worked for me from them.

Hope it helps someone :)

---

