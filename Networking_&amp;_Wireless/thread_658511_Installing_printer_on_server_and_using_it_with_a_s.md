---
title: "Installing printer on server and using it with a samba"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by murmel on 2008-01-04
Hello  everybody, I got a problem which neither google nor ubuntu forums search have given me a solution.
I've been trying to set up an older printer (Epson Stylus Photo 890, I've should work with Linux) on my Ubuntu Gutsy Gibbon server but without success. 
And here is my first problem:
[LIST="1"]How do I add a printer with cups or any other printing software? I've tried with both webmins printing administrator and printconf (it says: *''Unable to read printer database.  Please ensure the "foomatic-db" package is installed properly.''*).
It would be great if someone could tell me how to get printconf working, or guide me through the whole process. I've never done this before and haven't found anything that worked. If you know a guide/howto that works, please post the link![/LIST]

And the second problem will probably be quite easy when the printer is working. But I need to share the printer to Linux, Mac and Windows computer (samba'll do the work, right?).
And over to the question number two:
[LIST="2"]*How do I configure samba (got a working samba share) to share the printer? Will it do it without me interfering with the configuration? Would be wonderful if someone could post and tell me how to do this, if anything is needed and a guide/howto works as well.*[/LIST]

Thank you very much!

- Simon

---

### Post by murmel on 2008-01-05
Bump.. =)

---

### Post by Predator[23rd] on 2008-01-05
Which driver are you using.

My Google search came up with this:
[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_890](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_890)

First, try to make the printer work directly. Second step will be sharing ...

Check this for sharing:
[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/StandAloneServer.html#SimplePrintServer](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/StandAloneServer.html#SimplePrintServer)

---

### Post by murmel on 2008-01-06
> **'Predator[23rd] said:**
> Which driver are you using.

My Google search came up with this:
[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_890](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_890)

First, try to make the printer work directly. Second step will be sharing ...

Check this for sharing:
[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/StandAloneServer.html#SimplePrintServer](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/StandAloneServer.html#SimplePrintServer)
Thank you so much! Works perfectly!

- Simon

---

