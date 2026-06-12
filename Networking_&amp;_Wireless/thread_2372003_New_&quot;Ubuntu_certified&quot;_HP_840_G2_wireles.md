---
title: "New &quot;Ubuntu certified&quot; HP 840 G2 wireless drops out!!"
date: 2017-09-20
forum: Networking &amp; Wireless
---

### Post by kazakore on 2017-09-20
So I have a new (to me) laptop, with a large part of the decision on buying this model being that the system and contained hardware is supposedly Ubuntu Certified since 14.04! But surprise surprise, it works like ****!! From the fact you can't even boot into a Linux install without manually setting a Custom Boot line in the BIOS to the Wireless not working properly!

Why the hell does Ubuntu give laptops Ubuntu Certification when they do not work with the hardware!!!!!!???!! 

[https://certification.ubuntu.com/hardware/201411-16148/](https://certification.ubuntu.com/hardware/201411-16148/)

But anyway, this thread is to try and get some help with getting the wireless working. It does seem more stable on some networks than others so it's not that it doesn't work at all....

First things to try from searching were to disable Power Saving, no change. Then second suggestion was to try 11n_disable modes 1 and 8, both tried and neither help. This page mentions Intel wireless firmware which should fix it but the link to the specific version is dead.


[https://askubuntu.com/questions/583574/intel-dual-band-wireless-7265-dropping-connection](https://askubuntu.com/questions/583574/intel-dual-band-wireless-7265-dropping-connection)

So what should I do to get this working? And why hasn't Ubuntu done it saying they certify the hardware as being fully compliant?!?!


I would copy and pate in results of the likes of dmesg showing the disconnects and ifconfig but as I don't have a stable enough connection to post it I can't right now! If you tell me exactly which outputs may be useful I will try and get them saved in files to post once I'm on a connection that works (maybe I can try tethering the phone when I'm somewhere with better phone reception.)

---

### Post by praseodym on 2017-09-20
Please run the wireless script from the sticky thread and show the outputs (tar.gz file)

---

### Post by kazakore on 2017-09-20
I thought the WPS/Reset button would reboot the router when held down but it appears it did a hardware reset of the router, well it at least reset the UUID and cleared the security password. Used to hardware resets needing a little pin or something.... So after that I re-entered what I believe are the correct settings (it's one of the areas at work, not my personal one) and everything is working again as it was. From the researching before doing that post I made a couple of changes I hope wont effect any other users, namely disabling N, leaving it using only B/G and also changing the DHCP lease time, down from Infinite to 12 hour.

Does the computer need to be on the problem network to give a useful to you output? Or it just collates hardware information?

I run Ubuntu Studio (should have said before) and I have some recollection of having issues with its wifi before, I believe in the end I installed a Gnome module to replace the standard XFCE and most things worked a lot better after it (although the occasional problem when you're connected but don't even get a Ping returned from the router your connected to, for which I had a script I've now lost....)

Anyway in the short term it is working but as this laptop will be coming travelling with me I really could do with getting it so that the wifi will work happily on any network I am likely to come across. So key point for now is if that script output is useful when on the working network.

Thanks.

---

### Post by kazakore on 2017-09-21
It's currently on a working network but hopefully this output can assist you in helping me solve the issue with problem networks....

[http://paste.ubuntu.com/25586006/](http://paste.ubuntu.com/25586006/)

---

### Post by praseodym on 2017-09-21
```
sudo iwconfig wlo1 power off
```
deactivates the power management.

---

### Post by kazakore on 2017-09-22
> **praseodym said:**
> ```
sudo iwconfig wlo1 power off
```
deactivates the power management.

That was the first thing I tried after hitting Google and it didn't help at all.

---

### Post by praseodym on 2017-09-22
Install LinSSID and look for free channels. Channel setting in your router to fixed then

---

### Post by jeremy31 on 2017-09-22
The problem is that the command sudo iwconfig wlo1 power off is not persistent anymore as the Network Manager can override the setting, see if
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
```
systemctl restart network-manager.service
```
Works any better

---

### Post by kazakore on 2017-09-23
Deleted as Copy & Paste would then prevent the Go Advance button from working so writing post again from scratch below.[COLOR=#000000][INDENT][/INDENT]
[/COLOR]

---

### Post by kazakore on 2017-09-23
> **praseodym said:**
> Install LinSSID and look for free channels. Channel setting in your router to fixed then

The point is it needs to work on every router wherever I am when on the road, I can't exactly go and change the router settings in each guesthouse or hotel each week as I arrive and find it not working now can I!!

> **jeremy31 said:**
> The problem is that the command sudo iwconfig wlo1 power off is not persistent anymore as the Network Manager can override the setting, see if
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
```
systemctl restart network-manager.service
```
Works any better

As mentioned above I ended up changing some settings on the router at work and that is now working but I'll keep a note of this to try when I next come across a trouble hotspot. It did show the Power Management as disabled when checking with iwconfig after running the other command though.

---

