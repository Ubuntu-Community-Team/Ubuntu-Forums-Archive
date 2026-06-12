---
title: "Wireless networks not detected in gnome/networkmanager"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by adaniels on 2007-01-09
Hi,

I've browsed through some 'doesn't detect wireless networks' post, but I didn't find this one. Sorry if I've missed it and double-posted.

Within gnome (network admin as well as gnu network manager) wireless networks aren't detected. In the network manager I can only select 'wired network'. However (and here comes the twist) I can scan for networks with iwlist.  

Does this sound familiar to anyone?

I'm currently using ubuntu edgy. The network adapter is a PCMI card.

```
arnold@arnold-laptop:~$ iwlist ra0 scanning
ra0       Scan completed :
          Cell 01 - Address: 00:30:BD:FB:2B:BA
                    Mode:Managed
                    ESSID:"Javeline_ap"
                    Encryption key:on
                    Channel:11
                    Quality:62/100  Signal level:-65 dBm  Noise level:-206 dBm
          Cell 02 - Address: 00:90:96:F8:4C:DB
                    Mode:Managed
                    ESSID:""
                    Encryption key:on
                    Channel:1
                    Quality:0/100  Signal level:-65 dBm  Noise level:-206 dBm
          Cell 03 - Address: 00:18:39:28:3F:AC
                    Mode:Managed
                    ESSID:"Amiko"
                    Encryption key:on
                    Channel:11
                    Quality:0/100  Signal level:-96 dBm  Noise level:-206 dBm
```

Thanks a lot,
Arnold

---

### Post by el-sio on 2007-01-10
Hello !

I am no guru but I read a lot of forums about wireless networking on edgy and I heard that there is a bug in edgy network manager that makes it "don't see" the wireless networks, it is not concidered as a blocking problems by the packets mainteners (or so I was told so don't hit me if it's not true) because some "easy" workaround exists.

One of the workarounds I found was to install "wifi-radar" which is a small GUI for wireless network configuration. You can hav it with a simple

```
sudo apt-get install wifi-radar
``` 

(or using Synaptics of course)
and it will automatically be added in your menu ( Applications -> Internet)

This program shows you the available networtks, their signal force and allows you to configure the connection to each of those networks.

It should work fine even if it doesn't seem to work very well with my Airport card (I'm running edgy on a ibook G4...)

Hope this will help ^ ^

---

### Post by emperon on 2007-01-10
it is wifi-radar, not wifiradar

---

### Post by adaniels on 2007-01-10
I've tried wifi-radar, but I don't like it. It doesn't switch well between wireless and wired connection.

Will updating to feisty solve the problem? If not, does a manual download/make of networkmanager and/or libnm solve this?

Arnold

---

### Post by emperon on 2007-01-11
Yes, it doesn't switch automatically. But still it is an improvement since it successfully preserves your settings within consecutive reboots within the same ESSID. 

For fiesty, remember it is at alpha stage, you are inviting a lot trouble for little benefit. I discourage you to do it before it is released (at least a beta release)

---

### Post by englert.james on 2007-01-12
I thought that running [code] iwlist scanning [code] returned the cached list of wireless ap's.  Running [code] sudo iwlist scanning [code] returns the freshly scanned wireless ap's.  I could be completely wrong though, let me know.

---

### Post by adaniels on 2007-02-01
The problem seems to be solved with linux kernel version 2.6.17-10. (was broken with 2.6.17-6)

---

### Post by frick on 2007-02-01
Greetings,

I have been working on my own WIFI issues for several weeks now but I am still new to Ubuntu 6.10.

As far as I am concerned there are no easy fixes with Edgy and WIFI.

What I have discovered is that you must turn off all WEP or WPA on your wireless router to get Edgy to connect.

I am using an older  Dell Lattitiude 750 meghertz, with a 20 gig hard drive and an Orinoco Gold Pmcia wifi card to a d-link router. The Orinoco worked right out of the box with Edgy. 

But I have tried every fix that I can find and have crashed all the Edgy networking to the point of two re-installs. (mostly on the terminal commands - useing the sure fire idea to make WEP or WPA work on wifi.)

I have tried WIFI-radar - every worked but WEP and WPA.
I have Tried  Network Manager - everything worked but WEP and WIFI.

But the way - the add/remove tool under the Application Pull down menu work just fine to intall the programs and aplets... but you have to be on line to do it.

sorry I can't not be of more help

FRICK



Give that a try just to see if your pmcia card will connect.

---

