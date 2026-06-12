---
title: "Wireless won't connect in Ubuntu 13.10"
date: 2013-12-24
forum: Networking &amp; Wireless
---

### Post by meffle-paul on 2013-12-24
Hi everybody,

I have now worked a while with Ubuntu but still not really into it.
However everything worked fine after the Installation, now about after a weak I'm getting issues with my wifi. In the biginning all wokred as it should but then it got slower and slower and even completely stopped sometimes, so that I had to reconnect to my network. But since yesterday I'm not able to connect to my network at all.
It just loads and loads and after a few minutes it says "disconnected". Now I tried to delete it and reconnect to it and when I enter the passcode for my network and I click ok it tries to connect, but after a minute or two the box appears again but with my passcode already entered. I am sure the passcode is right
so my question: How can I get my wifi back to work?

Thank you for your replies :)

Paul

---

### Post by Hodevah on 2013-12-25
Hi and welcome. What you might need to do is put the output of your wireless information from this link here  [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)  to your post. This way, the people that can help you best have all the information available to them.

---

### Post by grahammechanical on 2013-12-26
My ISP has a utility on its web site that will test the connection speed between their servers and my machine. Also I can use a web browser to access the setup program in the router. Then I can check connectivity between the router and the ISP. There might be issues with the service provided by the ISP and this is causing the disconnection message. I had the same message a couple of days ago and the connection from the router to the ISP was broken and the router was trying to reconnect. It can be caused by the ISP doing maintenance and upgrades to it servers. 

A bounce back to the authentication dialog usually means that the passcode is incorrect or the encryption type is incorrect. Network manager usually identifies the encryption type for us (on the latest version of Ubuntu, certainly) but the pass phrase is down to us.

Regards.

---

### Post by wildmanne39 on 2013-12-26
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

