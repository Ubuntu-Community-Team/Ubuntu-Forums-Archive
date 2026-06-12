---
title: "cannot send mail with postfix"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by Charlietje on 2007-07-23
hello,

I have my old computer running as a mailserver.
I use Postfix and Dovecon Imap server.

I can send en receive mail localy with no problem.
But when I want to sent email on an external mailaddres, then it doesn't go.

Although i entered my ISP mail address in the "relayhost"

What could be the problem?

Thanks for your help

---

### Post by Mr. C. on 2007-07-24
Show relevant log messages and commands that you try.

There aren't enough details here to answer your question easily.

MrC

---

### Post by Charlietje on 2007-07-24
when I send localy with Evolution i have no problem. Not on the server and not on another local computer

then i tried /usr/sbin/sendmail -v [email]verstraete.carl@skynet.be[/email]               (my email add)
this is what i received:

> Reporting-MTA: dns; ubuntu-server.localdomain
X-Postfix-Queue-ID: EA64410A80
X-Postfix-Sender: rfc822; [email]root@local.doma[/email]in
Arrival-Date: Tue, 24 Jul 2007 20:36:07 +0200 (CEST)

Final-Recipient: rfc822; [email]verstraete.carl@skynet.be[/email]
Action: deliverable
Status: 2.0.0
Remote-MTA: dns; relay.skynet.be
Diagnostic-Code: smtp; 250 recipient <verstraete.carl@skynet.be> ok




when I tried to send mail with evolution to my address this is what the mail log says
> 
Jul 24 20:16:52 ubuntu-server postfix/postfix-script: stopping the Postfix mail system
Jul 24 20:16:52 ubuntu-server postfix/master[8654]: terminating on signal 15
Jul 24 20:16:57 ubuntu-server postfix/postfix-script: warning: group or other writable: /etc/postfix/./generic
Jul 24 20:16:58 ubuntu-server postfix/postfix-script: warning: group or other writable: /etc/postfix/./generic~
Jul 24 20:16:58 ubuntu-server postfix/postfix-script: starting the Postfix mail system
Jul 24 20:16:58 ubuntu-server postfix/master[9329]: daemon started -- version 2.3.8, configuration /etc/postfix
Jul 24 20:17:51 ubuntu-server postfix/pickup[9330]: 4E02D10A80: uid=0 from=<root>
Jul 24 20:17:51 ubuntu-server postfix/cleanup[9362]: 4E02D10A80: message-id=<20070724181751.4E02D10A80@ubuntu-server.localdomain>
Jul 24 20:17:51 ubuntu-server postfix/qmgr[9331]: 4E02D10A80: from=<root@local.domain>, size=308, nrcpt=1 (queue active)
Jul 24 20:17:52 ubuntu-server postfix/smtp[9364]: 4E02D10A80: to=<verstraete.carl@skynet.be>, relay=relay.skynet.be[195.238.5.128]:25, delay=0.96, delays=0.27/0.02/0.59/0.09, dsn=2.0.0, status=deliverable (250 recipient <verstraete.carl@skynet.be> ok)
Jul 24 20:17:52 ubuntu-server postfix/cleanup[9362]: 4541710A82: message-id=<20070724181752.4541710A82@ubuntu-server.localdomain>
Jul 24 20:17:52 ubuntu-server postfix/bounce[9367]: 4E02D10A80: sender delivery status notification: 4541710A82
Jul 24 20:17:52 ubuntu-server postfix/qmgr[9331]: 4E02D10A80: removed
Jul 24 20:17:52 ubuntu-server postfix/qmgr[9331]: 4541710A82: from=<>, size=1965, nrcpt=1 (queue active)
Jul 24 20:17:52 ubuntu-server postfix/local[9368]: 4541710A82: to=<carl@local.domain>, orig_to=<root@local.domain>, relay=local, delay=0.11, delays=0.02/0.02/0/0.07, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Jul 24 20:17:52 ubuntu-server postfix/qmgr[9331]: 4541710A82: removed
Jul 24 20:19:32 ubuntu-server postfix/smtpd[9429]: connect from unknown[192.168.1.200]
Jul 24 20:19:32 ubuntu-server postfix/smtpd[9429]: NOQUEUE: reject: RCPT from unknown[192.168.1.200]: 554 5.7.1 <verstraete.carl@skynet.be>: Relay access denied; from=<verstraete.carl@skynet.be> to=<verstraete.carl@skynet.be> proto=ESMTP helo=<[192.168.1.200]>
Jul 24 20:19:32 ubuntu-server postfix/smtpd[9429]: disconnect from unknown[192.168.1.200]
Jul 24 20:20:30 ubuntu-server dovecot: IMAP(carl): Disconnected
Jul 24 20:22:51 ubuntu-server postfix/anvil[9431]: statistics: max connection rate 1/60s for (smtp:192.168.1.200) at Jul 24 20:19:30
Jul 24 20:22:51 ubuntu-server postfix/anvil[9431]: statistics: max connection count 1 for (smtp:192.168.1.200) at Jul 24 20:19:30
Jul 24 20:22:51 ubuntu-server postfix/anvil[9431]: statistics: max cache size 1 at Jul 24 20:19:30

