---
title: "Can you tell me what password I have to use here?"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by TRiCiDE on 2009-01-28
[IMG]file:///home/justin/Desktop/Screenshot-pips.png[/IMG]


I doubt my image worked, I am 4 hours new to Linux but here's a description:

I have a .tgz file.
I extract it and get the install file.
I click the install file
I get Please install/unistall as root user
Password:

I tried my Administrator password and that didn't work.  :popcorn:

Thank you for your time!

---

### Post by billgoldberg on 2009-01-28
Use 

```
sudo /path/to/installfile
```

and then enter your password you use to log in.

What are you trying to install?

---

### Post by TRiCiDE on 2009-01-28
I am trying to install drivers for my Epson printer.

That command needs to be used in the command line?

---

### Post by mikewhatever on 2009-01-28
Can you link to the tar.gz file you downloaded.

---

### Post by TRiCiDE on 2009-01-28
> **mikewhatever said:**
> Can you link to the tar.gz file you downloaded.

pips-snx100-ubuntu8.04-3.3.0-CG.tgz then extracted it to
pips-snx100-ubuntu8.04-3.3.0-CG.install  - which I click on and it asks for that password.

---

### Post by billgoldberg on 2009-01-28
> **TRiCiDE said:**
> I am trying to install drivers for my Epson printer.

That command needs to be used in the command line?

Yes.

Assuming the file is on your desktop, the command would be

```
sudo /home/yourusername/Desktop/pips-snx100-ubuntu8.04-3.3.0-CG.install
```

---

### Post by TRiCiDE on 2009-01-28
> **billgoldberg said:**
> Yes.

Assuming the file is on your desktop, the command would be

```
sudo /home/yourusername/Desktop/pips-snx100-ubuntu8.04-3.3.0-CG.install
```


Thank you, that command worked.  Would there have been a point and click way to do it?

---

### Post by thegreenblob on 2009-01-28
> **TRiCiDE said:**
> Thank you, that command worked.  Would there have been a point and click way to do it?

I haven't tried this but I believe you could have right clicked on it and went to properties, then went to the "Permissions" tab and check the "Allow executing file as program", then double clicking on it and clicking execute.

That might have also worked. :)

---

### Post by TRiCiDE on 2009-01-28
> **thegreenblob said:**
> I haven't tried this but I believe you could have right clicked on it and went to properties, then went to the "Permissions" tab and check the "Allow executing file as program", then double clicking on it and clicking execute.

That might have also worked. :)

Thats how this all started. :D  So no, it didn't work for me atleast.

Doesn't matter, the driver didn't work. :(

---

### Post by thegreenblob on 2009-01-28
> **TRiCiDE said:**
> Thats how this all started. :D  So no, it didn't work for me atleast.

Doesn't matter, the driver didn't work. :(

Hmm... too bad it didn't work. Though, have you tried just configuring the printer? :P

Ubuntu comes with support for a lot of printers and they just need to be configured from System-->Administration-->Printing.

Hope this works for you. :)

---

### Post by TRiCiDE on 2009-02-06
Ya, I configured the printer.  Still nothing. :(


> **thegreenblob said:**
> Hmm... too bad it didn't work. Though, have you tried just configuring the printer? :P

Ubuntu comes with support for a lot of printers and they just need to be configured from System-->Administration-->Printing.

Hope this works for you. :)

---

