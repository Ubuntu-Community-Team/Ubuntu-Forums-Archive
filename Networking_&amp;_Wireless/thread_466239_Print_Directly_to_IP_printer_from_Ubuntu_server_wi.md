---
title: "Print Directly to IP printer from Ubuntu server with no GUI"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by bensode on 2007-06-06
I'm setting up a Hylafax server that will receive faxes on an existing Ubuntu Dapper server install that does not have a desktop or gui installed.  I'm trying to set up basic console printing for text files and a default printer for Hylafax to dump incoming faxes.  The target printer is an IP based HP Jetdirect printer.  Any ideas where I can start?  Thanks!

Bensode

---

### Post by mitch.c on 2007-06-07
Printing from the command-line is done using either 'lp' or 'lpr'. For example:
```
$ lp myfile.txt   # prints 'myfile.txt' to default printer
$ lp -d my_printer myfile.txt   # prints 'myfile.txt' to default printer

$ lpr myfile.txt   # prints 'myfile.txt' to default printer
$ lpr -P my_printer myfile.txt   # prints 'myfile.txt' to default printer

$ sudo lpadmin -d my_printer  # sets 'my_printer' as default system printer
```
If you are asking how to set up the printer, start here: [https://help.ubuntu.com/7.04/printing/C/printing.html](https://help.ubuntu.com/7.04/printing/C/printing.html)

Come back with some specific printer information if you need further assistance.

[[COLOR="Red"]UAResolved[/COLOR]]("http://ubuntuforums.org/showthread.php?t=377083")

---

