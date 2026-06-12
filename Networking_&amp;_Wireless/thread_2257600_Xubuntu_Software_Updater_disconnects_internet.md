---
title: "Xubuntu Software Updater disconnects internet"
date: 2014-12-21
forum: Networking &amp; Wireless
---

### Post by chris-willis-g on 2014-12-21
Hi there, hope you're all well.

I use my old laptop a lot - it's an Acer Aspire One ZG5 with 1.5gb memory, Atom 1.6 cpu ([http://www.engadget.com/products/acer/aspire/one/zg5/specs/](http://www.engadget.com/products/acer/aspire/one/zg5/specs/)). It came with Windows XP pre-installed. As XP isn't supported I've tested quite a few distros and settled on Xubuntu. Quick and clean, and surprisingly good looking.

I don't know what version I'm running. I can't find it in the system. I ran [http://www.howtogeek.com/howto/ubuntu/how-to-tell-what-version-of-ubuntu-you-are-running/](http://www.howtogeek.com/howto/ubuntu/how-to-tell-what-version-of-ubuntu-you-are-running/) this command and it says Ubuntu 14.04.1 LTS /n /l but I'm running Xubuntu, not Ubuntu. I downloaded it from the site about a week ago.

Right, well, the problem is when I use the Xubuntu "Software Updater" (Menu -> All Settings ->Software Updater), I can see everything that requires installation but when I click to Install, it disconnects all devices from the internet. By this, I mean all PC's, laptops, phones, iPads, etc lose internet connection. The modem we use doesn't appear to be affected. It flashes like it's supposed to and doesn't have the red eye on it which shows the modem's not working properly.

I've been googling this for a day and can replicate the problem (about 8 times so far). I don't think I'm doing anything wrong, and clearly something's not right.

Bit stumped, really. Any thoughts on remedying this will be appreciated.

---

### Post by r.stiltskin on 2014-12-21
You mentioned a modem.  Exactly what is it?  A DSL modem/router?  A cable modem/router?  The specific model name and number might help us help you.

How is the laptop connected to the internet?  Wifi?  Wired ethernet?

What happens to the other devices when the laptop connects to websites other than the Ubuntu repositories?

---

### Post by flaymond on 2014-12-21
If you stuck to update via the GUI (Software Updater), just run this command to update and upgrade your software via CLI/Terminal

```
sudo apt-get update && sudo apt-get upgrade
```


Xubuntu is using Ubuntu as the base. So it will appear as Ubuntu when you run the command even you using Xubuntu, Kubuntu or others.

---

### Post by chris-willis-g on 2014-12-21
I'm thinking probably best to re-install the whole thing. Doesn't take too long and might work. Good learning curve for me, also. If not, I'll put in the above info. Thanks for replying. Maybe I should've re-installed before my post. Beginner's mistake, sorry.

---

### Post by chris-willis-g on 2014-12-21
OK, so here's the update.

First install I did included updating per this thread [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108). The internet didn't disconnect and seemed to be flawless. This morning I installed updates through the Update Manager and it disconnected all devices from the internet (more about this later). When installing, I was not connected to the internet.

Second install was after I registered with this forum. This time, I didn't update through terminal to see if the error returned. I'm no computer wizard but it struck me as odd. Again, the sudo commands updated without a hitch, but using Update Manager disconnected all devices from the internet. Again, I didn't connect to the internet whilst installing.

