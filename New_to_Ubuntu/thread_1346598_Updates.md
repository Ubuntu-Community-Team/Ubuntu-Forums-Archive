---
title: "Updates"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by frigate13 on 2009-12-05
Just installed Ubuntu last week.  How does one get updates manually?  Do you have to choose certain updates, or should you just download all updates?  Thanks.

---

### Post by The Cog on 2009-12-05
Check if there are any with System->Administration->Update Manager.
I recommend you always install updates. They are all security updates. For new features, you have to look in backports or wait for the next version.

---

### Post by frigate13 on 2009-12-05
> **The Cog said:**
> Check if there are any with System->Administration->Update Manager.
I recommend you always install updates. They are all security updates. For new features, you have to look in backports or wait for the next version.

Thanks.  Also, about your last sentence..."backports," etc.  What do you mean by this.  I am not computer-gifted in any way.  Is this sentence talking about something other than an update?

---

### Post by Paddy Landau on 2009-12-05
> **frigate13 said:**
>  How does one get updates manually?
I suggest that set your updates to automatic. It will check daily for you and put an icon in your panel when it finds any.

---

### Post by howefield on 2009-12-05
> **frigate13 said:**
> ..."backports," etc.  What do you mean by this.  I am not computer-gifted in any way.

Explanation on what backports are...

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

You would have to have manually enabled this in your repository settings, you probably haven't given you do not know what they are ;)

---

### Post by Paddy Landau on 2009-12-05
> **frigate13 said:**
> about your last sentence..."backports,"
Don't worry about this.

A backport is where a newer program is made available for an older version of Ubuntu. For example, Ubuntu Hardy still uses OpenOffice 2.4, so you'd need a backport (ported backwards from Jaunty) to use OpenOffice 3 if you still used Hardy.

---

### Post by mikechant on 2009-12-05
> Thanks. Also, about your last sentence..."backports," etc.

Unless you're desperate to have a newer version of some important program you're using, don't worry about backports.

Example: On Ubuntu 9.04 (Jaunty) the standard version of firefox is 3.0.x (currently 3.0.15). The normal update process will give you security updates - e.g. if a serious security problem is found there will be a 3.0.16 and it will be automatically presented to you for installation.
But if you want the new firefox features found in version 3.5.x then you either have to upgrade the whole of Ubuntu to version 9.10 (Karmic), which comes with Firefox 3.5.x, or you have to use the backports or other non-standard method to install Firefox 3.5.x in Ubuntu 9.04.

Summary: If you're happy with the current versions of the software you use most, don't worry about backports etc.

---

