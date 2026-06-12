---
title: "Ralink RT5390"
date: 2014-11-01
forum: Networking &amp; Wireless
---

### Post by Ryan_Carey on 2014-11-01
Hi folks.

This was my first attempt at installing a Linux system, and I got in some difficulty with a wireless driver. My Asus F551CA laptop has a Ralink RT5390 chipset, which has not been working for me. I attempted to install the driver, carefully following instructions, but it exits with [errors]("http://error: incompatible types when assigning to type ‘int’ from type ‘kuid_t’    pOSFSInfo->fsuid = current_fsuid();") 'incompatible types assigning int to ...'

When I rfkill list all, I see two devices, [one of which]("http://paste.ubuntu.com/8779159/") is hard blocked, and the other is not blocked. I'm not sure whether it's a problem that there are two devices shown.

For diagnostic purposes, [here]("http://paste.ubuntu.com/8779135/") is my list of devices, and [here]("http://paste.ubuntu.com/8780665/plain/") is another wireless diagnostic script that I ran.

I'm not really sure what to try to get the driver to install without errors. Anyone got any ideas?

---

### Post by chili555 on 2014-11-01
You have a driver in place as the wireless script shows: rt2800pci. Installing an older, suspect driver isn't going to do anything whatever to solve this:>      Interface             Soft blocked  Hard blocked
0: phy0: Wireless LAN           no           [COLOR="#FF0000"] yes[/COLOR]
1: asus-wlan: Wireless LAN      no            no
When you manipulate the wireless key combination, Fn+F4, or some such, and run again:```
rfkill list all
```Does the 'hard block' change?

If not, I suggest you try a driver parameter:```
sudo -i
echo "options asus_nb_wmi wapf=4"  >  /etc/modprobe.d/asus.conf
exit
```Reboot and tell us if the key combination now enables the wireless.

---

### Post by Ryan_Carey on 2014-11-02
Excellent. rfkill list all didn't help, but the change to driver paramaters did the trick. The wireless now seems to be working well.

Thanks for your help here, and for providing similar assistance in many other threads.

---

### Post by chili555 on 2014-11-02
Awesome! Glad it's working. For the information of you and the searchers, this isn't a wireless driver issue; it is an Asus issue with the little helper module that translates key presses into action, *asus_nb_wmi*. If you searchers haven't an Asus laptop, this will be ineffective.

Please use thread tools at the top to mark the thread Solved.

---

