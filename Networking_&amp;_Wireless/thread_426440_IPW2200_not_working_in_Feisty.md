---
title: "IPW2200 not working in Feisty"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by kbarron on 2007-04-28
I am using Ubuntu for the first time and have no linux experience. I just got a new HD and decided to do away with windows are start with Ubuntu from scratch.

I cant get my wireless connection to work. The wired is working but I cant locate any wireless networks. I have read over the threads but havent been able to figure things out.

I have an Intel IPW2200 which is pretty standard. I had played around with the live CD of Edgy before and it was able to locate the network

but now that I did a full install of Fiesty I cant figure things out.

any help or directions or links would be appreciated. I really need this thing to get working. 

thanks

---

### Post by unclben on 2007-05-04
My IPW2200 is also not working. It worked under Dapper and Edgy using network-manager-gnome. It works using the Feisty LiveCD. When I did a clean Feisty install, however, it stopped working! (I'm posting this from the Feisty LiveCD.)

I can see networks without a problem. When I select my home network with the network-manager applet, it correctly prompts me to enter my WPA password. Then it just churns and churns and churns. The lower-left 'light bulb' in the nm-applet logo is sometimes green and sometimes not, but the upper-right bulb never lights up.

---

### Post by unclben on 2007-05-04
Well, I'll be darned. I booted back into my installed copy of Feisty to try out some fixes proposed in these fora, but it started working all on its own! Previously, it had worked flawlessly every time I booted the LiveCD and never worked on the several times I attempted it with the installed copy. Dubya-Tee-Eff?!

---

### Post by Rhesuso on 2007-05-10
That is really odd. With Network Manager (NM) enabled by default in Feisty, the ipw2200 adaptor should really just work. It does for me (It did in Edgy too, once I'd installed network manager).

Let's see, in System -> Administration -> Network, your wireless connection should be set to 'Roaming Mode Enabled'.
When you click on the network manager applet to create a wireless network, that should be pretty easy to fill in the dialog. Re-check that you're entering the details as are set on your Access Point(AP). I use WPA Personal security, and the encryption type is TKIP, but there is also the choice of AES. I think TKIP is the most common one to use but maybe you've set up your AP differently. Setting encryption type to Automatic might work, but I haven't tried it, and it's probably better to set it to what you know you're using.

Unfortunately with NM, you can't assign a static IP address to your adapter (I've recently discovered). It has to use DHCP, so make sure your AP offers a DHCP server and that it's enabled. If you can't run DHCP, you'll need to get rid of NM, and configure your static IP in System -> Administration -> Network, and use wpa_supplicant to provide WPA encryption (you really should use WPA rather than WEP). It's not hard to set up, search here on the forum for a guide, & I'll try to find the guide I used and post the link here.

@kbarron
If you can see your surrounding wireless networks under windows, but not linux, maybe your adapter is switched off. Run iwconfig or ifconfig in a terminal, and also in a terminal:

```
dmesg | grep ipw2200
```

to see if that provides a clue. I know on my laptop, when the wi-fi is switched off in windows and I reboot to ubuntu the adapter is still off, and I can't get it back on without rebooting and enabling it in windows again. There may be a fix for this, but it's not a priority for me right now so I just work around it for the moment.

I hope you get it working, it's pretty essential to have a net connection. On the plus side, when you do get it working, I've found wireless reception under linux to be much better than in windows (with no detrimental effect on the battery life of my laptop).

---

### Post by outlaw686 on 2007-07-24
wow. i wreaked my ubuntu install and messed up my drive partitions. then i turned off extended range mode on my dlink router and it worked on the install cd. now hopefull it will work when i do a fresh install. I would recommend turning off wep encryption to see if you can connect, thats how i knew it was working, then after that everything connected and i was able to get it working with wep.

---

### Post by outlaw686 on 2007-07-24
sorry for the double post but my wireless is working flawlessly now :D what others are trying to say in other threads and what I have found confused me before is going into administration and going into network and setting it up there doesn't work.  The solution was so simple I was laughing when I figured it out. 

Right click on the two computers in the top right of your screen click on your network. Hope some of you are having the same problem I had. 

That said, I wonder if its a bug that the network settings in administration doesn't work though.... I think what I'm clicking on is network manager and not the same thing. Oh well if you don't see two computers in the top right of your screen to to system> administration > Synaptic Package Manager and download NetworkManager and I hope it works for you.

Cheers and good luck guys.

---

