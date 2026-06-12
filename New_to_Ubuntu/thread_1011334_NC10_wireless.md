---
title: "NC10 wireless"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by kdm on 2008-12-14
Ahhhh, my wireless has stopped working all of a sudden on my Samsung NC10 Netbook with Ibex, anyone know what might be up ?

I have tried the instructions here...
[https://help.ubuntu.com/community/NC10#Wireless%20Networking%20-%20Atheros]("https://help.ubuntu.com/community/NC10#Wireless%20Networking%20-%20Atheros")
and it doesn't appear to have helped.

---

### Post by kdm on 2008-12-14
Well, if noone can help with this specifically, can anyone tell me how to remove the wireless drivers completely and start again ?

Thanks

---

### Post by ugm6hr on 2008-12-14
How did you install the driver the first time?

And what were you doing when it stopped working?  Have you had a kernel upgrade?

---

### Post by kdm on 2008-12-15
Literally just rebooted one day and it had stopped working !

---

### Post by XopherH on 2008-12-18
The same thing just happened to me, 

Yesterday just to get wireless working for the updates, I had followed the general documentation page listed above.  Wireless was then working after having downloaded the 3 other dependencies needed.  I downloaded and updated afterwards.

Now this morning wireless is not enabled or being recognized after the kernel updates.  

I am assuming I just have to fiddle with the blacklist.

Edit://  
I simply followed this and it worked for me, nothing else has been done out-of-the-box

```
sudo su
echo "blacklist ath_pci" >> /etc/modprobe.d/blacklist
echo "blacklist ath_hal" >> /etc/modprobe.d/blacklist
```

---

### Post by mikeboogsd on 2009-05-15
I had the same problem with my nc10, wireless all of a sudden disappeared from the notification applet. I modified the "blacklist ath_pci.conf" file in the /etc/modprobe.d directory, making sure that the line "blacklist ath_pci" has been hashed out. Example below of "blacklist ath_pci" file after editing.

# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
#blacklist ath_pci


Also modified the madwifi.conf file hashing out the line "blacklist ath5k" and unhashing all the lines below it. Example below of madwifi.conf file after editing.

## ath5k (mac80211)
## Comment out the following line, and uncomment all of the
## madwifi modules below to use the athk module
#blacklist ath5k

## madwifi (non-free)
blacklist ath_hal
blacklist ath_pci
blacklist ath_rate_amrr
blacklist ath_rate_onoe
blacklist ath_rate_sample
blacklist wlan
blacklist wlan_acl
blacklist wlan_ccmp
blacklist wlan_scan_ap
blacklist wlan_scan_sta
blacklist wlan_tkip
blacklist wlan_wep
blacklist wlan_xauth

Hope this helps I am also a bit of a newbie. Only been playing around with Ubuntu for a year now and love it....sure beets windows!

---

### Post by Montybank on 2009-05-17
Thanks for this.

just spent a couple of days beating my head against the wall and cursing the day I heard of madwifi.

back up and running due to the help here.

Cheers

---

### Post by smartroad on 2009-05-25
I have the same problem :( using wired at the moment. Have tried all the suggestions on this page. One thing I haven't been able to find is the madwifi.conf to try that one. Really want to get wifi working again.

-edit-
One thing, when I tried "sudo apt-get install linux-backports-modules-intrepid" all i got in reply was:

E: Couldn't find package linux-backports-modules-intrepid

---

### Post by ugm6hr on 2009-05-25
@smartroad:

Probably best to start your own thread if your problem is not solved by the suggestions here.

Again - how did you install the driver the first time?  Which version of Ubuntu?

---

### Post by smartroad on 2009-05-25
Hi ugm6hr, sorry forgot to say, using Ubuntu 9.04 Netbook Remix. The drivers were installed with the OS installation. Since posting my post though, I put the machine into sleep just after as I had other work to get on with and now started again and it is working :confused:

If it happens again I'll start up a new post as u suggested :)

---

### Post by ugm6hr on 2009-05-25
Remember advice for Intrepid (8.10) may not necessarily apply to Jaunty (9.04) with regard to drivers, since the drivers included with each version change.

That is why there is no *linux-backports-modules-intrepid*; that is Intrepid specific.  The same driver (ath5k) is included as default in Jaunty.

---

### Post by smartroad on 2009-05-27
OK thanks :)

I have noticed that when it (the NC10) decides it doesn't want to use the wireless anymore, if I turn it off for a while (about 30 mins or so) I can reboot and it will reconnect, now I am really confused but atleast I have a workaround. Although it hasn't happened for a while now (fingers crossed!)

---

