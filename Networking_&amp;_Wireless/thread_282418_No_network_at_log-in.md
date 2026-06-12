---
title: "No network at log-in"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by zob on 2006-10-22
Hi.

I have this strange problem. My network-card (integrated in motherboard MSI K8N Neo2-FX) is not working when I log in to kubuntu.

Say I fire up my computer and login to the kubuntu desktop, open firefox - nothing.

I can make it work though. Opening up system administration and switching off eth0 and switching it back on, makes it run just fine.

I guess it would be easier to enter a terminal and as root do:
ifconfig eth0 down
ifconfig eth0 up
But I'm a newbie and I havn't got the hang of those terminals yet. But each day I use them more.

Now, the easiest by far would be if kubuntu would do it right by itself. Does anyone have a clue of what could be wrong here?

An ifconfig returns this (when its running that is):
```

root@ubuntu:/home/lars# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D3:A8:67:FF
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fea8:67ff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1583 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1330648 (1.2 MiB)  TX bytes:416423 (406.6 KiB)
          Interrupt:177

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:325 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:23760 (23.2 KiB)  TX bytes:23760 (23.2 KiB)


```

Edit: Just found out that I can do the job with a root terminal and a:
```
root@ubuntu:/home/lars# dhclient eth0
```
So if there is no other way, maybe it's possible to automate this action!?
I would of course prefer to find out what is wrong but...

Second EDIT:
I found out, thru forum research, that it must have something to do with the file in /etc/network/ called interfaces. Mine is like this:
> lars@ubuntu:/etc/network$ cat interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface

auto eth0
iface eth0 inet dhcp

Do you see anything here???

---

### Post by daou on 2006-10-22
I don't know what's wrong, but if the command fixes the network connection, you can make a shell script and tell it to run at start-up. A good temporary fix, if nothing else.

The script you have to make would be something like:

```
#!/bin/bash
dhclient eth0
```

and then make it executable. Then edit your session to run it at login.

---

### Post by zob on 2006-10-22
Thanks. I was thinking about doing something like that. The problem is that I don't know how to do it.
2 things:

How do I make something executable. Is it a file extension like in windows?

Where do I find the session to edit?

I'm going to try to find out, but you are very welcome to give me a hint.

---

### Post by daou on 2006-10-22
I'm not familiar with the KDE environment, but if it is anything like Gnome, you can edit your session from the System->Preferences->Session menu. There should be a place where you can tell the session to load a program at startup.

But before this you have to make the shell script like I told you earlier. You can use a text-editor to make it and save it with any name you like. For example, "fix_network.sh". The .sh is not needed. Unlike Windows, Linux doesn't care what extension a file has. It's only meant to help users remember what kind of file it is.

Then right-click and edit its properties and give it executable permissions. Another way to give a file executable permission is to do it through commandline:

```
chmod a+x fix_network.sh
```

---

### Post by daou on 2006-10-22
There might be some problems executing the script at startup, however. If the command you try to execute with the script needs sudo privileges, you'll need to hard-code your password into the file which is certainly not recommended from a security point-of-view. Or then have it prompt for your password which becomes a hassle if you need to type your password twice to log in completely.

---

### Post by zob on 2006-10-22
Kiitos daou;) 

I'm sorry I think I'm giving up for tonight. I can't find anything that looks what you have on your ubuntu.
I think I'm of to bed and I'll have another look at it tomorrow.

Just one more stupid question:
Can I by any chance put that shell script, or something like it, into my /etc/network/interfaces file???
My intuition tells me that etc/network/interfaces is close to the origin of the problem.

---

### Post by daou on 2006-10-22
There is a way (quite easy) to get around the sudo problem with the script. It does, however, require some fiddling with boot options so you'll have to do it at your own risk.

It takes 5 steps.

1. Make the script

2. Copy it to your /etc/init.d/ folder, ex:
```
sudo cp fix_network.sh /etc/init.d/
```

3. Go to the /etc/init.d/ folder
```
cd /etc/init.d/
```

4. Give the script correct read/write/execute permissions
```
sudo chmod 755 fix_network.sh
```

5. Update your boot config to load the script
```
sudo update-rc.d fix_network defaults
```

Now try rebooting the computer. Hopefully the network should be operational. This should work on KDE just like Gnome.

---

### Post by daou on 2006-10-22
You're welcome :-D . The script won't do any good in the interfaces folder. Yes, the problem is probably in the interfaces, but I've had some bad experiences with fiddling with those settings (I had a similar problem once. Internet never worked because it used the wrong network card everytime at boot to connect to the internet. Don't remember what I did exactly though).

---

