---
title: "vpnc/universe bugreports"
date: 2005-10-14
forum: Networking &amp; Wireless
---

### Post by asv on 2005-10-14
The latest vpnc package for breezy is missing vpnc-connect. I know vpnc is the universe, so is there a bugzilla for universe packages?

---

### Post by asv on 2005-10-18
Anyone have an answer for this question?

---

### Post by naomi on 2005-10-23
Hi, I read in some other thread (can't find it at the moment), that you don't need vpnc-connect anymore. Just use the vpnc command with your conf file and it should work! :)

---

### Post by mr_crimp on 2005-10-23
This may be a silly question but how do you disconnect then? I've tried vpnc-disconnect but without any luck.

---

### Post by mr_crimp on 2005-10-26
I don't know why but now sudo vpnc-disconnect is working.

---

### Post by OldPaulie on 2005-12-31
I have noticed this too.  You could create an alias for compatibility purposes:

alias vpnc-connect='vpnc'

Also, I cannot include the IPsec secret in either /etc/vpnc/default.conf or vpnc.conf  If I try and include it, I get:
vpnc: hash comparison failed: AUTHENTICATION_FAILED

Maybe someone has managed to include the secret in the conf file but I cannot!

---

### Post by shukle on 2006-01-04
seems to work here.

---

### Post by wfjm on 2006-01-08
The main thing broken with vpnc is the documentation. It still refers to vpnc-connect, which is not in included anymore and not needed either. The man page is thus outdated, wrong and missleading.

To connect execute: vpnc
To disconnect execute: vpnc-disconnect

I use the same /etc/vpnc/default.conf as before under 5.04 and Debian, and it works.

```
IPSec gateway ....
IPSec ID ....
IPSec secret ....
Xauth username ....
debug 1

```

---

