---
title: "cant mount ISO"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by mushroom08 on 2011-03-23
ok im trying to mount a ISO im useing the steps in 

[http://www.cyberciti.biz/tips/how-to-mount-iso-image-under-linux.html](http://www.cyberciti.biz/tips/how-to-mount-iso-image-under-linux.html)

but i cant get the second command to run plz help im running maverick meerkat

---

### Post by matt_symes on 2011-03-23
Hi

Do this and use sudo.

```
sudo mkdir -p /mnt/disk
sudo mount -o loop your_iso_name.iso /mnt/disk
cd /mnt/disk
ls -l
```

You will have to enter your password after the first command. It will not be echoed to the screen.

Post back any errors

Kind regards

---

### Post by mushroom08 on 2011-03-23
ok did first entered my pass and


mushroomstamp@MushroomEmpire:~$ sudo mount -o loop your_iso_name.iso /mnt/disk
your_iso_name.iso: No such file or directory

---

### Post by Dutch70 on 2011-03-23
> **mushroom08 said:**
> ok did first entered my pass and


mushroomstamp@MushroomEmpire:~$ sudo mount -o loop your_iso_name.iso /mnt/disk
your_iso_name.iso: No such file or directory

Replace...
```
your_iso_name
```

with the actual name of your iso. :D

_

---

### Post by BobSands on 2011-03-23
I'm not really sure if you need to do it by commands, but you can install gmount-iso: 
```
sudo apt-get install gmountiso
```

Very easy to use, you can check a nice how to here: [http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html](http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html)

But if you really want to do it by commands, what you are doing looks ok, but be sure you are writing the full path of where the .iso file is:

```
sudo mount -o loop /wherever/iso/image/is/your_iso_name.iso /mnt/disk
```

Hope this help.

---

### Post by mushroom08 on 2011-03-23
ok lol im still new at linux ill write in the name of the ISO i guess thats a problem most of the instructions out there assume you already know quite a bit

---

### Post by Dutch70 on 2011-03-23
> **mushroom08 said:**
> ok lol im still new at linux ill write in the name of the ISO i guess thats a problem most of the instructions out there assume you already know quite a bit

Most, if not all of us have been there, and have gotten really good at using google since.

---

### Post by oklokl on 2011-03-23
Furius ISO Mount 
furiusisomount

synaptic
install..
or 
sudo apt-get install furiusisomount

setting Loop mount..

your /home/user name/iso Directory folder Is generated
[http://cafe.daum.net/candan/HgwY/11](http://cafe.daum.net/candan/HgwY/11)
image..
:D

---

### Post by mushroom08 on 2011-03-24
thx you have all been awsome :popcorn:

---

