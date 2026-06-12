---
title: "Changing TCP Window Size"
date: 2014-06-28
forum: Networking &amp; Wireless
---

### Post by actionmystique on 2014-06-28
Hello,

How is it possible to change TCP window size, only for local traffic, not for connections using the route with the default gateway?

---

### Post by bashiergui on 2014-06-30
Based on this link [http://www.ubuntulinuxhelp.com/speed-up-your-internet-connection-in-ubuntu-linux-part-2/](http://www.ubuntulinuxhelp.com/speed-up-your-internet-connection-in-ubuntu-linux-part-2/) it appears that you can only set one default with a max, preferred, and min window size. 

You might be able to achieve what you're trying by setting net.ipv4.tcp_window_scaling to 1:
> net.ipv4.tcp_window_scaling
This refers to the increasing or decreasing of the window sizes. If memory serves me correctly, in Windows the size is static, but in Linux it is dynamic. Therefore, turning this on (by setting it to 1) enables the ability to change window sizes as needed.

---

### Post by actionmystique on 2014-07-01
Thanks for the link. I have also found this [**Linux Network (TCP) Performance Tuning with Sysctl**]("http://www.slashroot.in/linux-network-tcp-performance-tuning-sysctl").

Unfortunately,  these new settings have not improved the TCP performance with my  Android 4.4.4 Nexus 5 (SSH). There's no /etc/sysctl.conf file, and I'm  not aware of any TCP config app in Google Play.

---

### Post by bashiergui on 2014-07-01
Aha you're on Android. Found this app 
[https://play.google.com/store/apps/details?id=com.spirilis.bionictcp&hl=en](https://play.google.com/store/apps/details?id=com.spirilis.bionictcp&hl=en)
You'll see that the app description gives you paths to the window size settings. ```
/proc/sys/net/ipv4/tcp_[r|w]mem 
/proc/sys/net/core/[r|w]mem_[default|max] 
```
 Sounds like you need root regardless.

---

### Post by actionmystique on 2014-07-02
Thanks but: this app has been designed for Motorola Droid Bionic device on Verizon and it is almost 3 years old. Android has seen tremendous updates in the meantime.
My device is a rooted Nexus 5 with the most recent Android version 4.4.4...

Anyway, my new TCP settings on Ubuntu may improve the performance when communicating with other devices.

---

### Post by bashiergui on 2014-07-05
Right. But the path to the config might be valid, so you could poke around and see if you can manually set the window sizes.

---

