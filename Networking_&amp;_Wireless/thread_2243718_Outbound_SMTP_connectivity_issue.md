---
title: "Outbound SMTP connectivity issue"
date: 2014-09-10
forum: Networking &amp; Wireless
---

### Post by Woonjas on 2014-09-10
I'm at a loss here as to what's causing outbound SMTP connections to fail on both my Ubuntu systems. 

My server is running Ubuntu 12.04 with kernel 3.2.0-69 (64bit), my laptop 14.04 with kernel 3.13.0-35 (64bit).

I noticed that after a reboot the outbound mail queue on my server was filling up so I tested connectivity using telnet to port 25 of my provider's outbound smtp server.

From both Ubuntu systems telnet tells me it's connected but then hangs until it times out. No smtp server greeter is shown.

Wireshark shows that the greeter actually is received (including TCP Retransmissions)

However when I connect to port 25 on my server from the laptop it immediately returns my server's smtp greeter.

When I try the same telnet command from a Windows 2003 virtual machine (vmware player) it immediately returns the server's greeting/smtp banner (220) 
This to me means that at least outbound smtp traffic is not blocked by my cable modem.

Any idea where to start looking?

Thnx.

---

### Post by TheFu on 2014-09-10
Great troubleshooting.  Helpful.

I can only guess that the DNS isn't the same between Linux and Windows.  Try verifying which IP address the working and non-working environments get for the gateway SMTP server.  Try the telnet by ip, not DNS name. Probably already tried that, just isn't clear to me.

Could the outbound firewall be enabled?  **sudo iptables -L** - if you didn't do this, it isn't likely.

It could also be a mis-configuration for TLS connectivity. Perhaps the gateway requires a specific version of TLS and the linux machines can't set it?  This is an unlikely stretch guess, but ... 

BTW - which MTA is being used?  The telnet removes that, but ...

---

### Post by SeijiSensei on 2014-09-11
Have you tried connecting to the ISP's port 587, the mail submission service, instead of port 25?

---

### Post by Woonjas on 2014-09-21
> **SeijiSensei said:**
> Have you tried connecting to the ISP's port 587, the mail submission service, instead of port 25?

Same result. 
Anyway, I solved my problem by switching my cable modem to BRIDGE mode using my Fritzbox as router instead. Guess there is something foobarred with the router firmware of the mode. And the provider's helldesk wasn't exactly helpfull either - 'I don't know the telnet e-mail program, you should really try connecting using Outlook'

---

