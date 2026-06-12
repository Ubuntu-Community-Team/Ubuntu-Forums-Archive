---
title: "Ethernet not working"
date: 2014-01-21
forum: Networking &amp; Wireless
---

### Post by secuono on 2014-01-21
I've read these two threads. 
[http://ubuntuforums.org/showthread.php?t=830723&highlight=nforce+nic]("http://ubuntuforums.org/showthread.php?t=830723&highlight=nforce+nic")
[http://ubuntuforums.org/showthread.php?t=2198298]("http://ubuntuforums.org/showthread.php?t=2198298")


I entered this into terminal and now when I click on Network Connections, nothing comes up and the icon in the toolbar is now MIA. I restarted and no change, no internet and no NC window opening. 
```
$ sudo su
# rmmod forcedeth
# modprobe forcedeth msi=0 msix=0
# /etc/init.d/networking restart
```

I've just installed Lubuntu on a desktop that had Ubuntu 8 or similar. I would click to open the browser and enter Google.com. For a brief second, the real page would show. But suddenly, there came a blue screen hiding it saying something wasn't right. 
[ATTACH=CONFIG]249640[/ATTACH]

There is no way for the desktop to have wireless, we also have a router attached. I cannot check/mess with any settings now since the NC will no longer show up. How do I get the Network Connections to show again?? Are they still somehow disabled?
What else can I try to get things working?
Thanks.

---

### Post by secuono on 2014-01-21
Put in this code-
```
lspci -nnk | grep -iA2 net
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
lsmod
```


This is what I got. I don't have working ports to paste text into Pad and transfer it to a PC with internet. Sorry!
[ATTACH=CONFIG]249641[/ATTACH]
[ATTACH=CONFIG]249642[/ATTACH]
[ATTACH=CONFIG]249643[/ATTACH]
[ATTACH=CONFIG]249644[/ATTACH]

---

### Post by secuono on 2014-01-22
Ok, waited 3hrs and NC works. 
Yahoo.com works
EBGames.com works
Google.com does NOT work
Facebook.com works.........
Youtube doesn't work
Google of any kind doesn't work, so no Gmail. 
This site is now working.

---

### Post by secuono on 2014-01-22
anyone know why search engines don't work or youtube?
Ok, I can log into Facebook, but then it shows the blue screen.....
Help??

---

### Post by praseodym on 2014-01-22
Did you deactivate IPv6 in the network-manager applet?

---

### Post by secuono on 2014-01-22
How do you do that?

---

### Post by praseodym on 2014-01-22
Open the network-magaer applet, choose your wired connection -> Edit -> "IPv6-settings" set to "Ignore". Reconnect or reboot.

---

### Post by secuono on 2014-01-22
THANKS A TON!!! =D
Working now.

---

