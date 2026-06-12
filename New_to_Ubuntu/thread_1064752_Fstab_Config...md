---
title: "Fstab Config.."
date: 2009-02-09
forum: New to Ubuntu
---

### Post by tito_pt on 2009-02-09
I recently moved from Fedora to Ubunto, in my Fstab file I had severel mounted shares, and the same config in Ubunto dosen't give me full control of files on those shares..

I've cheged the permisions of /media/Disco? to 777 so when not mounted the Permisions are "drwxrwxrwx", after mounted de permisions are the same for all files ans subdirectories on the next level, at second Level are drwxrwxr-- and files are -rwxrw-r--.  


What might be the problem?

//192.168.6.6/F /media/DiscoI cifs auto,user,username=Agostinho,password=,uid=1000,gid=100,umask=000 0 0
//192.168.6.5/F /media/DiscoH cifs auto,user,username=Agostinho,password=,uid=1000,gid=100,umask=000 0 0
//192.168.6.4/G /media/DiscoG cifs auto,user,username=Agostinho,password=,uid=1000,gid=100,umask=000 0 0
//192.168.6.3/F /media/DiscoF cifs auto,user,username=Agostinho,password=,uid=1000,gid=100 0 0
//192.168.6.4/Qmultimedia /media/Musicas cifs auto,user,username=Agostinho,password=,uid=1000,gid=100,umask=000 0 0

---

### Post by cmnorton on 2009-02-14
I am confused. How is Ubuntu not giving you control in your fstab? Other than the install putting the entries in a little differently than the RPM-based systems I maintain, I have found no differences in Ubuntu.

This sounds more like a problem with owner and group permissions, so you would need to post a little more about directories on the mounted drive.

---

