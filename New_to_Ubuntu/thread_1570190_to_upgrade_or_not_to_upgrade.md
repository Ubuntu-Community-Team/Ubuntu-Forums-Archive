---
title: "to upgrade or not to upgrade?"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by Gwilmouski on 2010-09-07
I am running Ubuntu 8.04 LTS and am considering an upgrade to 10.04 LTS. I have already downloaded and burned a CD, but would like to ask some questions before commiting to the upgrade. I keep reading posts about upgrade failures so would a fresh install with the CD vs. an upgrade through the update manager be a better idea? This is a newbie question, but if I decide to go with the update manager does the upgrade wipe all of your previous data? I have backed up all my pictures and documents but would I lose everything else I have downloaded? There are probably questions I don't even know to ask to feel free to jump in with any advice. Thank you.

---

### Post by andrewthomas on 2010-09-07
> **Gwilmouski said:**
>  This is a newbie question, but if I decide to go with the update manager does the up upgrade wipe all of your previous data?
No, not if it works.> **Gwilmouski said:**
> 
 I have backed up all my pictures and documents but would I lose everything else I have downloaded? Only with a fresh install.  Which in my opinion is the way to go.

---

### Post by howefield on 2010-09-07
My preference is for clean installs, but the supported method is upgrading.

This should work perfectly and retain all your data and settings. It is certainly the easier option. 

As long as you have all your valuable data backed up, the worst that can happen with a failed upgrade is that you have to do a fresh install... nothing too serious :)

If you have the disk space, you might consider imaging your disk, (with something like Clonezilla) if push comes to shove, you can be back where you started in a short time.

---

### Post by flick on 2010-09-07
I prefer and always use fresh installs. I keep my home directory on a separate partition, makes the whole process easier. 

Some good info :

