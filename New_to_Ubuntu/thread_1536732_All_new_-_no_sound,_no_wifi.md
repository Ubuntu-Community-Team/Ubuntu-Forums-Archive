---
title: "All new - no sound, no wifi"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by RasmusUb on 2010-07-22
I got myself an ASUS eee pc PX and set up the netbook remix on it after watching a few clips on it. Seemed like a nice thing, and I am not a fan of windows.

So far, Ubuntu seems bloody lovely. It has ready access to all hte programs I want and it seems to run really very very well.
As soon as I connected it it updated a bunch of components, I installed java, skype and so on, and it is running along like anything.

I guess I am a bit dense, but two things are not working; wifi internet and sound.

I heard sound in the internal speakers, but when I plugged in the headphones the machine went quiet, and when I pulled it out there is still no music speakers. Did I do something wrong and how can I fix it?
Seems the mic is out too.
The speakers work just fine when I use the dualboot to test them in windows.

So that's one, and bear in mind that I know nothing about this stuff, so please don't spout techno at me without some sort of walkthrough or tutorial-link, pretty please?

The second is the wifi internet. I have a router set up which my phone can access, but the wifi on the ubuntu just wants me to manually enter a bunch of details I don't know. Does it not scan for connections like the windows client would?
Is there some kind of limitation on what kind of network I can use? I am running a WAP-PSK with 802.11g enabled. The phone gets this, so the network is clearly responding, but the netbook isn't getting it.
What can I do about it?


Thank you for helping me out with this - I am sure looking forward to running this little netbook and Ubuntu!

---

### Post by mapes12 on 2010-07-22
Sound - Applications>Accessories>Terminal ```
alsamixer
```and see if you can configure it to work from the GUI that pops up.

Wifi - In Terminal again and type ```
sudo lshw -C network
```and post the output back here.

---

### Post by RasmusUb on 2010-07-23
> **mapes12 said:**
> Sound - Applications>Accessories>Terminal ```
alsamixer
```and see if you can configure it to work from the GUI that pops up.

Yes, it puts out the soundcard (HDA Intel), Chip (Realtek ALC269) and two more rows then a graphic with grour columns with "master", "speaker", "PCM" and "Beep". Master and PCM are at 100%, Speaker and beep at 0%


> 
Wifi - In Terminal again and type ```
sudo lshw -C network
```and post the output back here.It came out like so...

```
*-network UNCLAIMED     

       description: Network controller

       product: Atheros Communications Inc.

       vendor: Atheros Communications Inc.

       physical id: 0

       bus info: pci@0000:02:00.0

       version: 01

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress bus_master cap_list

       configuration: latency=0

       resources: memory:fbff0000-fbffffff

  *-network

       description: Ethernet interface

       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter

       vendor: Atheros Communications

       physical id: 0

       bus info: pci@0000:01:00.0

       logical name: eth0

       version: c0

       serial: 48:5b:39:40:af:71

       capacity: 100MB/s

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation

        configuration: autonegotiation=on broadcast=yes driver=atl1c  driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes  port=twisted pair

       resources: irq:29 memory:f7fc0000-f7ffffff ioport:ec00(size=128)
```



Thank you for your help!

Edit: Shocking twist!
After fidgeting about with those four columns I now have sound on my speakers, but when I plug my headset into the RCA-plug I get nothing, the speakers mute (and unmute when I pul the plug out again) but the headphones are dead. The mic seesm to be out or turned down WAY low so I can only hear a whisper of the stuff I tried recording on the voice recorder. I cannot seem to get that to work even though soundcontrols are putting the mic at 100%

---

### Post by matrixblue on 2010-07-23
Which version of Ubuntu Netbook Remix are you using?

---

### Post by RasmusUb on 2010-07-23
> **matrixblue said:**
> Which version of Ubuntu Netbook Remix are you using?
The one I recently downloaded... so it has to be 10.04

---

### Post by matrixblue on 2010-07-23
> **RasmusUb said:**
> The one I recently downloaded... so it has to be 10.04

Try connecting it via ethernet and run:

sudo apt-get update
 Then
sudo apt-get dist-upgrade

