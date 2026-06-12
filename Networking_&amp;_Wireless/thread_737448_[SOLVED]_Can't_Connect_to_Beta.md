---
title: "[SOLVED] Can't Connect to Beta"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by Raccoon1400 on 2008-03-27
I just setup my XP desktop to host a wireless network called Beta.I want it to connect to the laptop beside it running Gutsy and Vista. I can get Vista to connect, but not ubuntu. My Broadcom card detects the network and asks for the password when I click on it. I give it the password, but it can't connect.
Any Help?

---

### Post by Raccoon1400 on 2008-03-27
I did  something to make the wireless option dissappear altogether. how do I make it come back?

---

### Post by #Reistlehr- on 2008-03-27
is MAC address filtering turned on/

---

### Post by Raccoon1400 on 2008-03-27
I got the wireless option back. I still can't connect to Beta.
What is this MAC thing?

---

### Post by jamesrfla on 2008-03-27
MAC filtering is a type of security that prevents anyone that doesn't have their MAC address listed in the router they can't connect. Hear is more information on it [http://en.wikipedia.org/wiki/MAC_filtering](http://en.wikipedia.org/wiki/MAC_filtering)

---

### Post by Raccoon1400 on 2008-03-27
Beta does not connect to a router. It connects to the desktop computer.
How do I check if MAC filtering is on?

---

### Post by jamesrfla on 2008-03-27
There is a way you can check to see if MAC filtering is on. One of them is to take another wireless device (if you have one) and see if it will connect to your desktop. If you are creating a wireless network using a desktop I don't think MAC filtering will be enabled by default. If you use the same wireless card for vista as you do with ubuntu  then MAC filtering shouldn't be the problem. What program are you using to create this wireless network?

---

### Post by Raccoon1400 on 2008-03-27
I created the network in XP. In linux, I am just using network manager to pick it up.

---

### Post by jamesrfla on 2008-03-28
Maybe the network you created in XP isn't compatable with Ubuntu. Try connecting to the network by using the network icon on the top right of the desktop. Click it and then select your wireless network.

---

### Post by Raccoon1400 on 2008-03-28
That's how I was trying to connect. I think the problem is a driver issue with my card. I've heard the Broadcom drivers don't work well.

---

### Post by Raccoon1400 on 2008-03-29
with these instructions, I can now connect to Beta. 

[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

I still can't access the web through the shared internet connection on the host computer(XP). Vista running on this same laptop can access everything fine.

---

### Post by Raccoon1400 on 2008-03-29
I created another wireless network , this time without encryption, and it works fine, but I am not prepared to use an unsecure connection.

---

### Post by jamesrfla on 2008-03-29
I don't know if you can with the XP computer enable MAC filtering. I have never tried to create a wireless access point using XP. If you can add MAC filtering then you won't have to worry about people connecting to your wireless access point. The only problem is your data won't be encrypted from the wireless access point to the computer. Just don't make any credit cards purchases or do online banking. I don't recommend doing any type of banking on wireless.

---

### Post by Raccoon1400 on 2008-03-30
I seem to have fixed it. When I tried to connect to the network, it asked for the password. In the box, it said security type was 128 bit passphrase. I changed it to ANSII(or something like that) and now it works. I guess ubuntu and xp both thought it was a different type on encryption.

---

