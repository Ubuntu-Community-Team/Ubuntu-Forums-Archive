---
title: "Final configurations for wireless?"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by robulus on 2007-07-11
Hi all,
I just switched from winxp to feisty and am trying to finish off the wireless part of the setup.
My pci network card, the belkin F5D7010 v3000 seems to work out of the box - well, the wifi radar app discovers a few of the nearby wireless connections, so I'm assuming that means it's fine.(plus ummm the lights are flashing)

My problem is that even though I have the correct 128bit WEP key to use, and the NetworkManager Applet shows that I'm (77%) connected to the right account - I still get Server not found when I run my default browser (firefox) to try and load any webpage.

I'm new to this, so I don't know how to even start debugging this problem in linux - any tips?  Please, don't assume any linux knowledge on my part!
thanks folks,
Rob.

---

### Post by stevenw66 on 2007-07-11
Although this doesn't help I have the same problem with mu USB Wireless on my HP Proliant.:(

---

### Post by matei24 on 2007-07-11
i just finished installing feisty for the second time, since the first time it wouldn't recognize my sound card, now i am having the same problem as you. I am connected (signal strength 87%) but i cannot access the internet.

Could somebody point us to a thread or provide some help.

thanks

---

### Post by robulus on 2007-07-12
I think what may be happening is that the wireless connection isn't being assigned an ip address via dhcp - which does seem to happen when I use an ethernet cable.

any ideas anyone?  I'm getting 100% connection  to the wireless network - but still no content when I try and use firefox.

thanks!
Rob.

---

### Post by rwoodsathome on 2007-07-12
I'm having the same problem with my Belkin USB Wireless. I can see my Wireless Router using network manager. I enter my 64/128 HEX key (copy/pasted right from the router) and select shared mode. It wireless icon spins itself crazy (negotiating key/mode?) and then reconnects to my wired connection.

I've seen posts recommending WEP open instead of shared - but that is too much of a security compromise for me. I have 3 wireless devices connecting to the router without a problem and I'm really hesitant to change to WPA.:confused:

---

### Post by robulus on 2007-07-14
Hi Folks,
well I've finally an answer for this one - sort of - I came across another wireless utility, the KDE wireless assistant, and thought that for giggles I'll try it.  (even though I was using Gnome).

Just like the other utilities I used, it detected that there were wireless networks about - but I still couldn't connect when I put in the right hex key.
 
The problem was that I was running all these wireless apps from the menu without sudo privillages - when I ran the wireless assistant from the command line (with sudo) I was able to connect just fine - following exactly the same method as before.  Now I've no idea how to get those other wireless apps to prompt me for a root password when they don't offer it,  and now that it works I won't care about it for a while- no more ethernet cable for me.

and did I mention 'for giggles'?  When it worked, that turned into maniacal laughter.....
Rob.

---

