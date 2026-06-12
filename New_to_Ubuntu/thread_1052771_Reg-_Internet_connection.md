---
title: "Reg:- Internet connection"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by halovivek on 2009-01-28
HI
I am having two internet connection in home. One is Broadband and i get max download speed is 32kbs and another one is wireless which is connected to my friends home it is also 32Kbps.
Is there any software or setting like that so I can use the both internet at same time to get speed more. Is it possible for us to combine both internet to work?

---

### Post by skymera on 2009-01-28
Yes, my download speed is also slow.

I made a guide on another forum, i'll copy parts over that *should* help you. They helped me. 

[color=red]** Speed Up Internet **[/color]
Internet in Ubuntu is SLOW. The reason for this is the usage of IPv6. It slows internet down mega.
[color=blue]*Disable IPv6*[/color]
```
 sudo gedit /etc/modprobe.d/aliases 
```
Look for this line: alias net-pf-10 ipv6
Delete it, and REPLACE it with this:
```
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6 
```

[color=blue]*Changing DNS Servers*[/color]
This helps me a big, generally in browsing speed. Type in terminal:
```
 network-admin 
```
Click unlock, type your password then click the DNS tab.
Click "Add" and type these two:
```
 
208.67.222.222
208.67.220.220

```
Close network admin.
In terminal:
```
 
sudo cp /etc/resolv.conf /etc/resolv.conf.auto
sudo gedit /etc/dhcp3/dhclient.conf

```
Look for the line that says: prepend domain-name-servers. Replace it with:
```

prepend domain-name-servers 208.67.222.222,208.67.220.220;

```

[color=blue]*Broadband Tweaks*[/color]
These tweaks significantly help my internet speed:
```
 sudo gedit /etc/sysctl.conf 
```
At the end of the file, add this:
```

net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

```
Save and Close. Now run this:
```
 sudo sysctl -p 
```

---

### Post by billgoldberg on 2009-01-28
> **halovivek said:**
> HI
I am having two internet connection in home. One is Broadband and i get max download speed is 32kbs and another one is wireless which is connected to my friends home it is also 32Kbps.
Is there any software or setting like that so I can use the both internet at same time to get speed more. Is it possible for us to combine both internet to work?

32 Kbps isn't broadband.

Correct me if I'm wrong, but what you are asking to do isn't possible.

---

### Post by 3rdalbum on 2009-01-28
I have asked about this before - at the best, it's extremely difficult; at the worst, it's impossible. Better to just upgrade your own Internet plan, or arrange with your friend to go halves in a fast broadband plan and share his wireless network.

---

### Post by halovivek on 2009-01-28
> **billgoldberg said:**
> 32 Kbps isn't broadband.

Correct me if I'm wrong, but what you are asking to do isn't possible.

Here in India if you subscribe for Broadband they will give 132kbps, 512 kbps but you will get download 322- 40 Kbpbs. Really worst.

---

### Post by sysadmn62 on 2009-01-29
It's possible, but you probably won't see much benefit.  As a simple analogy, you're making the road wider, but not raising the speed limit.  If you want to do one thing faster, it's still (likely) use one road.  If you're trying to do many things, you might be able to spread the load across two roads.

If the problem is that everything slows down when you max out the connection (i.e., VOIP or ssh gets choppy when downloading big files...) try wondershaper first.

---

### Post by GepettoBR on 2009-01-29
> **billgoldberg said:**
> 32 Kbps isn't broadband.

Correct me if I'm wrong, but what you are asking to do isn't possible.

I think he means his download speed from an arbitrary server, not his actual connection speed. Dial-up is either 28.8 or 56k, I've never even heard of 32.


I think I remember seeing something on LinuxQuestions about merging two network interfaces and distributing the load between them, but it was a very complicated setup, kept you from being able to use them separately and if one went down every other request your computer sent to the network would be lost. I don't think it's a good idea.

---

