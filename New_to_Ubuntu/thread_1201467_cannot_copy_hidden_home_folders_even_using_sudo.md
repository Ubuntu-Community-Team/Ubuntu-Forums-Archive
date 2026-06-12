---
title: "cannot copy hidden home folders even using sudo"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by Duke Togo on 2009-07-01
hi
I did find a page through google about this but then my system locked up and when I rebooted I couldn`t find it again
anyway....
I want to do a fresh install so I am copying my home folders across to my other computer by usb (home folder is too big to do all at once) as back up
the problem is the .hidden folders, when I try to copy to the usb it says there is no permission 
this is even with sudo nautilus or sudo thunar
whats going on?
how can I copy these files to my flash drive?
thanks

---

### Post by snakeman21 on 2009-07-01
open a Terminal (Applications > Accessories > Terminal) and type:

```
gksudo nautilus
```

It will ask for a password.  Type your password and hit enter.  This will open Nautilus, a file browser with root permissions.  You should be able to do it from there.

---

### Post by Jakey_TheSnake on 2009-07-01
First question, why are you doing a fresh install? 

Secondly, gksudo nautilus doesn't work? Alt + F2, enter that, then copy them using it and drag into USB folder (doesn't have to be as root this one). 

If not, right click on the hidden folder (Ctrl + H if you can't see it inside your home) and select properties, make sure you have read/write/access/modify etc permissions, if you do then it sounds like you don't have permission to write to the USB device rather than move the folders. 

What happens when in terminal you apply the command "sudo cp ~/.* /media/disk"? This would copy all of your hidden folders to your USB, assuming it is mounted at /media/disk (most likely if you only have one USB device connected). 

Report back afterwards please =)

---

### Post by Duke Togo on 2009-07-01
whats the difference between gksudo and sudo?
btw the files seem to be copying ok now
thanks

---

### Post by drs305 on 2009-07-01
> **Duke Togo said:**
> whats the difference between gksudo and sudo?


Here's a link that explains it fairly well:
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