Sometimes issues like this are solved with an update

---

### Post by mapes12 on 2010-07-23
Wifi:-

Have a look at this: [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

### Post by RasmusUb on 2010-07-23
> **matrixblue said:**
> Try connecting it via ethernet and run:

sudo apt-get update
 Then
sudo apt-get dist-upgrade

Sometimes issues like this are solved with an update

I did that and when I unhooked the ethernet I got an "identification of networks has been deactivated".
That's new. Where would I reactivate this "identification of networks"?

> **mapes12 said:**
> Wifi:-

Have a look at this: [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

I tried, but the package it wants depends on another package which depends on another package and so on so I can't manage it. Is there a setting to let it do it itself?

Edit: Tried the instructions found here
[http://www.sampletheweb.com/2007/12/09/ubuntu-on-the-asus-eee-pc-part-1-or-how-to-run-a-functional-ubuntu-install-off-a-usb-drive/](http://www.sampletheweb.com/2007/12/09/ubuntu-on-the-asus-eee-pc-part-1-or-how-to-run-a-functional-ubuntu-install-off-a-usb-drive/)   step 5
but sadly the wget could not connect to madwifi.org so that failed on the second line.


When I look at System>Administration>hardwaredrivers I get an empty window. I am guessing there is supposed to be a driver for my wireless card there. Any idea how I get that?

I looked at [http://code.google.com/p/eee-ubuntu-support/](http://code.google.com/p/eee-ubuntu-support/) too, but it does not seem to be maintained. Can I still use it and if so, how?
Sorry for the abundance of queries, but I am a curious little beast.

---

### Post by matrixblue on 2010-07-23
I'm unclear. Did the update complete downloading and installing?

---

### Post by RasmusUb on 2010-07-23
> **matrixblue said:**
> I'm unclear. Did the update complete downloading and installing?

As far as I can tell it did. There was a lot of package-text that rushed passed on the terminal and none said "failed" so I have to assume it did. Is there a way to determine if the updates are installed correctly or if there is something that remains to be done?

I am beginning to see why people like Linux - the help I am getting here is outstanding, and fast too!

---

### Post by matrixblue on 2010-07-23
Run the **sudo apt-get dist-upgrade** again and restart the PC.

---

### Post by lidex on 2010-07-24
For your audio try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by lidex on 2010-07-24
Microphone.
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then use pulseaudio volume control (pavucontrol) or 'Sound Preferences' to select and unmute your mic in 'Input Devices' tab.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

---

### Post by RasmusUb on 2010-07-24
> **matrixblue said:**
> Run the **sudo apt-get dist-upgrade** again and restart the PC.

I got 0 upgraded, 0 to reinstall, 0 to remove and 3 that could not be upgraded (linux-generic, linux-headers-generic and linux-image-generic)

> **lidex said:**
> For your audio try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
```
That file was blank. I am guessing it is not supposed to be as "the bottom" means normally something is above it?

> **lidex said:**
> Microphone.
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```Then use pulseaudio  volume control (pavucontrol) or 'Sound Preferences' to select and unmute  your mic in 'Input Devices' tab.

Did that, and the "capture" (I am guessing that is the mic) was at the top already. Only the "beep" (whatever that is) was at the bottom

I am still just getting "add wireless network" and no "these are the wireless networks that are available to you". Is there such a function in this version, or am I barking up the wrong tree?

Speakers now work (thanks guys!) but the headphones are still out, and the best I can get out of the mic is on the soundrecorder, and it is a vague hissing, nothing more. Skype won't pick up any sound on the mic at all.

Edit: So I went through the directions found here [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros#KurianAlternative](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros#KurianAlternative)
That has as far as I can tell changed nothing at all.
I do get a warning stating that "Identification of network services disabled. Your current network has a .local-domain which is not recommended and not compatible with the avahi-identifier for network services. This service has been disabled."  What can I do to get this network identification up and running again?

Edit again: I installed a "wicd" as per the document above, and while I get that running I found two things. First of all, it finds no networks at all (sitting next to router my phone can find just fine) and second there is something odd about the settings, displaying a blank row for "wireless interface" but "eth0" for "wired interface"

---

