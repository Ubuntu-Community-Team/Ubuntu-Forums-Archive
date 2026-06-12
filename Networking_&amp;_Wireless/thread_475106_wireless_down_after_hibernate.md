---
title: "wireless down after hibernate"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by tommie74 on 2007-06-15
I am using xubuntu feisty 7.04. When I wake my computer from hibernation the wireless network is down. Typing the following commands makes it functioning again: 
```
sudo ifdown -a
sudo ifup -a
```
The problem seems to be that after waking from hibernation my computer doesn´t have an ip-adress.
Anybody knows how to fix this?

---

### Post by yang on 2007-06-16
I too have the same problem - I have an ipw2100 and Ubuntu 7.04 with all latest updates. When coming back from hibernate, I have to do:

sudo ifconfig eth1 up
sudo dhclient

That's if I'm lucky and am associated with my AP when I resume - otherwise I have to do sudo iwconfig eth1 essid myap key blah, and I can never remember what the key is, so I restart instead.

I haven't tried the ifdown/ifup commands you have there.

---

### Post by tommie74 on 2007-06-17
The following command also gets it going again: ```
~$ sudo /etc/init.d/networking restart
```

---

### Post by tommie74 on 2007-06-17
I´ve solved this problem by changing /etc/default/acpi-support

Editing this file, look for the line below, where to add [networking] after that no problems anymore:

# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="networking"

Hope this will work for you to,
Thomas.

---

### Post by yang on 2007-06-17
> **tommie74 said:**
> I´ve solved this problem by changing /etc/default/acpi-support

Editing this file, look for the line below, where to add [networking] after that no problems anymore:

# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="networking"

Hope this will work for you to,
Thomas.
I don't actually see that; I only have:

```

STOP_SERVICES="mysql "

```

---

### Post by tommie74 on 2007-06-17
Yep, for me that was the same. If you write *networking* where now *mysql* is written, for me the problem was solved. If you want to keep mysql there, you might try

```
STOP_SERVICES="mysql networking"
```

but I don´t know if that will work. I have checked what mysql is, and it seems something that is not running on my computer.

so what works for me is:

```
STOP_SERVICES="networking"
```

---

### Post by tommie74 on 2007-06-17
And if that problem is solved, you might find that your sound is also not working after waking from hibernation... this problem was also solved on my computer:


[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893)

The problem seems to be related to a change in the kernel. An updated kernel is available for download:

[http://rookery.ubuntu.com/~kyle/kernels/salgado/2007-04-25/linux-image-2.6.20-15-generic_2.6.20-15.28_i386.deb](http://rookery.ubuntu.com/~kyle/kernels/salgado/2007-04-25/linux-image-2.6.20-15-generic_2.6.20-15.28_i386.deb)

install using package manager or 

```
dpkg -i /home/***your user name***/Desktop/linux-image-2.6.20-15-generic_2.6.20-15.28_i386.deb
```

hope this works for you too, if needed,
Thomas.

---

### Post by Woody@N87 on 2007-06-20
Yang,
  This is mostly for you.  Did you have to go the NDIS Wrapper route to get the IPW2100 working?  I've read docs that indicate it's supported directly by ubuntu, but I'm having quite a time getting the wireless working at all on a tablet computer.  
  It works fine wired.
     Any direction?
      thanks in advance.

---

### Post by yang on 2007-06-20
Mike - No, my wireless was working since installation (barring this particular problem) - I didn't have to do anything, really.

---

### Post by yang on 2007-06-20
Thomas - Adding that to the config file still doesn't seem to do the trick for me, sadly. Any other things I might try?

---

### Post by yang on 2007-08-31
Can anybody help me out?

Just to re-summarize: sometimes, after resuming from standby/hibernation, the network agent goes dumb - it doesn't auto-associate me with my wireless connection, and single-left-clicking on it no longer brings up a menu list of wifi APs, but rather the Connection Properties for my wireless interface (eth1). This is not just me not having a DHCP assignment (ifdown -a;ifup -a doesn't work); it's not having the association. Killing and restarting the network agent has no effect. Hence, I have to either go and find out what my AP's key is to pass it into iwconfig, or (more likely) reboot. I'm using a popular wireless controller (ipw2200).

To be honest, this is a large factor in making me lazy/reluctant to boot into Ubuntu. I would even be more comfortable knowing that there is a dev working on this.

---

### Post by Zef_ on 2007-09-02
i had a problem similar to this. However now my wireless simply does not associate me with my network at all, even after multiple shutdowns and restarts. The whole system is dead for no reason. I can see my network in the wireless network list, but it is simply impossible to connect to it.

---

### Post by AaronMT on 2007-09-21
I am experiencing the same problem and would like a solution.

---

### Post by duralex69 on 2007-12-06
Hi,

I have the same problem : wireless AND ethernet network are down after hibernation.
I have Kubuntu 7.10 on a laptop Dell Inspiron 6400 with Intel Wireless Card.

I've tried your commands but no results.
It is written on terminal :
" [I]Listening on LPF/eth0/00:1c:23:a7:87:b4
Sending on LPF/eth0/00:1c:23:a7:87:b4
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received
No working leases in persistent database - sleeping[/I]"

What does it mean, please ?

Thanks a lot for your help !

Alex

---

