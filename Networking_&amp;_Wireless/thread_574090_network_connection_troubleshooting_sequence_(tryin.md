---
title: "network connection troubleshooting sequence (trying HARD to transition from Windows)"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by mchnhed on 2007-10-12
Hi everyone,

I randomly became disconnected while connected from the Internet while I was connected to an external network (traveling). I restarted the computer and went into Windows and the Internet worked fine. So I went back in to Ubuntu and the Internet still didn't work.

After doing some research online I tried fooling around with the following commands:

netstat
ping (localhost) ([www.google.com](www.google.com))
ifconfig
arp
ethtool
route
mtr

But I really don't know much about these, so I didn't get far. Everything looked normal to me, except for "ping www.google.com", which returned "unknown host". Does this imply that there is a problem with DNS?

Now, I am trying very hard to use Windows less, but it's these kinds of issues that tend to force me back into the Windows (lack of time to spend hours upon hours learning the idiosyncrasies of Linux). Here is how I would normally do network troubleshooting in Windows (works 99.9% of the time):

1. Check the status of the LAN conncection (in the taskbar)
2. Check the status of the network connections (in the command line... typing "ipconfig")
3. Disable+Enable the Local Area Connection (in the Control Panel)
4. Repair the Local Area Connection (right click on the icon in the Control Panel)
5. In the command line, type "ipconfig /release", "ipconfig /renew")
6. Repeat steps 1-4
7. Disable+Enable the network driver (in Device Manager)
8. Uninstall+Reinstall the network driver
9. Steps 1-5

What I am wondering is... what are the equivalent steps to network troubleshooting in Linux systems?


I apologize if this is a newbie issue. Please see if you could offer some assistance, and let me know if I should post the results of anything from the terminal. THANKS.

---

### Post by Lulu58e2 on 2008-02-04
I'm a newb myself but I do know how to do the equivalent of an ipconfig /release + ipconfig /renew:

sudo ifdown <adapter>
sudo ifup <adapter>

where <adapter> is your network interface, e.g.:

sudo ifdown eth0
sudo ifup eth0

You should be able to figure out your interface from ifconfig ('f' instead of 'p')

You can combine them either in a shell script or on one line: 

sudo ifdown eth0 && sudo ifup eth0 

Where && means that the second command will only proceed if the first command succeeds.

---

### Post by Sit3UserX on 2008-03-19
> **Lulu58e2 said:**
> I'm a newb myself but I do know how to do the equivalent of an ipconfig /release + ipconfig /renew:

sudo ifdown <adapter>
sudo ifup <adapter>

where <adapter> is your network interface, e.g.:

sudo ifdown eth0
sudo ifup eth0

You should be able to figure out your interface from ifconfig ('f' instead of 'p')

You can combine them either in a shell script or on one line: 

sudo ifdown eth0 && sudo ifup eth0 

Where && means that the second command will only proceed if the first command succeeds.

xxxxx@yyyyyyyyy:~$ sudo ifdown eth0
ifdown: interface eth0 not configured

:confused:

---

### Post by Eiríkr on 2008-03-19
Hey there --

Since eth0 likely isn't the proper interface name on your machine, try this instead:
```
sudo ifdown -a
sudo ifup -a
```
The [font=courier]-a[/font] option tells the command to shut down and then bring up all interfaces marked for **a**utomatic configuration -- which should include your primary network interface, whatever its name might be.  

If that doesn't work, could you try running the following commands and post the results here:
```
ifconfig
cat /etc/network/interfaces
```
And if you're using a wireless connection, please also run and post the results from:
```
iwconfig
```

Wireless connectivity can be a real bear for any OSS OS, due to hardware manufacturers being extremely stingy with their specifications and releasing only drivers for Windows.  There are workarounds in many cases, but sometimes not.  Anyway, let us know what you find, and we'll go from there.  

Cheers,

Eiríkr

---

