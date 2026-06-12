---
title: "Can't connect to ad hoc networks? Specificaly from an android"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by perlgoodies on 2011-08-02
I have an android phone that I use to tether with to get internet during my lunch hour. I cannot get either two of my apps (Barnacle, WIFI Tether) which are the two best rated wifi tether apps in the market place to work on my Ubuntu laptop. I can get a Windows XP and a Windows 7 box to connect to the network without a problem but the Ubuntu box (actually I have two separate laptops with Ubuntu that won't work, same version but different model laptop) tries to connect but it never does.
 
I've read from a few others that they've also had this problem but never found a solution for it. Someone said Ubuntu doesn't allow connections to AD HOC networks right now. Another person said to change the WLAN0 settings to 1250 (which I did) but it didn't help.
 
Short version: I can't get my Ubuntu laptop to connect to my wifi tethered android phone. The apps and phone work just fine, they tether with my Windows laptops. I just can't get it to work on the ones with Ubuntu.

---

### Post by skatinjj on 2011-08-02
[https://help.ubuntu.com/community/WifiDocs/Adhoc]("https://help.ubuntu.com/community/WifiDocs/Adhoc")

Take a look here, it may help.

---

### Post by perlgoodies on 2011-08-02
> **skatinjj said:**
> [https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)
 
Take a look here, it may help.
 
Hi-

I've been to that page twice and unless I'm not seeing something it doesn't explain how to connect to an adhoc network. It shows how to make your laptop BE the network instead of connecting to an already established one.

---

### Post by skatinjj on 2011-08-02
"Joining an ad hoc network
Click on the tray icon and you will see the ssid of the ad hoc network with the ad hoc icon next to it, click on it to connect. "

Network manager should be in your tray.  Locate it and see if it picks up the adhoc network.

---

### Post by perlgoodies on 2011-08-02
Sorry, me again! Maybe Network Manager is confusing me. Is that something different than the wireless connection thing on the top of my screen? What I've been doing is clicking the sattelite/wifi thing and it sees my connection and I click it. Then it just tried to connect endlessly.

---

### Post by skatinjj on 2011-08-02
You look for the adhoc network like another wireless network.  If you see the adhoc SSID than you are in the right place.

You may have to configure your network manager with the security settings if there are any.

---

### Post by icebird1942 on 2012-11-16
If it doesn't show up in the Ubuntu available networks, click on the Network icon (if wired it's two arrows going in opposite directions) and select Connect to Hidden Network... Select the Connection name and connect.

---

### Post by 3rdalbum on 2012-11-17
I can tether my Android phone using Android's built-in tethering facility, which I believe makes itself out to be a regular "infrastructure" AP instead of an ad-hoc one.

Why not just use the regular Android tethering facility rather than downloading extra apps to do the same thing (not as well)?

Ubuntu can create ad-hoc networks so it definitely can connect to them too. However not all wifi cards can connect to ad-hoc, this may be your problem.

---

### Post by wildmanne39 on 2012-11-17
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

