---
title: "profound proprietary driver issues"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by hubcity on 2009-03-27
i just updated to hardy and have been having trouble.  this is the fourth time.  things are great for a few days, then my wifi connection starts cutting out.  then it doesn't recognize my network.  then my computer fails to load at boot.  it does a system check as it loads, then goes to a fdschk (?) and says it fails.  so i tried to reload again from the disk, and allis up and running, but there is no wireless  connection option, and when i go to system>admin>hardware drivers, the list is blank.  but i know it's there, from checking in bios, and a terminal line i picked up from another thread showed that its still there.

i know i listed a lot of issues, but my most pressing is the wifi.  the laptop i am using now is prone to overheating from a failed fan....

---

### Post by mlentink on 2009-03-27
I would say the most pressing problem is your hardware. Your fan is gone, your system overheats, things get writtten or not to disk before or just after it cuts out....

Get yourself decent hardware, I would say. To suit ubuntu, you wont have to rob a bank to pay for it.

---

### Post by stderr on 2009-03-27
Hi hubcity. 

Under 8.10, wireless and wired connections are mainly handled by NetworkManager. You can configure them with System->Preferences->Network Configuration. Depending on which network card you have, you may need to do a bit of work to get the network card drivers running beforehand.

Which network card do you have? If you're unsure, you should be able to run the following to find out:

```
lshw -C network
```

If that moans about not having lshw, please run this first:

```
sudo apt-get install lshw
```

Knowing your network card, we should be able to better assist you.

Also, you say Ubuntu failed to load at boot. Do you remember the kind of messages you were getting? I'm just hoping your problems don't extend to massive hardware issues involving far too much heat and resultantly a dodgy hard drive! Depending on how bad things are, it may be an idea to run a hard drive surface check with something like Spinrite (you have to pay for it though), or just the HDD manufacturer's testing tools (check their website).

---

### Post by Sef on 2009-03-27
What are your system specs?

---

### Post by ByteJuggler on 2009-03-27
I would agree that you have hardware issues.  It almost sounds like you end up suffering corruption of various kinds, which can be caused by overheating and/or failing hardware.  Have you tried running the memory test from the Ubuntu boot menu?

---

### Post by hubcity on 2009-03-27
note... i'm working on a second computer...so i can't cut and paste..

lshw liste two *-networks

one is network controller...PRO/wireless 3945ABG network connection.  the other is described as ethernet interface, and product is BCM4401-BO 100Base-tx.

the pro wireles lists bus info:pci@0000:0c:00.0, version : 02, widthe :32 bits, capabilities:bus_master cap_list, config: driver=iwl3945 latency=0 module iwl3945...

hope that covers it...

when the system fails, it does a bus or driver check in the middle of loading ubuntu, goes into what looks like a bios page, running checks on a whole bunch of files, and then says something about bad root or missing kernals, and to do a fschk manually, which results in a repeat of the whole thing....but i cannot for the life of me remember specifics.

---

### Post by hubcity on 2009-03-27
please note...

the computer  I AM CURRENTLY COMMUNICATING WITH YOU is the one prone to overheating.  it is a backup.  my dell, software issues aside, is hearty and hale.  but thank you.

---

### Post by hubcity on 2009-03-27
> **Sef said:**
> What are your system specs?

i'm not sure where to find that info..is it something under system>administration or do you mean the specs of my actual laptop?  which is a dell latitude d520....

---

### Post by stderr on 2009-03-29
Right, just to clarify, I understand that you've already re-installed Ubuntu, and resultantly are no longer getting those boot errors, but can't get wifi working - is this correct?

You've actually got the same network card as my laptop. It's using the right driver, and it looks like the iwl3945 module is loaded. You could double-check that with:

```
cat /proc/modules | grep iwl3945
```

Also, double check that you've got a wireless interface under

```
iwconfig
```

There should be one entry (such as wlan0) which *doesn't* say "no wireless extensions".

If all that's fine, I think it should just be a case of hooking it up to an Access Point. Have you configured a connection under

System -> Preferences -> Network Configuration ?

Wireless tab, add, enter your network name under SSID, configure any security under wireless security, (and if you need to, setup a static IP under ipv4 settings, otherwise leave as DHCP).

After setting it up, it may help to restart network manager with:

```
sudo /etc/init.d/NetworkManager restart
```

---

