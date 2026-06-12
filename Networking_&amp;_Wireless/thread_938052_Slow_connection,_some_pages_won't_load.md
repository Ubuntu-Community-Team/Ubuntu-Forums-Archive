---
title: "Slow connection, some pages won't load"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by alkamid on 2008-10-04
Hello

A few days ago I moved to a new flat with my friends. We have Internet connection from a local provider. Everything went smoothly but...
We bought a router (D-LINK DIR-300), set it up and I (and only I, as I am the only one who has Ubuntu, the rest has Win XP/Vista) have some problems with my connection. 
It's hard to explain what it really is, however, the most obvious effect is that some pages don't load. For example, youtube.com loads only the title of the page and then stops. I did "view page source" thing and it gave me whole nice code, but the page is blank! The same with ubuntuforums. Oh, almost the same as it won't even load the title.

I checked it on different web browsers (FF, Opera, Swiftfox). It works fine on my Virtualbox Windows XP (I'm using it right now). What could possibly cause this problem? I have no idea, seriously.

I use:
Firefox 3.0/Opera/Swiftfox
Lenovo ThinkPad T61
Ubuntu 8.04
Wifi Intel 4965

Please, help!

---

### Post by jigsaws on 2008-10-04
I have two ideas, but both are connected with network, not webbrowser.

First try:
sudo -i
echo "0" > /proc/sys/net/ipv4/tcp_window_scaling

And check the webpages.

Then check MTU by ipconfig:
root@lenovo:~# ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:37:21:70:57  
          UP BROADCAST MULTICAST  **MTU:1500**  Metric:1
(if it's the same as in windows, it's not it).

If it isn't help:

Check if it is web related - try download files from ftp.

---

### Post by alkamid on 2008-10-04
First one doesn't work, and for the second one I don't know how to check MTU value in XP.

---

### Post by jigsaws on 2008-10-04
I'm not sure, but try in regedit:
System Key: [HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Tcpip\Parameters\
Interfaces\[Adapter ID]]
Value Name: MTU

---

### Post by alkamid on 2008-10-05
There's no such thing. I'll try to google more about that...

---

### Post by alkamid on 2008-10-06
Maybe this will be helpful:
When I plug in the ethernet cable from my ISP into my laptop, everything's fine. It's something wrong with my router then.

---

### Post by superprash2003 on 2008-10-06
you could try changing MTU values to 1452 or something..
[http://prash-babu.blogspot.com/2008/06/how-to-change-mtu-values-in-linux.html](http://prash-babu.blogspot.com/2008/06/how-to-change-mtu-values-in-linux.html)

---

### Post by alkamid on 2008-10-06
I've asked my provider: he said its value should be 1500.

---

### Post by cariboo on 2008-10-06
What is the differencce if any between the windows setup and your setup. For windows go to Start-->Run-->cmd and hit enter. In the terminal window that opens type:

```
ipconfig /all
```

Then on your computer right click on the network icon in the top panel and select connection infogmation and compare the two.

Its strange that you have to use a terminal in Windows to do the same thing in Ubuntu with a gui. :)

Jim

---

### Post by alkamid on 2008-10-07
I've just found out what causes this problem: it's javascript. My friend has just set up Gentoo linux on his machine and experienced the same problem. He checked off "Enable JavaScript" in Firefox Preferences -> Content. Now everything goes smoothly. I think I should change the JavaScript parser or sth. How to do that?

PS And what the hell does it have to do with my router?!

---

### Post by alkamid on 2008-10-08
bump

---

### Post by alkamid on 2008-10-10
Any ideas?

---

### Post by alkamid on 2008-10-11
Please

---

### Post by alkamid on 2008-10-11
I solved the problem by changing router's firmware to DD-WRT version!

---

