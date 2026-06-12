---
title: "A simple bridge for Eth0"
date: 2006-10-07
forum: Networking &amp; Wireless
---

### Post by tesmar on 2006-10-07
Hi all, 

I am new to Ubuntu (using 6.06) and to these forums, but I have a quick question, and I hope the experts can help :)

I am trying to set up a simple bridge on eth0 to br0, so that when I want to access the internet, I have to go through br0, not eth0. I also want to use this so that Qemu using [Argos]("http://www.few.vu.nl/argos/") can access the internet. I have this in the /etc/net/interface file:
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto br0
iface br0 inet dhcp
  pre-up ifconfig eth0 down
  pre-up brctl addbr br0
  pre-up brctl addif br0 eth0
  pre-up ifconfig eth0 up
  post-down ifconfig eth0 down
  post-down brctl delif br0 eth0


auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

But whenever I reboot, both eth0 and br0 show up with 2 different DHCP assigned addresses, and lo appears twice; not quite the effect I was going for. Any takers?](*,) :mrgreen:

---

### Post by tesmar on 2006-10-07
I imagine it would work the same way in Debian, or would I be mistaken about that? Is there some other place on the system causing eth0 to also obtain a separate IP addr? So confused....

---

### Post by tesmar on 2006-10-07
Has anyone gotten an ethernet bridge working inside of Ubuntu????

---

### Post by tesmar on 2006-10-10
IS it alright o bump your own thread?

---

### Post by mips on 2006-10-10
Suppose so.

I never use bridging as it is kinda old school.

Have you tried vmware server as i know you dont have to bridge interfaces there.

---

### Post by tesmar on 2006-10-10
> **mips said:**
> Suppose so.

I never use bridging as it is kinda old school.

Have you tried vmware server as i know you dont have to bridge interfaces there.
For this project, I need bridging for Argos to work. And the project is Qemu-specific. I wish I could, it would be soooo much easier then :)

---

### Post by tesmar on 2006-10-10
bump

---

### Post by tesmar on 2006-10-11
bump

---

### Post by Mithrilhall on 2006-10-19
Does this help?

[http://www.linuxjournal.com/article/8172](http://www.linuxjournal.com/article/8172)

---

### Post by tesmar on 2006-11-02
No, not really; I still cannot get it to work; I though it would be so simple, but right after I take down eth0, add the bridge and binf it to eth0, br0 cannot get an IP addr, and I cannot even access the net from the host machine.

Any ideas?](*,) ](*,) ](*,)

---

### Post by tesmar on 2006-11-15
Ok,

I have it hacked to work, but it is kinda weird. I get a bridge & a connection where I want it, just some of the commands I now perform manually; I may automate them later but not yet. Thanks for all of your help!

---

