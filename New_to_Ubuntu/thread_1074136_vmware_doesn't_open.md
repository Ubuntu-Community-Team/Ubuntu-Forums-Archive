---
title: "vmware doesn't open"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by cartisdm on 2009-02-18
I just installed VMware-server using [this guide]("http://ubuntuforums.org/showthread.php?t=779934").  The only difference was I used the latest version:

```
Latest Version: 1.0.8 | 2008/11/06 | Build 126538
```

Everything seems to install ok using the defaults.  The only hiccup I had was it said it didn't have my kernel compiler version (or something close to that, I did my best to interpret it).  It said I could force the compiler but it may crash.  I ran it anyway and everything worked just fine.

I got a successful install printout and then when I tried to actually open vmware    Applications --> System Tools -->  VMware Server Console   nothing happens.  My cursor spins like it's working, then it loses interest after like 10 seconds.

Sorry I can't provide more information but if you tell me what to get you I'll certainly look!

---

### Post by Shazaam on 2009-02-18
One way to find out any errors is to run it in terminal using whatever launch code VMware Server Console needs. You can find this by opening Main Menu (System>Preferences>Main Menu) and finding the VMware listing. Right click it, go to Properties>command. Enter that command in terminal.

---

### Post by cartisdm on 2009-02-19
```
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

```


I tried installing two different versions, but I didn't get very far with the first one,  I'm guessing this must be causing part of the problem.  Why can't it find the right file?


EDIT:  I also did a search in synaptic for 'vmware' and these are the only results (see pic)

---

