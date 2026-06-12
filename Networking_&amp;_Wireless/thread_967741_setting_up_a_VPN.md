---
title: "setting up a VPN"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by oilspot on 2008-11-02
I need to be able to set up a virtual private network by this afternoon. I've got directions for windows but not for linux. 
 For windows it goes like this...

start/control panel/network connetions/new connection/connect at workplace/virtual private network connection/name/ "do not dial initial connection"/    and then asks me for the ip address

 I've tried to find how to set this up on ubuntu but I'm still confused!


thanks for your help!!!

---

### Post by oilspot on 2008-11-02
anybody... please:)

---

### Post by thefunnyman on 2008-11-02
Couple questions...

What version of ubuntu are you using?
What type of VPN are you connecting to?  ( ie. openVPN, CISCO, etc )
What type of authentication are you using?  ( key-based, password, combination of the 2 )

thefunnyman

---

### Post by oilspot on 2008-11-02
> **thefunnyman said:**
> Couple questions...

What version of ubuntu are you using?
What type of VPN are you connecting to?  ( ie. openVPN, CISCO, etc )
What type of authentication are you using?  ( key-based, password, combination of the 2 )

thefunnyman


8.04
what type... ??? I have to enter the IP address (this answer probably shows how much I know about what I'm doing)
password only

---

### Post by mesocal on 2008-11-02
its actually quite simple. first get the stuff:

   $ sudo apt-get install pptp-linux network-manager-pptp

next edit the file /etc/ppp/chap-secrets and add in (this stores your password for the network)

    username PPTP password *

now lets create the connection info.  

   $ gedit /etc/ppp/peers/myvpn (anyname you like)

add the following basic lines

    pty "pptp vpn.somesite.com --nolaunchpppd"
    name username
    remotename PPTP
    require-mppe-128
    file /etc/ppp/options.pptp #(this file is created from installing pptp-linux network-manager-pptp)
    ipparam myvpn(name of the file you created before /etc/ppp/peers/myvpn)

now connect to the network:

    $ sudo pppd call myvpn

next be sure to add the ip addresses so you can do your thing:

    $ sudo route add -net 192.168.2.0 netmask 255.255.255.0 gw 192.168.2.1 dev ppp0


thats it in a nutshell.  again, this is very basic but hopefully it will help you.

good luck.

---

### Post by oilspot on 2008-11-08
> **mesocal said:**
> its actually quite simple. first get the stuff:

   $ sudo apt-get install pptp-linux network-manager-pptp

next edit the file /etc/ppp/chap-secrets and add in (this stores your password for the network)

    username PPTP password *

n


 ran that in the terminal. found etc/ppp/chap-secrets but the file has an x over it. What now?

---

### Post by SaltySurfer on 2008-11-08
> **oilspot said:**
> ran that in the terminal. found etc/ppp/chap-secrets but the file has an x over it. What now?

If you're saying you can't edit the file, try editing it as Root with ```
sudo vim /etc/ppp/chap-secrets
```

---

