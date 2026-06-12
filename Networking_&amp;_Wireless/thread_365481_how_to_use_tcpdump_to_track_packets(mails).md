---
title: "how to use tcpdump to track packets(mails) ?"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by contactme on 2007-02-19
I am running 2 machines and trying to use IMAP.pm/Simple.pm perl modules to exchange mails between 2 systems.
Mail exchange is through SMTP(for sending the mail) and IMAP(for retrieving the mails).

Somehow it's not working So wanted to check where the packets are and what is their path. I was thinking of using tcpdump but not sure which options to use to track packets between those 2 systems. and to check if the mails are going out of one system and whether mails are coming in another system. Please advice.

Thanks

---

### Post by gradedcheese on 2007-02-21
The simplest way it to lock it to the port (25 usually for SMTP, for example).  Lets say the interface is eth0,

```

sudo tcpdump -i eth0 port 25

```

If you only care about packets from/to a certain ip address, then use 'host':

```

sudo tcpdump -i eth0 host put_ip_here and port 25

```

Options (here only "-i eth0" is used) go before the expression ("host ip_here and port 25").  If you want to log instead of dumping to the screen, give it the "-w path_to_log_file" option.  And of course run "man tcpdump" for more info :)

I usually then fire up ethereal (now known as wireshark) and read the log file with it.

---

