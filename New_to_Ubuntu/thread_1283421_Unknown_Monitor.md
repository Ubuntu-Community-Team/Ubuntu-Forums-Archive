---
title: "Unknown: Monitor"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by captgadget on 2009-10-05
This a 19" Westinghouse LCD monitor. Everything worked fine until yesterday when using the repositories I downloaded and installed a package, found out I didn't want it so I removed it. It was Mendely(sp) something about PDFs. In synaptic on the left side with status highlighted there was something in the installed that I didn't need anymore so as it suggested I uninstalled. Now, my resolution is all messed up and the display settings tell me it is an unknown monitor.

It's an onboard intel graphics card 82865G and it is recognized.

I won't be back for four hours, but any suggestions will be appreciated.

---

### Post by jward3010 on 2009-10-05
This should do it:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by captgadget on 2009-10-05
I get this message: xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20091005172213

Can someone tell me how to install the backup?

---

### Post by jward3010 on 2009-10-05
Don't worry about the backup, the backup is there in case this particular command goes wrong. Putting the backup back in place is easy if you really need to. After running the command do a restart, I should have mentioned that in my original post.

---

