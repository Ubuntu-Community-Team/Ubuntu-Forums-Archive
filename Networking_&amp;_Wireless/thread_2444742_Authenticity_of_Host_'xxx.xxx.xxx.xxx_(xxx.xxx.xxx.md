---
title: "Authenticity of Host 'xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx)' can't be established..."
date: 2020-06-03
forum: Networking &amp; Wireless
---

### Post by annihil2 on 2020-06-03
I hope this is the right place to post this - it was either here, or Network etc etc.

I had an SFTP connection to my file server (running Ubuntu Server) on my primary computer, was working great until a couple days ago when I started receiving a popup in Dolphin with the following message...

```
[COLOR=#000000]The authenticity of host '192.168.111.111 (192.168.111.111)' can't be established.[/COLOR]
[COLOR=#000000]ECDSA key fingerprint is SHA256:LotsOfRandomNumbersAndLettersForTheKeyHere.[/COLOR]
[COLOR=#000000]Are you sure you want to continue connecting (yes/no/[fingerprint])?[/COLOR]

```

My research tells me to wary of a MITM attack - but umm... ok.

Edit: Answering "Yes" just pops up another dialogue box with the same question, same key, etc...

Can someone just tell me how to fix it, what to check, where to go?

Thank you so much.

---

### Post by QIII on 2020-06-03
Moved to Networking & Wireless

---

### Post by SeijiSensei on 2020-06-04
Look at the file $HOME/.ssh/known_hosts on your client machine and and delete the line(s) that refer to the FTP server. Then try reconnecting again.

SSH always issues a warning like this when you're connecting to a new host, or to an old host with a new IP address.  You're not likely subject to an MITM attack when both the server and client are in a private network space like 192.168.111.0/24 unless someone else on your network is trying to do something shady.

Is the server configured to use a static address rather than getting one from DHCP? All servers should have static addresses or else a "reservation" on the DHCP server.  Reservations tie a specific IP address to the MAC address of a computer's network interface.

Are you using [keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")?  Makes life much easier.

---

