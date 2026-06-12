---
title: "Send GUI to xubuntu screen from other machine in LAN"
date: 2024-03-11
forum: Networking &amp; Wireless
---

### Post by egerlach on 2024-03-11
Hi, 
xbuntu 20.04 is quite good "closed", I can't send a app from second machine 10.0.0.104 (debian 10) to xubuntu user X11 desktop with XFCE window manager: 

I prepaired xubuntu to a accept apps to user screen, with "xhost +" of course: 
```

sshd_config:
AllowTcpForwarding yes
X11Forwarding yes

# sysctl -w net.ipv4.ip_forward=1
net.ipv4.ip_forward = 1
# cat /proc/sys/net/ipv4/ip_forward
1

lightdm.conf
xserver-allow-tcp = True  



```
I restarted sshd of course, and killed lightdm process.  
But from remote machine: 


```
root# export DISPLAY=10.0.0.9:10.0
root# xeyes
Error: Can't open display: 10.0.0.9:10.0
root#
```

What is missing to send a app, e.g. xeyes from a remote machine?  - I'm sure something with auth, .Xauthority , ... I have to add 10.0.0.104 to Xauthority ....

Or eliminate the "-auth ...." Xorg ? 
/usr/lib/xorg/Xorg -listen tcp :0 -seat seat0 -auth /var/run/lightdm/root/:0 -listen tcp vt7 -novtswitch

BTW: on xbuntu machine works: export DISPLAY=10.0.0.9:10.0 ; xeyes !! Only a problem from remote machine in same LAN. 
BTW: Port 6000 is open, and reachable even from from remote machine. 

tia
Eckard

---

### Post by uabfaho on 2024-07-21
modify /etc/lightdm/lightdm.conf as below
[Seat:*]
xserver-allow-tcp=True

---

### Post by uabfaho on 2024-07-21
Default TCP port is 6000, you need to set "export DISPLAY=[ip]:0.0"

---

