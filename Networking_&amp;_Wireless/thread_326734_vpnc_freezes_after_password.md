---
title: "vpnc freezes after password"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by sander marechal on 2006-12-28
I can't connect to my work anymore using vpnc. It used to work but it has stopped for some reason. After starting vpnc it asks for my password and then freezes. Nothing has changed, except about two months worth of dapper updates.

---

### Post by sander marechal on 2006-12-29
Anyone? Please? I had to boot back into Windows XP in order to log into work. I never realised how bad Windows is untill now after two years of Ubuntu use.

I have attached the output of vpnc-connect --debug 3 in the vpnc.txt file.

Thanks in advance.

---

### Post by lewiz on 2007-01-10
Hi,

Did you managed to resolve this?  A friend of mine has now run into this problem too!

Thanks,
Lewis.

---

### Post by Nikos.Alexandris on 2007-01-29
Really,

I have no idea if this helps you since I am not an expert... but I'll give it a shot:

1. Downloading manually the vpnc (+dependency packages from [http://packages.ubuntu.com/edgy/net/vpnc](http://packages.ubuntu.com/edgy/net/vpnc) )

2. Installing the aforementioned with "sudo dpkg -i *.deb"

**Here you can see that the "libc6" is degraded from [B]2.4-1ubuntu12.3** to 2.4-1ubuntu12[/B]

So, only this package is really the difference, I suppose !

3. Using the vpnc I get my vpn working ( ...although I have to manually change the 1st nameserver in the file /etc/resolv.conf and changing the files attributes with "sudo chmod 440 resolv.conf" which is necessary later I think [an expert told me so ;-P] ).

That's all...

Now my problem is *how to keep the older version of libc6* and *how to make the resolve function automatically to obtain the proper nameserver*?

---

### Post by Nikos.Alexandris on 2007-02-01
I tried today to utilise the vpnc (after upgrading all relevant packages from the repositories) to get into the university's vpn working... and it works!

I was satisfied that the DHCP works quite well and the correct nameserver(s) where assigned (in the file /etc/resolv.conf).

I disconnected immediately and tried all over again to make sure it works. The vpn connection works but (!) the resolv.conf was not automatically updated this time(?).

Any idea's?

---

### Post by sander marechal on 2007-02-02
For me the problem has been "resolved". I put that into quotes because I have no idea how. As unexpectedly as it stopped working it has started working again. First it would only work on eth0 (wired) and not on eth1 (wireless) but now everything works again.

Weird :-/

---

### Post by Nikos.Alexandris on 2007-02-05
It might have to do with the file's (resolv.conf) attributes... 

Try to change them to 440 (sudo chmod 440 /etc/resolv.conf).

This could solve the auto-nameserver-assigning problem...

Greetings!

---

