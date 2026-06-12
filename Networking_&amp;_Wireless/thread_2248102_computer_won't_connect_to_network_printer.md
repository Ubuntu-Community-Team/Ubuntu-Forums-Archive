---
title: "computer won't connect to network printer"
date: 2014-10-12
forum: Networking &amp; Wireless
---

### Post by kccv42 on 2014-10-12
I have a wired printer connected to a windows computer which is connected to my network. How do i connect to the printer through my network and through the windows computer? I have tried to enter the ip adress in windows but it doesn't allow for the dashes "\" --that way only this way "/" in ubuntu.

---

### Post by kc1di on 2014-10-12
Then normal way to access a windows networked computer would be through Samba.  
Here's a[ page]("https://help.ubuntu.com/community/WindowsXPPrinter") that may be of help it's a bit old but the procedure should be the same.

---

### Post by SeijiSensei on 2014-10-13
I assume you told Windows to share the printer over the network, yes?

If so, open a browser and visit [http://localhost:631/](http://localhost:631/) which will bring up the web interface for the CUPS printing system used by Ubuntu and most other Unix-based systems.  Choose the "Adding Printers" link, then press the "Add Printers" button.  Enter your username and password when prompted, then follow the steps to define your printer.

---

### Post by kccv42 on 2014-10-13
I tried the link you provided for the printer:[COLOR=#000000] [/COLOR][http://localhost:631/](http://localhost:631/)[COLOR=#000000] . What username and password do i use?[/COLOR]

---

### Post by Vladlenin5000 on 2014-10-13
> **kccv42 said:**
> I tried the link you provided for the printer:[http://localhost:631/](http://localhost:631/)[COLOR=#000000] . What username and password do i use?[/COLOR]

Where is it asking for authentication exactly?
A properly (network) shared printer from a Windows machine shouldn't ask for it...

---

### Post by kccv42 on 2014-10-13
I tried the other method using samba. It worked.

---

### Post by Vladlenin5000 on 2014-10-13
Nice.

Please use the thread tools to mark this one as solved so others can benefit.

---

### Post by kc1di on 2014-10-13
Glad it worked for you , Enjoy :)

---

