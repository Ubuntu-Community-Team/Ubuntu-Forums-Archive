---
title: "dpkg/synaptic error"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by zosolm on 2010-07-12
I was installing some updates on synaptic package manager when my power went and my pc was shut down. When i tried to open synaptic again, i got this:
"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."


Synaptic doesn't open. 
If i type ```
sudo dpkg --configure -a

```

i get:

```
sudo dpkg --configure -a
[sudo] password for zosolm: 
dpkg: parse error, in file '/var/lib/dpkg/updates/0000' near line 14 package 'libudev0':
 EOF after field name `'
```


 I'm running lucid. Help?
(My understanding of Ubuntu is still fairly limited, so please do step by step/simple instructions)

---

### Post by fooman on 2010-07-12
try the fix in post #2 of this thread:

[http://www.uluga.ubuntuforums.org/showthread.php?p=9540324](http://www.uluga.ubuntuforums.org/showthread.php?p=9540324)

that should work for you.

---

### Post by zosolm on 2010-07-12
Worked perfectly. Thank you very much!

---

### Post by zosolm on 2010-07-18
A new problem has appeared:
I can now open synaptic package manager, but, once I select "mark all upgades" and "apply", it downloads the packages, then gets as far as "trying to run dpkg", then it says "recovering from package failure" and then sys "changes cannot be applied" with this error message:

"W: Failed to fetch [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/m/mesa/libgl1-mesa-dev_7.9.0+git20100714.d023fb39-0ubuntu0sarvatt~lucid_i386.deb](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/m/mesa/libgl1-mesa-dev_7.9.0+git20100714.d023fb39-0ubuntu0sarvatt~lucid_i386.deb)
  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/m/mesa/mesa-common-dev_7.9.0+git20100714.d023fb39-0ubuntu0sarvatt~lucid_i386.deb](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/m/mesa/mesa-common-dev_7.9.0+git20100714.d023fb39-0ubuntu0sarvatt~lucid_i386.deb)
  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/m/mesa/libgl1-mesa-dri_7.9.0+git20100714.d023fb39-0ubuntu0sarvatt~lucid_i386.deb](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/m/mesa/libgl1-mesa-dri_7.9.0+git20100714.d023fb39-0ubuntu0sarvatt~lucid_i386.deb)
  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/m/mesa/libgl1-mesa-glx_7.9.0+git20100714.d023fb39-0ubuntu0sarvatt~lucid_i386.deb](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/m/mesa/libgl1-mesa-glx_7.9.0+git20100714.d023fb39-0ubuntu0sarvatt~lucid_i386.deb)
  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/m/mesa/libglu1-mesa-dev_7.9.0+git20100714.d023fb39-0ubuntu0sarvatt~lucid_i386.deb](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/m/mesa/libglu1-mesa-dev_7.9.0+git20100714.d023fb39-0ubuntu0sarvatt~lucid_i386.deb)
  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/m/mesa/libglu1-mesa_7.9.0+git20100714.d023fb39-0ubuntu0sarvatt~lucid_i386.deb](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/m/mesa/libglu1-mesa_7.9.0+git20100714.d023fb39-0ubuntu0sarvatt~lucid_i386.deb)
  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.35-8.13_i386.deb](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.35-8.13_i386.deb)
  404  Not Found


"

How do i fix it?

---

### Post by da burger on 2010-07-18
Are you connected to the internet.

---

