---
title: "iptables messed up after every reboot"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by mogliii on 2008-10-31
Hi,

I am using internet connection sharing to get the internet (via wireless) from my host to a guest (via cable).

Yesterday it somehow broke, and I just retyped the masquerade commands.  ow the situation is:N

I have to execute the following commands to 
a) get Internet on my "host"
b) get Internet on my "guest"
```
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
```

First it completely resets iptables.

Now if I reboot, I cant connect again, having to execute the commands (already in a script file).

Can anyone help me to resolve this issue, so I dont have to execute these commands over and over again? I didn't find any config-file called iptables.conf. Where is it saved?

*Note: Using Ubuntu 8.04, without firestarter.

---

