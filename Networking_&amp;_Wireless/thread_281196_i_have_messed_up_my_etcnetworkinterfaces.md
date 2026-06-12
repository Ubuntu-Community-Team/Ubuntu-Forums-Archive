---
title: "i have messed up my /etc/network/interfaces"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by Tones on 2006-10-20
An Ubuntu newbie here. 

First, I was trying to switch my box from dhcp to static by editing my 'interfaces' file. I switched 
> 
auto eth0
iface eth0 inet dhcp

to
> 
auto eth0
iface eth0 inet static
    address 192.168.0.100
    netmask 255.255.255.0


Then ran /etc/init.d/network restart . Unfortunately, I got an error:

> 
/etc/network/interfaces:2: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces" (fail)


So i decided to give up (for the moment) and revert the interfaces file back to the original DHCP settings. I did this and ran network-restart again, but received an identical error. :confused: 

Now, whatever I do, I'm unable to start my network services; all attempts generate this same error.

I'm at a loss! ](*,) any ideas?

=T=

---

### Post by linux2512 on 2006-10-20
could you post the interfaces file?

---

### Post by Tones on 2006-10-20
> **linux2512 said:**
> could you post the interfaces file?

Sure, here it is.

> 
# This file describes the network interfaces available on your system and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp


---

### Post by linux2512 on 2006-10-20
Did you edit the file in windows?
Try running dos2unix on it if you did, otherwise the file looks fine.

---

### Post by Tones on 2006-10-20
> **linux2512 said:**
> Did you edit the file in windows?
Try running dos2unix on it if you did, otherwise the file looks fine.
no, i'm editing with nano

---

### Post by jcrnan on 2006-10-20
your not supposed to add the adress and netmask there, just remove that. and to get your wireless net working try out the nidswrapper instructions on [www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by linux2512 on 2006-10-20
> **Tones said:**
> no, i'm editing with nano
hmm.... after restarting network, did you try doing 
sudo ifdown eth0; sudo ifup eth0 ?

---

### Post by Tones on 2006-10-23
> **jcrnan said:**
> your not supposed to add the adress and netmask there, just remove that. and to get your wireless net working try out the nidswrapper instructions on [www.ubuntuguide.org](www.ubuntuguide.org)

thanks, jcrnan!

I've tried this and it doesn't help. Right now I'd settle for working DHCP, so am not even trying for the 'static' setup.

I'm using a wired cat5 connection, no wireless.

---

### Post by Tones on 2006-10-23
> **linux2512 said:**
> hmm.... after restarting network, did you try doing 
sudo ifdown eth0; sudo ifup eth0 ?
i've been using "sudo /etc/init.d/network restart"

the commands you suggest give the same "couldnt read interfaces file" error message

---

### Post by linux2512 on 2006-10-23
> **Tones said:**
> i've been using "sudo /etc/init.d/network restart"

the commands you suggest give the same "couldnt read interfaces file" error message

what's the output of "ls -l /etc/network/interfaces" ?

---

### Post by Tones on 2006-10-23
OK, I was able to re-activate DHCP by using these commands, which I found [here]("http://ubuntuforums.org/archive/index.php/t-82258.html"):

> 
> sudo ip addr flush dev eth0 && sudo ip link set eth0 down
> sudo ip link set eth0 up
> sudo /sbin/dhclient eth0


Still no static IP, but at least I have basic DHCP running again!

---

### Post by Tones on 2006-10-23
The problem was an errant line-break in the "# This file describes..." line at the top of my file. I still don't have static IP running, but if I get stuck on it and am sure it's not a similarly stupid mistake, I'll open another thread.

That concludes this ubuntu-noob thread. Thanks for the help!

=T=

---

