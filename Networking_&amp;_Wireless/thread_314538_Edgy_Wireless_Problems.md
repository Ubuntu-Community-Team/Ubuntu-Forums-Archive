---
title: "Edgy Wireless Problems"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by SilverTab on 2006-12-07
I'm just reporting some problems that I noticed with Edgy and Wireless connections...

I have 2 wireless cards (Linksys WUSB54GC  and  D-Link DWL-G132

Both are working in Dapper with ndiswrapper (linksys with the rt73.inf  and the d-link with the 2 inf files on the CD ...cant remember the name, something like NetAUG505.inf and authfmsomething.inf  dont quote me on that LOL)

Anyway as I was saying, both work fine with a simple ndiswrapper installation in Dapper... I tried installing Edgy (from the Edgy CD, and not from apt update)... and I had weird errors with ndiswrapper for both cards...in fact, couldnt get eighter one to work...

The DWL-G132:
The two driver files cant install with ndiswrapper
(When I do a ndiswrapper -l  it says both drivers are Invalid)

The WUSB54GC:
The driver installs, says the hardware is present...However, I can't get a list of accesspoint, and can't connect to any networks (even when manually entering the essid etc..)

I just though it was worth mentioning as i've seen other people with the same cards that worked in Dapper and not in Edgy...

So I went back to Dapper, with both cards working...and I guess i'll wait a bit more to try edgy! :)

---

### Post by littlec on 2006-12-17
exact same card, exact same prob. how did you go back to dapper? did you have to reinstall?

---

### Post by hasuob on 2007-02-25
I too am facing this issue with Edgy & WUSB54GC networking. I'm going to try the walkthrough 

[here]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29")

and I'll post my results. Otherwise, I'll have to go back to Dapper (*sigh* i like edgy)

---

### Post by gradedcheese on 2007-02-25
typically, ndiswrapper will not 'survive' upgrades.  You likely need to remove it and install it all over again.

---

### Post by hasuob on 2007-02-25
Success!
This is on a clean install of edgy from CD, I don't know if this'll work for upgrades.
I followed [this]("http://wwwu.uni-klu.ac.at/agebhard/WUSB54GC/") walk through on how to make a kernel module, followed all its steps (went pretty quickly)

Then I added the following lines in my /etc/modprobe.d/blacklist
```

# Added when rt73 module was installed
blacklist rt73usb
blacklist rt2570

```

and added in /etc/network/interfaces
making sure auto rausb0 appears only once at the end of the file

```

# rt73 wireless network device using DHCP
iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
wireless-essid MY_ESSID
#uncomment 1 of the following 2 lines
# wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX       # This line for hexidecimal keys
# wireless-key s:XXXXXXXXXXXXX                  # This line for ASCII (string) keys
auto rausb0

```

and I got wireless after a restart

---

### Post by satrich on 2007-02-27
Read my last post in this thread:

[http://www.ubuntuforums.org/showthread.php?t=348008&highlight=rt73](http://www.ubuntuforums.org/showthread.php?t=348008&highlight=rt73)

I got my wireless working with the rt73 drivers from the ralink site. Maybe the sites mentioned in that thread will help you.

---

