---
title: "Partitions?"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by dayo-centos on 2011-03-18
Hi i have a linux application running in Virtual Machine on my windows OS Laptop. I want to partition a secondary storage  device for the application software with my 250G External hard drive. Already i have mounted the device from fstab on /etc. Now how will i instruct the application to output data to this device.

---

### Post by aeiah on 2011-03-18
it depends what the application is i suppose, but normally you'd find where it saves its data to, and mount --bind an area on the external drive to the data directory.

eg:
you have a 2nd hard drive mounted as /media/second/

you use apache, which by default serves pages that are located in /var/www/. without changing any config in apache, you could easily make /var/www point to another place.
```

sudo mount --bind /media/second/www /var/www
```

now /var/www/ exists on your 2nd drive. 

you wouldnt need to do this with apache because there are config settings that allow you to specify any location for the web data, but this solution will work for any application.

to permanently mount --bind you'll have to add it to your /etc/fstab file. you should be able to find google info on this.


you should probably make sure the external drive uses a filesystem that preserves permissions properly. you might have problems with FAT, but you may be able to get away with NTFS if its necessary.

---