---

### Post by Mr. C. on 2007-07-24
Ok, your logs have helped point out the problem.

Please post output from **postconf -n**

I presume that skynet.be is not your domainname, but actually the domainname of your ISP, right?  And you want to relay via their servers?

MrC

---

### Post by Charlietje on 2007-07-24
I also want to give this

> [B]main.cf

non-default parameters[/B]
alias_maps 	hash:/etc/aliases
append_dot_mydomain 	no
biff 	no
ignore_mx_lookup_error 	yes
inet_protocols 	all
mailbox_command 	procmail -a "$EXTENSION"
mailbox_size_limit 	0
mydestination 	ubuntu-server, localhost.localdomain, localhost, local.domain, ubuntu-server.localdomain
mynetworks 	127.0.0.0/8
mynetworks_style 	class
myorigin 	/etc/mailname
recipient_delimiter 	+
relayhost 	[relay.skynet.be]:25
smtp_generic_maps 	hash:/etc/postfix/generic
smtpd_banner 	$myhostname ESMTP $mail_name (Ubuntu)



[B]main.cf

parameters defined as per defaults[/B]
alias_database 	hash:/etc/aliases
config_directory 	/etc/postfix
tls_random_source 	dev:/dev/urandom



**master.cf**

**service	type	private	unpriv	chroot	wakeup	maxproc	command + args**
smtp	inet         n           -            -            -              -       	smtpd
relay	unix         -            -            -            -              -     	smtp

---

### Post by Charlietje on 2007-07-24
indeed skynet.be is my ISP.
I need to use my ISP for non-local addresses

Thanks for your help!

---

### Post by Mr. C. on 2007-07-24
That is not output from **postconf -n**.  

You are trying to relay from the IP 192.168.1.200, but that network is **not** in mynetworks, which only has lists 127.0.0.0/8.

Change mynetworks to:
```

mynetworks 127.0.0.0/8, 192.168.1.0/24
```

and then postfix reload.

MrC

---

### Post by Charlietje on 2007-07-25
Ok! That was the problem! Now it works

Now I have another question. If i want to use dyndns. Can I put there my dyndns domain name?

Anyway, I thank you for your suport

Carl

---

### Post by Mr. C. on 2007-07-26
No, mynetworks is a list of IP addresses or IP ranges.

```
man 5 postconf
```

and search for mynetworks for more details.

Dynamic DNS for incoming email does not work reliably.  A mail server really *needs* a static IP.

MrC

---

### Post by Charlietje on 2007-07-26
so, i guess, if i want to use an external pc, i use a webmail client


Carl

---

### Post by Mr. C. on 2007-07-26
Carl, I'm sorry, I don't understand what you are saying or asking.

MrC

---

### Post by Charlietje on 2007-07-29
I mean,

I want to use my laptop to connect to my mail server, not only from LAN, but also from the internet.
That's why i use Dyndns to have my dynamic IP connected to a domain.

But how can I do it, if I need to enter my network with an IP?

---

### Post by Koybe on 2007-07-29
DNS is just a relation between ip and name. When you'll get connected to your mail server trough squirrel mail or whatever, it's the server itself that will be sending the mails.

---

### Post by Mr. C. on 2007-07-29
Ok, I understand now.  You want to be able to relay mail through your server from any IP.  I will recommend two mechanisms - which one you implement will be up to your comfort and skill level.

The first method is the easiest.  You create an SSH tunnel for port 25, so that you can securely relay email through your server from anywhere, anytime.  All you need is the ssh server installed and configured, and an SSH client on your laptop.

