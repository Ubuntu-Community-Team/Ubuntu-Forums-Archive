---
title: "Not possible to wget or apt-get, but Internet = oke !"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by flying_nomad on 2006-12-13
Hello,

I'll have some problem, have searched around a lot, disabled Ipv6 after some suggestions (because it could be possible it's not supported here) and used static adress instead of dhcp but i am lost know.

--

The case, i am (in spare time) doing a install of Mythtv on a installed Kubuntu 6.10 somewhere behind a firewall
But while internetconnection is just oke there is no way i can wget of apt-get.

My former fault message's were (when Ipv6 was still enabled)

> 
 - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80] 


my interfaces =

> 
marco@mediacenter:~$ less /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 192.168.xxx.xxx
netmask 255.255.0.0
gateway 192.168.xxx.xxx

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

/etc/network/interfaces (END)


Who can show me what can cause this strange problem.

I can easily surf on the net but as soon as i try to apt-get or wget to get some packages i need to install i am in trouble.


regards,

M

---

### Post by Yopo on 2006-12-13
What happens if you select another server from which to download your repositories?
The easiest way is to go to synaptic->settings->repositories->download from:
Select a different server in this section.
Are you able to connect after this or do you still get the same error message?
Hope this helps...

---

### Post by zaflaucich on 2006-12-13
I suggest you also to check the /etc/resolv.conf file to see if you have the right DNS server in it.

P.S. - are you sure that ipv6 is disabled? In edgy you have to add ```
blacklist ipv6
```in the /etc/modprobe.d/blacklist file. On the net, sometimes, they suggest to only modify the /etc/modprobe.d/aliases (or alias) file.

---

### Post by flying_nomad on 2006-12-13
I am using Kubuntu, so a different graphic interface around apt-get.

*(thx for your answer)*

The sources are the normal 'dutch' repositories, see list below

> 
marco@mediacenter:~$ less /etc/apt/sources.list

deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy universe multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe
 multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy-backports main restricted univ
erse multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://dl.ivtvdriver.org/ubuntu](http://dl.ivtvdriver.org/ubuntu) edgy firmware
deb-src [http://dl.ivtvdriver.org/ubuntu](http://dl.ivtvdriver.org/ubuntu) edgy firmware


by the way my netstat -nr give's this output.

> 
marco@mediacenter:~$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.xxx.xxx   0.0.0.0         UG        0 0          0 eth0
marco@mediacenter:~$


---

### Post by flying_nomad on 2006-12-13
marco@mediacenter:~$ less /etc/resolv.conf
nameserver 192.168.xxx.xxx
nameserver 192.168.xxx.xxx


is my result.

I am going to add that blacklist as i havn't done that yet (wasn't mentioned in the instruction i got from another place) be back with the result later

---

### Post by flying_nomad on 2006-12-13
Oke, have blacklisted it and am getting now another fault message. (and the whole list shows the same message's, so i just cut and pasted a small part of it

>  ***Kon de socket voor 2001***:7b8:3:37::21:1 (f=10 t=1 p=6) ***niet aanmaken - socket*** (97 Address family not supported by protocol) [IP: 2001:7b8:3:37::21:1 80]
***Fout ***[http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) edgy/multiverse Packages


Translated (the ***dutch parts*** of it) it reads something like

Couldn't create socket for 2001 ...... - socket (.....

Error http .....

---

### Post by Yopo on 2006-12-13
> **flying_nomad said:**
> I am using Kubuntu, so a different graphic interface around apt-get.

*(thx for your answer)*

The sources are the normal 'dutch' repositories, see list below



by the way my netstat -nr give's this output.

O I forgot, you're on Kubuntu so the package manager is Adept, but the servers can't be the problem then since I'm from Holland too so I'm using the same servers as you and they work fine from here.

Strange problem though...

---

### Post by flying_nomad on 2006-12-13
**Yeahhhhh !!!!!!**

 I have found the solution, and post it here for future reference for someone who will experience some alike it.

To all, thx very much for brainstorming and your help.

I made and ***apt.conf file*** to point apt to the proxy as well as the browser was (because websurfing was working oke)

> 
marco@mediacenter:~$ sudo nano /etc/apt/apt.conf

Acquire {
     Retries "0";
     Http {
        Proxy "http://192.168.xxx.xxx:8080";;
     }


and everything was running  !!!!!

:-) i'm happy (and learned something again)
}

---

### Post by Yopo on 2006-12-13
What output do you get if you do
$less /etc/iftab

*EDIT*
Hey you solved it in the meantime, still strange what could have caused this...

---

### Post by samden on 2006-12-14
> **flying_nomad said:**
> **Yeahhhhh !!!!!!**

 I have found the solution, and post it here for future reference for someone who will experience some alike it.

To all, thx very much for brainstorming and your help.

I made and ***apt.conf file*** to point apt to the proxy as well as the browser was (because websurfing was working oke)



and everything was running  !!!!!

:-) i'm happy (and learned something again)
}
This sounds very interesting, and could be relevant to my situation. ([http://www.ubuntuforums.org/showthread.php?t=317996](http://www.ubuntuforums.org/showthread.php?t=317996)) I can ping websites, download mail and use the Gnome net-based dictionary utility. However I cannot apt-get, use Synaptic or browse the net. I am connecting through an ethernet network and a proxy server. Is it possible that neither apt or Firefox are being directed to the proxy correctly?

My /etc/apt/apt.conf file reads:

```
APT::Authentication::TrustCDROM "true";
Acquire::http::Proxy "http://websense@myworkdomain.ie";
```

I note that this is somewhat different to your file, but I am using Xubuntu 6.06 on an iMac G3, which is probably different to your setup. Should I modify this file, and if so what to? Is there a similar file that directs Firefox to the proxy, where would I find it, and what should it read?

EDIT:
I have edited this to read:
```
APT::Authentication:TrustCDROM "true";
Acquire {
Retries "0";
Http {
Proxy "http://websense@mywork.ie:8080";;
}
```

but still apt-get will not connect to online repositories. I just get a series of messages:

```
Failed to fetch http://archivewebsite Could not connect to websense@mywork.ie:8080 (127.0.0.1). - connect (111 Connection refused)
```

The only thing I notice in this message is the fact that the proxy is recognised as 127.0.0.1 - I thought this was my own computer? Should the proxy be this number or something else?

Any hints would be great. Thankyou.

---