(Additionally, although I installed SMPlayer through the GUI, it worked. When I installed Cheese, the error occurred again (eg, all devices disconnected.)

Third install, I selected to update as it installed. It disconnected all devices from the network, including the laptop I was using, so effectively I don't have an install and think I'll try Lubuntu for a time.

More info:
- the router is a Netgear DG834GU v5 ([http://support.netgear.com/product/DG834Gv5](http://support.netgear.com/product/DG834Gv5)).
- all devices connecting to it are wireless, including my ol' Acer
- to confirm, every device connected whilst installing updates simply disconnect. It includes Android and Apple phones and tablets, and desktop and laptop computers.
- no issues occurred when using the Firefox browser.

Thanks again.

---

### Post by r.stiltskin on 2014-12-21
During installation, did you use DHCP to automatically configure the Acer's network connection, or did you manually specify its IP address, etc.?

---

### Post by chris-willis-g on 2014-12-22
I've no idea what DCHP is. When installing, everything was done for me. I entered things like my name, laptop name, region, etc. It always detected network connections and I only had to enter its password.

I'm wondering though if it's possible to do something like change the internet driver to something else and see if that'd work. I wouldn't know how to start that process though.

---

### Post by r.stiltskin on 2014-12-22
DHCP stands for "Dynamic Host Configuration Protocol".  In simple terms it refers to a program that's running on your router which enables the router to automatically provide a network connection to your computer.  So, given that you let the installer configure your connection, yes, you used DHCP.  That being the case, I have no theory as to why or how the Update Manager is causing all other devices to lose their connections.

Suppose you run the installer but at the end do not update anything.  Then, can you open a browser on the laptop and access websites without interfering with your other devices?

If so, you can try installing Synaptic Package Manager (I prefer it to the Ubuntu software Center and Update Manager anyway) by running (in a terminal):
```

sudo apt-get install synaptic
```

Thereafter, you can use synaptic to do your updating and also for installing/uninstalling packages in general.

---

### Post by chris-willis-g on 2014-12-22
Hey, thanks for replying. Here's what I did:

1. Reinstalled Xubuntu and did not update during or after.
2. Using Firefox, I've accessed a number of sites without any type of disconnection.
3. After install I did the sudo command above and it didn't work, saying:

"Package synaptic is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source.

E: Package 'synaptic' has no installation candidate"

I appreciate the help. Will look into installing something else. Can't really use this Xubuntu. Will switch to something else I think.

Thanks again :)

---

### Post by chris-willis-g on 2014-12-22
I think somehow this is solved. I tried a couple of other Linux types and re-installed the Xubuntu system again without updating. I found out online how to install the Synaptic. Without thinking, I installed all updates using the built-in software updater and it didn't disconnect devices. Installed a few programs, and looks like this new system is chugging along quite nicely now :)

I can't see anywhere how installing Synaptic would've changed anything, or even a fresh install, but the Xubuntu system seems good on my little Acer now.

I'll mark as solved, thanks for all the input :) At least I'm aware how to install all these different distributions now in case someone I know wants one.

---

### Post by chris-willis-g on 2014-12-22
Ouch, it happened again. Will switch distros and close this thread.

---

### Post by flaymond on 2014-12-22
You can try lubuntu for light flavor...

---

### Post by chris-willis-g on 2014-12-22
I've had the same issues with Xubuntu, Lubuntu, Ubuntu, Kubuntu, and OpenSuse XFCE. Every time all devices are disconnected when I do an update. I'll add a new modem on to my Xmas list. Seems to be a very strange problem.

Thanks again, all. Suppose I have to put up with the XP for a little while longer. I'll be back in a few months ..!

---

### Post by r.stiltskin on 2014-12-22
Yeah, it sounds more like a flaky router than a 'buntu problem.  You may just be loading it with more traffic than it can handle.  Maybe XP is "working" simply because it's past its end-of-life and not updating itself anymore.  If you complain to your ISP maybe they'll replace the modem for free.  But just tell them it fails when you're downloading large files.  If you mention Xubuntu they'll probably say "we don't support Linux".

---

### Post by chris-willis-g on 2014-12-23
Thanks again r.stiltskin. I'm disappointed I can't switch to Linux. Will keep an eye out on cheap routers during the January sales. Thanks for your help and pointers. I've appreciated it.

---

### Post by kostkon on 2014-12-23
What's your wifi card. To find out give:
```
lspci | grep -i network
```

---

### Post by ancient2 on 2014-12-27
Been a learning curve this Linux stuff. I think the problem's solved by  installing something called WICD  ([https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)). Installed software updates and  no device disconnects. Touch wood. Fingers crossed. I just finished  downloading about 250mb of updates without a hitch.

The terminal code above (although I only put it in after installing this WICD thing) says ....

"Ethernet controller Qualcomm Atheros AR242x / AR542x Wireless [COLOR=#ff0000]Network [/COLOR]Adapter (PCI-Express) (rev01)" (The word network was in red in the terminal screen)

Another thing I could've tried is to switch channel, but hey, the WICD works so I'm not going to touch it.

Thanks again all, hope these posts help others at some point.

---

