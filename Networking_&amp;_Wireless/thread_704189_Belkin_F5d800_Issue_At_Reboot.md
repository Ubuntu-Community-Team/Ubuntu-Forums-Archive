---
title: "Belkin F5d800 Issue At Reboot"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by technotika on 2008-02-22
first off Im very pleased with Ubuntu; this is prob 5th attempt at getting everything running and moving forward with a stable linux based system and it's looking very good now - perseverance is the key!!

I have managed to get the above network card working through using different aspects of various posts in this forum however I need to probe a bit more.

Basically I used synaptic update to get ndiswrapper and the GUI and from a post in another linux forum got the drivers that were actually detected when using the ndiswrapper; prior to that my cd driver just came up as "invalid driver"!

Anyway  - Driver installed - shows up in wireless management - and connects to the net. HOWEVER when I reboot  - no wireless. I can get the wireless working again by taking off DHCP and setting up STATIC IP. How ever if I reboot again I lose wireless again and then to start it up again I have to set to DHCP - the it works. Its as if I need to do something in that management tool that starts the networking.

Since then I read somewhere that  there network tool in ubunts is a bit funny with some cards and people said that alternative apps for wifi management worked. I tried WIFI RADAR and that seemed to do the trick however Its suddenly reverted back to losing the wireless after each restart. 

Any help would greatly be appreciated.

Thanks Jerry

---

### Post by technotika on 2008-02-24
SORTED!

Found this comment

[I]"I was having the same problem for months. I decided to look into it today and found this solution. 
Add this to your /etc/rc.local file

/etc/init.d/networking restart

I only tried one restart after using this option and it worked for me. Give it a try. I'm going to reboot again to make sure"[/I]

Tried after everything seemed to be pointing to not working and it worked
a treat have done 4 reboots and its wicked news - who ever posted that is a legend. Now I am running with ubuntu and all i could do in windows i can now do FOR FREE!!!!!

And to boot i have virtual box with xp in just in case. What a system!!!

---

