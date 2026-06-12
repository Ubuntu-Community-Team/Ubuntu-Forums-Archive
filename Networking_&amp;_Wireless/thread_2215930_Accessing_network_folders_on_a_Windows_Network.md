---
title: "Accessing network folders on a Windows Network"
date: 2014-04-09
forum: Networking &amp; Wireless
---

### Post by rob44 on 2014-04-09
Hi,

I am totally new to Ubuntu. Given the end of support for Windows XP, I have decided to attempt to move my existing system over to Ubuntu.So far so good. However, I am using this PC on a company network and want to access my network folders that I can usually access when I log in to my network account in Windows XP.The question is how exactly do I do this? I have tried playing around with "Connect to Server" in Nautilus, but it is a little temperamental - 1st attempt seemed to connect but wouldn't let me  access the particular folder I should be able to access.Further attempts just kept hanging.

Can anyone help me with a step by step guide to being able to access my network folders? I have seen a few articles online but they are more focused on sharing folders in Windows for use in Ubuntu which is not what I'm trying to do. Also, is there anywhere in Windows XP which will tell me the server info I need to enter into Ubuntu, i.e. Domain, Workgroup. I have guessed this so far but unsure if I'm missing something.Many thanks for your help

Rob

---

### Post by TheFu on 2014-04-09
If your work uses NT-Domains or "Active Domains", then the admin will need to add your system to their network. I haven't a clue how that is done.  If it is just a workgroup, then your credentials need to be entered as workgroup\userid, then the password.

---

### Post by rob44 on 2014-04-09
Hi TheFu,

I'm a little confused with your response as I have been using this system on the network with Windows XP for years. So the computer name/IP is already registered with the network admins. Are you suggesting that using Ubuntu means something else has to be changed by admin? The PC hasn't changed, just the OS.

Also, when you say enter credentials, where do I do this? Via "Connect to Server => Windows Share?

Thanks
Rob

---

### Post by sudodus on 2014-04-09
I think you must discuss with and get help from the admin of the company network, as indicated by TheFu.

I hope that with some help from here you can get things working well, and maybe you can also convert some of your colleague's computers to some Ubuntu version and flavour.

Good luck :-)

---

### Post by TheFu on 2014-04-09
> **rob44 said:**
> Hi TheFu,

I'm a little confused with your response as I have been using this system on the network with Windows XP for years. So the computer name/IP is already registered with the network admins. Are you suggesting that using Ubuntu means something else has to be changed by admin? The PC hasn't changed, just the OS.

Also, when you say enter credentials, where do I do this? Via "Connect to Server => Windows Share?

Thanks
Rob

Well - I'm confused all the time. ;) Don't get me started with LDAP/Zimbra and Posix settings.

Perhaps this link will help? [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto) In this situation, the OS instance must be connected to the AD system ... run by the Windows Admins. Every system added to AD needs to be added to the "domain controller". This isn't just hostname/IP stuff. It is an exchange of keys for supposed increase security. Alas, even AD with Kerberos has been hacked.

Of course, there are different ways that Widnows runs on a network. There's pure IP, Workgroups, NT-Domains or ActiveDirectory - you need to figure out which is being used on YOUR network.  Anything other than Active Directory (AD), then you should be able to authenticate like I said above. [https://www.linux.com/learn/tutorials/336477:how-to-join-a-ubuntu-machine-to-a-windows-domain](https://www.linux.com/learn/tutorials/336477:how-to-join-a-ubuntu-machine-to-a-windows-domain) might explain better.

---

