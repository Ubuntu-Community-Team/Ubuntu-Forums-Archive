---
title: "Epson Stylus Printer SX515W Catastrophic error"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by Anthony Stutchbury on 2010-12-18
Can anyone help me solve this problem?

Have bought an Epson_Stylus SX515w. The idea is to replace my Epson Stylus DX3800.

On connection and sending a test page the following error message occurred:-

< Catastrophe! -KNotify

A print error occurred. Error message received from system:

cupsdoprint -P 'Epson_Stylus_SX510W' -J 'KDE Print Test' -H '/var/run/cups/cups.sock:631' -U 'root' -o ' multiple-document-handling=separate-documents-uncollated-copies orientation-requested=3' '/usr/share/apps/kdeprint/testprint.ps' : execution failed with message:
client-error-document-format-not-supported >

End of error.


No entry is made in the 'Jobs' queue as happens when I do the same to the DX3800.

Operating system - Kubuntu 8.04.1.

Please define terms you use in your reply!

With thanks,

Anthony Stutchbury

---

### Post by davidmohammed on 2010-12-18
hi there,
  how have you  installed the printer drivers?

[avasys]("http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/") have very good drivers for your printer - suggest use these if you havent already.

N.B. - you should really start thinking of upgrading your version of kubuntu to the current LTS 10.04 - printer support is much better with this version.

---

### Post by Anthony Stutchbury on 2010-12-18
how do you use avasys?

---

### Post by davidmohammed on 2010-12-18
just search for your model in that web-page - you need to install the 510 deb file suggested.  Full instructions in the manual link next to that section.

---

