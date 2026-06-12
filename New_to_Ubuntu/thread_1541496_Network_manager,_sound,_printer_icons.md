---
title: "Network manager, sound, printer icons"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by nooshin on 2010-07-29
Hi, 
I am a new user of ubuntu, till two months ago I'm using it.
Actually I can not see Network manager , sound and printer icons any more.
I searched a lot in the forums, but all were the same as the people said. I have indicator applet, but it does not show these icons.
after that I made some changes on startup application, and now it got worst.
when I start my computer, it took a long time to come up and then when I log in to the os, first it stop for a minute then one terminal opens and all the up an down panel bar become invisible, after that these bars appear but without these icons.

I am really sad of this. :sad:please help me in this regard.

Many thanks.

---

### Post by nooshin on 2010-07-29
Hi, 
I am a new user of ubuntu, till two months ago I'm using it.
Actually I can not see Network manager , sound and printer icons any more.
I searched a lot in the forums, but all were the same as the people  said. I have indicator applet, but it does not show these icons.
after that I made some changes on startup application, and now it got worst.
when I start my computer, it took a long time to come up and then when I  log in to the os, first it stop for a minute then one terminal opens  and all the up an down panel bar become invisible, after that these bars  appear but without these icons.

I am really sad of this. :sad:please help me in this regard.

Many thanks.

---

### Post by chopinhauer on 2010-07-29
> **nooshin said:**
> 
Actually I can not see Network manager , sound and printer icons any more.


Actually Network Manager and Printer live in the Notification Area, so check if you have it.

To force the start of the sound applet run:
```
/usr/lib/indicator-sound/indicator-sound-service
```
while Network Manager can be added with:
```
nm-applet
```

---

### Post by nooshin on 2010-07-29
Thanks, 
when I entered 
nm-applet 
it returned:
** (nm-applet:3157): DEBUG: old state indicates that this was not a disconnect 0
and stop then I have to push ^c to get out.

for the sound :
/usr/lib/indicator-sound/indicator-sound-servicenooshin@nooshin-desktop:~$ /usr/lib/indicator-sound/indicator-sound-service
bash: /usr/lib/indicator-sound/indicator-sound-service: No such file or directory

and I have notification area, but when I add it to the panel nothing happen but just a separator added to the panel.

is there any way to define notification area?

thanks,

---

### Post by chopinhauer on 2010-07-29
> **nooshin said:**
> 
** (nm-applet:3157): DEBUG: old state indicates that this was not a disconnect 0
and stop then I have to push ^c to get out.


Add an ampersand (&) to force it into background:
```
nm-applet &
```

for the sound :
> **nooshin said:**
> 
/usr/lib/indicator-sound/indicator-sound-servicenooshin@nooshin-desktop:~$ /usr/lib/indicator-sound/indicator-sound-service
bash: /usr/lib/indicator-sound/indicator-sound-service: No such file or directory


Reinstall **indicator-sound**:
```
sudo apt-get --reinstall install indicator-sound
```

---

### Post by nooshin on 2010-07-29
this is what I get for the sound:(

nooshin@nooshin-desktop:~$ sudo apt-get --reinstall install indicator-sound
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-packagekit libpackagekit-qt-12 kpackagekit
  libboost-program-options1.40.0 libakonadiprivate1 kdepimlibs-data
  software-properties-kde gstreamer0.10-gnomevfs install-package packagekit
  gdebi-kde kdepimlibs5 update-manager-kde libpackagekit-glib2-12 python-kde4
  packagekit-backend-apt
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  indicator-sound
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 24.8kB of archives.
After this operation, 147kB of additional disk space will be used.
Get:1 [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) lucid-updates/main indicator-sound 0.2.3-0ubuntu1 [24.8kB]
Fetched 24.8kB in 0s (371kB/s)     
Selecting previously deselected package indicator-sound.
(Reading database ... 216401 files and directories currently installed.)
Unpacking indicator-sound (from .../indicator-sound_0.2.3-0ubuntu1_amd64.deb) ...
Setting up indicator-sound (0.2.3-0ubuntu1) ...


nooshin@nooshin-desktop:~$ /usr/lib/indicator-sound/indicator-sound-service
** (process:3802): DEBUG: Root ID: 1
** (process:3802): DEBUG: update pa state with state 0, availability of 0, mute value of 0 and a volume percent is 0.000000
** (process:3802): DEBUG: Building new Slider Menu Item
** (process:3802): DEBUG: !!!!!!**in the rebuild sound menu - slider active = 0
** (process:3802): DEBUG: Emitting signal: SINK_AVAILABILITY_UPDATE, with value 0
** (process:3802): DEBUG: Emitting signal: SINK_VOLUME_UPDATE, with sink_volme 0.000000
** (process:3802): DEBUG: Emitting signal: SINK_MUTE_UPDATE, with sink mute 0
** (process:3802): DEBUG: connecting - waiting for the server to become available
** (process:3802): DEBUG: authorizing
** (process:3802): DEBUG: context setting name
** (process:3802): DEBUG: PA daemon is ready
** (process:3802): DEBUG: server info callback
** (process:3802): DEBUG: Just set the default sink index to 1

** (process:3802): WARNING **: Default Sink info callback failure
** (process:3802): DEBUG: About to add an item to our hash
** (process:3802): DEBUG: After adding an item to our hash
** (process:3802): DEBUG: About to add an item to our hash
** (process:3802): DEBUG: After adding an item to our hash
** (process:3802): DEBUG: About to test for to see if the available sink is null - s->name = alsa_output.pci-0000_00_1b.0.analog-stereo
** (process:3802): DEBUG: PA_Manager ->  determine_sink_availability: 1
** (process:3802): DEBUG: software volume = 100.000000
** (process:3802): DEBUG: update pa state with state 1, availability of 1, mute value of 0 and a volume percent is 100.000000
** (process:3802): DEBUG: in the refresh menu method
** (process:3802): DEBUG: Emitting signal: SINK_AVAILABILITY_UPDATE, with value 1
** (process:3802): DEBUG: Emitting signal: SINK_VOLUME_UPDATE, with sink_volme 100.000000
** (process:3802): DEBUG: Emitting signal: SINK_MUTE_UPDATE, with sink mute 0

(process:3802): libindicator-WARNING **: No watchers, service timing out.
** (process:3802): DEBUG: Service shutdown !
** (process:3802): DEBUG: freeing the pulse context
** (process:3802): DEBUG: I just closed communication with Pulse

and for the nm-applet nothing appears again !!!:mad::(

now even I missed the panel which I could switch between 4 windows, they disappeared also:confused:
thanks a lot

---

### Post by nooshin on 2010-07-29
sound is now appear,,,many thanks....

but still I have no network manager icon, and the icon related to the 4 different desktops or sessions which are offered by ubuntu.:(

I have also one extra and unwanted icon: "universal access preferences". what should I do to disappear it?

thanks and please help me!!

---

### Post by dineshs on 2010-07-29
Did you try this?
Right click on the top panel-click add to panel-select notification area -click add

---

### Post by hhh on 2010-07-29
Set your startup applications back to what they were, that's what is causing the slow startup. Then reset your panels back to default...
[http://www.liberiangeek.net/2010/07/restorerecover-ubuntu-10-04-lucid-lynx-desktop-panels/](http://www.liberiangeek.net/2010/07/restorerecover-ubuntu-10-04-lucid-lynx-desktop-panels/)

---

### Post by overdrank on 2010-07-29
Hi and welcome, please do not create multiple threads on the same issue. Threads merged and moved to Absolute Beginner Talk :)

---

