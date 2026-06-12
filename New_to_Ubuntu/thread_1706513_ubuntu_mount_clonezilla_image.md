---
title: "ubuntu mount clonezilla image"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-03-14
clonzill web page says

    * Method 1: Use Clonezilla live to restore the image to a virtual machine (e.g. VMWare workstation or Virtual Box). Then mount the restored partition to read the contents.
    * Method 2:
         1. Prepare a large disk in Linux
         2. Say if your image is /home/partimag/YOURIMAGE/, if the image is like /home/partimag/YOURIMAGE/*-ptcl-img.* (e.g. /home/partimag/YOURIMAGE/sda1.ext4-ptcl-img.gz.aa), follow this to restore the image.
            If the the image is like /home/partimag/YOURIMAGE/sda1.ntfs-img.aa, sda1.ntfs-img.ab..., run
            "file /home/partimag/YOURIMAGE/sda1.ntfs-img.aa"
            to see it's gzip, bzip or lzop image. Say it's gzip, then you can run
            cat /home/partimag/YOURIMAGE/sda1.ntfs-img.* | gzip -d -c | ntfsclone --restore-image -o sda1.img -
            Then you will have a "sda1.img" which you can mount it by
            mount -o loop -t ntfs sda1.img /mnt
            Then all the files are in /mnt/
            You can do the similar thing for the ext3, ext4 or reiserfs file system.
    * Method 3: Use the tool partclone-utils to mount the image directly. (//NOTE// This program is not maintained by Clonezilla team. However, it will be included in the future release of partclone when the new release, e.g. 0.2 is released.). 

how do I do # 2 with the below files?

disk               sda1.ntfs-ptcl-img.gz.aa  sda-chs.sf
Info-dmi.txt       sda1.ntfs-ptcl-img.gz.ab  sda-hidden-data-after-mbr
Info-lshw.txt      sda1.ntfs-ptcl-img.gz.ac  sda-mbr
Info-lspci.txt     sda1.ntfs-ptcl-img.gz.ad  sda-pt.parted
Info-packages.txt  sda1.ntfs-ptcl-img.gz.ae  sda-pt.sf
parts              sda1.ntfs-ptcl-img.gz.af

---

### Post by lance bermudez on 2011-03-14
install partclone 
[http://sourceforge.net/projects/partclone/files/](http://sourceforge.net/projects/partclone/files/)

touch hda2.img

must be root sudo -s

sudo cat /media/M*assport/mount_image/2011-03-13-21-img/sda1.ntfs-ptcl-img.gz.* | sudo gzip -d -c | sudo partclone.restore -C -s - -O /media/M*assport/mount_image/sda1.img

sudo ntfs-3g -o loop sda1.img /mnt

or

sudo mount -t ntfs-3g -o loop sda1.img /mnt

---

