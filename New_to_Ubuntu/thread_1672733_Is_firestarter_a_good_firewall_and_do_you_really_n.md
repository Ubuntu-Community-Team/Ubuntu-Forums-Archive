---
title: "Is firestarter a good firewall and do you really need a firewall?"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by bradthewanderer on 2011-01-21
I was wondering is firestarter a good firewall to use? Is there another firewall program that is better? And if you run transmission do you need a firewall to block unwanted connections? 

Thank you all in advance for any answers/suggestions you might have for me :)

---

### Post by JKyleOKC on 2011-01-21
I've read in the forums that firestarter hasn't been well-supported for several years, so if you have any problem with it you might have trouble getting much help. The current favorite seems to be "ufw" which is extremely simplified.

Actually, they are both simply front-ends to help you configure the real firewall that's built into the system, called "iptables." Until you install something like a server that needs to be accessed from the internet, the default installation won't respond to any packets that are not replies to something you sent out, so no other firewall is needed. When you enable "ufw" (it's installed by default but disabled) you block everything, and have to specifically enable each type of thing you want to get through.

I don't use any p2p programs and have removed "transmission" from my systems for security's sake, so someone else will have to comment on whether it needs a firewall. I configure iptables manually rather than using any of the helpful front ends, to block everything except the very few things I want to get through to me...

---

### Post by Dr Small on 2011-01-21
Firestarter is not a firewall. It's just a frontend for iptables.

---

### Post by nevius on 2011-01-21
> **bradthewanderer said:**
> I was wondering is firestarter a good firewall to use?
No. It is not a good firewall to use. It is unsupported and not under active development. This means no bug fixes and no security fixes. 

> Is there another firewall program that is better?
Use UFW. You can start it by typing in the terminal ```
 sudo ufw enable
``` and you're done.


>  And if you run transmission do you need a firewall to block unwanted connections?

No. If you are very paranoid you may want to confine Transmission with an apparmor policy. 

By default Ubuntu has no open ports. Please read the [security sticky]("http://ubuntuforums.org/showthread.php?t=510812") at the top of the security forum. The important question to ask is "why do you think you need a firewall?"

---

### Post by Rex Bouwense on 2011-01-21
Probably not.  Try:  [https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

---

### Post by lotus@terminal on 2011-01-21
Agree with the post above. Why do you need a firewall? Most/if any at all threats are script based, and seeing Linux is defaulted with 0 ports, you would have no need to worry about a firewall. If you are worried about any network monitors/key loggers/etc then just run

```
sudo iptables -F
```before logging out.

---

### Post by ajgreeny on 2011-01-21
Firestarter is not actually the firewall.  It used to be useful, but is now deprecated and no longer supported, as far as I'm aware, so is not a good choice for a firewall configuration application.

Firestarter is not the firewall for ubuntu, but simply a way to configure iptables the actual firewall application used.  If you are running a desktop machine with no running server utilities or programs, you probably do not need to use anything to change the default setup of iptables in ubuntu.  If you want to look into things in more detail look at:-
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[https://wiki.ubuntu.com/Security/Features](https://wiki.ubuntu.com/Security/Features)
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

Transmission will run perfectly safely and well without you doing anything to the standard security settings.

Remember, Ubuntu is not Windows, so you need to have a rethink about your normal security needs.

---

### Post by pl@yer on 2011-01-21
Guarddog is a nice gui app to configure iptables. Better than firestarter in that it is configurable.

---

### Post by bradthewanderer on 2011-01-21
Thank you all for your great suggestions and answers, it warms my heart when people answer so well and quickly without all the 'you are a noob and idiot stuff'.:D

---

