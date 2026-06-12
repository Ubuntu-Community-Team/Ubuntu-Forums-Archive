---
title: "Bridging networks?"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by Masterion on 2010-07-23
I'm just wondering, I am using a dynamic IP address as far as I know and Firestarter, although I am unaware of what to do from there.

I am trying to bridge my Internet connection (going through my wireless card) to my Xbox 360 (going through my ethernet cable).

Any suggestions?

---

### Post by Zzl1xndd on 2010-07-23
If you are attempting to share your connection from your Ubuntu computer to your Xbox then this should work.

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by bodhi.zazen on 2010-07-24
> **Masterion said:**
> I'm just wondering, I am using a dynamic IP address as far as I know and Firestarter, although I am unaware of what to do from there.

I am trying to bridge my Internet connection (going through my wireless card) to my Xbox 360 (going through my ethernet cable).

Any suggestions?

What are you wanting to do exactly ?

You almost certainly are going to have to use an alternate to firestarter , either learn iptables or an alternate tool that will help you configure your firewall.

---

### Post by Masterion on 2010-07-24
> **bodhi.zazen said:**
> What are you wanting to do exactly ?

As my computer is connected to the internet via wireless, I want to bridge that to my Xbox 360.

---

### Post by YesWeCan on 2010-07-24
Hi there. I agree with the suggestions so far. Some more info:

You may be confusing bridging in the normal sense of the word with bridging in the networking sense. A networking bridge simply connects two networks together almost as if they were physically connected with a cable. But networks also have a logical distinction called a subnet. To share the internet connection directly the xbox also has to share the subnet of the internet gateway. If they are on independent subnets (which is highly likely) they will not be able to communicate. That is sort of what a subnet is for.

When you merge two LANs with a bridge (or physical switch) their subnets remain separate (unless their subnet address ranges overlap already). So bridging won't get you anywhere.

You need to create a route from your xbox subnet to your gateway on your wireless subnet. This requires a "router" function rather than a bridge function.

---

### Post by PaulReaver on 2010-07-24
I managed this on ubuntu with firestarter and gnome network manager in the past. I can't remember exactly how as I'm on mandriva now and it uses a different connection manager, but it is definitely possible with firestarter and network-manager.

---

### Post by PaulReaver on 2010-07-24
So your laptop connects to the wifi, and you want to share your laptops connection through a cable to the 360?

Just forward the ports 
* UDP 53
* TCP 53
* TCP 80
* UDP 88
* UDP 3074
* TCP 3074
from wlan0 to eth0 in firestarter
your wifi and cable could be named something different? we can't be more specific without more information.

and in nm-applet (network-manager-applet) set your wifi connection as "shared to other computers"

Then you'll need to open the above ports on your router or you'll get strict NAT issues  :(
good luck

---

