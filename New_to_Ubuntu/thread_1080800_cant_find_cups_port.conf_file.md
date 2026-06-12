---
title: "cant find cups port.conf file"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by bnhrobotics on 2009-02-25
Hello,

I just installed a new network printer with cups on an 8.04 machine. I wanted to be able to access it from other Ubuntu computers as well as WinXP. I can print from the original computer, but not any of the others.

I keep reading about making a modification to /etc/cups/cups.d/ports.conf for this to work. The problem is that this file does not seem to exist for me. I can already login to cups with [http://myip:631](http://myip:631) from another computer, but I cant print. The farthest I can navigat to is /etc/cups. What do I do?

Thanks

Bryan

---

### Post by iaculallad on 2009-02-25
Shouldn't the file to edit be /etc/cups/cupsd.conf and not /etc/cups/cups.d/ports.conf?

---

### Post by cmnorton on 2009-02-25
It looks like that directory is deprecated. I don't have it on my Ubuntu 8.10 system, and I just checked a Red Hat Enterprise Linux 4 system. However, you should be able to connect to this system. For Windows connectivity, you need to share the printer out through /etc/samba/smb.conf.

For connecting remotely, I am not completely sure how to do that.

---

### Post by bnhrobotics on 2009-02-25
Maybe I was looking at old documents. Turns out that I needed to simply check "Show printers shared by other systems" on the other ubuntu computer to see the printers.

Now I am left with two problems:
1) I checked "Allow printing from the Internet" in the Server section of Admin tab for cups. I then hit Change Settings. Now whenever I uncheck it and hit Change Settings, the page comes back with the check mark still present. How do I get rid of that?

2) How do I see CUPS printers from windows?

I am using CUPS 1.3.7

Thanks

---

### Post by cmnorton on 2009-02-26
1) What interface are you using to configure CUPS and is this Kubuntu or Ubuntu? 

I'm using Kubuntu and cannot see the field to which you are referring. I suggest -- as root -- looking for and changing that field in the appropriate CUPS. I believe you add a line like this, if it's not already there:

listen *:631

As to seeing this printer from Windows. You need to modify /etc/samba/smb.conf as root.

---

### Post by cariboo on 2009-02-26
Have you got:

```
Share published printers connected to this system
```

enabled on the Administration page?

Jim

---

