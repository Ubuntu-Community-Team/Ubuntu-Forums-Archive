---
title: "Cannot open Windows Wireless Drivers (ndiswrapper)"
date: 2015-03-03
forum: Networking &amp; Wireless
---

### Post by KayeNg on 2015-03-03
Hi guys, I download the ndiswrapper thru Software Center.  When I go to System Tools -> Windows Wirelss Drivers , a small window pops up and disappears.  It can't be opened.  

Before I tried the Software Center approach, I tried this [http://tinymelinux.com/forum/thread-865-post-3760.html#pid3760](http://tinymelinux.com/forum/thread-865-post-3760.html#pid3760)

I failed at that, so I tried thru Software Center

Is it possible my system is corrupted? Should I just reinstall the whole OS?

---

### Post by Bucky Ball on 2015-03-03
*Thread moved to **Networking & Wireless**.*

Please give us the output of:

```
sudo lshw -C network
```

Why do you think you need ndiswrapper? It is a nightmare generally and best to avoid, as well as being largely superceded and rarely used now. The thread you linked to is nearly five years old, a long time in Linux land. ;)

[QUOTE=KayeNg] Is it possible my system is corrupted? Should I just reinstall the whole OS? [/QUOTE]

Doubtful and definately no. Don't reinstall. What release are you using?

---

### Post by KayeNg on 2015-03-04
Hey Bucky Ball, currently I'm using my smart phone's wifi connection for my  desktop computer (which is running Lubuntu 14.04 (?) the Long Term Support).  I plug the smart phone via a cable into the usb port of my desktop computer in order to have internet connection.

homet@homet-01:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 02
       serial: 00:19:66:74:8d:e8
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:d800(size=256) memory:f9fff000-f9ffffff memory:f9fe0000-f9feffff memory:fdfe0000-fdffffff
homet@homet-01:~$

I need the ndiswrapper so I can use my Linksys AE2500 on the Lubuntu system.  it's a wireless wifi adapter.  Does ndiswrapper not work anymore? it's in the repository.  It still worked 3 years ago, by the way. [http://www.grailbox.com/2012/05/installing-cisco-linksys-ae2500-wireless-adapter-in-linux/](http://www.grailbox.com/2012/05/installing-cisco-linksys-ae2500-wireless-adapter-in-linux/)

---

### Post by KayeNg on 2015-03-04
By the way Bucky Ball, I highly value your opinion, but on the off chance that my Lubuntu OS has been corrupted, would it be because I executed the following commands?

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
and I think "purge" also.

Because when I executed one of these commands (forgot which one caused it), my gnome movie player was gone.  Tried it on both laptop and desktop computers.  Gnome movie player, which comes with Lubuntu installation, disappeared.  So I'm pretty sure one of the above commands was the culprit for the missing gnome movie player.  And now I'm wondering if it has anything to do with ndiswrapper not being able to install properly.

---

### Post by Bucky Ball on 2015-03-04
> **KayeNg said:**
> By the way Bucky Ball, I highly value your opinion, but on the off chance that my Lubuntu OS has been corrupted, would it be because I executed the following commands?

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
and I think "purge" also.



Doubtful. After that, you should run:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

What did you purge? That is different and you need to purge a particular package/app. Try and remember, could be important.

Looks like your Linksys is one of the very few devices that needs ndiswrapper, yes (I'd personally buy a cheapie something that is Linux compatible and works out of the box). [This]("http://www.grailbox.com/2012/05/installing-cisco-linksys-ae2500-wireless-adapter-in-linux/") link might help. Apparently you need to use the 32bit Win driver with ndiswrapper and not the 64bit one.

---

### Post by KayeNg on 2015-03-04
The link you gave me is the one I started with.  I failed with that, then I turned to Software Center, failed with that as well.  Did you read about the part where my gnome movie player disappeared? I'm almost certain the above commands or the purge was responsible, because it happened TWICE, on my laptop and on my desktop.  Two separate computers.  The only things I remember that I wanted to uninstall was Gnumeric and Abiword.  I did not try to uninstall gnome movie player.

---

### Post by Bucky Ball on 2015-03-04
So you purged those two programs?

---

### Post by KayeNg on 2015-03-05
I uninstalled them thru the Software Center ("Remove from the system" button).  Then I purged. Does purge command require a specific program name? like "pugre gnumeric"? If so, I probably did that.

---

### Post by KayeNg on 2015-03-05
By the way, I executed the 3 commands you suggested:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

Then just for good measure I reinstalled mplayer thru Software Center.  Then I installed ndiswrapper thru Software Center too. This is what I got.



homet@homet-01:~$ sudo ndisgtk
Traceback (most recent call last):
  File "/usr/sbin/ndisgtk", line 408, in <module>
    NdisGTK()
  File "/usr/sbin/ndisgtk", line 123, in __init__
    self.setup_driver_list()
  File "/usr/sbin/ndisgtk", line 151, in setup_driver_list
    self.get_driver_list()
  File "/usr/sbin/ndisgtk", line 163, in get_driver_list
    output,retcode = getoutput("ndiswrapper", "-l")
  File "/usr/sbin/ndisgtk", line 35, in getoutput
    universal_newlines=True)
  File "/usr/lib/python3.4/subprocess.py", line 848, in __init__
    restore_signals, start_new_session)
  File "/usr/lib/python3.4/subprocess.py", line 1446, in _execute_child
    raise child_exception_type(errno_num, err_msg)
FileNotFoundError: [Errno 2] No such file or directory: 'ndiswrapper'
homet@homet-01:~$

Any ideas?

---

### Post by KayeNg on 2015-03-06
No idea?

---

### Post by Bucky Ball on 2015-03-06
Sorry. Don't know anything about ndiswrapper. Haven't used it since 2007 (and then only briefly) and make a point of buying hardware that 'just works' where possible. ;)

---

### Post by KayeNg on 2015-03-07
I re-installed Lubuntu and downloaded the ndiswrapper thru Software Center.  It worked.  I'm currently connected to the internet thru my Linksys AE2500.  Trying to connect is a frustrating hit and miss, though.  If I reboot my computer, it probably won't reconnect automatically, and I have to tweak the connection for several minutes before it would work again.

---

