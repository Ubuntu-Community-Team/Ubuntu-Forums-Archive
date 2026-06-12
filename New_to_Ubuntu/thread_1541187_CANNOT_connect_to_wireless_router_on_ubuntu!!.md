---
title: "CANNOT connect to wireless router on ubuntu!!"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by alli-bug on 2010-07-28
Okay, I just downloaded the newest operating system from ubuntu, and I CANNOT find any possible way to connect to my wireless router! If I go to the "connect to hidden network" thing, it does list my router as an option and it includes the encryption key and everything. But when I click connect, it simply dissapears and rudely reminds me in the upper right hand corner that i'm STILL not connected!! I also tried going the other direction with the BSSID and MAC addresses, and I do not understand any of this AT ALL.  So for my sake, while answering this, you're temporarily explaining this to a 10 year old. . .so take it slow. Any help will be GREATLY appreciated!! 
Peace, Love, and Thank You! 
~alli

---

### Post by McFinnigan on 2010-07-28
You may have to go into the Applications menu and use the software finder to download the Windows Wireless Network driver.

---

### Post by alli-bug on 2010-07-28
Hmm. . .trying to do that now. When I try to download it, its like the downloading thing shows up for a split second on the left hand bar, then dissapears, and the software is no where to be found

---

### Post by JustinR on 2010-07-28
Assuming it's not a driver problem and your using an encryption better than WEP you need to set your router to B/G mode (most of these are called Legacy in the router settings). Ubuntu + WPA doesn't work so well.

---

### Post by alli-bug on 2010-07-28
Thank you very much. But its already set to that, and no changes. :(

---

### Post by Chris1274 on 2010-07-28
Is your wireless card enabled and picking up available networks, or is it disabled?

---

### Post by alli-bug on 2010-07-28
its enabled. as long as I'm running on windows, my internet is great. But in unbuntu, it still picks it up and everything, it just won't connect!

---

### Post by typal on 2010-07-28
To connect to a wireless network:

[LIST=1]
[*]Click the wireless icon at the top right.
[*]Select your network from the list of available networks.
[*]A window should pop up that says, "Authentication required by wireless network."
[*]Enter your password for the network. If it is already filled in, re-enter it, anyway.
[*]Click connect.
[/LIST]
Do you know the password for your network?

---

### Post by Chris1274 on 2010-07-28
Maybe your wpa supplicant isn't working? Go into System > Administration > Synaptic Package Manager, search for wpasupplicant and see if it's installed.

---

### Post by alli-bug on 2010-07-29
> **typal said:**
> To connect to a wireless network:

[LIST=1]
[*]Click the wireless icon at the top right.
[*]Select your network from the list of available networks.
[*]A window should pop up that says, "Authentication required by wireless network."
[*]Enter your password for the network. If it is already filled in, re-enter it, anyway.
[*]Click connect.
[/LIST]
Do you know the password for your network?

Yes, I do. But when i click on the wireless icon on the top right, the first 2 things listed are not enabled for me to click on. I'm stuck with the bottom 3. I honestly don't know what the hecckkk is up with this?? Seriously, my internet is perfect on Windows. Could it be ubuntu?

---

### Post by typal on 2010-07-29
Does it look like this, or something different? Is there nothing listed under "Available?"

Can you list the output of this when entered in a terminal? Applications > Accessories > Terminal.
```
lspci |grep Network
```

---

### Post by alli-bug on 2010-07-29
> **typal said:**
> Does it look like this, or something different? Is there nothing listed under "Available?"

Can you list the output of this when entered in a terminal? Applications > Accessories > Terminal.
```
lspci |grep Network
```

It looks like that, except the entire "available" thing isn't even there! I tried re-installing and there was nothing different. And it came up command not found.

---

### Post by linux18 on 2010-07-29
```
 lshw -C network && iwlist scan && ifconfig && iwconfig > ~/net_debug.log   
```

this will create a file in your home directory called net_debug.log that you can post to help us get a better understanding of your problem.

---

### Post by lkraemer on 2010-07-30
Open a Terminal Window and use these commands to get more information
on your hardware, wireless, Windows loaded drivers, and Linux drivers
that are currently blacklisted. Copy & Paste to prevent errors!
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig
dmesg tail

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
Please post the output of each command........


After you have posted the above information, and everything appears to be
correct, you may want to try and bring it up manually.......

**Manual Method:**
If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```
example......for Airlink and Wlan0
sudo iwconfig Wlan0 essid "Airlink"


lk

---

