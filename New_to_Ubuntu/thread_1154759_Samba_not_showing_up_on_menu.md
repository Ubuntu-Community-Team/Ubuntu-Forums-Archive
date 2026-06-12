---
title: "Samba not showing up on menu"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by Scunnered on 2009-05-10
I downloaded Samba from Synaptic and wanted to check the help only to find that looking for Samba on the menu lists nothing showed.  I double checked Synaptic and yes I find that is is marked as loaded.

Where will I find Samba and what do I need to do to have it display on a menu?

---

### Post by Didius Falco on 2009-05-10
The first thing I'd try is ```
man samba
``` - that should bring up some documentation, and possibly lead you to more.  

I also found this. It looks like a good place to start:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

There are quite a few links at the bottom of this Community Documentation, for further reading.

Regards,

Didius

---

### Post by Scunnered on 2009-05-10
Thanks Didius

The links will help but my initial problem is more of where the expletive deleted is it within the menu structures.  I know I downloaded it ok so it is more a case of come out come out where ever you are.

I will work through the links and see if I can get my head round things but still need to know how once I know what has to be done I can do it by accessing it in Ubuntu

Thanks again

---

### Post by blueridgedog on 2009-05-10
There is no menu item for samba.  It is a server process and is configured via a text file and generally started and stopped via there terminal.  There are some GUI applications that will help you, but they are separate applications.

---

### Post by blueridgedog on 2009-05-10
Mick Bauer started a six part series on configuring and securing samba in the November issue of the Linux Journal.  In his article, he mentions swat as a graphical web-based configuration tool  You can read more here:

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/SWAT.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/SWAT.html)

Also, I recommend his articles on samba (and others).

The first in the series:

[http://www.linuxjournal.com/article/10224](http://www.linuxjournal.com/article/10224)

And the second with instructions/discussion regarding swat:

[http://www.linuxjournal.com/article/10256](http://www.linuxjournal.com/article/10256)

---

### Post by Scunnered on 2009-05-10
**blueridgedog**

Thank you for your posts.  I have had a look at the various items refered to but find that they are well over my head and don't meet my needs.

I have been working with the Ubuntu Help Centre aiming to have my printer (USB connected to my laptop) available to a friend using XP.  Both Laptops are wireless connected to the internet and my laptop is exclusively running Jaunty.

From the section network printing it implied that Samba was required and this prompted me to download it.  However as I could not find a menu item this caused the question.

I will see what I can find elsewhere and hope that I can set up the printer to share.

Once again my thanks

---

