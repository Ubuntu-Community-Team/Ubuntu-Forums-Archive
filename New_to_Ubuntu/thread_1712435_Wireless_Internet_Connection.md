---
title: "Wireless Internet Connection"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by kprobe88 on 2011-03-22
Hey there everyone. 

I dual boot Windows and Ubuntu 10.10. I am a huge fan of Ubuntu. It really is a great OS and I am very pleased, but im just kinda working out the kinks. On my laptop (Dell Inspiron 14R) I recently installed Ubuntu 10.10. I can't figure out how to connect to my home wireless network. It won't show up automatically. Nothing will. All that appears is: 
      Wired Network
        disconnected
        
        VPN Connections >

Is it my hardware, or me?

---

### Post by samcot on 2011-03-22
Probe, I had the same issue. I'm a newbie, and even though I solved it, I can't say with any certainty that my solution is the easiest or the best.
 
Your network icon should be on the top right side of your screen (next to the volume control icon). Right-click on the icon and click on "Edit Connections." Then click on the "Wireless" tab and "Add." On the "Wireless" tab I had to manually type in the name of the network I wanted to connect to in the SSID field. And then, under the "Wireless Security" tab, I chose "WPA & WPA2 Personal" and typed in the network password key. Once it's set up, you don't have to set it up again.
 
Oh, and of course "Enable Wireless" has to be checked.
 
As I say, this may not be the best and easiest way to set it up, but it worked for me!
 
Good luck!

---

### Post by aussielinuxguy on 2011-03-22
[LEFT]kprobe88, With my wireless connection i did this.

On the taskbar where the network manager is, right click on it and select edit, click the Mobile Broadband tab and click on Add.

Then a box wil appear with your wireless broadband name at the bottom, mine is ( HUAWEI Technology HUAWEI Mobile ).

Then click forward and enter the details:

where you live
your provider 
billing plan.

[/LEFT]

---

### Post by wep940 on 2011-03-22
You may want to take a look at this thread - I posted a link there for getting the 14R running.
 
[http://ubuntuforums.org/showthread.php?p=10579608#post10579608](http://ubuntuforums.org/showthread.php?p=10579608#post10579608)

---

### Post by kprobe88 on 2011-03-24
nevermind, got it running. just had to install the broadcom driver.

---

