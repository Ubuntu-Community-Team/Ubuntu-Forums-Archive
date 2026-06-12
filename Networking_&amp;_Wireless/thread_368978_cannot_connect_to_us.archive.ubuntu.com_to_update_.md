---
title: "cannot connect to us.archive.ubuntu.com to update ubuntu"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by hacc on 2007-02-24
cannot connect to us.archive.ubuntu.com to update ubuntu.

could someone please help - i would prefer you IM me my im accounts ar hacc09@yahoo, msn, and aol

hacc

---

### Post by yabbadabbadont on 2007-02-24
Just change to a different mirror or to the primary mirror.

sudo <yourfavoriteeditor> /etc/apt/sources.list

Either change the "us." to a different mirror in another country, like "ca.", or just remove the "us." from the front of each line so that it will use the primary mirror.  You will need to run:

sudo apt-get update

After you make (and save) changes to /etc/apt/sources.list

---

### Post by Lagginator on 2007-12-30
I can't connect to us.archive.ubuntu.com, ca.archive.etc, archive.ubuntu.etc, and security.ubuntu.com.  It says "Failed to fetch [address]  Temporary failure resolving '[address]'"  where [address] is any of the above mentioned four.  What do I do? 

7.10 server i386 on an older computer, I was following the "alternate installation" instructions on the wiki.  I got to the part where you get a GUI but it wouldn't work because of the aforementioned problem.

---

### Post by Lagginator on 2007-12-30
bump

---

### Post by Lagginator on 2007-12-31
bump

---

### Post by kegobeer on 2007-12-31
Have you already checked the software location configuration file?  System -> Administration -> Software Sources?

---

### Post by Lagginator on 2007-12-31
> **kegobeer said:**
> Have you already checked the software location configuration file?  System -> Administration -> Software Sources?

I don't know what that is, but I tried doing what the second post suggested and it still didn't work.  Did I mention I don't know anything about linux?

---

### Post by kegobeer on 2008-01-01
You don't know how to navigate a menu system?  I already told you where to look.

---

### Post by Lagginator on 2008-01-01
> **kegobeer said:**
> You don't know how to navigate a menu system?  I already told you where to look.

I have a command line interface, there are no menus.

---

### Post by Lagginator on 2008-01-10
bump

---

### Post by GavinZac on 2008-01-10
sounds like the server is down

---

### Post by Lagginator on 2008-01-10
> **GavinZac said:**
> sounds like the server is down

Do servers ever go down for a whole week?

---

### Post by GavinZac on 2008-01-10
> **Lagginator said:**
> Do servers ever go down for a whole week?

no, but someone could be very, very unlucky!

---

### Post by diskotek on 2008-02-03
i have the same problem, i can connect internet but no repo's.

this is my second installation of gutsy and i had this error before. what can be an another solution; since i tried to connect different servers.

note: i also used graphical interface.

---

### Post by mmoo9154 on 2008-05-18
I just had this problem, and the clue is the "Temporary failure resolving..." message.  It looks like the DHCP client needs to be refreshed.[1]  either ifdown/ifup, or [FONT="Courier New"]**sudo dhclient -r; sudo dhclient**[/FONT].

[1] [http://www.cyberciti.biz/faq/howto-linux-renew-dhcp-client-ip-address](http://www.cyberciti.biz/faq/howto-linux-renew-dhcp-client-ip-address)

---

