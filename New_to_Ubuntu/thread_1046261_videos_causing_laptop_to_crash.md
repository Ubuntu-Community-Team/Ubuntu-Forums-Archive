---
title: "videos causing laptop to crash"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by thestretchman on 2009-01-21
G'day

I am an Ubuntu virgin, I have only been turned from the Dark Side in the past 2-3days and I am having problems with shop bought DVD's and wmv files. This is all I have tried so far, so it may be others.When I try to open the media my laptop crashes/freezes, requiring a hard reboot. I thought I had installed VLC (per the instructions given to me by the person who turned me to Linux) and uninstalled Totem. When the program opens I don't see any reference to VLC, just Mplayer. I have tried to uninstal Mplayer and uninstal/reinstal VLC (via applications&#5171;add/remove) but apparently I can't, or I am not doing it right.

I am using Ubuntu 8.04 LTS. I know where the terminal is, I know how to copy paste.

I have the feeling I am still thinking windows though and still haven't quite grasped the Linux.

The instructions given to me are :

Install all proprietary codecs and software in order to play and stream media...

-Copy and paste the following into Terminal:

sudo apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

You will be asked to accept the License Agreement (EULA) to install Java.  Press TAB and ENTER to accept.

Step Three:  Assign MPlayer to stream media...

Copy and paste the following into Terminal:

sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-plugin-vlc totem-mozilla xine-plugin

and then this:

sudo apt-get install mplayer mozilla-mplayer

IMPORTANT:  Open the main MPlayer application (Applications > Sound and Media > MPlayer Movie Player) after installing it for the first time, this will then cause it to create it's default folder in your home directory. Also, please navigate to "Preferences > Audio" in MPlayer, and make sure the "Enable Software Mixer" option is ticked.

Next, you have to adjust your Mplayer config file:

gksudo gedit /etc/mplayerplug-in.conf

The file will open.  Delete EVERYTHING in the file and replace with the following:

download=1
cachesize=1024
cache-percent=25
keep-download=0
dload-dir=$HOME
noembed=0
autoplay=1
enable-wmp=1
enable-qt=1
enable-rm=1
enable-gmp=1
enable-dvx=1
enable-mpeg=1
enable-mp3=1
enable-midi=0
enable-pls=1
enable-ogg=1
enable-smil=1
enable-helix=1
nomediacache=0
nopauseonhide=1
black-background=1
rtsp-use-http=0
rtsp-use-tcp=0

Click SAVE and then CLOSE.

Install the software necessary to Play, Rip and Burn Proprietary DVDs...

Copy and paste the following into Terminal:

sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 vlc

Now, change the default DVD player from Totem Media (the player included with Ubuntu) with VLC (which is a better, lighter, more reliable player).  Copy the following into Terminal:

gksudo gedit /etc/gnome/defaults.list

This will bring up a text file of your default programs.  Press Ctrl+F and search for "x-content/video", then change the "totem.desktop" entries to "vlc.desktop". Save and close the file

The next bit is a little detailed:

Next, navigate to "Places > Computer > Edit > Preferences > Media > DVD Video", and make sure VLC is selected, then test whether automatic launch and playback with VLC works for you by inserting a DVD. If playback doesn't work properly, navigate to "Video > Deinterlace" within VLC and select mode "Blend". If that still doesn't solve your issue, or you just want more features enabled upon launch (such as fullscreen upon launch), follow the intructions in the next paragraph.

Right-click on "Applications" in the top panel and select "Edit Menus" to open the default menu editor. Navigate down to "Sound & Video" in the left pane and click on it to show all those applications in the pane to the right. Scroll down the list of applications displayed until you see "VLC media player", right-click on it, then click on "Properties" in the context menu to open "Launcher Properties", and change the launch command from "wxvlc %F" to:

vlc --volume 512 --fullscreen %m

DVD Ripping:

You can rip DVDs from the desktop, but DVDRIP is a more powerful ripper.  To install, paste the following into Terminal:

sudo apt-get install dvdrip

Basic burning of DVDs can be accomplished by right-clicking on an ISO image and then selecting the "Write to Disc" option in the context menu. If you want to author and burn DVDs for use in standard DVD players, then your best bet is to install Tovid, DeVeDe, and Avidemux. Tovid is an all-in-one video authoring suite with a GUI in early devolopement, DeVeDe is another popular DVD authoring application, and Avidemux is a very useful video editing application. Experiment with both video authoring applications to see which suits your needs the most:

sudo apt-get install avidemux devede todiscgui tovidgui

What else would you need to know? 

Thanks 

Stretch

---

### Post by thestretchman on 2009-01-21
After a bit more looking(yes I did do a search before I posted, just didn't look at the right things apparently) I realised I have a Dell Studio Laptop, and there seems to be problems with these & Ubuntu. Should I give up and head back to vista or is there a solution? I get black screen and everything freezes.

Stretch

---

### Post by thestretchman on 2009-01-21
Still looking for help

---

### Post by handydan918 on 2009-01-21
How about posting the output of ```
lspci
``` 
Often, blackscreen/freezing issues are a result of driver installation issues. lspci will show us what you got.

---

### Post by thestretchman on 2009-01-21
Thankyou very much for the reply. I have as suggested. I hope this makes sense to someone.




dad@dad-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Intel Corporation Unknown device 4232
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
dad@dad-laptop:~$

---

### Post by handydan918 on 2009-01-21
Well, the operative entry seems to be 
```
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

I don't have any knowledge of that chipset, but I do know that Intel supports it's graphics chips with open source drivers better than most manufacturers. [Here is a link to their driver download page.]("http://intellinuxgraphics.org/download.html")

If you do ```
lsmod | grep -i intel
```
Perhaps you can discern which driver is loaded and either reinstall or look for a better one.

---

### Post by thestretchman on 2009-01-22
I have fixed problem by upgrading to 8.10.

Thanks to HandyDan for taking the time to reply.

Stretch

---

