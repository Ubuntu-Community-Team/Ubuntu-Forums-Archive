---
title: "Installing the driver for Dell Photo Printer 720"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by kogger on 2009-02-11
I'm having issues getting the driver for my printer to install. I downlaoded the Lexmark Z615 driver from Lexmark's website, and I extracted the tar file, but according to [these directions](http://www.answerbag.com/articles/How-to-Install-a-Dell-Photo-720-Printer-on-Linux/7895bcc4-0960-ed0b-9f8d-49ead4afaad6) I have to extract it again. I tried that, but I get this:

```
damien@Zeus:~/Desktop$ tar -xzf z600cups-1.0-1.gz.sh

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

```

Basically my questoin is, how do I use TAR to extract a gz.sh file?

---

### Post by halitech on 2009-02-11
according to openprinting.org, they say use the Lexmark z600 driver (Dell doesn't actually make printers, they rebrand from other companies)

[http://openprinting.org/show_printer.cgi?recnum=Dell-Photo_Printer_720](http://openprinting.org/show_printer.cgi?recnum=Dell-Photo_Printer_720)

---

### Post by kogger on 2009-03-02
Any idea where I can get a Linux version for that driver? The only one I found is an .exe file.

---

### Post by achase79 on 2009-03-02
can you post an ls of that directory.  The file I downloaded from Lexmark was in all caps and linux is case sensitive. You may have not had the name typed correctly to execute the tar program.

---

### Post by kogger on 2009-03-02
No, I had the name typed correctly...although I think I used the wrong command. I went back and tried another command, but I ran into another error:

```
[~/Desktop/CJLZ600LE-CUPS-1.0-1] > sh z600cups-1.0-1.gz.sh
Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory
Error in check sums 2331425966 225780837
```

---

