---
title: "Getting wireless to work on kubuntu 10.10"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by maembe on 2011-04-07
I have a Toshiba Satellite L645-S4102 laptop.  I am connected via an ethernet cable but I can't seem to get wireless to work.  When I go to manage connections, I can't even click on the wireless tab.  I read that this means it is likely a driver issue.  I went into windows to uncheck the "allow windows to turn off wireless" tab already.  It also did sudo apt-get install knetworkmanager because it wasn't installed but I can't figure out how to get the drivers I need.  I found the additional drivers app, but I don't know what to do with it, it just says "no proprietary drivers are in use on this system" and displays two blank boxes.  

What else do I need to do?

---

### Post by rosencrantz on 2011-04-08
Hi maembe, 
you can look at /var/lib/NetworkManager/NetworkManager.state Make sure it says NetworkingEnabled=true.
I used it a lot, although in my case it probably had to do with botched hibernation issues.
Generally speaking, it shouldn't be a driver issue. Kubuntu/Ubuntu has very good hardware support, and Intel wireless chips are well supported generally.
You can also run [FONT="Courier New"]sudo lshw -C network[/FONT] and post the output here. You should get some chipset, driver and network information out of that.
Knetworkmanager is a curious package - it was KDE's main networking tool in the old KDE3 and initial KDE4 days, but it had always been in conflict with plasma-networking. On Maverick, it's only listed as a virtual package, so I assume they have switched completely to the plasma tool and keep the virtual package to satisfy dependencies, so Knetworkmanager probably doesn't make a difference.

---

### Post by rosencrantz on 2011-04-08
Another thing - it's the Realtek 8176 chip, isn't it?
Check lspci to make sure. I assumed it to be Intel, which it wasn't, and apparently there *are* driver issues.
There is a lengthy launchpad discussion regarding that chip, try  the instructions in the third to last post.
[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667)

---

### Post by maembe on 2011-04-08
The Network Controller is a Realtek RTL8188CE 802.11b/g/n WiFi adapter.  I assume that's what you're looking for.
sudo lshw -c network shows "*-Network unclaimed" before the information about the realtek adapter.  Not sure if that means anything or not.

Is there a way to copy/paste outputs from the command terminal?

---

### Post by maembe on 2011-04-08
Problem Solved.
I ran this:
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
from Canucked in this thread:  [http://ubuntuforums.org/showthread.php?t=1608908](http://ubuntuforums.org/showthread.php?t=1608908)

and I am currently connected to my wireless network.
Thanks for your help.

---

