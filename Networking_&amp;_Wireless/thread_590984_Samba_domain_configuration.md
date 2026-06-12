---
title: "Samba domain configuration"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by ginge6000 on 2007-10-25
Hi, I am trying to experiment with the idea of setting up a network of completely Ubuntu machines which are logged onto via domain authentication.  I set up my smb.conf on the server according to [http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10_p4](http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10_p4) and have successfully logged a Windows XP Pro machine onto the domain.

However, when I try to connect my Ubuntu desktop machine to the Samba domain it says that it has joined the domain successfully but next time I get to the logon screen it doesn't let me log on with a domain account, only with the account on the local machine.  Do I need to alter my smb.conf on the desktop machine?  It is currently this:

```
[global]
    security = domain
    workgroup = myworkgroup
    password server = server

```

According to the [SAMBA howto]("http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/domain-member.html#domain-member-server") this should be enough.  Sure enough, when I do the command ```
net rpc join -S server -UAdministrator%password
``` I get the "Joined domain MYWORKGROUP" message.

I have a feeling that the instructions in the SAMBA howto are for joining to a windows server domain but, having googled for hours, don't seem to be able to find the answer to my problem.

Please help me someone!

---

### Post by ginge6000 on 2007-10-25
Anyone?

---

