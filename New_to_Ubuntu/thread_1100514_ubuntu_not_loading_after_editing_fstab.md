---
title: "ubuntu not loading after editing fstab"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by OliH on 2009-03-19
Hi,

My goal was to create a new partition for the /usr directory but I fear that i have made a mistake due to my carelessness as ubuntu will now not boot!

This is what I did:
1. I loaded the gparted live cd, resized an existing parition (sda3) to make some space for a new parition, and then created that partition (sda4).
2. I booted into ubuntu and the new partition was recognised. I then edited my fstab file (see below) to add a new line for sda4 to mount it to the /usr folder.
3. This is the part i think i did wrong. After editing the stab file I then typed in the terminal "sudo mount -a". this is when everything started to go wrong - no applications would open, ubuntu didn't shut down correctly and now wont restart (it shows the splash screen but stops when it gets to lines saying "/etc/acpi/start.d/ command not found" or something like that).

Any help would be appreciated. I know I have done this wrong, but could you help me get it back? Many thanks. my fstab file is:

> proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=c6f49724-ec29-401d-9e1f-2e9358f8a3cc / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda3 :
UUID=39e9ccdb-410a-421b-9b23-95d666ee8e1a /home ext3 relatime 0 2
# Entry for /dev/sda2 :
UUID=4f3ac544-ec2c-417d-9955-b9532c39efee none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
# Entry for /dev/sda4 :
/dev/sda4 /usr ext3 defaults 0 2
# Entry for /dev/sdb1 :
/dev/sdb1 /media/vista64 ntfs-3g defaults,locale=en_US.utf8 0 0

The line I added is:

> # Entry for /dev/sda4 :
/dev/sda4 /usr ext3 defaults 0 2

Many thanks for your help!

Oli

---

### Post by drs305 on 2009-03-19
If you can't boot to the recovery mode, an option is to boot to the livecd desktop and edit the fstab file from there. You will have to mount the sda1 partition first.
```

sudo mkdir /mytemp
sudo mount /dev/sda1 /mytemp
cd /mytemp/etc
gksudo gedit fstab

```

Now, as to what to change. Since it booted correctly after you made the new partition, your UUIDs and the sda1 entries should be correct.

I don't your reasons for choosing "/usr" for a mount point for sda4, but /usr is a system folder. It doesn't stand for "user" but I believe for "unix system resources".

Change the sda4 mount point to something else (for example, /mydata). You will also have to create that new mount point and will probably want to be the owner:
```

sudo mkdir /mnt/mydata
sudo chown -R yourusername: /mnt/mydata

```
Reboot and see if your system now mounts.

Alternatively, you can just comment out the sda4 /usr line in fstab and deal with it after you get back into your normal boot.

---

### Post by OliH on 2009-03-19
OK...I commented out the extra line in the fstab file and now it's all working - many thanks.

Oli

---

