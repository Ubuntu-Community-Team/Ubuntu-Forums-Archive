---
title: "Print Server Configuration"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by Edward in CT on 2010-11-07
I have a Linksys WPSMS54G Print Server.  Does anyone know how to configure it in Ubuntu.  I am a total beginner and need step by step instruction.

Thanks

---

### Post by Karakh on 2010-11-07
This works with my shared printer:

[LIST=1]
[*]System > Administration > Printing
[*]Click "Add"
[*]Select 'Network Printer"
[*]Find Network Printer
[*]If you know the IP address of the server, then add it. If not, just click find.
[/LIST]


If that didn't work:

[LIST=1]
[*]System > Administration > Printing
[*]Click "Add"
[*]Select 'Windows Printer via SAMBA'
[*]Browse
[*]And add your printer
[/LIST]

---

