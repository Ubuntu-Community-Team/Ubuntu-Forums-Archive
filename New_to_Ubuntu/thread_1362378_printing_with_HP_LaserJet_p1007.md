---
title: "printing with HP LaserJet p1007"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by kunchimon on 2009-12-23
How to configure a USB printer (HP LaserJet p1007) on Ubuntu 9.04 and share with another RHEL 4 & windows machines. Can I use hp printer CD as driver.

---

### Post by cariboo on 2009-12-24
The printer should be detected by default when you plug it in. If not get the latest drivers [here]("http://hplipopensource.com/hplip-web/downloads.html"), follow the Debian instructions.

To share your printer with other systems, go to:

```
http://localhost:631
```

and on the Administration page make sure that the **Share printers connected to this system** radio button is selected.

---

