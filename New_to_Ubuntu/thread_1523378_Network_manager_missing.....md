---
title: "Network manager missing...."
date: 2010-07-03
forum: New to Ubuntu
---

### Post by tweety_r78 on 2010-07-03
We tried to fix so we could connect to internet via USB, but in the process I managed to uninstall the network-manager, and totally remove it it seems. 
I have downloaded via ubuntu's homepage the network-manager and installed it through a USB port. But it won't show. and there is now no way to connect to internet. 
Could someone please help me solve this? :)

---

### Post by warfacegod on 2010-07-03
Right click a panel> select Add to Panel> find the "Indicator Area"> click Add.

---

### Post by tweety_r78 on 2010-07-03
Thank you for answering, but I'm afraid that did not solve the problem...
The network manager is not there either.. We did a really good job removing the network-manager obviously.. I am not 100% sure I managed to install the correct version of the network manager either.
I have installed: [network-manager-dev_0.8-0ubuntu3_i386.deb]("http://no.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager-dev_0.8-0ubuntu3_i386.deb") which I found on 
[http://no.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/](http://no.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/).
Should this be sufficient? Or do I need somethng else? And do I need to launch it somehow in Terminal?

---

### Post by spiky001 on 2010-07-03
Just a thought is it setup in start up applications just check see if it is ticked

---

### Post by warfacegod on 2010-07-03
You have the Development package (that's the dev in the file name). You need network-manager 0.8-0ubuntu3. Choose the .deb package that suits your computer, i386 is for 32 bit and AMD64 is for 64 bit. Processor brand doesn't matter. It's at the bottom of the page.

I believe you'll also need the network-manager-gnome 0.8-0ubuntu3. Unfortunately, I don't see it in the list. Try the highest numbered version and then do an update.

---

### Post by ajgreeny on 2010-07-03
Is NetworkManager running and active?

Have a look in ```
System >Administration >System Monitor
``` to see if it's listed in processes (with "all processes" showing, not just "your processes"), or run ```
ps aux | grep Network
``` in terminal.

---

### Post by tweety_r78 on 2010-07-03
Yes, it is ticked off in the start up panel...:) 
But I'm not sure wether the path is correct. The folder containing the network manager I've downloaded is placed on the desktop, so I've tried editing the path to there. But that did not help.... 
If it is difficult advising on the mess I've started, I'll be very happy if someone could guide me through the whole process on retrieving the network manager:)

---

### Post by tweety_r78 on 2010-07-03
I haven't checked that, thnx for the tip:)
I'll check this in a few minutes, the screen is currently occupied with a certain football match...

---

### Post by warfacegod on 2010-07-03
With .deb files settings a path is unnecessary. Simply double click the file and it will install where it needs to go.

---

### Post by tweety_r78 on 2010-07-03
> **ajgreeny said:**
> Is NetworkManager running and active?
 
Have a look in ```
System >Administration >System Monitor
``` to see if it's listed in processes (with "all processes" showing, not just "your processes"), or run ```
ps aux | grep Network
``` in terminal.
 
I have tried this now, I can't see it in the system monitor, and when I type the command in the Terminal I get some sort of respons, but I'm not quite sure what I'm looking for here...

---

### Post by tweety_r78 on 2010-07-03
> **warfacegod said:**
> You have the Development package (that's the dev in the file name). You need network-manager 0.8-0ubuntu3. Choose the .deb package that suits your computer, i386 is for 32 bit and AMD64 is for 64 bit. Processor brand doesn't matter. It's at the bottom of the page.
 
I believe you'll also need the network-manager-gnome 0.8-0ubuntu3. Unfortunately, I don't see it in the list. Try the highest numbered version and then do an update.
 
I'm sorry, I do have the deb package not the dev... I'll try to install the gnome thing as well. Thank you for all your help here:)

---

### Post by bshosey on 2010-07-03
I just did a fresh install on a system and have this problem as well. It is running and I can set network seeting in the System>Preverences>Network Connections. I aslo have the notification applet on the gnome panel. But no icon for network in the notifacation applet

---

### Post by warfacegod on 2010-07-03
> **tweety_r78 said:**
> I'm sorry, I do have the deb package not the dev... I'll try to install the gnome thing as well. Thank you for all your help here:)

network-manager-***dev***_0.8-0ubuntu3_i386.deb

You have a .deb but it is the -dev package, not the one you want.

---

### Post by warfacegod on 2010-07-03
> **bshosey said:**
> I just did a fresh install on a system and have this problem as well. It is running and I can set network seeting in the System>Preverences>Network Connections. I aslo have the notification applet on the gnome panel. But no icon for network in the notifacation applet

Assuming you are using 10.04 Lucid, you want the Indicator Applet not the Notification Area.

---

### Post by ajgreeny on 2010-07-03
This is what you should see, or something similar, when you run that **ps** command
```
ps aux | grep Network
root       791  0.0  0.1  18644  3780 ?        Ssl  19:48   0:00 NetworkManager
root       897  0.0  0.0   2228   956 ?        S    19:48   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-18aa4e28-4e47-4fb5-82db-4b9d165ee687-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
*username*    2842  0.0  0.0   3324   860 pts/0    S+   21:49   0:00 grep --color=auto Network
```
By the way, the item showing in the Startup Application list is just the panel applet, not the actual manager.

---

### Post by bshosey on 2010-07-03
I have the enolope, speacker icon, and bluet tooth icon I do have the inicator applet on the panel and yes I am running 10.4

---

### Post by tweety_r78 on 2010-07-03
> **tweety_r78 said:**
> I'm sorry, I do have the deb package not the dev... I'll try to install the gnome thing as well. Thank you for all your help here:)
 
I've now tried to install the newest version of the gnome applet, but the version is too old, it doen't seem like it is compatibel with Lucid.
 
I've also tried downloading a version on the gnome projects website, there is one version called LATEST. But this is a gz file, and it won't extract the files..
 
Do you have any other tips?

---

### Post by tweety_r78 on 2010-07-03
> **ajgreeny said:**
> This is what you should see, or something similar, when you run that **ps** command
```
ps aux | grep Network
root       791  0.0  0.1  18644  3780 ?        Ssl  19:48   0:00 NetworkManager
root       897  0.0  0.0   2228   956 ?        S    19:48   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-18aa4e28-4e47-4fb5-82db-4b9d165ee687-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
*username*    2842  0.0  0.0   3324   860 pts/0    S+   21:49   0:00 grep --color=auto Network
```
By the way, the item showing in the Startup Application list is just the panel applet, not the actual manager.
 
I get this when running the command:
 
root    760       0.0   0.2    8404   3784    ?     Ss    Jul01    0:27   NetworkManager
user    14690   0.0   0.0   3324   888  pts/0 S+ 22:33    0:00  grep  --color=au to Network
 
 
Does this make any sense to you?

---

### Post by tweety_r78 on 2010-07-03
> **warfacegod said:**
> network-manager-***dev***_0.8-0ubuntu3_i386.deb
 
You have a .deb but it is the -dev package, not the one you want.
 
No, I wrote it wrong the first time you see...
The package I downloaded and installed is this: [network-manager_0.8-0ubuntu3_i386.deb]("http://no.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.8-0ubuntu3_i386.deb"). That is the right one isn't it?

---

### Post by warfacegod on 2010-07-03
> **tweety_r78 said:**
> No, I wrote it wrong the first time you see...
The package I downloaded and installed is this: [network-manager_0.8-0ubuntu3_i386.deb]("http://no.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.8-0ubuntu3_i386.deb"). That is the right one isn't it?

Ah! Now I understand. Yes that is the correct one. If you can find the network-manager-gnome with the same version numbers, you should be back in business.

Looking at your previous post. it looks like you may have Internet access. Try this code in the Terminal:

```
sudo apt-get install network-manager-gnome
```

---

### Post by bshosey on 2010-07-03
I also have that packages installed as well.

---

### Post by tweety_r78 on 2010-07-03
> **warfacegod said:**
> Ah! Now I understand. Yes that is the correct one. If you can find the network-manager-gnome with the same version numbers, you should be back in business.
 
Looking at your previous post. it looks like you may have Internet access. Try this code in the Terminal:
 
```
sudo apt-get install network-manager-gnome
```
 
That didn't work unfortunately...:( It seems like the lack of internet connection is the problem, because it claims it fails to get the archives from no.archive.ubuntu.com..
I do think I found the right file though: [http://ftp.gnome.org/pub/GNOME/sources/network-manager-applet/0.8/](http://ftp.gnome.org/pub/GNOME/sources/network-manager-applet/0.8/)
 [LATEST-IS-0.8.0.999]("http://ftp.gnome.org/pub/GNOME/sources/network-manager-applet/0.8/LATEST-IS-0.8.0.999")
 
Do you think that sounds like the right one?
But then again... this is a .gz file, and I don't know how to make an installation from a file like this. I have tried to extract the files, but it won't do it. Do you have any idea why?

---

### Post by warfacegod on 2010-07-03
That looks correct to me. No idea why you can't extract.

---

### Post by bshosey on 2010-07-03
Try this in terminal

sudo gedit /etc/network/interfaces

Edit file to look like this

auto lo
iface lo inet loopback

then reboot system and see if it is there

---

