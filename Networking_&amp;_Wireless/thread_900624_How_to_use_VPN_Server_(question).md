---
title: "How to use VPN Server? (question)"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by Usta_AsH on 2008-08-25
Hi I want to install VPN Server. All I need is connect that machine and use that machine's internet connection instead of mine. So I won't use Hamachi. How can I do that?

My server can use:
ubuntu-6.06-i386-minimal (155MB)
ubuntu-7.10-i386-minimal (135MB)
ubuntu-8.04-i386-minimal (121MB)
OS's

---

### Post by Orlsend on 2008-08-25
Hamachi its a kind of week vrsion of VPN, I would not recommend it

Try VPNC oh a normal VPN

---

### Post by SpaceTeddy on 2008-08-25
and here comes my favorite answer to this question - OpenVPN !
Here is a (very short) description of how to [[COLOR="Blue"]setup[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5076501&postcount=4") the server.

If any questions are left - just ask (but please read first). Also, the os does not matter - but i'd suggest 8.04.

hope it helps :)

---

### Post by Usta_AsH on 2008-08-25
> **SpaceTeddy said:**
> and here comes my favorite answer to this question - OpenVPN !
Here is a (very short) description of how to [[COLOR="Blue"]setup[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5076501&postcount=4") the server.

If any questions are left - just ask (but please read first). Also, the os does not matter - but i'd suggest 8.04.

hope it helps :)

I don't want OpenVPN because it needs to set up a program. I want windows bundled version.

---

### Post by Usta_AsH on 2008-08-25
> **Orlsend said:**
> Hamachi its a kind of week vrsion of VPN, I would not recommend it

Try VPNC oh a normal VPN

Can you give me a documentation?

---

### Post by SpaceTeddy on 2008-08-25
mhm... so that only leaves something that supports IPSec - as that is the only VPN windows can speak. I cannot think of the package anymore that supplied this... i had this setup as a test at one time (about four years back). 

As for hamachi. Use it if you want to - i would not trust a service that is supplied by a third party to create a VPN (virtual **[COLOR="Red"]private[/COLOR]** network).

in the end it is your choice :)

---

### Post by Usta_AsH on 2008-08-25
I found something it gives

$xecuting the following command as root: ^Imknod /dev/ppp c 108 0

error in log

[http://forums.bit-tech.net/showthread.php?t=132029](http://forums.bit-tech.net/showthread.php?t=132029)
looked from here.

when I entered that code to ssh it gives

-bash: :s^Imknod /dev/ppp c 108 0: substitution failed

this error.

---

