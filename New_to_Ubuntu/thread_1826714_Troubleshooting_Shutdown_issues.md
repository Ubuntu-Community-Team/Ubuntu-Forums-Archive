---
title: "Troubleshooting Shutdown issues"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by gcave on 2011-08-16
I am running 11.04 32-bit Lubuntu on my netbook.  What a fantastic OS it is.  I am really pleased.

My issue is that when I shut the machine down it stops at the logout screen.  There is a message that says "all processes end in 2 seconds" or something similar.

I check /var/log/syslog and /var/log/dmesg but do not see a "smoking gun".  What is the best way to troubleshoot this?

---

### Post by amjjawad on 2011-08-28
> **gcave said:**
> I am running 11.04 32-bit Lubuntu on my netbook.  What a fantastic OS it is.  I am really pleased.

My issue is that when I shut the machine down it stops at the logout screen.  There is a message that says "all processes end in 2 seconds" or something similar.

I check /var/log/syslog and /var/log/dmesg but do not see a "smoking gun".  What is the best way to troubleshoot this?

Hi,

Try this:

Accessories > LXTerminal

```
 sudo shutdown -P now
```

---

### Post by laidback on 2011-08-28
Problems I've had with shutdown from version 10.x onwards have been associated with Quickstarter in Open Office (Libre Office now I think).

Open the Wordprocessor (or any other application from the suite). Choose Tools>Options>Memory and then make sure that "Enable systray Quickstarter" box is unchecked.

I believe that in version 11.x Quickstarter is enabled by default.

---

### Post by amjjawad on 2011-08-28
> **laidback said:**
> Problems I've had with shutdown from version 10.x onwards have been associated with Quickstarter in Open Office (Libre Office now I think).

Open the Wordprocessor (or any other application from the suite). Choose Tools>Options>Memory and then make sure that "Enable systray Quickstarter" box is unchecked.

I believe that in version 11.x Quickstarter is enabled by default.

> **gcave said:**
> I am running 11.04 32-bit Lubuntu on my netbook.  

Lubuntu does NOT have Open Office nor Libre Office. Lubuntu comes with AbiWord, Gnumeric and Osmo for Office Apps ;)

---

### Post by Kevin McCready on 2012-03-26
which is why in Lubuntu I wiped out abiword and installed libreoffice-writer and have never looked back. if only I could easily do the same for PCManFM.

---

### Post by Elfy on 2012-03-26
Old thread closed.

---

