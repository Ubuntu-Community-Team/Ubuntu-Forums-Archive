---
title: "Set Static IP"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by jkries on 2010-07-22
I have just installed Ubuntu 10.04 and need to set a static IP on my system.

Here is what I need to set:

IP: 172.16.0.61
Gateway: 172.16.0.1
Subnet: 255.255.0.0
DNS: 172.16.0.6, 204.186.0.201

I appreciate any help!

---

### Post by dineshs on 2010-07-22
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection you want and click edit
select ipv4 
method-manual 
click add 
address 172.16.0.61
mask 255.255.0.0
gateway 172.16.0.1
[COLOR="Red"]then hit enter [/COLOR]
DNS 172.16.0.6, 204.186.0.201
then click apply
[ref [https://help.ubuntu.com/community/NetworkManager0.7]](https://help.ubuntu.com/community/NetworkManager0.7])

---

### Post by jkries on 2010-07-22
OK, I did that and I was able to change my IP address.  I can even reach the server from another computer on the network.

Now, however, I cannot access the Internet.

Any thoughts on that?

---

### Post by The Cog on 2010-07-22
I guess it's probably a DNS issue. Two questions:

What's the output from these two commands:
> ping ubuntuforums.com
ping 91.189.94.186

Did you configure the DNS servers into Network Manager? I can't remember if it has a place to do that. If it doesn't, you can edit the file /etc/resolv.conf and put these contents in:
> nameserver 172.16.0.6
nameserver 204.186.0.201You can edit the file using the command > gksudo /etc/resolv.confand it will ask you for your password again.

---

### Post by dineshs on 2010-07-23
Can you ping 4.2.2.1?
```
ping -c3 4.2.2.1
```
If yes ,instead of> DNS 172.16.0.6, 204.186.0.201Just use 4.2.2.1 and apply.Then restart the machine and see

---

