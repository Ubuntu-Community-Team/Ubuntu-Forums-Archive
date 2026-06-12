---
title: "Ubuntu update failed - what do I do now?"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by wscrivens on 2009-12-06
I have Ubuntu 9.10 installed on a Eee 1005HA.

Update Manager told me it had critical updates to install, so I told it to go ahead.  At the tend it told me that 4 files had failed to download:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_2.6.31.15.28_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_2.6.31.15.28_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.31.15.28_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.31.15.28_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.31.15.28_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.31.15.28_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.31-15.50_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.31-15.50_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]

----------------
I went to the download directory ([http://us.archive.ubuntu.com/ubuntu/pool/main/l/](http://us.archive.ubuntu.com/ubuntu/pool/main/l/)) wiht Firefox, and the files do not exist there.
With great trepidation, I followed the instructions to re-boot, and the computer did come back up.

My question is, how serious a problem is this, and what do I do next?

TIA

Walt

---

### Post by whoop on 2009-12-06
Wait a while, or select another server via software sources...

---

### Post by aktiwers on 2009-12-06
Yeah the server seams to be down..  look at the other posts here.
I suggest changing servers or wait til they get up again :)
> 
aktiwers@HAL2:~$ ping 91.189.88.31 80
PING 80 (0.0.0.80) 56(124) bytes of data.
^C
--- 80 ping statistics ---
17 packets transmitted, 0 received, 100% packet loss, time 15999ms

aktiwers@HAL2:~$ 

---

