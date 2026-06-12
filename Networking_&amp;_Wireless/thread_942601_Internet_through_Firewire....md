---
title: "Internet through Firewire...?"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by icanfly0307 on 2008-10-09
Hi,
      I was setting up networking on my Ubuntu 8.04 system a few days ago when a thought popped up into my head. I have a Windows XP desktop with wireless internet. The wireless connection and the firewire connection are bridged. My question is, is it possible to pass on the internet connection from the bridged wireless and firewire connection down to my Ubuntu system with a firewire cable? If it is possible, could someone tell me how to do that? Can I just plug in the firewire cable and start surfing the web? Any thoughts on this issue would be appreciated.

---

### Post by superprash2003 on 2008-10-09
well its not that simple with firewire.. it has to be detected as a LAN card.. or a connection.. but you could connect these to via wired LAN.. almost all pcs and laptops have a LAN card..

---

### Post by Lars Noodén on 2008-10-23
Did you make any progress on networking via Firewire?  This is available in OS X and would be *very* useful in Ubuntu.

---

### Post by alexthunder on 2010-01-09
I've connected 2 computers through firewire as described at
[http://stream-recorder.com/forum/connecting-two-ubuntu-9-10-computers-over-t5347.html](http://stream-recorder.com/forum/connecting-two-ubuntu-9-10-computers-over-t5347.html)

```
sudo modprobe eth1394
sudo ifconfig eth2 192.168.200.1 up

sudo modprobe eth1394
sudo ifconfig eth8 192.168.200.2 up
```

I can ping both computers and remote viewing works fine, but I don't have any Internet access on the second computer.


I tried to bridge connections:

```
sudo apt-get install bridge-utils
sudo brctl addbr laptop-desktop
sudo brctl addif "laptop-desktop" eth0
sudo brctl addif "laptop-desktop" eth2
```

but I only get the following error:
```
can't add eth2 to bridge laptop-desktop: Invalid argument
```

Has anybody managed to share Internet over firewire? Any ideas how to do this?

---

### Post by iponeverything on 2010-01-09
If the machine with the ip address of 192.168.200.1 is the one with the internet connection:

on the 192.168.200.1 machine do:
```

sudo iptables -t nat -A POSTROUTING -s 0/0 -j MASQUERADE
sudo echo 1 > /proc/sys/net/ipv4/conf/all/forwarding

```
on the 192.168.200.2 do:
```

sudo route add default gw 92.168.200.1

```

---

### Post by alexthunder on 2010-01-09
> **iponeverything said:**
> If the machine with the ip address of 192.168.200.1 is the one with the internet connection:

on the 192.168.200.1 machine do:
```

sudo iptables -t nat -A POSTROUTING -s 0/0 -j MASQUERADE
sudo echo 1 > /proc/sys/net/ipv4/conf/all/forwarding

```on the 192.168.200.2 do:
```

sudo route add default gw 192.168.200.1

```
Thank you. I get the following problem on 192.168.200.1:
```
sudo echo 1 > /proc/sys/net/ipv4/conf/all/forwarding
bash: /proc/sys/net/ipv4/conf/all/forwarding: Permission denied
```

---

### Post by iponeverything on 2010-01-09
Sorry about that, I am not sure why the sudo echo does not work..

Add the line to /etc/rc.local before the "exit 0" at the end and reboot..

```

echo 1 > /proc/sys/net/ipv4/conf/all/forwarding

```

also.. the value is 1 or 0 - 1 is for on - 0 is for off

---

### Post by alexthunder on 2010-01-11
> **iponeverything said:**
> Sorry about that, I am not sure why the sudo echo does not work..

Add the line to /etc/rc.local before the "exit 0" at the end and reboot..

```

echo 1 > /proc/sys/net/ipv4/conf/all/forwarding

```also.. the value is 1 or 0 - 1 is for on - 0 is for off
I did the following:
```
sudo gedit /etc/sysctl.conf
```and uncommented the following line
```
net.ipv4.conf.default.forwarding = 1
```Forwarding was still disabled, but this can be solved by
```
sudo sysctl -p
```or rebooting.

Now:
```
cat /proc/sys/net/ipv4/ip_forward  
1
```I'm not sure whether I used 
```
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 
or 
sudo iptables -t nat -A POSTROUTING -s 0/0 -j MASQUERADE
```but it works like a charm now. 

Thanx a bunch!

---

### Post by alexthunder on 2010-01-30
I can no longer access Internet...  I don't really know the reason. It just stopped working.  I can ping another computer, but not any Internet server...

---

### Post by alexthunder on 2010-02-20
I can ping the server, but my Internet doesn't work on 192.168.200.2. Any idea how to solve it or how to find out what causes that?

---

