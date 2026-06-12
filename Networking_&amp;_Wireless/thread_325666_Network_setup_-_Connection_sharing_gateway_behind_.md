---
title: "Network setup - Connection sharing gateway behind Smoothwall"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by bergkamp on 2006-12-26
Hi guys,

I was hoping I could get some help on setting up my network. I have been running a smoothwall box as a firewall for a couple of years, and recently I wanted to add something in between smoothwall and my lan which would be a central point where i could manage my network a bit better (more specifically to be able to view the bandwidth each pc is using etc).

Anyway, I was able to setup a edgy server in the middle with internet connection sharing working, but I wasn't happy with the way it was setup. For example, to open up ports on PC's in my LAN, I have to forward ports twice, and I think some double NATing is going on too.

The setup is as follows.

Modem ---> Smoothwall ---> Ubuntu Edgy (Alternate)---> Switch ---> PC's


What I want to be able to do is have a box in the middle, in which I can install stuff on to monitor and control the network, as well as been able to install and run server components on like Apache and an FTP server, but without having to forward things twice and without been double NATed.  I'm not sure if ethernet bridging is an option (which I've read isn't a good path to go down).

Is there anyway I can setup my network to act like described above.

Thanks and sorry about the wall of text :)

---

### Post by bergkamp on 2006-12-26
bump

---

### Post by bergkamp on 2006-12-26
anyone have any ideas?

---

### Post by n3gbz on 2006-12-26
This is the setup that I have.  I just got it working with Ubuntu today! 
[B]
  internet ---> wlan0 ---> Ubuntu Edgy ---> eth0 --->  switch ---> PC's[/B]

The internet is accessed via WiFi on a pc running Ubuntu Edgy.

I then use a crossover cable from eth0 to a switch with two PC's attached.  Neither of those PC's has WiFi capability.

(This physical configuration works and I have used it regularly with Windows XP but wanted to use Ubuntu instead.)

To get Internet Connection Sharing (ICS) to work, I needed to install **firestarter** and set a preference to allow Internet Connection Sharing. 

The online firestarter documentation was a big help --  **[http://www.fs-security.com/docs/](http://www.fs-security.com/docs/)**   -- especially the section on ICS --   **[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)**   --

The Ubuntu Edgy wiki --  **[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)**  -- 
explained how to install firestarter  --  **[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Firewall_.28Firestarter.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Firewall_.28Firestarter.29) ** --  a lot of good info there!!!

I hope this helps!!!

---

### Post by bergkamp on 2006-12-26
hey, thanks for your answer.

however, i think by installing firestarter, network traffic will be double NATed, which I want to avoid doing. I have been able to get firestarter working before, and I have to double forward ports which isnt ideal.

---

