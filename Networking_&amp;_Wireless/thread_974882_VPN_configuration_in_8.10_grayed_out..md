---
title: "VPN configuration in 8.10 grayed out."
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by cody50 on 2008-11-07
Hello all,

clicking on the network manager applet and choosing configure vpn, I come to the vpn window and all of the buttons are grayed out so no action is possible to configure vpn, anyone know why this would be? attached is a screenshot.

---

### Post by iLemon on 2008-11-08
I think this means you need to install a VPN client.  I had the same problem until I installed vpnc.

---

### Post by mk4umha on 2008-11-09
i installed VPNC and it's still grayed out. Which vpn client did you install?

---

### Post by cody50 on 2008-11-09
same for me. I was able to get vpnc to work via console however.

---

### Post by zordid on 2008-11-10
You need to install a vpn plug-in for the network-manager. Depending of which vpn clients you use, you can install one or more of the following packages.

For vpnc
```
sudo apt-get install network-manager-vpnc
```
For openvpn
```
sudo apt-get install network-manager-openvpn
```
For pptp
```
sudo apt-get install network-manager-pptp
```

---

### Post by tombott on 2008-11-10
Many thanks for that, but I am unable to make a connection to a Windows VPN.
Get the message:

The VPN Connection failed because there were no valid VPN secrets.

If I remove stored password, I get prompted to enter a password then the message that the VPN connection failed but with no reason.

I've tried removing CHAP as an authentication method, as I know this has caused problems in the past.

Anybody got any ideas?

Cheers

T.

---

### Post by legolas_w on 2008-11-10
> **tombott said:**
> Many thanks for that, but I am unable to make a connection to a Windows VPN.
Get the message:

The VPN Connection failed because there were no valid VPN secrets.

T.


I am getting the same error, please let me know if you have been able to resolve it.

Thanks.

---

### Post by mk4umha on 2008-11-10
> **zordid said:**
> You need to install a vpn plug-in for the network-manager. Depending of which vpn clients you use, you can install one or more of the following packages.

For vpnc
```
sudo apt-get install network-manager-vpnc
```
For openvpn
```
sudo apt-get install network-manager-openvpn
```
For pptp
```
sudo apt-get install network-manager-pptp
```

that worked, thanks.

---

### Post by estebe on 2008-11-11
> **legolas_w said:**
> I am getting the same error, please let me know if you have been able to resolve it.

Thanks.

Me too, now I'm writing the vpn password always when I want to connect and I don't store it in the keyring. But this is very bad solution....

---

### Post by openid.batie.org/alan on 2008-11-21
This raises a point that is setting me off more and more as I constantly run across this: if you're going to grey out something in the ui, *tell me why the F you did it*!  Especially something as basic as "add" or "ok"!  Why even *have* the vpn tab in the ui if it's not really installed?  (though it is nice to have all the options shown, as long as it tells you what you need to do to actually use them).

OK, I'm *much* better now...

And thanks for the info...

---

### Post by cody50 on 2008-11-21
I would say I totally agree with you. Luckily we have a great community!

---

### Post by Madize on 2008-11-24
For me the connection is still not working. Can anyone give some suggestions how to get it work???

---

### Post by estebe on 2009-01-09
I have still the same problem and also I must change the value of the MRU size (in old network manager is possible) to permit send data to internet.

Have a solution?

Best regards

---

### Post by xoroz on 2009-02-20
no need to get aggressive.
Ubuntu is a free system, why dont you debug the problem and write a solution? This way you help yourself and the whole communtity!

THe solution for these problem is here:
[http://www.splatdot.com/2008/11/19/ubuntu-810-how-connect-microsoft-vpn]("http://www.splatdot.com/2008/11/19/ubuntu-810-how-connect-microsoft-vpn")

---

### Post by It's-Me on 2009-03-23
Encountring the exact same problem ... A total noob in case of linux and just stunmbled upon this problem :s. Imagine my condition, i will give it a go though.

Will update about my endeavour :).

---

### Post by It's-Me on 2009-03-26
Ahh .. finally succeded in creating a VPN :).

Just a li'i problem ...

Can't get it to work :-s.

---

### Post by tastybrains on 2009-04-28
thanks zordid! that helped me. we're using watchguard firewall and pptp on active director authentication (i also added our netbios domain under "NT domain") so after installing the *secret* pptp plugin it turns outi needed to to enable "use point-to-point encryption" mppe in the advanced tab

---

### Post by ferjero989 on 2009-06-18
this worked for me:
on the vpn advanced setting from the first tap.. check the one that says something about mppe ...
i hope this works for ya :)

---

### Post by Joel Barnes on 2010-02-14
Anyone else can't save the connection settings? I have tried setting other random values (like in "Advanced") that I don't need, blanking out the values, name, IP, etc. I've closed it and reopened it.

[IMG]file:///tmp/moz-screenshot.png[/IMG]

Thanks

---

