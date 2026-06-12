---
title: "Acer Travelmate 292 Centrino wireless working with IPW2200 on Breezy!"
date: 2005-10-22
forum: Networking &amp; Wireless
---

### Post by terminalspin on 2005-10-22
I've had a few problems with the wireless networking  since upgrading, but I seem to have it working OK now. The following is for an Acer Travelmate 292, but may or may not be applicable to other Centrino machines...

The problem:-
On a clean install of Breezy, the wireless network card is very slow, and stops working within a few minutes of boot up. 

It had worked fine on Warty - which I had been using up until last week.

Additionally, the wireless switch on the side of the machine doesn't work - the machine has to be soft rebooted after switching on the network in Windows.

The solution:-
...seems to be to use version 0.9 of the IPW2200 drivers! 
I have no idea why, I guess it's possible that there is something slightly non-standard about the Acer TM292 - perhaps someone with more experience in this area can shed some light on this?

Having looked through some of the threads on this forum, it seems that a number of people have solved this, or similar problems, by installing version 1.0.6 or 1.0.0 of the ipw2200 drivers, but when I tried it, I found no improvements.

So, I tried version 1.0.6, 1.0.0, 0.22, 0.16 & 0.9 and of those, 0.9 seems to be OK.

I'll post a detailled step by step how-to later (if it would be useful to anyone) but there are a couple on these forums already for the 1.0.0 & 1.0.6 versions, and the steps are pretty much the same.

For the time being, the process that worked for me was as follows:-

[LIST]
[*]From a clean install of Breezy, install the linux headers, gcc3.4 & make packages
[*]DownLoad and untar the version 1.0.6 of the IPW2200 drivers from IPW2200.sf.net. Run the included remove-old script to remove the existing drivers from Breezy.
[*]Download and untar the latest version of the IEEE80211 drivers from ieee80211.sf.net. Run the included remove-old script to remove the existing ieee80211 drivers from Breezy.
[*]Download and untar the version 0.9 of the IPW2200 drivers from IPW2200.sf.net. Install this with make & make install.
[*]Download and untar the version 2.0 of the firmware from IPW2200 (this is the version that matches with IPW2200 v0.9) - copy these files to /usr/lib/hotplug/firmware and remove any existing firmware files from this directory.
[/LIST]


To get the wireless switch to work :-
[LIST]
[*]Add "acerhk" to /etc/modules
[*]create a file called "acerhk" in /etc/modprobe.d/ containing the line "install acerhk modprobe --ignore-install acerhk usedritek=1 autowlan=1 force_series=290; echo 1 > /proc/driver/acerhk/wirelessled
[/LIST]

After doing this, my machine now connects to the wireless lan on bootup, and holds onto the connection. 

Good Luck!

---

### Post by daller on 2005-11-28
I have the very same laptop, and what you describe here, works on mine out-of-the-box! (Breezy that is!)

---

### Post by Treviño on 2005-12-06
Hello, I've an acer Travelmate 292LMi, i'm using the latest version of the ipw2200 drivers with the wpa_supplicant to connect to my house wifi connection protected using wpa-psk.
Connection works, but sometimes it starts to become really slow...
I've a 4mb connection here, but now I can download only at about 50kB/s instead of 512kB/s (that I can get using an ethernet connection).

Do you suggest to downgrade the ipw driver to make it works well? The strange thing is that when my network reduces, if I open amule, all stops and neither it can't connect to a server... 
Wpa_supplicant isn't has no responsabilities because disabilng wpa protection in the problems rests.... I'm really near the router, and the signal seems good.
Thanks.

---