[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by oldsoundguy on 2010-09-07
I upgraded 4 machines here.  Not a problem.  BUT to keep safe .. copy your home folder to a USB Flash at least .. then IF your upgrade goes south and you have to go fresh install from the CD, you have everything you need on that flash drive .. just drag the contents back after the install.

---

### Post by uRock on 2010-09-07
I would like to chime in with an experience I have had with going from pre10.04 releases to 10.04 without formatting /home has brought nothing but headaches with themes and such.

This may not be the case with going from 8.04 to 10.04 as I have only transitioned from 9.10 on multiple machines and have had the same outcome every time.

---

### Post by bodhi.zazen on 2010-09-07
> **Gwilmouski said:**
> I am running Ubuntu 8.04 LTS and am considering an upgrade to 10.04 LTS. I have already downloaded and burned a CD, but would like to ask some questions before commiting to the upgrade. I keep reading posts about upgrade failures so would a fresh install with the CD vs. an upgrade through the update manager be a better idea? This is a newbie question, but if I decide to go with the update manager does the upgrade wipe all of your previous data? I have backed up all my pictures and documents but would I lose everything else I have downloaded? There are probably questions I don't even know to ask to feel free to jump in with any advice. Thank you.

I upgrade as much as possible, but I am perhaps more comfortable then most at fixing problems.

At this point, the upgrade form 8.04 -> 10.04 should go as smooth as possible. Back up your data first, then upgrade. If you run into problems post back. If the problems can not be solved, do a fresh install of 10.04 and restore your data. If that fails, fresh install of 8.04 and restore your data.

Nothing to loose, IMO, from trying the upgrade.

---

### Post by wojox on 2010-09-07
Have you used your Live-CD and the "Try without installing" option to see how things work?

---

### Post by ssulaco on 2010-09-07
When the time is right,I will also opt for the upgrade....I read somewhere,it was highly recommended to purge your PPA's before upgrading,is there any truth to that?

---

### Post by Sef on 2010-09-07
If you upgrade, remove all the proprietary drivers that you installed before upgrading.  If there are problems, that's often the cause of them.

---

### Post by Gwilmouski on 2010-09-09
Yes, I tried the 'live' version of the CD and liked it, I also used my CD to install 10.04 LTS on a friends computer who wanted tp try Ubuntu so I know its a good CD.  I am just worried about losing all my settings and not knowing how to get them back.

---

### Post by SpockVulcan on 2010-09-09
The best way is to use MintBackup. [http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html](http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html)

Install this backup tool on your existing ubuntu install and then backup both home folder and software selection to removable media.

Install it on your new install and then just restore your software selection and home folder.

---

### Post by quadproc on 2010-09-09
> **Sef said:**
> If you upgrade, remove all the proprietary drivers that you installed before upgrading.
Yes, I ran into that problem in a very serious way on the 8.10 to 9.04 transition.  I ended up with a black display; totally dead.  I eventually (after two very long days) found that I had to uninstall the fglrx driver and reinstall it to get things to work.  Better to uninstall it before the upgrade; that way, you can at least use the system's normal tools to reinstall the driver.  I had similar but less severe problems on the 9.04 -> 9.10 transition because I forgot to uninstall first.

quadproc

---

### Post by jmszr on 2010-09-09
@SpockVulcan,

 The PPA you have listed is only for Karmic, Lucid, and Maverick. There is a MintBackup_1.62_all.deb that installs in 8.04 and is then listed under System > Administration > mintBackup. It is available here: [http://packages.linuxmint.com/pool/main/m/mintbackup/](http://packages.linuxmint.com/pool/main/m/mintbackup/) . How it compares with the new version I do not know.

---

### Post by Gwilmouski on 2010-09-11
I am not exactly sure what a fglrx driver is, the only proprietary drivers I found so far are the Nvidia drivers. Should I disable this before an upgrade?

---

### Post by bodhi.zazen on 2010-09-11
> **Gwilmouski said:**
> I am not exactly sure what a fglrx driver is, the only proprietary drivers I found so far are the Nvidia drivers. Should I disable this before an upgrade?

fglrx are ATI drivers. Yes disable the nvidia driver, upgrade, then re-install or re-enable the nvidia driver.

---

### Post by borth92 on 2010-09-11
i would try upgrading since the worst thing that can happen is it skrews up and you do a clean install anyways

---

### Post by Gwilmouski on 2010-09-19
Well, I finally plucked up the courage to try the upgrade an here's what happened. I copied my home folder to USB flash, disabled the proprietary drivers, cleaned out the trash and pressed 'upgrade'. All went along fine for about four hours then when it got down to installing upgrades it hit this:
 
Find: File system loop detected; ' etc/skel/wine/dosdevices/2:/sys/devices/platform/pcspkr/input/input6/subsystem/input2/device/driver/1-2:1.0/subsystem/drivers/usblp/2-1:1.10/usb_endpoint/usbdev2.7_ep01/subsystem/usbdev2.7_ep00/device/usb2/2-0:1.0/driver/1-0:0'
 
it repeats this over and over with the final entry having 'system is' then a box at the end. It is now just sitting there idling and has been for 7 hours. Anything I can do to jumpstart the process? Should I just conceed I have a failed upgrade and break out the disc?
I don't know if this helps but here's my system info:
custom built, Athlon AMD X 2 2.2 GHz, 64 bit, 160 gb SATA 3.0 gbs hard drive, 1024 mb DDR2, Nvidia Geforce 7200 gs.
Any suggestions/help would be appreciated. Thanks in advance.

---

### Post by luceerose on 2010-09-19
I always do a fresh install. I have 4 computers so I've installed that many times over the last few years, I decided to start keeping an office document listing all additional packages & programs for me to install, settings to change, etc after installation is finished.
As far as backups go, I just keep a copy of my entire home folder on a second (& third) hard drive. The only other thing I need to backup before re-install is my hidden thunderbird/icedove folder.

Funly enough, your computer sounds almost identical to the 2.2Ghz X2 I just installed Debian Sid on.
I've overclocked mine to 2.6Ghz.
If yours is a locked Brisbane core, I can give you some advice on what settings it might like if you're thinking of overclocking.

---

### Post by Gwilmouski on 2010-09-19
Thanks, larsenguitars
I am not quite sure what kind of core I have being a newbie, guess I should find out. anyway exellent idea about keeping a document with package info to re-install after you've upgraded your system. I have not kept a document but what I have done is move all important info to my other computers, made backup discs, and copied my home folder to flash drive. You apparently are light years beyond my capabilities right now if I can't accomplish a upgrade without disaster I think over-clocking is way in my future.

---

### Post by bodhi.zazen on 2010-09-19
> **larsenguitars said:**
> I always do a fresh install. I have 4 computers so I've installed that many times over the last few years, I decided to start keeping an office document listing all additional packages & programs for me to install, settings to change, etc after installation is finished.
As far as backups go, I just keep a copy of my entire home folder on a second (& third) hard drive. The only other thing I need to backup before re-install is my hidden thunderbird/icedove folder.

Funly enough, your computer sounds almost identical to the 2.2Ghz X2 I just installed Debian Sid on.
I've overclocked mine to 2.6Ghz.
If yours is a locked Brisbane core, I can give you some advice on what settings it might like if you're thinking of overclocking.

You could probably convert that list of post-install items into a bash script.

---

### Post by luceerose on 2010-09-19
> **bodhi.zazen said:**
> You could probably convert that list of post-install items into a bash script.

Not much point. It's all fairly simple.
This one's for Debian, (I haven't worked on my Ubuntu list for a while);
```

Install keyring for debian-multimedia.org;
wget http://www.debian-multimedia.org/pool/main/d/debian-multimedia-keyring/debian-multimedia-keyring_2008.10.16_all.deb
Then;
sudo dpkg -i debian-multimedia-keyring_2008.10.16_all.deb

Install keyring for Google Chrome;
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -

gksu gedit /etc/apt/sources.list

deb http://mirror.internode.on.net/pub/debian/ squeeze main non-free contrib 
deb-src http://mirror.internode.on.net/pub/debian/ squeeze main non-free contrib 
deb http://mirror.internode.on.net/pub/debian/ squeeze-proposed-updates main non-free contrib 
deb-src http://mirror.internode.on.net/pub/debian/ squeeze-proposed-updates main non-free contrib 
deb http://www.debian-multimedia.org sid main non-free 
deb-src http://www.debian-multimedia.org sid main
#Google Chrome
deb http://dl.google.com/linux/deb/ stable non-free main 
deb http://dl.google.com/linux/deb/ testing non-free main

Install;

apt-get install libdvdcss2 w64codecs gstreamer0.10-lame flashplayer-mozilla gstreamer0.10-plugins-ugly gparted icedove vlc mozilla-plugin-vlc amarok libxine1-all-plugins compiz compizconfig-settings-manager compiz-fusion-plugins-extra simple-scan nvidia-glx nvidia-settings nvidia-xconfig nvidia-glx-ia32 compiz-fusion-plugins-main libgutenprintui2-1 devede photoprint panflute-applet panflute-daemon glunarclock google-chrome-beta ibus ibus-anthy gettext qtscript-tools

To ensure openoffice has Quickstarter;
openoffice.org-gtk

For Japanese Fonts;
apt-get install ttf-kochi-gothic-naga10  ttf-kochi-mincho-naga10 ttf-sazanami-gothic ttf-sazanami-mincho xfonts-intl-japanese xfonts-intl-japanese-big 

For Chinese Fonts;
apt-get install ttf-arphic-uming ttf-wqy-zenhei

Mp3 encoding settings through sound-juicer;

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 quality=3 preset=standard vbr-max-bitrate=320 ! Id3v2mux

Google Earth;
sudo apt-get install lib32nss-mdns googleearth-package
sudo make-googleearth-package –force
sudo dpkg -i <.deb file resulting from previous command>

Compiz Settings;

Open Configuration Editor (gconf-editor)
apps >>> compiz >>> general >>> screen0 >>> options
& change 'hsize' to '4'

Open CompizConfig Settings Manager
In General Section
General Options >>> Desktop Size
& change 'Horizontal Virtual Size' to '4'

In Desktop Section
- Tick 'Desktop Cube' & 'Rotate Cube'

Rotate Cube >>> Bindings >>> Rotate Cube >>> Initiate
change to button '2' ( or whatever button corresponds to wheel-click)

Initiate Compiz – First time Run
Alt+F2 & Run compiz to run first time to test.
After that, it needs to be added to Startup Applications for it to start on every login.

Ugly Thumbnail Borders;
delete thumbnail borders from /usr/share/pixmaps/nautilus
Log out & Back in to see changes

In the Interest of Keeping a Clean System;
Add the following to the end of the Shortcuts/Menu entries for Google Chrome & Chromium
--disk-cache-size=1 --media-cache-size=1

```

---

### Post by manny43 on 2010-09-19
Hello friends,

I'm running Ubuntu 9.10 for almost 8 months already and am going to stay with it until 9.10 is no longer supported because as of now i really dont see the benefit of upgrading to 10.04 that might change in the 
future if i buy some new hardware and it wont work with 9.10. I .Since i'm new to Linux my first OS is 9.10
and dont know much about 8.04 version maybe people who used 8.04 can say if 9.10 version is a better
OS and it was worth for them upgrading.

---

### Post by Gwilmouski on 2010-09-20
> **manny43 said:**
> Hello friends,

I'm running Ubuntu 9.10 for almost 8 months already and am going to stay with it until 9.10 is no longer supported because as of now i really dont see the benefit of upgrading to 10.04 that might change in the 
future if i buy some new hardware and it wont work with 9.10. I .Since i'm new to Linux my first OS is 9.10
and dont know much about 8.04 version maybe people who used 8.04 can say if 9.10 version is a better
OS and it was worth for them upgrading.
Manny, I agree with you change for changes sake is pointless. However I opted to upgrade, even though I loved my 8.04 LTS because there were programs I needed to use which were simply not compatible with Hardy. We have many friends in the UK we wanted to Skype and I was forced to use Windows (gag). This was unacceptable to a Ubuntu devotee, hence 10.04 LTS.
Just to keep everyone updated after my post yesterday,  The upgrade failed apparently because of dependency issues that could not be worked out. I ran  sudo apt-get  --configure a  and it worked on the problem for 2 hours and then told me 'no can do'. I broke out the disk and installed 10.04 as a clean install. Here's the part I love about Ubuntu it offered to let me save on a portion of my hard drive the partial upgrade  so I could save all my downloaded music, and programs which are no longer available on 10.04. I LOVE UBUNTU !!!!

---

