---
title: "Default route troubles."
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by lvl_jmpr on 2008-09-24
OK, so, the precursor to my situation: I've had VMWare installed, as I use it for my XP virtual machine.  And prior to now, I had my eth0 working on my native Xubuntu install and the network connection working on my Virtual XP Machine as well.

What has happened between the precursor and now (when I'm experiencing a problem): I've been having some ISP troubles, so, instead of fighting through their garbage, at one point I decided to use my PDA as a modem to connect to the internet (with pppd).  For reference purposes, the PDA is a Palm Centro and the modem program was USBModem.  The command I use to connect it is:
*sudo pppd /dev/ttyACM0 call ppp-script-treo/ppp-script-evdo-template*

So, I was able to get that connected and running.  But now that I'm not having trouble with my ISP and I wish to go back to my simple old eth0 connection, I'm having issues.

Whenever I restart my machine and execute the command:
*route -n*
My only connection now is my vmnet device (for VMWare).
When I run:
*ifconfig*
It lists eth0 on there, but from *route -n* there aren't any default routes to my router or ISP created.

It seems as though through my temporary (yet frequent) use of my USBModem with pppd, it stopped my eth0 from initializing normally.

I'm kind of reaching out here, does anyone have any ideas?  I've been looking for answers for almost a month now.

Thanks in advance to anyone who offers any suggestion.  :)

---

### Post by willca on 2008-09-25
Can you post the output for this?

sudo ifconfig 

Other things you can try.
sudo /etc/init.d/vmware stop
sudo /etc/init.d/networking restart

If at this point it does not get an IP... then try this.

sudo dhclient eth0

If at this time it gets an IP, then browse and all and test.
Then start vmware again

sudo /etc/init.d/vmware

---

### Post by lvl_jmpr on 2008-09-25
Firstly, thanks for posting a reply.
Secondly, I think that I forgot to mention a few things... After any reboot where I have my non-working connection and the only thing on my *route -n* is my vmnet device, the way for me to enable it again is doing:
*sudo ifdown vmnet0*
And then stopping all vmnet services, and doing:
*sudo ifup eth0* OR
*sudo ifup eth0 --force*

If I bring eth0 up without stopping the vmnet services/connection, it will bring up eth0, but it doesn't seem to route it to my router.  Strangely though, in that scenario, I can ping my router.

I also forgot to mention that I have my eth0 set as a static IP as I port forward with my router for many things, such as a VNC connection from my PDA.

I will edit this post and post the output of *sudo ifconfig* when I return home from work today, as to get my "bad" setup back, it will require a reboot and such.

Thanks again.  :)

---

### Post by HangMan101 on 2008-09-25
You say that your setup for eth0 is static did you configure the gateway to the ip of your router? 
and don't forget to configure a DNS server if you want todo name resolution for the internet 
(DNS server is likely your router)

(example below)

/etc/network/interfaces
```

auto lo eth0
iface lo inet loopback

iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0         
gateway 192.168.1.254             # router

```

/etc/resolv.conf (for dns)
```

nameserver 192.168.1.254

```

---

