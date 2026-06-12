---
title: "Evolution gets just a few mails"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by MrZehl on 2007-04-11
When I recieve mails from a pop account I get only a few of the 440 messages. Then I get an error.
> 
Error while Fetching Mail.

Cannot get message 6b05fee86b9d2b1cb191c937bf9cad3a: Connection timed out

I contacted my provider but there is nothing wrong on the server. They say that it's probably an firewall or router that's the problem. 

I use feisty beta with all current updates and changed nothing to the default firewall settings. My computer is connected to a multimedia modem DV-201AMR, which also is a router. 

Do I've to forward a port for evolution? Or do I have to change the firewall settings?

---

### Post by bnuytten on 2007-04-21
> **MrZehl said:**
> Do I've to forward a port for evolution? Or do I have to change the firewall settings?

No and no.
You do not have to forward a port, I am 100% sure if you are using POP, 99% IMAP. Since the connection times out after a few mails, it means it has been established and (unless you have a very advanced firewall config) the firewall already allowed the connection.

So what else than? You can telnet to your mail server and speak a little POP/IMAP yourself to analyse the problem further. Or easier, install wireshark and sniff what exactly happens. Don't post the output here since this would reveal your username/password etcetera.

---

### Post by MrZehl on 2007-04-21
> **bnuytten said:**
> No and no.
You do not have to forward a port, I am 100% sure if you are using POP, 99% IMAP. Since the connection times out after a few mails, it means it has been established and (unless you have a very advanced firewall config) the firewall already allowed the connection.

So what else than? You can telnet to your mail server and speak a little POP/IMAP yourself to analyse the problem further. Or easier, install wireshark and sniff what exactly happens. Don't post the output here since this would reveal your username/password etcetera.

I installed Thunderbird now. And that works. So it seems nothing is wrong with the server. Something is wrong with evolution. Any way it's an suitable workaround. I don't need Evolution. Just need my mail.

---

