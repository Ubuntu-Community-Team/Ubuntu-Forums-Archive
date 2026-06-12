---
title: "IPW2200: Magically Working???"
date: 2006-08-15
forum: Networking &amp; Wireless
---

### Post by dfa_geko on 2006-08-15
Hi Everyone!

I am a total noob when it comes to Linux. But I finally got my wireless is working!!! :p :D  I have a Dell Inspiron 9300 running Ubuntu 6.06 (Dapper) with a Intel Wirless/PRO 2200BG. 

What did I do? Surprisingly, I really didn't do much. I was frustrated and reinstalled Ubuntu. Through various research, I have found out that Dapper comes wireless ready. The firmware is already installed in folder /lib/firmware and not /usr/lib/hotplug/firmware. I didn't install any new firmware or driver. If it ain't broke, don't fix it. :D 

I just had to install network-manager and network-manager-gnome from Synaptic Package Manager (or apt-get). Also, make sure you turn on the wireless (Fn-F2). iwconfig should tell you if it is on or off.

After network-manager was installed and the wireless turn on, it just started to work. I have read somewhere that someone did the same thing, just installed network-manager and it worked. (After a fresh install of course)

I hope this helps someone because I was totally frustrated trying to get this damn wireless to work!!!

dfa_geko

---

### Post by dfa_geko on 2006-08-15
Here is a link for anyone who is interested.

[http://doc.gwos.org/index.php/Network_Manager_with_WPA]("http://doc.gwos.org/index.php/Network_Manager_with_WPA")

---

