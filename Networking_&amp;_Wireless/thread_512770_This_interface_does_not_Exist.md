---
title: "This interface does not Exist"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by polygone on 2007-07-29
I recently got my Belkin Wireless driver up and running on my laptop, via. this tutorial: [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

I ran:

 ```
sudo iswlist wlan0 scanning
```

And got:

```
wlan0     Scan completed :
          Cell 01 - Address: 00:18:D1:48:94:06
                    ESSID:"myID"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:70/100  Signal level:-51 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0

```


So, I know my wireless card can see my router.  Under Network tools->Devices, I can see two wireless selections.  One does nothing.  It says wlan0,  The other seems to be detecting the router, but has the name wlan0:avahi.  When I unplug the land line, or disable it in Network, it doesn't work though.  Finally, when I go to configure it, I get this error:

The interface does not exist.
Check that it is correctly typed or is supported by this system.

Any ideas on what I am doing wrong?

Edit:

I tried this at work and it seems to be trying to get a DCHP 'offer' :
```
sudo dhclient wlan0 
```

I haven't tried it at home and none of the ones here at work are giving me anything.  Isn't there a way to make this happen automaticaly?  I think my default setup in loopback....

---

### Post by spd106 on 2007-07-30
The appearance wlan0:avahi interface means that you are not fully connecting with the AP, to be more precise you aren't receiving an IP address. This interface is a kind of virtual interface that doesn't really exist, that's why you currently get an error (it's a small bug).

It's difficult to diagnose exactly what's wrong, so you'll have to check the logs to find out at what stage things are going wrong. Try looking through the /var/log/syslog file for any error messages.

Have you checked that ndiswrapper is properly installed. Run this command
```
ndiswrapper -v
```

I have read that there is a bug in ndiswrapper that means you might have to reload it to get it working.
i.e run these two commands
```
sudo modprobe -r ndiswrapper
```
```
sudo modprobe ndiswrapper
```

---

### Post by polygone on 2007-07-30
Hey man,

Thanks for taking the time to help.  I ran that last command I put up top and it seemed to clear out that other one and now it works like a charm.

--John  :)

---

### Post by happyanimal on 2008-04-26
Thanks SPD106. I had similar problem and your advice worked perfectly.

---

### Post by Beto0707 on 2008-05-25
I'm told that ndiswrapper does not  exist and to install with apt-get.

Problem is I have no internet connection.

---

### Post by spd106 on 2008-05-25
You can download the packages separately and install them manually (just double-click). This wiki page will tell you how [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

As it's not been updated for Hardy yet you'll need to search for the right packages over in the web archive at [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

