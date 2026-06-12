---
title: "Ubuntu 7.04 + Samba PDC problem"
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by blackknightr89 on 2007-09-28
Well, since a few months I've been working to setup a Linux Samba PDC, looking in the Internet and reading some documentation (SAMBA's official docs and some third party guides). Finally, I found this great site [http://www.linuxhomenetworking.com/wiki/index.php/Main_Page](http://www.linuxhomenetworking.com/wiki/index.php/Main_Page) and following the steps as in [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch10_:_Windows,_Linux,_and_Samba](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch10_:_Windows,_Linux,_and_Samba) (except the SWAT encryption part as I found it irrelevant to my network) I managed to have a running SAMBA PDC. But then the problem came. When I try to add a PC as member of the domain, it found the domain, accept my root credentials but then pop up this message:

> The join operation was not succesful. This could be because an
existing computer accoutn having name "PC-04" was previously
created using a different set of credentials. Use a different computer
name, or contact your administrator to remove any stale conflicting
account. The error was:

Access is denied.

I found it weird 'cause I didn't add a computer before, so I first thought that it was another Windows-Vista-damned-problem, so I tried adding a Windows XP Pro computer to domain. Same response, same problem.
Then I tried to manually add the machines as users and smbusers of the server, nothing happened. I tried to config IPtables to let Samba traffic work without restriction. Nothing except the Server was inaccessible from other computers of the network. I undo that and get back to the server wich machines can't logon but at least is visible as PDC.
Well, I will be gratefull if someone can help me.

PD: I`m sorry for the bad english.

---

