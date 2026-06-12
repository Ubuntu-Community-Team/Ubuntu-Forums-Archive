---
title: "Samba password containing a '#' &amp; CUPS"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by DeiMudder on 2006-10-25
Hi everyone,

I'm having a little trouble printing via Samba/CUPS and a password that contains a '#' character. I'm using Ubuntu 6.06 and a Lexmark C760 attached to a windows network. My user is called 'user' and has the password 'passw#rd' (i.e. with a # in the password), the printer is called 'PRT' on the server 'SRV' in the domain 'DOM'. I configured the printer with the Gnome Printer Utility. Right after that my /etc/cups/printers.conf looks like this: 

```

# Printer configuration file for CUPS v1.2.2
# Written by cupsd on 2006-10-24 15:55
<DefaultPrinter C760>
Info C760
DeviceURI smb://user:pasw#rd@DOM/SRV/PRT
...
</Printer>

```

It works like a charm, I can print without problems. However, after a while (I cannot yet say what exactly causes that) the printers.conf gets corrupted, it then looks like this:

```

# Printer configuration file for CUPS v1.2.2
# Written by cupsd on 2006-10-24 16:00
<DefaultPrinter C760>
Info C760
DeviceURI smb://user:pasw
...
</Printer>

```

It looks like the # character is interpreted as the beginning of a comment and everything after that gets truncated. The printer URI is then of course invalid an I have to reconfigure the printer.

Has anyone an idea what I could do - besides changing the password? Is it possible to store the password in a credential file or something, so that the printers.conf won't get corrupted? Is it possible to escape the # character in the password? Or is there some completely different solution?

I'm sorry, this probably is a pretty basic question, but I really could not find anything usefull in the forums or on google -- '#', 'password' and 'samba' just are a pretty common combination ;-)
Thanks in Advance,

DeiMudder

---

