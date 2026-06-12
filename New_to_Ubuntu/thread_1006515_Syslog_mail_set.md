---
title: "Syslog mail set"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by peterhof on 2008-12-09
Sorry for the decptive title, but kind of at a loss.

I have Ubuntu 8.10 server.  It sits behind the company firewall.

Setting up for two uses:

1) As a Syslog server to collect logs from Windows servers.
2) As a Snort box to see what is coming through the firewall.

Now, as a Syslog server, I would like to receive alerts by mail to my corporate account along with the log information (and yes I realize that this will need some tweaking so that I do not get inundated with useless events).

On my Windows boxes I have NTSyslog running and apparently it is sending alerts to the server, but quite sure as reading through logs using nano is a bit of a challenge.

On the server I thought I could set up Exim to send me the E-mails (comes with Ubuntu) would this be the "easiest" option?

TIA

---

### Post by lykwydchykyn on 2008-12-09
I've always found exim to be confusing to set up.  I usually use postfix or nullmailer to relay to our company's SMTP server.  You can use webmin to configure postfix as well.

---

