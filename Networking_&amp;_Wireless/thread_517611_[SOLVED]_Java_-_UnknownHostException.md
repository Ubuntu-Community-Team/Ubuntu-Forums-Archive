---
title: "[SOLVED] Java - UnknownHostException"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by purdticker on 2007-08-04
I've explained my complete problem on this thread, but I think perhaps it might have been the wrong place to put it:

> [http://ubuntuforums.org/showthread.php?t=517453](http://ubuntuforums.org/showthread.php?t=517453)

Basically, I'm getting an java.net.UnknownHostException on some java apps when I try to run them (so far apache geronimo and netbeans)

My theory so far is I've incorrectly or incompletely set up my network?  A DNS issue?  I'm a complete networking newb so please be patient with me :)

> $ ping fermmons
ping: unknown host fermmons

But this is my computer name!  Shouldn't I be able to ping myself with my computer name?

---

### Post by noob12 on 2007-08-04
Can you post the output of these commands

```

grep "hosts:" /etc/nsswitch.conf

cat /etc/hosts

cat /etc/network/interfaces

```


You may need to add an entry in /etc/hosts.  You'll probably just want to point it to your loopback IP.

---

### Post by purdticker on 2007-08-04
Here's output:

> 
$ grep "hosts:" /etc/nsswitch.conf
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4


> 
$ cat /etc/hosts
127.0.0.1 fermmons.fermmons
127.0.1.1 fermmons.fermmons

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


> 
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


---

### Post by purdticker on 2007-08-04
What do I add to the file?
This?
>  127.0.0.1 fermmons

---

### Post by purdticker on 2007-08-04
> $ cat /etc/hosts
127.0.0.1 fermmons
127.0.1.1 fermmons.fermmons

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Geronimo started successfully!  Going to reinstall netbeans and try it again.

---

### Post by noob12 on 2007-08-04
Um.  Yes.  The **fermmons.fermmons** is because you seem to have set your domain name to fermmons in (Systems | Administration | Network | General tab).  That would have worked for you if you had left the domain blank.

---

### Post by purdticker on 2007-08-04
I see... but now all my java apps are completely gray :(  no errors... ugh hopefully I can figure this out now.

---

### Post by noob12 on 2007-08-04
I don't know what you mean by that, but if you did set your domain name blank you probably want to eliminate any duplicate entry for fermmons in your /etc/hosts file.

---

### Post by purdticker on 2007-08-04
When I start netbeans, I get no errors in the terminal, and I can see the netbeans window open.  But the window is all gray.  I can see the title bar, but the contents of window is nothing but grey :/  Tried with both downloaded netbeans and netbeans in repositories

---

### Post by noob12 on 2007-08-04
I don't think this is related to your earlier problem resolving your own hostname "fermmons".

Is this behavior new after adding the /etc/hosts entry? or removing the "fermmons.fermmons" entry?

Can you **cat /etc/hosts** and show it to me now?

---

### Post by purdticker on 2007-08-09
You're right this isn't an issue with my /etc/hosts.... now I'm just having some sort of java issue... going to close this thread... thanks for help!

---

