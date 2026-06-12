---
title: "Someone knocking at dovecot's door AND Log files which to check"
date: 2014-12-08
forum: Networking &amp; Wireless
---

### Post by trojan222 on 2014-12-08
Hi, should i be worried when someone is knocking on my mail servers door. in my log lines i read this Like a thousend times in a couple of minutes:  

flameon dovecot: pop3-login: Aborted login (tried to use disallowed plaintext auth): user=<>, rip=80.55.213.205, lip=192.168.0.230, session=<bs0n2KIJYQBQN9XN>
flameon dovecot: pop3-login: Disconnected: Inactivity (tried to use disallowed plaintext auth): user=<>, rip=80.55.213.205, lip=192.168.0.230, session=<f9MG2KIJTwBQN9XN>
 flameon dovecot: pop3-login: Disconnected: Inactivity (no auth attempts in 180 secs): user=<>, rip=80.55.213.205, lip=192.168.0.230, session=<Pe9j2KIJtgBQN9XN>

I'm not an expert i just started this mail server up for about two weeks now with a couple of tutorials i've read on the net. and i mostly based it on this tutorial:[URL="http://www.krizna.com/ubuntu/setup-mail-server-ubuntu-14-04/?PageSpeed=noscript"]Setup mail server on ubuntu 14.04 ( Postfix - dovecot ) 
[/URL]

My second question is about the log files. which ones do i defenitly need to check and do they clear themselfs up. It seems they do in my case i can't find any entries before 7 december in mail.log

Many thanks in advance

---

### Post by wyliecoyoteuk on 2014-12-08
What sort of mail are you serving, and who for?
POP3 is for retrieving mail, so looks like someone trying to do so without an unencrypted password.
If you are port forwarding 110, it may just be a scan.

You might want to set up fail2ban to block repeated login attempts

---

### Post by trojan222 on 2014-12-08
It's just a personal server. A hobby server with the purpose to collect and send the mail from and to my domain name. The whole purpose is to gain more understanding of postfix and dovecot. It's not my intention to be an open relay and annoy my provider or others. The server is going to be a setup with a windows 2008 domain controller and maybe a dns server from ubuntu. At this moment  i only want to gain more experience from the logs. i knew in advance these, scans and login attempts would happen. The only thing is i'm not sure what to do next, en which log files (besides mail.log) to study further on. Is it wise to use this fail2ban?

Kind regards

---

### Post by wyliecoyoteuk on 2014-12-08
Well, they are trying to retrieve mail from your server using POP3, which you don't want to allow externally anyway. Or is this an external server? Sorry, I assumed it was behind a router.

Fail2ban just blocks repeated failed login attempts.
It is a simple way to discourage dictionary attacks.
For example, you can configure it so if a user fails to login 3 times their IP is blocked for 10 minutes, this is a good deterrent for a creep who is trying to flood your server with login attempts.

google "hardening a server" for other tools.
A good idea to learn how to reduce the attack surface.
For example, I changed my default ssh port, disabled root logins, I run Fail2ban, rkhunter and chrootkit, closed all unused ports, etc.

---

### Post by tgalati4 on 2014-12-08
```
whois 80.55.213.205
```

If you don't expect any mail from Poland, then you might consider using IP blocking using large, country-wide IP blocks.

---

### Post by trojan222 on 2014-12-10
Thanks for the replies i will give fail2 ban a go

---

### Post by trojan222 on 2014-12-11
Hi, I,ve set up fail2ban with the help of several resources. I've configered the jail conf and the dovecot conf. Fail2ban is sending me mail messages it's started up. Is there a proper way to test the set up rather then waiting for someone to bash me with several login attempts. I've tried to login faulty from my windows machine with squirrelmail that gave no result.

---

