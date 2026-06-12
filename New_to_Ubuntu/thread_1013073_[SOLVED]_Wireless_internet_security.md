---
title: "[SOLVED] Wireless internet security"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by echo314 on 2008-12-16
If I'm using an unsecured wireless network at home or school, is it safe to use online banking or other sensitive service as long as I am using https so the connection is encrypted? Or is it still not ok because the network itself is not secure...

---

### Post by Nxion on 2008-12-16
> **echo314 said:**
> If I'm using an unsecured wireless network at home or school, is it safe to use online banking or other sensitive service as long as I am using https so the connection is encrypted? Or is it still not ok because the network itself is not secure...

Even though it is encrypted. There still is that chance that something could happen. IT is possible to still sniff out sensitive data.

---

### Post by Hospadar on 2008-12-16
I would say so, https connections use ssl encryption which is very hard to break without having a virus at one end, forging a dns to use your own cert., etc.  Anyone could theoretically sniff out your https packets, but making sense of them would still be extremely difficult.

More importantly, if anyone is clever enough to break ssl or pretend to be your bank when they are not, then they are more than clever enough to break wireless encryption, which is much weaker. This is the reason that most major organizations with wireless (universities, big companies) generally don't even bother with wireless encryption, it'll keep your dumb dorm-mates from cruising porno on your router, but it won't hold off a determined criminal for more than 10 minutes usually.

If you have the choice, a wired connection is certanly safer, and if you see some creeper parked right outside with a van and a ton of expensive hacking equipment, probably hold off the wifi.

So I would say don't worry about it, but don't do anything stupid either, If your bank website looks totally different than it did last time, maybe wait a while or try a wired connection before you type in your password.  I would hope that'd be common sense though.

---

### Post by Nxion on 2008-12-16
> **echo314 said:**
> If I'm using an unsecured wireless network at home or school, is it safe to use online banking or other sensitive service as long as I am using https so the connection is encrypted? Or is it still not ok because the network itself is not secure...

Also, for your home network, you really don't have to worry about that. I would recommend if you do any kind of finance or transmission of sensitive data at home, setup your router so it is secure and who ever connects to it, needs to put in a password. is there a reason why you don't have your router secured?

---

### Post by nhasian on 2008-12-16
I would strongly caution you against accessing sensitive material over an unsecured wifi network.  sure viewing webpages or youtube is okay, but i wouldnt enter my username and password to my banking website or enter my credit card number, etc.

why dont you use an encrypted network at home?  it is easy to setup WEP or preferably WPA2 within your wifi router.

---

### Post by mbsullivan on 2008-12-16
> If I'm using an unsecured wireless network at home or school, is it safe to use online banking or other sensitive service as long as I am using https so the connection is encrypted? Or is it still not ok because the network itself is not secure...

Because you are operating through an encrypted connection, you shouldn't worry too much about somebody sniffing your username and password.

If this is your home network, the biggest security risk really comes from allowing other people to enter your network and probe any unsecured computers (shared folders, servers with weak passwords, etc). 

Also, know that any basic FTP connection sends username/password completely unencrypted, so it's as good as giving your information away. This is one good reason to not share the same password between too many accounts.

However, when doing online banking, etc, make sure that the page you go to is the actual website you intend. An unencrypted wifi network will make it easier for somebody to use a DNS cache poisoning attack or some other method to redirect you to a malicious site.

> 
If you have the choice, a wired connection is certanly safer, and if you see some creeper parked right outside with a van and a ton of expensive hacking equipment, probably hold off the wifi.

This really depends on the nature of your hardwired network. It is possible to ascertain the exact same information that you get from sniffing an unencrypted network if you operate a router anywhere en route to a destination, so you can't really treat a hard-wired connection as a security measure.

Also, if you're on a large LAN (like on a college campus), ARP spoofing attacks and other things can wreak major havoc. It's certainly possible to sniff traffic off of a LAN, as well as wireless networks.

Mike

---

