---
title: "Name of interfaces in ifconfig"
date: 2016-05-15
forum: Networking &amp; Wireless
---

### Post by SpeakerForTheDeath on 2016-05-15
Hello,
I've a quastion on names of interfaces network.
Ifconfig command return on my device that names:
enp4s3 for eht0
enp4s7 for eth1
wlx54e6fc950000 for wlan

I trayed solution on this site:
[http://askubuntu.com/questions/590029/argh-udev-wont-stop-renaming-my-interfaces](http://askubuntu.com/questions/590029/argh-udev-wont-stop-renaming-my-interfaces)

But it's not working on my ubuntu 16.04 and debian testing.
I can use names for eth, but name of wlan is mac adress, and I want change that.
Someone knows other solution that problem?

---

### Post by houstonbofh on 2016-05-15
Welcome to "Predictable Network Interface Names" brought to you by systemd!  And yes it is a total mess, and most people hate it.  It does not even do what it is supposed to do and has bitten me several times.

How it works, and how to disable it is here.
[https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)

---

### Post by Morbius1 on 2016-05-15
Gosh, 
> enp4s3
You have an ethernet card (en) sitting on PCI bus 4 (p4) slot 3 (s3). What could be more intuitive?

Just messin' with y'all. Sorry.

---

### Post by SpeakerForTheDeath on 2016-05-15
> **Morbius1 said:**
> Gosh, 

You have an ethernet card (en) sitting on PCI bus 4 (p4) slot 3 (s3). What could be more intuitive?

Just messin' with y'all. Sorry.


Yes, It's simple. But name wlan as mac adress is terrible mistake in my opinion, becouse i must know each mac if I've few cards.

---

### Post by Morbius1 on 2016-05-15
I was actually trying to be sarcastic because I don't find it at all intuitive.

The argument for going with this new method is the same one used when we went from using /dev/sdxy to UUID=bunch-of-numbers to id different partitions. The actual booting of a computer has become so complex nobody knows how it works so depending of lunar cycles, humidity level, and cosmic radiation levels what the system sees as  sda1 on one boot it may see as sdb1 on another. Poettering ... urm ... Mr. Poettering simply extended this to networking hardware.

---

### Post by SpeakerForTheDeath on 2016-05-15
I'm used to standard name of interface. Name of ethernet I can understand.. and I remember. But if my card is use in USB port and i must type name that card.... 

@ houstonbofh

Solutions to this page (1 and 3) are the same as on askubuntu (my first post).
Or my "perfect" English is a problem.

---

### Post by houstonbofh on 2016-05-15
No, the instructions are very different, and much easier to parse in my link.  Look in the section "I don't like this, how do I disable this?" and pick one of the 3.  Option 1 is easiest.

---

### Post by SpeakerForTheDeath on 2016-05-15
Ok, I trayed first solution.
If I good understand I must copy that line 
```

ln -s /dev/null /etc/udev/rules.d/80-net-setup-link.rules

```
... and copy to my terminal? After that I restarted system and change nothing.

In 3. option "You pass the net.ifnames=0 on the kernel command line". Can I add that in etc/default/grub (as in article on askubuntu), Should I do it differently?

---

### Post by houstonbofh on 2016-05-16
Yes, you can add ```
GRUB_CMDLINE_LINUX_DEFAULT="biosdevname=0"
``` and don't forget to "sudo update-grub" after.

---

### Post by SpeakerForTheDeath on 2016-05-16
Thank You, that method works, but I had to add net.ifnames=0

```

GRUB_CMDLINE_LINUX_DEFAULT="net.ifnames=0 biosdevname=0"

```

Hmm but that method didin't change name of my wlan usb adapter, its name is still same. 

But, when I changed the old name interfaces i can't log by ssh to my device. 

```

ssh 192.168.1.106
ssh: connect to host 192.168.1.106 port 22: No route to host

```

---

