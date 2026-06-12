---
title: "Not accessing router"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by aa4bb on 2009-09-22
This is my first experience with Xubuntu (or any Ubuntu).

I successfully installed 9.04 from Alternate disk on 256 M HP Pavilion desktop. It has a generic Ethernet card that seems to have been identified by Xubuntu - there is a MAC address when I look at it through Terminal with - I think it's called - ifconfig. It is directly connected to a Linksys router that is connected to the Internet by a Sprint broadband card (WRT54G3G). Both sides are configured for DHCP. 

The router and the computer do not connect. The computer does not find the Internet and also cannot access the Web control page on the router 192.168.1.1.

When I was installing from the CD, there was a point at which it asked to install the network. Because I was not where I could hook it to the router at that point, I selected "Install later".

It's not impossible that the Ethernet card is bad, but assuming that it's not, is there something that I have failed to do that is necessary for it to work?

Ed

---

### Post by halitech on 2009-09-22
when you ran sudo ifconfig, what was the IP address that was shown as well?

---

### Post by aa4bb on 2009-09-22
I'm afraid I don't yet know what sudo is, but I typed sudo ifconfig and it showed:

inet addr 127.0.0.1 mask 255.0.0.0

and a bunch of other stuff...

---

### Post by halitech on 2009-09-22
Sudo is what allows you to run admin tasks (ifconfig is one of them)

If the only IP address you are seeing is 127.0.0.1 then it probably shows lo next to it. Her's mine as an example

```
daryl@debian:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:bf:b2:f2:b4  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:bfff:feb2:f2b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10705678 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11026172 errors:122 dropped:0 overruns:0 carrier:122
          collisions:0 txqueuelen:1000 
          RX bytes:7188676632 (6.6 GiB)  TX bytes:4365839672 (4.0 GiB)
          Interrupt:21 Base address:0xdc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6088 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6088 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:994287 (970.9 KiB)  TX bytes:994287 (970.9 KiB)

```

can you post the output of  ```
lspci | grep Ethernet 
```

---

### Post by aa4bb on 2009-09-22
01:0b.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)

---

### Post by halitech on 2009-09-22
thats the exact same card I have (onboard AMD board) and it worked out of the box. When you run sudo ifconfig do you get eth0 and lo or just lo info?

---

### Post by aa4bb on 2009-09-22
Just lo

---

### Post by halitech on 2009-09-22
try installing network manager, it should ask for the cd

```
sudo apt-get install network-manager
```
it will ask for your password, type it in (you won't see anything) and hit enter

---

### Post by aa4bb on 2009-09-22
It tells me that network manager is already the latest version.

However, I don't find network manager in the applications->system menu!?!

---

### Post by halitech on 2009-09-22
it won't show up in the menu. I'm not sure why its not working.

---

### Post by aa4bb on 2009-09-22
Thanks for your help. At least I know a few more things that I didn't before. I'll keep messing around and seeing what I can figure out.

---

### Post by relay_man on 2009-09-22
Linksys routers (WRT 54XXX)  can be a pain.  Connection problems aren't always the fault of your computer.

If you are connected to the router using a cable:

1. Shut down your computer.

2. Disconnect the cable connecting the computer in question to the router.

2. Remove  power from the router for 30 seconds.  Restore power and let the router complete it's reboot.  

3. Reconnect the cable to the router.

4. Reboot your computer.  After you sign in, wait for at least 3 minutes without disturbing anything.  Give the computer a chance to negotiate a new connection.

If that doesn't work, I would try a hard reset of the router.
I don't know what it is about Linksys routers that causes this, but I know from past experience that is does happen with regularity.

If you have to do a hard reset, make sure you save the configuration or write everything down before you reset.

For me, 8.10 and 9.04 have been very good at establishing wired connections on their own.  I'd try the router thing before I changed too many network settings.

---

### Post by halitech on 2009-09-22
if they don't have a device showing in ifconfig then how could that be an issue with the router?

---

### Post by aa4bb on 2009-09-22
Thank you for your suggestion. I went through the sequence you set out, but the router and computer still did not recognize one another.

I will try resetting the router tomorrow. Thanks again!

---

### Post by aa4bb on 2009-09-22
Just saw your last reply, halitech, and I see your point.

Thanks for your help.

I'm shutting down for now.

---

### Post by relay_man on 2009-09-23
I've read more carefully and I see your point now halitech.  I confused your earlier post with the OP's response.

My apologies to you and OP.
I'll be more careful the next time.

Halitech is on the right track.   You've got to get the network card (eth0) recognized and running before you pursue any other possible problems.

---

### Post by aa4bb on 2009-09-23
I've now used a USB Ethernet adapter, and it works fine. Must be something bad about the Ethernet card. At any rate, I'm airborne on the Internet. Thanks!

---

