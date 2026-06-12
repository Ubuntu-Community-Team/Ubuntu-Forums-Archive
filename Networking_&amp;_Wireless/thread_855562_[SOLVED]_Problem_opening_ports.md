---
title: "[SOLVED] Problem opening ports"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by computer_freak_8 on 2008-07-10
I can't seem to get my open ports to work. I go into Firefox and Opera and type in "localhost:8001", "localhost:8002", and "localhost" (without quotes) one-by-one, and get nothing - despite me having LAMPP (port 80) and Motion (ports 8001 and 8002) running. 

They all three used to work - until I got my Ad-Hoc connection working. 

Does anyone know what happened/how to fix it?

---

### Post by superprash2003 on 2008-07-10
does it work when you replace localhost with 127.0.0.1 ?

---

### Post by lswb on 2008-07-10
It could be a firewall problem, if you have one running make sure those ports are open.

---

### Post by computer_freak_8 on 2008-07-11
No, there's no firewall. 

No, 127.0.0.1, 127.0.1.1, 192.168.3.2 (IP on network) are all no-gos.

(So is multiboot, my computer's name)

Any other ideas?

---

### Post by superprash2003 on 2008-07-11
post the contents of your /etc/hosts file

---

### Post by computer_freak_8 on 2008-07-12
> **superprash2003 said:**
> post the contents of your /etc/hosts file

Alright, it is below, but I'm not sure how it could be the problem, since it won't work even when I type in the IP address.

(File is between the {}s.)

{
127.0.0.1 localhost
127.0.1.1 multiboot

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
}

As you can see, I do have the IP addresses set correctly (at least to my knowledge).

---

### Post by superprash2003 on 2008-07-12
hmm..that looks good.. ensure apache is running.. type sudo /etc/init.d/apache2 restart

---

### Post by computer_freak_8 on 2008-07-13
Okay...

> sudo: /etc/init.d/apache2: command not found

is the result. I kind of figured. I use LAMPP - lets try
```

sudo /opt/lampp/lampp start
```

that yeilds:

```
Starting XAMPP for Linux 1.6.6...
XAMPP: XAMPP-Apache is already running.
XAMPP: XAMPP-MySQL is already running.
XAMPP: Another FTP daemon is already running.
XAMPP for Linux started.
```


So yes, it is running. Also, the ports for Motion (8001 and 8002) don't work, either. Take a look at when I run the following:

```
jaredtbrees@multiboot:~/Downloads/ophcrack-3.0.1$ lsof -i :8001
COMMAND  PID        USER   FD   TYPE  DEVICE SIZE NODE NAME
motion  6595 jaredtbrees    6u  IPv4 4727835       TCP *:8001 (LISTEN)
jaredtbrees@multiboot:~/Downloads/ophcrack-3.0.1$ lsof -i :8002
COMMAND  PID        USER   FD   TYPE  DEVICE SIZE NODE NAME
motion  6595 jaredtbrees    5u  IPv4 4727787       TCP *:8002 (LISTEN)
jaredtbrees@multiboot:~/Downloads/ophcrack-3.0.1$ lsof -i :80
COMMAND PID        USER   FD   TYPE  DEVICE SIZE NODE NAME
firefox 327 jaredtbrees   40u  IPv4 3546568       TCP 72-63-181-124.area2.spcsdns.net:51545->httpcs106.msg.ac4.yahoo.com:www (ESTABLISHED)
firefox 327 jaredtbrees   44u  IPv4 3549158       TCP 72-63-181-124.area2.spcsdns.net:57161->httpcs103.msg.ac4.yahoo.com:www (ESTABLISHED)
firefox 327 jaredtbrees   46u  IPv4 3550208       TCP 72-63-181-124.area2.spcsdns.net:52383->httpcs103.msg.ac4.yahoo.com:www (ESTABLISHED)
firefox 327 jaredtbrees   47u  IPv4 3549333       TCP 72-63-181-124.area2.spcsdns.net:44833->httpcs103.msg.ac4.yahoo.com:www (ESTABLISHED)
firefox 327 jaredtbrees   55u  IPv4 3542046       TCP 72-63-181-124.area2.spcsdns.net:39805->httpcs104.msg.ac4.yahoo.com:www (ESTABLISHED)
firefox 327 jaredtbrees   83u  IPv4 4724474       TCP 72-63-181-124.area2.spcsdns.net:36897->205.234.225.56:www (ESTABLISHED)
firefox 327 jaredtbrees   85u  IPv4 4724469       TCP 72-63-181-124.area2.spcsdns.net:38793->205.234.225.83:www (ESTABLISHED)
firefox 327 jaredtbrees   86u  IPv4 4724470       TCP 72-63-181-124.area2.spcsdns.net:38794->205.234.225.83:www (ESTABLISHED)
firefox 327 jaredtbrees   87u  IPv4 4724471       TCP 72-63-181-124.area2.spcsdns.net:38795->205.234.225.83:www (ESTABLISHED)
firefox 327 jaredtbrees   88u  IPv4 4724472       TCP 72-63-181-124.area2.spcsdns.net:38796->205.234.225.83:www (ESTABLISHED)
jaredtbrees@multiboot:~/Downloads/ophcrack-3.0.1$ 
```

I can't figure out why LAMPP doesn't show up, but keep in mind that

localhost:8001, localhost:8002, 127.0.0.1:8001, 127.0.0.1:8002, et cetera 

don't work, either.

I tried using your IPTABLES tutorial, (for those three ports,) but that didn't help.

Any other ideas?

---

### Post by PTo on 2008-09-15
I've read your posts on this forum and the linux forum. I don't know much about the topic but you might check if your loopback is working properly. I know that a not-working loopback can give problems with the connection to localhost.

About the firewall I've heard saying that it is always working (something with the so-called iptables). So maybe it's an idea toinstall firestarter and open the concerned ports? I'm not sure about this so please correct me if I'm wrong.

---

### Post by computer_freak_8 on 2008-09-16
Okay, I think I figured out what was causing my problem. 

I had posted about my gnome-settings-daemon giving me errors, and this started around the same time as I got my ad-hoc connection, which was *also* around the same time as I discovered my ports were clogged. 

I have recently done a clean install of Ubuntu (this time 64-bit - I really wanted to see all four gigs of RAM).

I have avoided EnvyNG at all costs, as it was the source of my repeating gnome-settings-daemon error, and I have not run into port-clogging (yet...).

I hope this helps someone else with the same issue.


Thanks everyone,

computer_freak_8

---

