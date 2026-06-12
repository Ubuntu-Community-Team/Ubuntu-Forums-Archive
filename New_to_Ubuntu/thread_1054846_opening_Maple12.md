---
title: "opening Maple12"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by M0GEJ on 2009-01-30
I have just installed Maple 12 on my laptop. I wrote the ISO files to disc and then went on to install it. Install seemed to go well and the log shows all files were successfully installed. Can't seem to open it though. I am not really sure how to add it onto the applications tab either. Any ideas?

---

### Post by Nepherte on 2009-01-30
You remember in what directory you installed maple? When you installed maple as root, the default installation directory is /root/maple but you might have changed the installation path. To run maple, execute
```
<installlation path>/bin/maple
```
for the command line version and
[code]<installlation path>/bin/xmaple[code[
for the graphical version.

To add maple in the application menu, right click on applications in the gnome panel and pick edit menu. From then on, it should be pretty obvious.

---

### Post by M0GEJ on 2009-01-30
I try that and get-

Maple initialization error, Local checkout filter rejected request
Feature:       Maple12
License path:  /home/chloe/maple12/license/license.dat
FLEXlm error:  -73,125
For further information, refer to the FLEXlm End User Manual,
available at "www.macrovision.com".
SN=......serial number is here..........

I am really not sure what I should be looking for on that site or what else I could be doing...

---

### Post by mikechant on 2009-01-30
[I]I try that and get-

Maple initialization error, Local checkout filter rejected request
etc.[/I]

A quick google led me to this:
[http://www.maplesoft.com/support/faqs/detail.aspx?sid=6465](http://www.maplesoft.com/support/faqs/detail.aspx?sid=6465)

Which basically says that there's a problem with your license file not being suitable for Linux, and that you need to get Maplesoft Tech support to generate you a new one.

---

### Post by Nepherte on 2009-01-30
You also have the solution now:
> [...] The solution is to contact Maplesoft Technical Support and have a license file generated without a DISK_SERIAL_NUM.

---

### Post by M0GEJ on 2009-02-01
well I have sent off a request, so hopefully should have it sorted shortly...cheers

---

