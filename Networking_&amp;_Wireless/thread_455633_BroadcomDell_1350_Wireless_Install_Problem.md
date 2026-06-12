---
title: "Broadcom/Dell 1350 Wireless Install Problem"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by bgissal on 2007-05-26
First, here are a few details of my system:

Puter: Dell C400 Laptop
OS: Ubuntu Feisty Fawn 7.04 GNOME
Router: Belkin 54g Wireless

I have two problems:

1) When I go up to the network notification area, I see the Wireless Network "belkin 54g" option available, but when I click it, it seems to time out and just revert to the wired connection. When my Windows Wireless Drivers seemed to work correctly,I dropped the bcmwl5.inf file into it, but it said I already had the driver installed.

2) Now, when I try to access System->Administration -> Windows Wireless Drivers the app only runs for about a second and then disappears. I can't access the program to see if I have installed everything properly.

I used the following guidance to help me so far. I am an absolute n00b at this...

> **Rescue9 said:**
> Ok... I'm doing this from memory, so bear with me. Also, please note that the card I have is a Truemobile 1450, but I believe the procedure should be the same. Also, please note that a good majority of this information came from this page: [http://ubuntuforums.org/showthread.php?t=340689&highlight=ndiswrapper+4306]("http://ubuntuforums.org/showthread.php?t=340689&highlight=ndiswrapper+4306")

First, use synaptic package manager to get ndiswrapper-common and ndiswrapper-utils.

Then remove the bcm44xx module and blacklist it:
```
sudo modprobe -r bcm43xx
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

Now, for me, I had the Dell drivers on my windoze partition, so I just copied over the files. If you don't have the correct Truemobile drivers, you'll have to search them out for your card.

You will need the following files: bcm43xx.cat, bcmwl5.inf, and bcmwl5.sys. If your drivers are different, you will need the appropriate files, just make sure you have a .cat, .inf, and .sys file.

Now, we'll "install" the drivers into ndiswrapper.
```
sudo ndiswrapper -i bcmwl5.inf
```

After that we can load the ndiswrapper module and test it out:

```
sudo depmod -a
sudo modprobe ndiswrapper
```

Then we'll add the ndiswrapper module to the modules dir to make sure it autostarts on boot. 
NOTE: The link above has instructions on renaming your interface to wlan instead of eth. This isn't necessary, but does help out a bit if you have multiple interfaces.

```
sudo nano /etc/modprobe.d/ndiswrapper
```

That should get the driver up and running. If you have problems, check the above link first. If that doesn't seem to help, repost.

---

