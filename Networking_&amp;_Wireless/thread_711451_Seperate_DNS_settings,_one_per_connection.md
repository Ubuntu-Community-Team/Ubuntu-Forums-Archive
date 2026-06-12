---
title: "Seperate DNS settings, one per connection"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by Alfr&#1077;do on 2008-02-29
I was wondering whether it's possible to keep different DNS settings for different connections? Kinda like you have in Windows, where every network connection has its own DNS address.

Thanks

---

### Post by Mr. C. on 2008-02-29
DNS is system-wide.

Programs use the system resolver library, and there is no per-network DNS setup.

If you run your own DNS server, you can configure how DNS resolutions occur per network.

---

### Post by Alfr&#1077;do on 2008-03-01
Thanks for your reply.

I don't run my own DNS server, so that's not an option.

Is it so for every distro, or Ubuntu specific? I regularly switch between a LAN connection without DHCP and a wireless one with. This means I have to reconfigure my DNS around three times a day, which really sucks.

---

### Post by Mr. C. on 2008-03-01
This is the way *nix systems work.

While you can only use one at a time, you can use network manager to create locations, which you switch when you switch networks.  

Open Network Manager by clicking the network manager icon in the upper right.  Select Manual Configuration.  Select the Wired connection, and click Properties.  Disable Roaming Mode.  Click the DNS tab, and set the DNS server you want.  Then click the Diskette Icon to save the profile.  Give it a name that suits you.  Now, when you connect to the network, just select your named profile and it will change the DNS server to what was saved.  You can do likewise as you please with your other interfaces.

You can also do this via script.

---

### Post by Alfr&#1077;do on 2008-03-01
Guess I'll have to settle for that then, thanks for your help! :)

---

### Post by aidanr on 2008-03-01
[Wicd]("http://wicd.sourceforge.net/") lets you specify different dns settings per connection.

---

### Post by Alfr&#1077;do on 2008-03-01
I'll try it out, thanks a lot!

---

### Post by Mr. C. on 2008-03-01
But does it play nicely with Network Manager ?

Again, this is a pretty trivial script that just overwrites resolv.conf when you connect to the non-DHCP network.

---

### Post by aidanr on 2008-03-01
No, it replaces Network Manager. It let me connect to wpa2 on my Eee where Network Manager wouldn't, also let me save the password instead of inputting it on every boot, and also got rid of NM's annoying error messages on shutdown. I'm surprised it hasn't replaced NM officially. But whatever works, choice is good.

---

### Post by kesomir on 2008-03-01
Can't you just put in all the nameservers from each location into /etc/resolv.conf ? I < think > it iterates through them all until it finds one that works.

---

### Post by Mr. C. on 2008-03-01
> **kesomir said:**
> Can't you just put in all the nameservers from each location into /etc/resolv.conf ? I < think > it iterates through them all until it finds one that works.

No, these are not a list of random servers to try.  Rather, they are tried in order, and later listed **nameservers** are not used until a long timeout.  This will delay all network name lookups, and perceived networking performance, significantly.

Multiple **nameserver** listings are for *backup* nameservers when the primary server does not respond.

---

### Post by Mr. C. on 2008-03-01
> **aidanr said:**
> No, it replaces Network Manager. It let me connect to wpa2 on my Eee where Network Manager wouldn't, also let me save the password instead of inputting it on every boot, and also got rid of NM's annoying error messages on shutdown. I'm surprised it hasn't replaced NM officially. But whatever works, choice is good.

Nice to know - thanks.  I personally find Network Manager to be poorly implemented and confusing to users.  It is certainly better in 7.10 than previous releases.

---

