---
title: "Cisco AnyConnect Client fails on ubuntu hardy hernon"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by sarath_it on 2008-06-24
My AnyConnect VPN client from cisco fails to connect on Hardy.

It fails with
```
Connection attempt has failed due to server certificate problem.
```

Screenshots and more [here]("http://blog.sarathonline.com/2008/06/cisco-anyconnect-client-on-ubuntu-fails.html")

My IT guys seem not to be very intersted as this is happening only on my linux system. If I reboot to Vista it works. Please help.

---

### Post by jacquesaronius on 2008-06-24
I am having the same problem with the Cisco AnyConnect VPN client (version 2.2.0133).  I am running Ubuntu 8.04.  Any help would be greatly appreciated.

Thanks,

-Jacques

---

### Post by cviro on 2008-07-08
Hi,

I've heard that self signed certificate is being used and VPN client doens't like it. I tried to get it working by adding certificate to CA certs (/usr/share/ca-certificates) and then running 

```
sudo update-ca-certificates
```
but id didn't help. Let me know if you were able to resolve this problem, please.

Tomas

---

### Post by cviro on 2008-07-08
Finally I got it fixed. I just followed instructions on [http://www.experts-exchange.com/OS/Linux/Distributions/Fedora/Q_23440723.html]("http://www.experts-exchange.com/OS/Linux/Distributions/Fedora/Q_23440723.html") and did this:

```
sudo ln -s /usr/lib/libnss3.so.1d /usr/lib/libnss3.so
sudo ln -s /usr/lib/libplc4.so.0d /usr/lib/libplc4.so
sudo ln -s /usr/lib/libnspr4.so.0d /usr/lib/libnspr4.so
sudo ln -s /usr/lib/libsmime3.so.1d /usr/lib/libsmime3.so
```

I am no Linux exptert, just wanted it to work. This is bug and is supposed to be fixed in AnyConnect 2.3. Here is what I did. Location of the libraries may vary.

Hope this helps,

Tomas

---

### Post by ugutugut on 2008-10-21
Hi, where can I download AnyConnect-Linux-Release-2.2 ?
TIA

---

