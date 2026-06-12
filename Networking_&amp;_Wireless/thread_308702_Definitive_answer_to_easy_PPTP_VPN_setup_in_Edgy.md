---
title: "Definitive answer to easy PPTP VPN setup in Edgy"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by allanlewis on 2006-11-28
Hi,

(Preamble: I've read all the threads on this topic in these forums, so please don't redirect me to other threads unless you think there's something I've missed.)

I'm looking for a way to connect to my university's PPTP VPN in Edgy. I have the following information:
[LIST]
[*]hostname
[*]username
[*]password
[*]MPPE is required
[/LIST]
I used to use pptpconfig in Dapper but I understand that this no longer works. (I didn't like the app but it was the best around.) So what can I do? I know I can use pptp on the command line, but the number of options that app has just bewilders me! Given that I have a relatively simple setup - although I am behind a NAT router - how can I connect to my VPN, preferably from a desktop link (or two: one to start the tunnel, one to stop)?

I'm happy using the command line, but I'm not happy searching through the documentation for pptp (which isn't very comprehensive) when my situation seems pretty ordinary.

Basically, is there a one-line command I can run to connect/disconnect the tunnel?

(I have created the chap-secrets file, as described in the pptp docs, as well as the various options files for pppd.)

Thanks in advance!

---

### Post by koenn on 2006-11-28
I'm using Dapper with pptp client and pptpconfig but as you say there are no packages for edgy (yet ?) A had a look around and found the following : 

[http://pptpclient.sourceforge.net/howto-debian.phtml#configure_by_hand](http://pptpclient.sourceforge.net/howto-debian.phtml#configure_by_hand)

step by step instructions so should be easy : you create 3 config files, and when that's done, you can stop and start a tunnel with a single command (which you can create launchers for)

there's also an extensive diagnosis and troubleshooting howto at
[http://pptpclient.sourceforge.net/howto-diagnosis.phtml](http://pptpclient.sourceforge.net/howto-diagnosis.phtml)

---

### Post by allanlewis on 2006-11-28
I've done that, and it doesn't work. If I run the debug command, I see that my IP address is sometimes reported as 0.0.0.0, which might well be the problem, but pptpconfig worked for me on Dapper, so I thought someone must have written some app - at least an sh script or similar - to configure pptp for a simple situation like mine.

I can post the output from the debug option of pptp if you want.

---

### Post by RikBlankestijn on 2006-11-29
> **allanlewis said:**
> I've done that, and it doesn't work. If I run the debug command, I see that my IP address is sometimes reported as 0.0.0.0, which might well be the problem, but pptpconfig worked for me on Dapper, so I thought someone must have written some app - at least an sh script or similar - to configure pptp for a simple situation like mine.

I can post the output from the debug option of pptp if you want.Although pptpconfig doesn't work anymore you can still start the vpn connection with ```
sudo pon yourconnection
``` and shut it down with ```
sudo poff yourconnection
```.

---

### Post by allanlewis on 2006-11-29
So I can use pptpconfig to do all the configuration and then start the tunnel from the command line using pon/poff?

---

### Post by LostShootingStar on 2006-12-04
pon and poff did not work for me. someone please help! i cant use network-manager, so that is not an option

---

