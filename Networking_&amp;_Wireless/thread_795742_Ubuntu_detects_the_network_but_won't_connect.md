---
title: "Ubuntu detects the network but won't connect"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by Infini on 2008-05-15
Hi, I'm using a Dell Inspiron 1520 and I'm having a bit of a problem with my wireless here. I did a fresh install of Ubuntu 8.04 and at first I used my ethernet cable to connect to the internet. It prompted me to download the drivers for my broadcom b43 wireless and I said yes to the fetching and extracting part. I then checked and it was detecting my wireless network but when I entered my wireless key it would just keep trying to connect, fail and then ask me again for my wireless key. I've tried updating, rebooting and still no luck.

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

That's my hardware.. now that I mention it, maybe I'm using the wrong drivers or something? Most help regarding broadcom is to do with the BCM43 stuff.

---

### Post by Ayuthia on 2008-05-15
> **Infini said:**
> Hi, I'm using a Dell Inspiron 1520 and I'm having a bit of a problem with my wireless here. I did a fresh install of Ubuntu 8.04 and at first I used my ethernet cable to connect to the internet. It prompted me to download the drivers for my broadcom b43 wireless and I said yes to the fetching and extracting part. I then checked and it was detecting my wireless network but when I entered my wireless key it would just keep trying to connect, fail and then ask me again for my wireless key. I've tried updating, rebooting and still no luck.

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

That's my hardware.. now that I mention it, maybe I'm using the wrong drivers or something? Most help regarding broadcom is to do with the BCM43 stuff.

You are using the correct drivers and firmware.  I read somewhere that you have to check and see if roaming is checked.  I could be wrong about it though.  Unfortunately, I am using Kubuntu and the Network Manager in there is different then Ubuntu.  You might try turning off encryption to see if you can connect.

Another option to try is to install Wicd. Some people have better luck connecting with wireless on it.

---

### Post by Infini on 2008-05-16
Thanks for the reply. I was a little unsure as to what I was meant to be using. I tried using ndiswrapper but still no luck, I heard its worked for a lot of people with the same hardware as me. Maybe I should give Kubuntu a try and see if it works there?

---

### Post by Ayuthia on 2008-05-16
> **Infini said:**
> Thanks for the reply. I was a little unsure as to what I was meant to be using. I tried using ndiswrapper but still no luck, I heard its worked for a lot of people with the same hardware as me. Maybe I should give Kubuntu a try and see if it works there?

If you are thinking of going that route, you might want to try installing Wicd first.  I have been reading a lot of posts that are saying that Network Manager is not working well.  I am trying to figure out how to open up another partition in my laptop to test out Ubuntu.

Did you try turning off encryption on your router?  What encryption are you using?

---

### Post by Infini on 2008-05-16
I'm using WEP at the moment. Not really too sure when it comes to routers and stuff, can you instruct as to how I can disable encryption?

I also gave Wicd a try, it was a little better. Gave some more options and stuff but still no luck.

I've switched over to Kubuntu right now. It's detecting my network after an install of the broadcom b43 wireless driver that it prompted me to install. When attempting to connect however it gets stuck at the configuring IP part.

---

### Post by Ayuthia on 2008-05-16
Let's try to see if we can do this from the Konsole:
```
sudo iwconfig wlan0 essid <name> key <passkey>
sudo dhclient wlan0
```

EDIT:
Forgot to add that <name> should be replaced with the name of the access point and <passkey> is replaced with your password.

---

### Post by Infini on 2008-05-16
```
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1c:26:5f:dc:12
Sending on   LPF/wlan0/00:1c:26:5f:dc:12
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

That's what the Konsole tells me.

---

### Post by Rudedawg on 2008-05-16
Try connecting to an unsecured network. I was finally able to get my realtek wireless card working using ndiswrapper, but it will only connect to unsecured networks. There is a how to guide in the networking/wireless forum that gives some detail on how to connect to a secured network that I plan on trying when I get home.  

If you are familiar with your router settings, unencrypt your wireless and try your connection. If you can connect, re-encrypt your network and check out that guide. 

Hope this helps. 

Edit: Oops! I skipped over the part about not knowing routers too well. If you can "see" wireless networks, but cannot connect to them, the encryption is probably the issue. Check that guide out!

---

### Post by Infini on 2008-05-16
Oh my God. I just looked at the back of my router and it tells me that it's a 64bit hexidecimal wep key... I was using the wrong encryption the entire time. It's working flawlessly now. ..Jeez, what is wrong with me? I spent a whole day trying to get this working, trying everything.. and this was the problem?

Thanks for your assistance anyway. I appreciate it.

---

### Post by Ayuthia on 2008-05-16
> **Infini said:**
> I'm using WEP at the moment. Not really too sure when it comes to routers and stuff, can you instruct as to how I can disable encryption?

I also gave Wicd a try, it was a little better. Gave some more options and stuff but still no luck.

I've switched over to Kubuntu right now. It's detecting my network after an install of the broadcom b43 wireless driver that it prompted me to install. When attempting to connect however it gets stuck at the configuring IP part.

I am not for sure about how to configure your router.  Sometimes the way to access it is to go into a browser and go to 192.168.0.1.  You will need to do this from a working connection.  If you have Windows, you might try to connect from it that way.  I have only been able to access mine wirelessly.

---

### Post by Ayuthia on 2008-05-16
> **Infini said:**
> Oh my God. I just looked at the back of my router and it tells me that it's a 64bit hexidecimal wep key... I was using the wrong encryption the entire time. It's working flawlessly now. ..Jeez, what is wrong with me? I spent a whole day trying to get this working, trying everything.. and this was the problem?

Thanks for your assistance anyway. I appreciate it.
At least you found it!  Congratulations!!!!  Glad to see it working.  Are you going back to Ubuntu or staying with Kubuntu?  :)

---

### Post by Infini on 2008-05-16
Dual boot. :popcorn:

---

