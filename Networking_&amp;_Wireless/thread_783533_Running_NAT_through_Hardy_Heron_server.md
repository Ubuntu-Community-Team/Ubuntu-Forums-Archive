---
title: "Running NAT through Hardy Heron server"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by Geran on 2008-05-05
So, I have my DHCP server up and running on my Hardy Heron server and I have my client computer connecting to my eth0 via an X-over cable. DHCP works fine, connection from Hardy Heron server to internet, fine, connection from client computer to Hardy Heron, fine. But what I can't get that I'm trying to get is a connection from my client computer to the internet.

My topology is very basic:

client --- Hardy Heron --- Internet

Can anyone help me bridge the gap?

---

### Post by Geran on 2008-05-05
I saw something about using IPtables -t NAT, but my iptables insists that this table does not exist...

---

### Post by larry007 on 2008-05-07
This iptables problem only seems to be applicable to the server version...  I am experiencing the same problem.

After playing with UFW, I gave up, and uninstalled ufw.  I need to forward incoming http traffic to tomcat (8180), and have used 3 simple iptable rules for the past 2 years.   

Psynopsys:
sudo iptables -t nat -A OUTPUT -d (MYHOST) -p tcp --dport 80 -j REDIRECT --to-ports 8180

sudo iptables --list 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination



So it basically shows up nothing.... what happened to the line that I just added????

---

### Post by Geran on 2008-05-11
Actually, the rule you created is there, but you're looking at the wrong table. By default iptables uses the "filter" table for every command you send it, unless you specify another table. You have specified the "nat" table, and rightly so. If you want to see chains that you created in the nat table then.. 


iptables -t nat -L 

is necessary, otherwise it is the equivalent of...

iptables -t filter -L

---

### Post by .rdg on 2008-05-11
There are two ways to do the NAT: SNAT or Masquerade. The first one is faster, but should be used when you have a static IP or have an additional IP(s), which are used for translation purposes.

SNAT:

iptables -t nat -A POSTROUTING -o eth1 -j SNAT --to-source Your_Server_IP

Masq:

iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

That should pretty much do the trick. Keep in mind these will NAT every type of traffic - the rules can be much more complicated.

---

### Post by SpaceTeddy on 2008-05-12
internet sharing are the magic words - There are three parts to it. 
1.) getting the clients configures 
i suspect that is done
2.) getting iptables right
that was answered in the previous posts on how to do it - altough i prefer the MASQUERADE over SNAT target as it does not require to put in an ip
3.) enable IP Forwarding
there was no talk of it (yet)... check if it is enabled via this
```
sysctl net.ipv4.ip_forward
```
if this returns 0 then your server *will not* forward any paket. this is the default behaviour. 
to enable it, edit your /ect/sysctl.conf and set it via
```
sudo sysctl -w net.ipv4.ip_forward=1
```

that was it in a nutshell - the full tutorial i have written for it can be found here : [http://ubuntuforums.org/showthread.php?t=713874]("http://ubuntuforums.org/showthread.php?t=713874")

hope it helps

---

