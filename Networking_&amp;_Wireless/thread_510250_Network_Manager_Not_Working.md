---
title: "Network Manager Not Working"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by Luther786 on 2007-07-26
I'm having some issues with the network manager.  I'm currently running Feisty Fawn 7.04 and can't seem to get the network manager to work.  It runs and I can get it to display my wireless network I have set up in a list of available networks.  However, when I connect to it such that the nifty little bars show on the menu bar it disconnects me from the internet (mozilla won't work, nor any other connection-requiring applications).  I can do a manual configuration and type in the network name and do either a static IP or an automatic dhcp and everything is dandy again.  I am little irritated and would appreciate a reply if anyone else has had this problem.

Thanks :)

---

### Post by MrFSL on 2007-07-26
Welcome to the forum!

This question has been answered a million times on this forum; in a million different ways; covering just about every possible option for a fix; over just about all possible hardware; using all possible software; in all possible configurations.

There are also several Documents and HowTo's and Community Documents here and available through the Ubuntu Help documentation.

I hope I don't sound standoff-ish because that is definitely NOT what this forum is all about. The wonderful thing about this forum is that people of ALL skills, levels, and experience can openly collaborate regardless of the question. It's just that you are more likely to get replies and help if you have exhausted your other resources first. :)

That being said I'll do my best to assist: ;)

This is a wireless connection; are you using encryption (WEP/WPA/etc)?

What are you using for a wireless adapter? You can try either of these:
```
lspci | grep -i wireless
# or
lspci | grep -i net
```

Once connected (seemingly connected) what is the output of:
```
iwconfig
```

You are seeing a connection but applications don't seem to work what is the output of:
```
sudo cat /etc/resov.conf
```

Can you ping a remote host?
```
ping www.google.com
```

Can you ping a remote address?
```
ping 209.85.173.99 
```

---

### Post by Luther786 on 2007-07-26
Hey thanks for actually responding...  I figured I would be flamed as a newbie and am glad I was not.

I tried what you put down.   This is the wireless card I have (I'll put what the command line says you can probably interpret that better than my botched computer jargon)

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

iwconfig gave me
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Luther"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:B3:AC:DC:3A
          Bit Rate:12 Mb/s   Tx-Power:14 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=35/100  Signal level=-88 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:699   Missed beacon:0

As for sudo cat /etc/resov.conf- There apparently is no such directory or file
I cannot ping a remote host or address when allegedly connected using the network manager.  If I play around with a manual configuration either using a static IP address or an automatic configuration once I type in the network name I can ping both a remote host and address.  
Do you know of any pages that explain how to change things around in the network manager?  All I have found is stuff about how to install it, how to use it and not how to fix some sort of weird glitch I probably created on the install...

Thanks again

---

### Post by MrFSL on 2007-07-26
If you look at my posts on this forum you will find that I am not a fan of Network Manager at all in Ubuntu. I prefer and always recommend a program called WICD ( I think it stands for Wireless Internet Connection Daemon or something like that.)

Looking at the output from your previous post it looks like you have an Intel wireless card so it should have a driver loaded in Ubuntu. Your output of iwconfig shows that you only have one wireless adapter and it is seeing your AP with alright strength and acceptable signal to noise ratio. The file resolv.conf holds the addresses on your DNS servers but since you can't ping a IP either I am not worried about dns servers so you have a bit of a mystery. What do you mean about "manual configuration?" 

> If I play around with a manual configuration either using a static IP address or an automatic configuration once I type in the network name I can ping both a remote host and address...

Are you talking about a manual configuration in Network Manager? Or a manual configuration such as editing the file *"/etc/network/interfaces"*. I thought you meant the later....

Anyhow, for wireless internet WICD is the only application that I have gotten to work perfectly 99% of the time.

If you are interested you can check out their website at:
[http://wicd.sourceforge.net](http://wicd.sourceforge.net)

Here are some basic instructions:

1) Download the wicd deb file from here:
[http://superb-west.dl.sourceforge.net/sourceforge/wicd/wicd_1.3.1-all.deb](http://superb-west.dl.sourceforge.net/sourceforge/wicd/wicd_1.3.1-all.deb)

2) Open a terminal and stop the network manager applet
```
sudo killall nm-applet
```

3) Remove network manager
```
sudo apt-get remove network-manager 
```

4) Then double click on the Wicd deb file you downloaded or open a terminal... navigate to the directory where wicd was saved and install it using dpkg. Something like this:
```
cd ~/Desktop/
sudo dpkg -i wicd_1.3.1-all.deb
```

5) You can then restart wicd from init.d (if you don't know what that is then you can just restart your computer and I suggest you look into starting/stopping daemons and services from /etc/init.d sometime since it is a good skill to have in Linux.

6) There should be wicd launcher in your applications menu but if not you can press <atl><F2> and run:
```
/opt/wicd/tray.py
# OR
/opt/wicd/gui.py
```

Let everyone here know how things turn out for you alright? By all means don't feel obligated to use wicd just cause I said so. I hate it when I ask for help with an application and everyone just tells me to use something else. Sometimes I don't care if there is something better out there... I just want to get a certain program working.

---

