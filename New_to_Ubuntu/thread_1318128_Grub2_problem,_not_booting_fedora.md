---
title: "Grub2 problem, not booting fedora"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by skaldyr on 2009-11-07
Grub2 errror?

i have a triple boot with fedora ubuntu and xp. 

the problem is that i cant boot fedora.

i tried to make a 40_custom entry in grub.d like this 

```
echo "Adding fedora (on dev/sda5)" >&2 
cat << EOF
menuentry "fedora" {
        set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 so quiet splash
        initrd /initrd.img
}
EOF
```
my fedora boot is on sda5.

when i try to boot fedora i get 

error not an assignment.

what am i doing wrong?

---

### Post by oldfred on 2009-11-07
Why is osprober not finding it? And is the location correct? It is often /boot/....

There was a bug as it only found part of it before:
[https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/420900](https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/420900)

---

### Post by skaldyr on 2009-11-07
I dont know why os_prober is not finding fedora. 
I might revert back to 9.04 again. Cant seem to get this working.

---

### Post by josephdietrich on 2009-11-18
Since it's sda5, and grub is zero-indexed, shouldn't it be:
```
 
set root=(hd0,4)

```

---

### Post by drs305 on 2009-11-18
@ josephdietrich - The counting of partitions in G2 now starts at 1. Devices still starts at 0.

Here is one user's successfull G2 entry for Fedora. Adjust as necessary:
> 
[noparse]menuentry "Fedora" {
        set root=(hd0,8)
        linux /boot/vmlinuz-2.6.31.1-56.fc12.x86_64 root=/dev/sda8 ro quiet splash
        initrd /boot/initramfs-2.6.31.1-56.fc12.x86_64.img
}[/noparse]

I not your example has "so" instead of "ro" as well.

---

### Post by BOZG on 2009-11-18
> **drs305 said:**
> @ josephdietrich - The counting of partitions in G2 now starts at 1. Devices still starts at 0.

Here is one user's successfull G2 entry for Fedora. Adjust as necessary:


I not your example has "so" instead of "ro" as well.

Should that not include } at the end?

---

### Post by drs305 on 2009-11-18
> **BOZG said:**
> Should that not include } at the end?
Yes it should. I overwrote it when I edited it with a "noparse" tag. Thanks.

By the way, I haven't used the above entry. I just know it is a format that works on at least some setups.

---

### Post by josephdietrich on 2009-11-18
@drs305 - Thanks for catching that. I just came back here to correct myself after re-reading the Grub2 entry on the wiki! :oops:

---

### Post by BOZG on 2009-11-18
> **drs305 said:**
> Yes it should. I overwrote it when I edited it with a "noparse" tag. Thanks.

By the way, I haven't used the above entry. I just know it is a format that works on at least some setups.

Yeah, it worked for me.  At least it worked until I updated Fedora 12 a few minutes ago, rebooted and now I find that it tells me that it can no longer find a root device and so won't boot. :)

---

### Post by drs305 on 2009-11-18
> **BOZG said:**
> Yeah, it worked for me.  At least it worked until I updated Fedora 12 a few minutes ago, rebooted and now I find that it tells me that it can no longer find a root device and so won't boot. :)

If the entry is made in a custom menu file, the contents won't be updated and the user would have to edit the file and make the changes manually. 

I don't know how Fedora updates, but if it removed the kernels/images in /boot then you would have to manually add the new ones. If the old kernel/image was still there, the old menuentry should continue to work. 

If Fedora writes to the MBR or installs it's own bootloader then that is a separate issue.

---

### Post by BOZG on 2009-11-19
> **drs305 said:**
> If the entry is made in a custom menu file, the contents won't be updated and the user would have to edit the file and make the changes manually. 

I don't know how Fedora updates, but if it removed the kernels/images in /boot then you would have to manually add the new ones. If the old kernel/image was still there, the old menuentry should continue to work. 

If Fedora writes to the MBR or installs it's own bootloader then that is a separate issue.

That's what I assumed the problem was but there was no update of the kernel images.  I had a look into Fedora's grub.conf and changed grub.cfg to mirror what was contained in there and it managed to get rid of the "No root device found" error but now it's locking up during boot.

---

