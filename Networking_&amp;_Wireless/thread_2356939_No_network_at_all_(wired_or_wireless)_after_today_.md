---
title: "No network at all (wired or wireless) after today s 16.10 update"
date: 2017-03-28
forum: Networking &amp; Wireless
---

### Post by tercoide on 2017-03-28
Hi
Acer Aspire V laptop with an updated 16.10 so far. But after todays update, both ethernet and wireless apear UNCLAIMED in 

sudo lshw

help!
tnx

---

### Post by tercoide on 2017-03-28
this solved the problem, for now....

[http://askubuntu.com/questions/343066/how-to-delete-a-non-working-kernel-after-update](http://askubuntu.com/questions/343066/how-to-delete-a-non-working-kernel-after-update)

---

### Post by jeremy31 on 2017-03-28
What kernel caused the issue?  It seems that some updates are installing a new linux-image without linux-image-extra and the extra is where a lot of the modules for ethernet and wireless are

---

### Post by tercoide on 2017-03-28
I purged the 4.8.0-44-generic

the update was done by the system, not manual

---

### Post by STPitcher on 2017-03-29
I had the same problem on a System76.  Running 16.10.  Kernel 4.8.0-44.  No network.

Also, on my system, the laptop did not recover from Suspend.  I think it was ok except that the display didn't turn on, so I saw nothing.

Same fix worked.  Remove 4.8.0-44.

Something drastically wrong.

- stp

---

### Post by pizzafarmer_jk on 2017-03-29
I had the same problem with no networking and it also seems to have lost the video drivers. The basic driver it decided to use didn't recognize my second monitor and retained none of my settings. Booted to 4.8.0-42 and it all worked. I guess I'll be removing 4.8.0-44 also.

---

### Post by jeremy31 on 2017-03-29
You might not have to remove the kernel just try reinstalling the linux-image-extra package while booted into a good kernel ```
sudo apt-get install --reinstall linux-image-extra-4.8.0-44-generic
```

---

### Post by pizzafarmer_jk on 2017-03-29
Thanks, jeremy31, that worked. All is back to normal.

---

### Post by STPitcher on 2017-03-30
Just upgraded to VMLINUZ-4.8.0-45.

Seems to work.

Thanks all.

- stp

---

### Post by tercoide on 2017-03-30
> **jeremy31 said:**
> You might not have to remove the kernel just try reinstalling the linux-image-extra package while booted into a good kernel ```
sudo apt-get install --reinstall linux-image-extra-4.8.0-44-generic
```

don't forget that some of us are not that smart

---

