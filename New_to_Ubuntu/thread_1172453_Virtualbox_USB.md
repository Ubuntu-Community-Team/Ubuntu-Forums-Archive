---
title: "Virtualbox USB?"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-05-28
OK I want to print from an XP Virtualbox but how do I setup virtual box and USB? I've selcted the printer from within the virtualbox settings button but when i'm in the virtual machine it's not there....

---

### Post by albinootje on 2009-05-28
> **kamitsukai said:**
> OK I want to print from an XP Virtualbox but how do I setup virtual box and USB? I've selcted the printer from within the virtualbox settings button but when i'm in the virtual machine it's not there....

Are you using the OSE or the PUEL version ? 
And which VirtualBox version ? 
Is your user in the vboxusers group ?
Are other usb devices working in your guest VM ?

---

### Post by kamitsukai on 2009-05-28
> **albinootje said:**
> Are you using the OSE or the PUEL version ? 
And which VirtualBox version ? 
Is your user in the vboxusers group ?
Are other usb devices working in your guest VM ?

OK sorry for the lack of info;)

it's the latest version off the site so it's V.2.2.2 and its the PUEL version

whats the vboxusers?

no it's says no activity when hovering over the icon in the bottom right although if i right click I can see the printer but it's greyed out..

---

### Post by kamitsukai on 2009-05-28
OK I think I've added myself to the vboxusers group? with:

```
sudo adduser carl vboxusers
```

but it's still greyed out, I'll try logging in+out again

---

### Post by kamitsukai on 2009-05-28
It works =] lol

---

### Post by albinootje on 2009-05-28
> **kamitsukai said:**
> 
it's the latest version off the site so it's V.2.2.2 and its the PUEL version

Thanks.
> 
whats the vboxusers?


Try this :
```

sudo adduser your_username_here vboxusers

```
After that log out of the desktop, and log in again, and check whether the groups :
```

groups

```
And then try VB again.

---

### Post by albinootje on 2009-05-28
> **kamitsukai said:**
> It works =] lol

Excellent! :)

---

