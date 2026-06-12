---
title: "About 2 or more domains on same IP address"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by satimis on 2007-11-07
Hi folks,

Can two or more domain names be mapped to the same IP address, e.g;

aaa.com
bbb.com
ccc.com

mapped to the same IP 123.123.123.123.  Would confusion be created on sharing the same IP address?  TIA


satimis

---

### Post by callan79 on 2007-11-07
> **satimis said:**
> Can two or more domain names be mapped to the same IP address, e.g;

aaa.com
bbb.com
ccc.com

mapped to the same IP 123.123.123.123.  Would confusion be created on sharing the same IP address?


Hello,

Yes this can be done, you can point as many domains as you want to the same machine.

The question though, is can the server software handle it? For example if you want to host websites with Apache, then you will need to use VirtualHosts so that Apache can work out which website address has been typed in, and display the appropriate content.

SMTP Mail is the same thing - you just need to configure the mail server with the domains in there.

What exactly is it that you're wanting to do?

Cheers
Callan

---

### Post by satimis on 2007-11-07
> **callan79 said:**
> Hello,

Yes this can be done, you can point as many domains as you want to the same machine.

The question though, is can the server software handle it? For example if you want to host websites with Apache, then you will need to use VirtualHosts so that Apache can work out which website address has been typed in, and display the appropriate content.

SMTP Mail is the same thing - you just need to configure the mail server with the domains in there.

What exactly is it that you're wanting to do?
Hi Callan,


Thanks for your advice.

I'll use the 2nd domain for test only, following;
PostfixVirtualMailBoxClamSmtpHowto
[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

The test needs at least 2 domains.

I have my own domain running on static IP and will register another subdomain on changeip.com for this test.  They will detect the static IP address.


B.R.
satimis

---

