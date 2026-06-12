---
title: "EDIMAX EW-7318USG Keep having to reinstall"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by BarnyB on 2008-03-26
Hi

I'm a fresh Linux user and this is the first install I have done...ok I lie I did have Mandrake 2007 but was recommended to use Ubuntu befire I ever used that and I have only gotten round to doing so now.

I eventually installed the Edimax 7318USG adaptor using the sh script found on  this page (I had a cd that came with it but there was no Ubuntu drivers listed and I didn't know how to install regardless): [http://www.lockergnome.com/linux/2007/11/04/ubuntu-gutsy-with-expresscard-working-options/](http://www.lockergnome.com/linux/2007/11/04/ubuntu-gutsy-with-expresscard-working-options/)

This works fine but I have found that when i reboot the PC it does not connect to the nwrk and when I go to system-admin-network (is this NM that is referred to in other posts?) it does not list a wireless connection. If I run the sh script again it shows and connects fine. How can I get it to remember that there is a usb wireless card installed?  

Yday I also found that the connection was being dropped numerous times where I had to keep re-entering the WPA info in the Network tool but now it seems to be working, What could be causing this issue? (I've only been on 15 mins at the mo and it's working fine).

Thanks. (Man this Linux isn't as straightforward as I thought it would be!)

Driver version listed is 1.4.3

---

### Post by BarnyB on 2008-03-27
I saw this in the HOWTO:RT2500 wireless cards  etc. sticky and will give it a go

•	
sudo gedit /etc/network/interfaces 
•	...and add these 2 lines if they are not there yet [
Quote:
auto wlan0
iface wlan0 inet dhcp 

Hopefully that will get it picking up the connection.

Anyone able to confirm if I am on the right track?

---

### Post by BarnyB on 2008-03-27
Well that didn't work. Sigh.

So any other ideas bar re-running the sh install script every time I log in?

Just even posting up links to the answer elsewhere will be sufficient, I looked at the stickies but nothing seems appropriate for my issue.

---

### Post by harraparra on 2008-03-28
Hi

I found this link - haven't tried so I don't know if it will work!

[http://www.lockergnome.com/linux/2007/11/04/ubuntu-gutsy-with-expresscard-working-options/](http://www.lockergnome.com/linux/2007/11/04/ubuntu-gutsy-with-expresscard-working-options/)

I'm going to try it tonight so I'll let you know what happens.

H

---

### Post by BarnyB on 2008-03-28
Thanks for the reply, there is life out there! That's the same link though that I posed in my original q. I have now installed Wicd which auto uninstalls NM. But it's the same issue. Once the sh script is run all is fine no probs. Reboot or shutdown and you have to run the sh script again. I've posted on the same link too that you gave but not heard nothing yet. V frustrating cos bar that i'm enjoying getting to grips with this O/S.

---

### Post by BarnyB on 2008-03-29
Hey all,

After posting up on locker gnome linux fanatics at the web add given in my orig post, I followed Matt's advice and did a fresh install. Then I ran the sh script provided on his site and my usb dongle works fine, No need for reinstalls after reboots. I must have had a screwy initial install.

Come on! Stick a [Solved] in this baby!

---

### Post by geezerone on 2008-05-31
Hi

I have bought an Edimax 7318UG USB wireless adapter. Is there a tried and tested way of getting it to work?

I have tried the serial monkey python script which created two wired networks (one wired and other wireless) but couldn't connect to wired one.

I then tried wicd but after this was removed no wireless networks are seen?

---

