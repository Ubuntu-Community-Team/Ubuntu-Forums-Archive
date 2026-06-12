---
title: "Help setting up MoBlock"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by mmitt on 2009-05-02
Hey guys! I was just wondering how I could set up MoBlock to keep people from connecting to my IP on FrostWire or Transmission. Thanks guys!

---

### Post by lovinglinux on 2009-05-02
To install, follow the instructions on [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/) according to your Ubuntu version.

During the installation it will prompt for the configuration. Just follow the instructions on screen, which are well explained. Then ask more specific questions if you have doubts about a particular step. You will be able to reconfigure it any time you want if you do something wrong. You can also install mobloquer, to control and configure moblock via GUI, which is recommended for novices. 

A good place for asking questions is the [General Moblock thread](http://ubuntuforums.org/showthread.php?t=803183)

---

### Post by mmitt on 2009-05-02
Ok. But is there anything else I need to do after the beginning installation to keep people from connecting to me on a torrent client?

---

### Post by lovinglinux on 2009-05-02
> **mmitt said:**
> Ok. But is there anything else I need to do after the beginning installation to keep people from connecting to me on a torrent client?

You need to select the option to start moblock on boot and also keep your blocklists updated. I don't think there is anything else. Once you start the computer, moblock will be blocking connections system wide. If you use mobloquer you can monitor blocked connections in the GUI, but you can also do this via terminal using the following command:

```
tail -f /var/log/moblock.log
```

Moblock comes with several blocklists options, that are downloaded from [Bluetack](http://www.bluetack.co.uk/forums/) and [iBlocklist](http://iblocklist.com/lists.php) web sites. Update them at least once a week. Updating every day is too much in my opinion.

---

### Post by mmitt on 2009-05-02
Thanks for all your help. One more question: afterwards, my Thunderbird (Set up with an aol account) was getting a connection refused. So I told it to allow SMTP and IMAP both outgoing and incoming. Is this a good or bad idea?

---

### Post by lovinglinux on 2009-05-02
> **mmitt said:**
> Thanks for all your help. One more question: afterwards, my Thunderbird (Set up with an aol account) was getting a connection refused. So I told it to allow SMTP and IMAP both outgoing and incoming. Is this a good or bad idea?

Is a BAD idea to allow incoming connections, because you don't actually need them to get your mail. Incoming connections are connections requested by the remote machine. Whenever you use Thunderbird, it will be your client that request the connection, so only outgoing is necessary. Nevertheless, allowing a single IP is more secure than allowing an entire protocol (HTTP, SMTP, IMAP), specially when using p2p. What happens is that a torrent peer with bad intentions, might configure his client to accept connections on http, smtp, ftp or imap. They do this because these are common ports that people usually allow in the firewall/ipblock for regular Internet usage. So if you allow SMTP on moblock and a peer is using port 25 for torrenting, then moblock won't block the connection if your torrent client tries to connect to his. It will still block if the peer requests the connection, because moblock will still be filtering the port you use to accept torrent connections. But since your torrent client initiate request all the time and you don't have control over which peer to connect, then you might get a connection to some peer you don't want.

---

### Post by jre on 2009-05-03
Further to what lovinglinux said, I recommend to only whitelist ports, if the application in question connects to a wide range of IPs. E.g. this is the case for websurfing, so http (80) and https (443) are whitelisted in WHITE_TCP_OUT. If your mail client only connects to one server with one IP address (or just a few) I suggest to whitelist this IP with WHITE_IP_OUT.
Of course this is only important for paranoid people ;-)

EDIT: Real paranoid people can combine port and IP whitelisting with custom iptables scripts. And real real paranoid people should not whitelist anything, especially not ports.

---

