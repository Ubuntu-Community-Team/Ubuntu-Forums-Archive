---
title: "Wireless issue"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by oddmage on 2009-04-23
I have an HP DV6119us and installed Ubuntu 8.1.0 on an 8GB thumb drive.  I got it mostly working but my wireless is having issues (I am using ENUWI-G2 because the built in wireless stopped working).  When I use the default driver/mod (rtl8187) I can connect to my wireless (wep encryption) fine, but I have a 40-70% packet loss.  So I downloaded and installed the windows xp driver using the ndiswrapper gui and blacklisted and removed the rtl8187.  The issue is I can't connect to WEP.  I checked my router for the one setting folks said to switch (can't remember off my head) but it didn't have it (it's an older, cheap, Belkin).  I am also using the built in NetworkManager and all the installed software is up-to-date.  Does anyone have any suggestions on either getting the default mod working better, or on how to tweak the xp ndis'd one to work with wep?

Thanks for your time,
odd

---

### Post by holyskeleton on 2009-04-24
I have dv9540us and didn't have to do anything to get the wireless work because it worked right out of box. 

was there any issue or anything unusual during installation?

can you connect via cable?

if sometimes you can connect to wireless can you ping servers ok?

---

### Post by oddmage on 2009-04-24
I can connect wirelessly using the built in driver through wep, but I get 40%+ packet loss.  The cable works fine, but my router is upstairs and my laptop is downstairs, so I want to get the wireless working.  As I said I am also not using the built in wireless (it stopped working at Christmas).

---

### Post by oddmage on 2009-04-24
I just disabled my wep and made it so my network is hidden, working fine now.  Any ideas why wep would throw a fit?

---

### Post by holyskeleton on 2009-04-24
hope your network didn't get hacked heh. better use WPA2.

---

### Post by oddmage on 2009-04-27
So I updated to 9.04 but I still have a ridiculous packet loss.  When I take off WEP it's fine.  I tried using WPA2 and it wouldn't connect, either with built in or ndis'ed windows driver.  Could it be the built in network manager isn't as good?  I noticed with I hit configure network on the ndisgtk it says Network Manager not found.

---

### Post by holyskeleton on 2009-04-27
for me jaunty connected as easy as it is on windows, both at home with WPA2 personal and at school with WPA enterprise with CA. so i'd say with a clean full on install there shouldn't be any problems with the OS.

i guess you can check the newest router's firmware and your BIOS firmware. maybe take your laptop somewhere else to see if it's the laptop or the router.

---