The second method is more difficult, as it requires configuring SMTP AUTH and TLS.  You configure your mail server to support TLS connections, and then configure it to use SMTP AUTH (authentication).  Then, your mail client can securely connect and authenticate anywhere.  This is a simpler in the sense that you don't need to first connect to your SSH server with an SSH client.

Here are the two issues with running a mail server using a dynamic IP:
[LIST]
[*]Mail servers are likely to reject your outbound email
[*]Mail servers are likely to have difficulty reaching your domain's mail server
[/LIST]

MrC

---

### Post by Charlietje on 2007-07-30
Thanks,

I'll try it... But I'm sure I still will need some help ;)

If I use TLS connection, how must I fill in the NETWORK parameter?

---

### Post by Mr. C. on 2007-07-30
Which "network" parameter are you referring to?  I know of no such variable.

MrC

---

### Post by Charlietje on 2007-07-31
i meant the variable "mynetworks"

the ip address will change because of the dynamic ip

---

### Post by Mr. C. on 2007-07-31
The mynetworks variable tells postfix which clients should have additional privileges.  It indicates which clients can relay email.  You can minimally set it to 127.0.0.0/8 if you want.  What additional networks you add depends on how you have your network configured.  If your LAN is NATed, you can add your private IP range as well.

TLS has nothing to do with the mynetworks variable.  TLS simply encrypts the communication between client and host.  I think what you are asking is how you can connect and relay email via your server when your dynamic IP changes.

There is a smtpd_client_restrictions parameter called permit_sasl_authenticated, that allows authenticated clients to relay email.  An example usage in main.cf would be:

```
smtpd_client_restrictions =
   permit_mynetworks
   permit_sasl_authenticated
   reject
```

MrC

---

### Post by Charlietje on 2007-08-07
Hi,

sorry for the long delay...
I managed to set up SMTP AUTH.
Now I can send and receive mail when am on my own network, but when I am on another network i can receive my mail but cannot send because the ISP block port 25

How can I use a different port number?
Does I need to change Dovecot and Postfix port or only Dovecot?


Thanks for your help MrC !!

---

### Post by Mr. C. on 2007-08-07
You have several choices:

 1) VPN
 2) SSH tunnel
 3) Use the submission port (587), or alternate.

Do yo need more explanation about these ?

MrC

---

### Post by Charlietje on 2007-08-08
yes please,

isn't the simples thing to do, to use an alternate port on what postfix/dovecot is listening?
I'm not familiar yet on Virtual Private Networking and SSH tunneling..

what would you think is the best solution?


Carl

---

### Post by Mr. C. on 2007-08-08
Before recommending a solution, let's point out that you probably want to relay mail via your server securely, and not let the world have relay access.  To do this, you can:

1) Establish a VPN connection.  This is more complicated, and requires support from your router.  I'll ignore this option for now.

2) install the ssh-server and configure it to allow remote connections.  You make an ssh connection from your laptop back to your server, and that connection is configured to tunnel port 25 (or 587) back to the server.  How you configure the client, depends on the client you use.  Configuring SSH and opening your firewall for the correct port is not difficult.

3) Direct connections to port 587.  Enable postfix's "submission" port in the master.cf file.  This by default will listen on port 587.  However, it is important to note that this connection is not a secure connect, and postfix cannot distinguish between you and some random user connecting to this port.  So you must configure TLS and SMTP AUTH in postfix.  This is very difficult for some users.  Until you are ready for this option, and want to invest the time in working out the details, I'd suggest #2 above.

Using the SSH tunnel option gives you quick access to your already configured setup.  With port 25 tunneled, you will have a) a secure shell connection to your server, and b) a secure connection to your mail server.

So, which route do you want to take ?

MrC

---

### Post by Charlietje on 2007-08-08
I did option 2 and it works.
I can send and receive mail for my local accounts, localy and from another location. However, if i want to sent mail to hotmail it doesn't go.

