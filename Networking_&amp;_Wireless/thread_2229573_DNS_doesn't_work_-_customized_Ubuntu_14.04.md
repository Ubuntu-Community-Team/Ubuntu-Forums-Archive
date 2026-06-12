---
title: "DNS doesn't work - customized Ubuntu 14.04"
date: 2014-06-13
forum: Networking &amp; Wireless
---

### Post by plinc on 2014-06-13
I've made a Ubuntu 14.04 VM, customized it a bit (apps, etc),  and created an .iso via REMASTERSYS. I then made a bootable USB w/  unetbootin. 


  The DNS works on the VM and on multiple laptops in the house but the  bootable USB fails to resolve URLs. The bootable USB does successfully  connect to the internet and can ping IPs. 


  I've searched and tried editing the  /etc/resolvconf/resolv.conf.d/head  and base files, I've tried adding  google DNS (8.8.8.8) in the network manager, nothing works. (It's worth  noting I make these changes on the VM, reboot, then create the .iso  again and make it bootable). 
  
Any help would be greatly appreciated. Thanks!

---

### Post by SeijiSensei on 2014-06-14
Usually just adding
```
nameserver 8.8.8.8
```
to /etc/resolvconf/resolv.conf.d/head has worked for me.  Is that what you used as well?

---

### Post by plinc on 2014-06-14
I did this, but when I created the .iso and then made it bootable DNS did not work =/
Any other thoughts?

---

### Post by SeijiSensei on 2014-06-15
If you [mount the ISO]("http://www.cyberciti.biz/tips/how-to-mount-iso-image-under-linux.html") and examine the contents of /etc/resolvconf, are your changes preserved?

```

sudo mkdir /mnt/iso
sudo mount -o loop /path/to/image.iso /mnt/iso
sudo ls -lR /mnt/iso/path/to/etc/resolvconf

```

---

