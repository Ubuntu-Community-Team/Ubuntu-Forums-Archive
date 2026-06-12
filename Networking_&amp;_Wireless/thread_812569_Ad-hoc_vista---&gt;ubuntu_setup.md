---
title: "Ad-hoc vista---&gt;ubuntu setup"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by biohazardousguy on 2008-05-30
Hi to you all,
I run into some trouble trying to configure a small wireless network for personal use. I have an desktop computer running Vista which is connected to the internet using lan adapter. This computer has a second lan device wich is connected to my laptop. Using this set-up I can connect to the internet from my laptop. I would like to do the same thing but using two wireless usb sticks. What I have done so far:
- on the desktop side, I have disabled the secondary lan connection, pluged in my Asus wl-167G stick. The card was configured to use static IP:192.168.0.1. I have disabled ICS and then re-enabled it. I also have created an ad-hoc network using the Vista built-in wireless client, with ESSID:mmihasan, Security Type: No authentication(open), Encryption type: WEP, Network security key: simon. I connect the desktop to this network and the status is:Waiting for users to connect.
- on the notebook side. It is an old compaq armada laptop, running an basic install of Ubuntu 8.04 an top of which Xfce was instaled. The wireless adapter is an D-Link DWL-G122 revison C1. I would say that the adapter is working using the rt73usb adapter. I am tring to connect to the wireless network using the network manager applet from system tray. I right click it and hit connect to other wireless network. In the window wich pops up I enter Network Name: mmihasan,Wireless security: WEP128Bit passphrase, passphrase: simon, Authentication: open system. I hit connect, the icons is animated and the status is: attempting to connect to the wireless network mmihasan. After 1 or two minutes the wireless network key required windows pop up again, asking for the Wireless security, passphrase and Authentication. I reenter then, hit connect and the same thing happens again.
What did I do wrong?
Any clues that could help my solve this problem would be really apreciated.

Sorry for my poor english

---

### Post by pytheas22 on 2008-05-30
Coincidentally, I just got done doing a very similar thing a couple days ago--setting up a Windows XP machine to create an ad-hoc network via ICS for my Ubuntu computer to connect to.  I also have a DWL-G122 card.  I ran into the same problem as you--the card looked like it was connecting, but ended up timing out after a few minutes--and after a lot of frustration, I realized the problem was that the rt73usb driver does not support ad-hoc mode.  Try typing:
```

sudo iwconfig wlan0 mode ad-hoc
```

and you'll get an error.

In principle it's possible to get rt73usb to go into ad-hoc, but it involves downloading a kernel patch or something and looked really complicated to me.  An easier solution is to blacklist rt73usb and install the rt73 legacy driver from [http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads) .  Using rt73, I was able to connect to my ad-hoc network without a problem.  Unless you need to use rt73usb for some reason, I'd advise you to try using rt73 and your problem should be solved.  I'm using my DWL-G122 card with rt73 to type this and it's been working great on my ad-hoc network for two days.

---

### Post by biohazardousguy on 2008-05-30
Thank you for the quick reply.
The erorr thay you described I have noticed it. It is required for my laptop adaptor to be in ad-hoc mode?
It you have some time, could you please post how did you proceed on installing the driver and black-listing the old one?
Thank you in advance.

---

### Post by pytheas22 on 2008-05-30
Yes, your card needs to be in ad-hoc mode in order to connect to an ad-hoc network (normally your card would function in "managed" mode).  Here's a quick overview of what to do to get the better drivers:

1. install compiler if you didn't already, as well as the Rutilt wireless manager:
```

sudo apt-get install build-essential rutilt
```

2. download driver source code:

```
wget http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz
```

3. extract source code:
```

tar -xzvf rt73*
```

4. cd into directory and build:
```

cd rt73*
cd Module
make
sudo make install
```

5. blacklist rt73usb driver:
```

sudo -s
echo "blacklist rt73usb" >> /etc/modprobe.d/blacklist
```

6. insert rt73 module and bring up interface:

```
sudo rmmod rt73usb
sudo depmod -a
sudo modprobe rt73
sudo ifconfig wlan0 up
```

7. now launch Rutilt and you should be able to connect.  Note that you *cannot* use the rt73 driver with Network Manager--you may be able to see networks, but it will be buggy and probably won't connect.  Rutilt is a wireless utility made especially for the rt73 and other legacy Ralink drivers.  Using it you should be able to connect to your Windows network without a problem:
```

sudo iwconfig wlan0 mode ad-hoc ###this step is probably not necessary as Rutilt will know to put the card in ad-hoc mode, but it can't hurt
sudo rutilt
```

Let me know how this goes.

---

### Post by biohazardousguy on 2008-05-30
It worked OK, thank you very much.
Now I can connect to an unsecured open acces network created from my vistadesktop, but the noteboook can not take its IP. I also can not put an ip manualy, so I am again a bit stuck in this. Now I am I want to see maybe there is a newer version of rutilt which support inputing  an manual IP.
thanks again for your time and effort


The version in the hardy repo seems like it is the latest. I will dig a little bit more to see why the ip it is not served. Maybe there is also a problem on the vista side.

---

### Post by pytheas22 on 2008-05-30
Glad you can connect at least.  You can set a static IP using the ipconfig command, e.g. (for an IP address of 192.168.0.10):
```

sudo ifconfig wlan0 192.168.0.10
```

You can use a graphical interface to set a static IP by going to System>Administration>Network.

But I think that your Windows box should be giving you an IP via dhcp by default, so I would check that everything is working right on that end before trying to configure a static IP on Ubuntu.  When I first tried to set up my ad-hoc network, it took some work to get things working because Windows was not giving out local IP addresses as it should have.

---

### Post by biohazardousguy on 2008-06-02
> **pytheas22 said:**
> Glad you can connect at least.  You can set a static IP using the ipconfig command, e.g. (for an IP address of 192.168.0.10):
```

sudo ifconfig wlan0 192.168.0.10
```

You can use a graphical interface to set a static IP by going to System>Administration>Network.

But I think that your Windows box should be giving you an IP via dhcp by default, so I would check that everything is working right on that end before trying to configure a static IP on Ubuntu.  When I first tried to set up my ad-hoc network, it took some work to get things working because Windows was not giving out local IP addresses as it should have.

Sorry, I was away for some days in a local trip with my motorbike. The thing worked like a charm. The only point was that the rutilT application was reseting my ip setting for the card. Finally I got it, it has an option to leave the ip setting alone, so now it works. I am now writing from my old laptop using the wireless connection.
The next point will be to set up an more secured connection, and this will try in the next future.
All the best,
Marius Mihasan

---

