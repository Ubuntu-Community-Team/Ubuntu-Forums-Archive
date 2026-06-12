---
title: "Network-manager configuration"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by druhboruch on 2006-11-11
My network-manager stopped remembering my SSID.
It is trying to connect to wrong network by default.

Where is the configuration stored?

Every time I am logging in I have to type my SSID, then key, and then keyring password.  It is driving me nuts.

---

### Post by richjoyce on 2006-11-11
Try opening gconf-editor and looking at the information stored there.

---

### Post by druhboruch on 2006-11-11
I have already checked gconf, /etc, /var/lib, all the usuall suspects.
Cannot find anything...

---

### Post by druhboruch on 2006-11-11
I found it.  It was under the .gconf in my home directory.

---

### Post by frisket on 2008-02-01
I clicked on Manual Configuration on my NM icon to test my wireless network
and now I can't find out how to go back to auto-detect. The Wireless Networks 
entry in the NM icon is greyed out! How do I tell it to get out of Manual Config?
It persists in manual mode even over a reboot. Where is this setting stored?
(And no, it's not in gconf-editor -- there is no mention of network-manager
anywhere in gconf-editor)
[Gutsy]

---

### Post by frisket on 2008-02-01
> **frisket said:**
> How do I tell it to get out of Manual Config?

Panic over...found it. It's *in* the manual config, a little box to click to set "roaming mode".
What an amazingly silly place to put it!

---

### Post by gsaggior on 2008-05-26
The exact directory is /.gconf/system/networking/wireless/networks$,starting from the user's home directory...

Any SSID used will have a directory. Remove those directory then you will be prompted to re-insert passwords, certificats etc etc...

---

