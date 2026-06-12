---
title: "First time with Moblock, advice?"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by danielkabrinski on 2009-10-28
When I used windows I loved peer guardian.  Along with Avast!, Spybot, and a couple other programs it was great for some added protection.

MoBlock is nice.  I learned the basic commands for it and followed the Ubuntu site documentation to set it up...  I would like a more in-depth look though.  I followed instructions and tried to allow these things but I had no success:

- Google POP3 through Thunderbird
- Vendetta Online
- Pidgin (For AIM and Yahoo!)

I set the configuration file back to its standard setting so there is nothing new listed.

If anyone can help me it would be greatly appreciated by this n00b.

---

### Post by lovinglinux on 2009-10-28
> **danielkabrinski said:**
> When I used windows I loved peer guardian.  Along with Avast!, Spybot, and a couple other programs it was great for some added protection.

MoBlock is nice.  I learned the basic commands for it and followed the Ubuntu site documentation to set it up...  I would like a more in-depth look though.  I followed instructions and tried to allow these things but I had no success:

- Google POP3 through Thunderbird
- Vendetta Online
- Pidgin (For AIM and Yahoo!)

I set the configuration file back to its standard setting so there is nothing new listed.

If anyone can help me it would be greatly appreciated by this n00b.

To allow those services you can add the protocol, the port or the service provider to the allow list. For example for Google POP3 you can allow incoming connections on port 995 or allow Google IP addresses. I personally prefer allowing addresses, because when you allow a port then all traffic on that specific port will not be filtered. You will probably need to allow outgoing connections on port 465, so you can send e-mails trough Google SMTP. If you are using IMAP, then use port 993 instead of 995.

For games, I guess allowing the port will be a better option, if you need to allow other players to connect to you. Otherwise, just add the game server IP address to your allow list.

Keep in mind that you can specify different allow lists for incoming, outgoing and forwarding, which gives you a lot of flexibility. You can edit moblock's configuration through the file **/etc/blockcontrol/blockcontrol.conf**.

For example:

```
# blockcontrol.conf - configuration file for blockcontrol

# This file is sourced by a shell script. Any line which starts with a # (hash)
# is a comment and is ignored. If you set the same variable several times,
# then only the last line will be used.

# Refer to blockcontrol.defaults (/usr/lib/blockcontrol/blockcontrol.defaults)
# for the complete set of possible configuration variables with comments.

# Do a "blockcontrol restart" (sometimes even "reload" is enough) when you have
# edited this file.

WHITE_TCP_OUT="http https 465"
WHITE_TCP_IN="995"
MOBLOCK_CRON="0"
ALLOW_IN="/home/you/allow-in.p2p"
ALLOW_OUT="/home/you/allow-out.p2p"
ALLOW_FW="/home/you/allow-fw.p2p"
CRON="0"

```

In this example any outgoing web traffic is allowed for http and https protocols (ports 80 and 443) and also on port 465 (Google SMTP). All incoming traffic on port 995 is also allowed. Additionally, there are also three separate allow ip lists for incoming, outgoing and forwarded traffic.

---

### Post by danielkabrinski on 2009-10-28
Very nice example, thank you.  I see what I was doing wrong now.

Let's say I wanted to set up vendetta online... I could just make one line telling it to allow the server web address?

Or would it work like you have it above?

```

WHITE_TCP_IN="http https vendetta port"
WHITE_TCP_OUT="vendetta port"
MOBLOCK_CRON="0"
ALLOW_IN="vendetta address here"
ALLOW_OUT="vendetta address here"
ALLOW_FW="vendetta address here"
CRON="0"

```

---

### Post by lovinglinux on 2009-10-28
> **danielkabrinski said:**
> Very nice example, thank you.  I see what I was doing wrong now.

Let's say I wanted to set up vendetta online... I could just make one line telling it to allow the server web address?

Or would it work like you have it above?

```

WHITE_TCP_IN="http https vendetta port"
WHITE_TCP_OUT="vendetta port"
MOBLOCK_CRON="0"
ALLOW_IN="vendetta address here"
ALLOW_OUT="vendetta address here"
ALLOW_FW="vendetta address here"
CRON="0"

```

I don't know how vendetta works, but to allow the server, just add the IP range to the outgoing and incoming allowed ip lists.

About your config:

```
WHITE_TCP_IN="http https vendetta port"
```

This is wrong. As far as I know you can only put port numbers or protocols there. For example:

```
WHITE_TCP_OUT="http https ftp"
```

or

```
WHITE_TCP_OUT="80 443 21"
```

Keep in mind this will allow ALL outgoing traffic on those ports or protocols.


About the ALLOW lists:

```
ALLOW_IN="vendetta address here"
```

Instead of putting the IP address in the line above, you should put the path to an IP list, then add the IP ranges to it.

For example:

```
ALLOW_IN="/home/you/allow-in.p2p"
```

The contents of the file **allow-in.p2p** would be something like this:

```
Vendeta Server or whatever:204.15.102.4-204.15.102.4
```

Please notice that the address is repeated because it's an IP range. If you just want to allow a single address, then put the same number as the initial IP and final IP. Additionally, that IP is not necessarily the IP of the server. I just took Vendetta web site IP number as an example.

---

