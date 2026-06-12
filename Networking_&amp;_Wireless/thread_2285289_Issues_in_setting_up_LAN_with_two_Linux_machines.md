---
title: "Issues in setting up LAN with two Linux machines"
date: 2015-07-04
forum: Networking &amp; Wireless
---

### Post by zergling on 2015-07-04
Hello everyone,

I am opening this thread because I would like to access my Banana Pro with my File Browser and I was wondering how I could achieve this.

I am a really new in LAN configuration in Linux but this is what I have done so far:

**Desktop Linux:**

sudo nano /etc/network/interfaces

```

auto lo
iface lo inet loopback


#My IP description
# IPv4 address
iface eth0 inet static
        address 192.168.1.102
        netmask 255.255.255.0
        network 192.168.1.1
        broadcast 192.168.1.255
        gateway 192.168.1.1

```


**Banana Pro:**

sudo nano /etc/network/interfaces

```

auto lo
iface lo inet loopback


#My IP description
# IPv4 address
iface eth0 inet static
        address 192.168.1.110
        netmask 255.255.255.0
        network 192.168.1.1
        broadcast 192.168.1.255
        gateway 192.168.1.1

```

In case you are wondering, I am able to access the Banana Pro from my Desktop Linux via SSH, X11VNC and FTP (Filezilla).
So my question is, what am I missing? Could someone please let me know?

In case you need more info about my Linux machines, please do not hesitate to contact me.

Bye Everyone and have a nice and safe 4th of July in case you are in USA.

---

### Post by TheFu on 2015-07-04
Try sftp://192.168.1.110/ in the URL for any file browser.

No need for FTP anymore - best to purge that server. sftp is much preferred for a number of reasons.  FTP shouldn't be used anymore - since 1994-ish.

---

### Post by frankmorris2 on 2015-07-04
Hello,

The configuration file for your static IP looks like mine, but there are a few differences:

```


# The line "auto" is missing
auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
# the line "network" ends with 0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

```

The rest of the file seems OK to me.

Have a nice day

---

### Post by TheFu on 2015-07-04
Actually - network and broadcast are deprecated. Remove both of those.

If you want DNS to work, you need to add  a **dns-nameservers**  line inside the stanza on each.

---

### Post by ddesanti on 2015-07-05
Hi:
The first test is to be able to ping each machines itself:

From your Desktop and Banana Pro
ping localhost or ping 127.0.0.1

if you don't get a response back check your network interface with ifconfig to see if your eth0 interface is up

If all is good then try to ping each machine

From Desktop
ping 192.168.1.110

From Banana Pro
ping 192.168.1.102

if one of them doesn't response back it could be a LAN problem (faulty cabling, problem with the switch/router), or a firewall issues which is blocking your PC. 

Also in your interface configuration depending on your subnet mask it should be the first IP address from that subnet. In you case it should be 192.168.1.0.

Hope this will guide you to troubleshoot your problem.

---

### Post by Morbius1 on 2015-07-05
>  In case you need more info about my Linux machines, please do not hesitate to contact me.
I have a question. What operating systems are running on these machines?

The reason I ask is because I don't understand the question:
>  I am opening this thread because I would like to access my Banana Pro  with my File Browser and I was wondering how I could achieve this.
Given this:
> In case you are wondering, I am able to access the Banana Pro from my Desktop Linux via SSH, X11VNC and FTP (Filezilla).

The answer to the qustion might also reveal why you felt you needed to give these machines static ip addresses. Modern Linux machines can access each other using mDNS like:
```
nautilus ssh://hostname.local
```
[COLOR=#0000cd]*Where "hostname" is the host name of the Banana Pro - whatever that is.*[/COLOR]

---

### Post by TheFu on 2015-07-05
This is where I disagree with Morbius - though he is pretty much always correct.

IMHO **ALL** Linux/Unix machines should have a static IP. That way you can forward an ssh port from the WAN to your "server" and always know which IP traffic is originating from, among other uses like managing outbound firewall rules. Guess it depends on your network, which services you run and the risk levels involved.

The .local LAN idea is good, for certain end-user-only networks.  You are here, so not a typical end-user. I would stay with static IPs.  Of course, you can set these up using DHCP reservations which might be easier; that is controlled by the DHCP server (often the home router).

Also, wouldn't the address be **nautilus sftp://hostname.local** ?  I don't have nautilus, but **pcmanfm sftp://hostname** works here - thanks to static IPs and /etc/hosts management across all the machines via ansible. Tried ssh:// and was surprised it worked with pcmanfm too. Interesting - it really was sftp.  scp:// did NOT work. Too bad - scp file transfers are a little more efficient.

---

### Post by Morbius1 on 2015-07-05
I have no objections to static ip addresses. All of the other mechanisms used to browse networks by some kind of name need to resolve to ip addresses anyway. The only down side is that you need to know the ip address of whatever it is you are trying to access.

Depends on how "fluid" the network is you are setting up. If you have client machines coming and going it's a bit of a hassle. You can set up avahi service announcements for Samba, SSH, SFTP, and probably FTP ( although I never tried it with FTP ) that will "announce" their services to the LAN when you select "Browse Network" in Nautilus for example. Since we are talking about 2 machines in this network you are probably right.
> Also, wouldn't the address be **nautilus sftp://hostname.local** ?  I don't have nautilus, but **pcmanfm sftp://hostname**  works here - thanks to static IPs and /etc/hosts management across all  the machines via ansible. Tried ssh:// and was surprised it worked with  pcmanfm too. Interesting - it really was sftp.  scp:// did NOT work. Too  bad - scp file transfers are a little more efficient.         
 
Depends on the operating system and the file manager. 

"nautilus ssh://..." will resolve into "sftp://..." by default.
"dolphin ssh://..." resolves into
 > couldn't create slave: "Unable to create io-slave:
klauncher said: Error loading 'ktelnetservice %u'.
But sftp://... works.

---

### Post by SeijiSensei on 2015-07-05
In Dolphin, the URL fish://server will use SFTP to provide encrypted access to remote shares ([about FISH](https://en.wikipedia.org/wiki/Files_transferred_over_shell_protocol)).  I use it all the time to move files to my web server.  Being able to split the window in Dolphin and drag-and-drop files from the local system to the remote is a nice convenience.

---