here is my mail log connection from another location:
> 
Aug  8 20:25:38 ubuntu-server postfix/smtpd[6477]: connect from 217.118-245-81.adsl-dyn.isp.belgacom.be[81.245.118.217]
Aug  8 20:25:39 ubuntu-server postfix/smtpd[6477]: 2973110A7F: client=217.118-245-81.adsl-dyn.isp.belgacom.be[81.245.118.217]
Aug  8 20:25:39 ubuntu-server postfix/cleanup[6480]: 2973110A7F: message-id=<1186597541.5327.2.camel@leen-ubuntu>
Aug  8 20:25:39 ubuntu-server postfix/qmgr[5932]: 2973110A7F: from=<leen@local.domain>, size=476, nrcpt=1 (queue active)
Aug  8 20:25:39 ubuntu-server postfix/local[6481]: 2973110A7F: to=<carl@local.domain>, orig_to=<carl>, relay=local, delay=0.27, delays=0.23/0.02/0/0.02, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Aug  8 20:25:39 ubuntu-server postfix/qmgr[5932]: 2973110A7F: removed
Aug  8 20:25:39 ubuntu-server postfix/smtpd[6477]: disconnect from 217.118-245-81.adsl-dyn.isp.belgacom.be[81.245.118.217]



here is the mail log from local location to sent to hotmail
> 
Aug  8 21:07:48 ubuntu-server postfix/smtpd[9483]: connect from carlverstraete.homeip.net[81.243.133.198]
Aug  8 21:07:48 ubuntu-server postfix/smtpd[9483]: NOQUEUE: reject: RCPT from carlverstraete.homeip.net[81.243.133.198]: 554 5.7.1 <sagittarius23@hotmail.com>: Relay access denied; from=<verstraete.carl@skynet.be> to=<sagittarius23@hotmail.com> proto=ESMTP helo=<[192.168.1.3]>
Aug  8 21:07:48 ubuntu-server postfix/smtpd[9483]: disconnect from carlverstraete.homeip.net[81.243.133.198]
Aug  8 21:11:08 ubuntu-server postfix/anvil[9485]: statistics: max connection rate 1/60s for (submission:81.243.133.198) at Aug  8 21:07:48
Aug  8 21:11:08 ubuntu-server postfix/anvil[9485]: statistics: max connection count 1 for (submission:81.243.133.198) at Aug  8 21:07:48
Aug  8 21:11:08 ubuntu-server postfix/anvil[9485]: statistics: max cache size 1 at Aug  8 21:07:48



and here is my postconf -n
> 
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
ignore_mx_lookup_error = yes
inet_protocols = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = ubuntu-server, localhost.localdomain, localhost, local.domain, ubuntu-server.localdomain
mynetworks = 127.0.0.0/8, 192.168.1.0/24
mynetworks_style = class
myorigin = /etc/mailname
recipient_delimiter = +
relayhost = [relay.skynet.be]:25
smtp_generic_maps = hash:/etc/postfix/generic
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks,


---

### Post by Mr. C. on 2007-08-09
You can always use your own email server to send email to your own accounts on the server, since your mail server is the final destination for your domains.

However, your server will not allow remote users to relay email through your server to some other server.  This would create an open relay.

Note your IP address of the connecting client:

Aug 8 21:07:48 ubuntu-server postfix/smtpd[9483]: connect from carlverstraete.homeip.net[**81.243.133.198**]

This indicates you are on a remote network (relative to postfix's mynetworks).  This also indicates your connection is not tunneled.  If you were tunneled, your IP would appear as 127.0.0.1.

So, get your port 25 tunnel working, and then you'll notice connections from localhost[127.0.0.1].  Postfix will recognize you are on one of its networks, and will allow you to relay because your smtpd_recipient_restrictions allow mynetworks.

MrC

---

### Post by Charlietje on 2007-08-09
oh, I understand...

Can you give me a start on tunneling?

thanks

---

### Post by Mr. C. on 2007-08-09
Ensure 

```
AllowTcpForwarding yes
```

is set in your sshd_config file; restart the server.  Then, connect using ssh:

```
ssh -fNL 25:localhost:25 yourusername@yourhostname
```

The command

```
telnet localhost 25
```

on the laptop will show that you are connected to your mail server.  You configure your laptop mail clients to connect to **localhost**, not your remote host.

MrC

---

### Post by Charlietje on 2007-08-15
Hi,

It works with tunneling! Thanks!
I've got what I wanted and learned alot..

I use evolution for email. Is it possible for evolution to first execute the ssh command before sending?

I didn't find it...


Anyway thanks for the good help!

---

### Post by Mr. C. on 2007-08-15
You're welcome.  Glad its working for you.

I don't know if Evolution can start up a program on start. But you could write a script to start your ssh client and Evolution afterwards.

MrC

---

