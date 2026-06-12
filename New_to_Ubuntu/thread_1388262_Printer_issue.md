---
title: "Printer issue"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by sincerelyydavid on 2010-01-22
I went to system>administration>printing and tried to install the printer, but it just doesn't work. my printer is a dell photo printer 720 btw.

---

### Post by cjazz on 2010-01-23
FYI, when it comes to Linux and printing, the Linux Foundation's OpenPrinting Web site is a valuable resource. In my opinion, every Linux user should have it bookmarked. [This page]("http://www.openprinting.org/show_printer.cgi?recnum=Dell-Photo_Printer_720") says your model is a rebranded Lexmark z615 and should "mostly" work with the driver for the Lexmark z600.

---

### Post by blazemore on 2010-01-23
Here's a script which will get you up and running.
Download it to your home directory and run it with
```
clear; sudo sh lexmark.sh
```

---

### Post by sincerelyydavid on 2010-01-23
i tried that, but it says sh: can't open lexmark.sh

---

### Post by blazemore on 2010-01-23
> **sincerelyydavid said:**
> i tried that, but it says sh: can't open lexmark.sh

You need to be in the folder you downloaded it do
```
cd ~/Downloads
sudo sh lexmark.sh

```

---

### Post by sincerelyydavid on 2010-01-23
ohh, not it makes sense. it works now thanks =), btw what does sh stand for?

---

### Post by blazemore on 2010-01-23
> **sincerelyydavid said:**
> ohh, not it makes sense. it works now thanks =), btw what does sh stand for?

sh is your shell. You can also use bash.

---

### Post by sincerelyydavid on 2010-01-23
so
sudo bash lexmark.sh works too?

---

### Post by blazemore on 2010-01-23
yes
and
```
chmod +x lexmark.sh
sudo ./lexmark.sh
```
which is what people tend to do, although I don't know why.

---

