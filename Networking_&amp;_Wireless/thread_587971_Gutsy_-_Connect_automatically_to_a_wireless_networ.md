---
title: "Gutsy - Connect automatically to a wireless network"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by monchote on 2007-10-23
Hi!

I'm using Gutsy and I'm quite happy because the keyring is unlocked automatically, but now it never gets connected to my wireless network automatically.

Is there any way to do this?

Thanks a lot

---

### Post by Blackcomb on 2007-10-23
mine connects automatically by setting the wifi on roaming mode (this is actualy the default setting)

---

### Post by monchote on 2007-10-23
Mine it's set up like that and I always have to select the network I want to connect to... In fact, I didn't change any configuration for this.

Cheers

---

### Post by Blackcomb on 2007-10-23
And what if you set a static IP-address for the wireless connection (Manual Configuration) ?

regards

---

### Post by monchote on 2007-10-23
No,that's even more annoying...

What I don't understand is why it used to work in Feisty and not now...

---

### Post by jamesey on 2007-10-23
I have the same issue. It's really annoying to manually go into the network settings, and choose my saved settings, and hit apply. 

If I enable roaming mode, my wireless tries to join my neighbor's network which is a wireless router 30 yards farther away from my own wireless router.

---

### Post by sewmyheadon on 2007-10-23
I've also experienced this issue in Gutsy.  Will check Launchpad to see if it's reported there.

Here's my situation:

I upgraded my Inspiron 9300 and Compaq Presario V2000 laptops from Feisty to Gutsy, rather than performing a fresh install.  I connect to two networks: home and work.  Both are using either WPA or WPA2 encryption and have secure passwords.

I want PCs to have static IPs on my networks, but when I take wireless connections off of Roaming Mode, the wireless quality icon (showing the connection and how good it is) disappears.

Rather, I have the networking icon, which has no mention of wireless, unless you go into Manual Connection, where the individual connection profiles are setup.

When booting, I seem to have to manually select the connection and confirm, but also sometimes need to disable and re-enable Networking before I'm truly connected.

Maybe I'm not patient enough, but PCs with WinXP connect pretty flawlessly.  Thing is, I don't want to use them. :)  Of the wireless utilities that I've used, I really like Intel's Pro Wireless utility, which shows available networks and easily walks through the setup.

Would be interested to hear if people are experiencing the same issue on fresh installs of Gutsy.

---

### Post by dlublink on 2007-10-23
I am having this issue on both 7.1 and 7.06. Fresh install or not.

---

### Post by corncob on 2007-10-23
I am having the same problem (or very similar) on my fresh install of Gutsey.  Feisty was always connected as soon as I booted up but with Gutsey I have to open the Network Manager, uncheck the wireless connection, and, finally, recheck it again.  A window then opens saying "Changing Interface Configuration" and I'm connected.  I can live with this but my brother-in-law is coming for a visit and he won't be impressed with Ubuntu if he has to do this every time haha.   I"m using the Linksys Wireless-G PCI WMP54G.

---

### Post by seldenthuis on 2007-10-23
If you have the problem that NetworkManager always connects to a different network than the one you want to use, the following might help.

Start gconf-editor and go to /system/networking/wireless/networks.  There you should see a list of all the wireless network you have once been connected to. Go to each network you do not want (like your neighbours access point) and delete all the keys inside.  Unfortunately AFAIK there is no way to delete them all at once.

The next time you boot, NetworkManager will first try the networks that are still listed, before trying others.  I don't know of any other way to do this at the moment.

---

### Post by monchote on 2007-10-23
My problem is not that it gets connected to any other connection (that use to happen to me in Feisty), but it doesn't try to get connected to any network and I always have to click on the networkmanager tray icon and then select my wireless network...

Is that happening to any other people?

Cheers!

---

### Post by dmz17 on 2007-10-23
I find that putting a link to a simple script on the Desktop makes life easier:

sudo /etc/init.d/networking restart

Running this immediately after boot seems to select my access point every time, and not the neighbours, which is normally the 'default' because it is not encrypted.

---

### Post by corncob on 2007-10-23
I don't have  system/networking/ folder in gconf-editor.  However I was wondering what these entries are in the DNS tab in Network Settings:  DNS Servers: 192.168.1.254 and, in the Search Domains area: launchmodem.com.  It appears I would be able to delete them.

---

### Post by danteman on 2007-10-23
> **dmz17 said:**
> I find that putting a link to a simple script on the Desktop makes life easier:

sudo /etc/init.d/networking restart

Running this immediately after boot seems to select my access point every time, and not the neighbours, which is normally the 'default' because it is not encrypted.

Me too, but I also have to turn it off and on and put pauses between commands:

sudo /etc/init.d/networking restart
sleep 4
sudo ifdown ath0
sleep 3
sudo ifup ath0

Hope this will be fixed soon.

---

### Post by The Joe on 2007-10-23
The way I managed it was Manual Configuration in Network Admin.
In your notification area, there should be 2 moniters, click that and click Manual Configuration

On your Wireless device (Mine is wlan0) click properties, disable Roaming Mode and type in the network name for your router (mine is Belkin_G_Plus_MIMO_01DD8C, for example), type in a WEP/WAP key if you have one and set to Automatic Configuration on that bottom dropdown box unless you know it's any of the others.

Now when you boot, it *should* automatically connect. I'm not sure about other people's machines.

---

### Post by danteman on 2007-10-23
> **The Joe said:**
> The way I managed it was Manual Configuration in Network Admin.
In your notification area, there should be 2 moniters, click that and click Manual Configuration

On your Wireless device (Mine is wlan0) click properties, disable Roaming Mode and type in the network name for your router (mine is Belkin_G_Plus_MIMO_01DD8C, for example), type in a WEP/WAP key if you have one and set to Automatic Configuration on that bottom dropdown box unless you know it's any of the others.

Now when you boot, it *should* automatically connect. I'm not sure about other people's machines.

Well, thats what i did, but its not working.

---

### Post by The Joe on 2007-10-23
Connect to Other Wireless Network often works but it's not automatic..

If your on rt73 drivers theres a handy guide somewhere in these forums somewhere. I searched "Belkin Router"

It could be your WEP key, you might be selecting the wrong type or indeed typing it incorrectly, and remember the Network essid must also be exact.

---

### Post by jamesey on 2007-10-23
> **The Joe said:**
> The way I managed it was Manual Configuration in Network Admin.
In your notification area, there should be 2 moniters, click that and click Manual Configuration

On your Wireless device (Mine is wlan0) click properties, disable Roaming Mode and type in the network name for your router (mine is Belkin_G_Plus_MIMO_01DD8C, for example), type in a WEP/WAP key if you have one and set to Automatic Configuration on that bottom dropdown box unless you know it's any of the others.

Now when you boot, it *should* automatically connect. I'm not sure about other people's machines.


that worked for me on Feisty
not on Gutsy

---

### Post by bradster80 on 2007-10-23
I also do not have the network section in gconf-editor.

Is that the only way to set the wireless network preference such as connect order or to manage the list of wireless networks you want to automatically connect to if in range?

---

### Post by jamesey on 2007-10-26
bump for great justice!

---

### Post by fireflyfx on 2007-10-29
i have this problem too. very annoying- every time after boot i have to untick and retick the box in network config.

any further ideas?

---

### Post by vcbranco on 2007-11-01
Hi

Try this, worked for me

[http://ubuntuforums.org/showthread.php?t=576238](http://ubuntuforums.org/showthread.php?t=576238)

---

