---
title: "Login via ssh using hostname not working (local)"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by hovzio on 2009-02-22
Hi, as the title sais, I'm trying to log in to a box on the local network using it's hostname. This is not really working, if I specify the ssh-server's ip address it works fine.

ssh $USER@<hostame>       Doesn't work

ssh $USER@192.168.1.101   Works just fine

Using other programs such as quicksynergy I am able specify the servers hostname hence not having to specify an ip. This would be real cool if it worked with ssh because the routers's assigning ip's using DHCP, and I have to run over across the house to see what ip the ssh-server has.. I know I could set up static ip's but I'd like to avoid that. How do I get this machine to "broadcast" its hostname??...  Actually it is, nmap sais so.. Is there a an option in the sshd config files? Haven't been able to find such. Many thanks in advance, ;)

---

### Post by Rolcol on 2009-02-22
When you enter an address other than an IP address, it has to look up the name on a DNS server.  Here are a few solutions:

1- Use a custom DNS server
2- Edit your /etc/hosts file
Add this to the end:
```
192.168.1.101    <hostname>
```

---

### Post by hovzio on 2009-02-22
Thanks, I think I'll go with the hosts file. Stupid question, is this done on the client side? What if the server changes ips, its limited to 4 ips but it could be anyone between 192.168.1.10[1-4]. Is there a way to specify this in the hosts file?

Custom dns server sounds real interesting. How would I go about setting this up. Where would I start, do I have to mess with bind? I am very interested in learning about dns so I'd like to take a stab at it. Thanks

---

### Post by hovzio on 2009-02-24
Hi, I edited /etc/hosts as described above and it worked until the ssh-server got assigned a new ip (dhcp setup with router). I guess I expected this to happen, it would be so cool if I could call up the ssh server via a hostname that isn't dependent of it's current ip. Is there a way to do this, would really appreciate any help. Thanks :)

---

### Post by unutbu on 2009-02-24
Perhaps setup the ssh server with a static IP address. 
Here are instructions on how to do this: 
[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

---

### Post by Peter09 on 2009-02-24
Make sure winbind is installed

```
sudo apt-get install winbind
```

then edit 

/etc/nsswitch.conf

```
gksudo gedit /etc/nsswitch.conf
```

change the hosts line to look like this

> hosts:          files mdns4_minimal [NOTFOUND=return] dns wins mdns4


finally restart winbind

```
sudo /etc/init.d/winbind restart
```

this should solve your name resolution problems.

---

### Post by hovzio on 2009-02-25
> **Peter09 said:**
> Make sure winbind is installed

```
sudo apt-get install winbind
```

then edit 

/etc/nsswitch.conf

```
gksudo gedit /etc/nsswitch.conf
```

change the hosts line to look like this



finally restart winbind

```
sudo /etc/init.d/winbind restart
```

this should solve your name resolution problems.

Hi, will winbind solve the "hostname" issue. I googled a little and was not able to come up with much. For what is the file /etc/nsswitch.conf used for? What exactly does winbind do? If I follow the above directions will this solve my problem. When I googled winbind I found a lot of stuff mentioning samba and an NT server. I am using neither, I just wanna be a able to ssh into my ssh-server using its hostname as an address instead f its ip. (my gateway is a router running a dhcp server) From what it looks like I'm gonna be setting up static ips. (which kinda sucks when friends come over and want to go online with their pc so I'd like to avoid this)

In my old router I used to be able to set up a dhcp server that had an extra option for static dhcp with which a static ip could be applied to the server via mac-address. I just bought a linksys WAG5462 "gateway-router" (wirless) and I can't find any such option...:( Does anyone by chance know if the router can be configured as described above. All in all I am not happy with this router, it drops packages and has some serious routing issues. Often enough I'm not even able to ping/connect etc. to a specified box although it itself has flawless internet access.(firewall is correctly set up.) Thanks for the help :)

---

### Post by Peter09 on 2009-02-25
Well it is a bit confusing but it works. As far as I can tell there is an issue with DHCP and name resolution, although what is going on is not clear.. Winbind does resolve the names of machines on the LAN, while nsswitch appears to determine the order in which they are resolved.

I had a lot of trouble with name resolution and this worked for me. Neither of these things is irreversible, if it does not work un-install winbind and change the nsswitch line back to what it was.

---

