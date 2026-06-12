---
title: "Can't connect to any wireless networks."
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by drunkmatador on 2008-03-12
I'm running the newest version of Ubuntu, downloaded onto DVD ISO and then installed onto laptop computer. Everything worked right away other than the Broadcom BCM94311 wlan adapter. Drivers were downloaded as well as installed and since then networks have been showing up as usual.

However, I can't connect to the networks. At first I thought this was because my laptop's MAC was no longer allowed on the server machine (shared wifi at my apartment complex). Earlier today I called them and my MAC is actually still allowed, so it should be working. This was a surprise to me.

When running an iwlist scan, the two networks that usually show up, do. And have signal strength around -65 and around the same for noise. Kind of a lot of noise from all the access points and cordless phones around here (none of which are mine). Anyways the networks show up, I just can't connect to them for some reason.

When running dhclient on the machine it reports of having no dhcp offers recieved, and no working leases in persistent database. I don't know much about this program and whether that is relative or not, but maybe you could tell me.

And when i run sudo route -n it says that 169.254.0.0 is a destination connection using this card (eth0), but that's a fake IP, right? Could it be part of the problem?

If theres any advice you've got let me know. I'll be checking this all day.

---

### Post by PhrygianCat on 2008-03-12
Can you connect when you assign static IP, subnet, gateway, and DNS? It's possible that there is problem with the DHCP server. I've encountered this before at my office and after they restarted the DCHP server it works fine. Another way to test this is if other wireless device can connect to the access point.

---

### Post by drunkmatador on 2008-03-12
Yes, other devices can connect to the access point. In fact I'm connected to it right now on this computer... just for some reason I can't connect with my laptop (the computer in question). It's showing a good enough signal to connect, configured for G mode (network supports B and G), tries to connect... just nothing happens.

---

### Post by PhrygianCat on 2008-03-12
What happened when you try using static IP (manual configuration)?

---

### Post by drunkmatador on 2008-03-13
I'm not sure how to configure static IP for this connection. Would I have to ask them what IP and gateway and such to use?

---

### Post by PhrygianCat on 2008-03-13
I'd go to another computer that's connected to the same AP and find out the ip address, subnet mask, gateway, dns servers. Then start pinging ip addresses from the same subnet to see if there any that's not currently assigned to any device/computer. Then you can use that ip address for yours. To apply it on your Ubuntu, chose the manual configuration.

---

### Post by drunkmatador on 2008-03-13
ok a couple of questions. the network doesn't have a WEP key but there's no option for no encryption. and also after i change all the settings how do i make it connect to the network?

---

### Post by igotit on 2008-03-13
Hello and i'm new to ubuntu and i just put it on a compaq  presario v2000  and my wifi driver is not there and when i go to device manger i can not enable it please help  me thank  you




Andre'

---

### Post by drunkmatador on 2008-03-13
i'd suggest starting a new thread asking your question. post in that thread what kind of wireless card you have so that people can lead you to the right driver. you should be able to get it working with the restricted drivers manager.

now will somebody PLEASE help me with this? i've posted the output of all the commands i can think of that would help and i don't know what else to do.

---

### Post by Monstroxus on 2008-03-13
I fixed a similar problem yesterday. I couldn't connect as well. My wireless seemed to be working... saw several wireless networks... but couldn't connect to my wireless network, unless it was unencrypted... so that was strange.

What I did to fix it was... (assuming you'r are plugged in the wired network)

1) uninstall ndiswrapper/bcmcutter,
2) then reinstall ndiswrapper and the driver, see if it works.
3) if not, uninstall ndiswrapper and install bcmcutter and driver instead. (after this step, it worked in my case)
4) if it still doesn't work, uninstall networkmanager, and reinstall networkmanager.

After I did the last step, it worked fine. (one green dot... yes... two green dots... YES!) and I didn't have to mess around with the network settings at all. Just the clean install of the driver and click to connect... that was all.

I rebooted each time between these steps... just in case.

See if this works. (this option worked for me... now I can connect smoothly, even with WAP2 enabled.)

Good luck, just try this.

---

