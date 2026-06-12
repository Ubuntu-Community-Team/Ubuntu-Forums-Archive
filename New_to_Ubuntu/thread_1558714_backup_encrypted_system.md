---
title: "backup encrypted system?"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by janmartin on 2010-08-22
Hi all,

I have an encrypted system on my Laptop.
Installed using the 9.10 Karmic Koala Alternate CD. One large partition only.

Now I want to backup everything to my USB drive before installing 10.4.

So I did: 
sudo dd if=/dev/mapper/ubuntu-root of=/media/truecrypt1/910-20100822.img

As you can see the USB drive is encrypted using truecrypt.

However when testing the backup:
sudo mount -o loop /media/truecrypt1/910-20100822.img /home/me/backup

I get an error:
mount: you must specify the filesystem type

This did work the last few times before I installed a new Ubuntu version.

Whats wrong?

Thanks,
Jan

---

### Post by earthpigg on 2010-08-22
did you back up the system while it was still encrypted? it would make sense that ubuntu can't figure out the filysystem of an encrypted mish-mash of random-looking ones and zeroes.

---

### Post by janmartin on 2010-08-22
Well,
my understanding is that **/dev/mapper/ubuntu-root** is unencrypted?

Jan


/dev/mapper/control
/dev/mapper/sda1_crypt
/dev/mapper/truecrypt1
/dev/mapper/ubuntu-root
/dev/mapper/ubuntu-swap_1

---

### Post by juancarlospaco on 2010-08-22
**[COLOR="Blue"]-t[/COLOR]** parameter?

---

### Post by psusi on 2010-08-22
Yes, it told you that you have to specify the filesystem type.. add -t ext3 if ext3 is your fs type.

Also dd is NOT a backup tool!  If you want to backup you should use a backup tool such as tar.

---

### Post by sandyd on 2010-08-22
> **janmartin said:**
> Hi all,

I have an encrypted system on my Laptop.
Installed using the 9.10 Karmic Koala Alternate CD. One large partition only.

Now I want to backup everything to my USB drive before installing 10.4.

So I did: 
sudo dd if=/dev/mapper/ubuntu-root of=/media/truecrypt1/910-20100822.img

As you can see the USB drive is encrypted using truecrypt.

However when testing the backup:
sudo mount -o loop /media/truecrypt1/910-20100822.img /home/me/backup

I get an error:
mount: you must specify the filesystem type

This did work the last few times before I installed a new Ubuntu version.

Whats wrong?

Thanks,
Jan
mount it using truecrypt. Then, in the folder that you mounted it to, tar everything
```

cd /path/to/folder
tar -cf backup.tar *
```

---

