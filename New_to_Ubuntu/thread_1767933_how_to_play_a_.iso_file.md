---
title: "how to play a .iso file"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by gudurukarthik on 2011-05-26
hi 
i have downloaded a concert and the downloaded file is in .iso file type. so how do i extract/ mount so that i can play the file in vlc or movie player

---

### Post by Grenage on 2011-05-26
Job done!

```
sudo mkdir /media/iso
sudo mount -t iso9660 yourfile.iso /media/iso -o loop
```

---

### Post by sanguinoso on 2011-05-26
An iso file is a copy of a CD or DVD. You can mount a CD or DVD iso with the mount command. ```
sudo mount /path/to/your/file.iso -o loop /mnt
```
This command would mount your iso on the /mnt folder of your system.

---

### Post by oldos2er on 2011-05-26
Right-click, open with vlc.

---

### Post by gudurukarthik on 2011-05-26
hey but it replays this way 
karthik@karthik-laptop:~$ sudo mkdir /media/iso
[sudo] password for karthik: 
mkdir: cannot create directory `/media/iso': File exists
karthik@karthik-laptop:~$ 

fyi: im trying to extract from my hard disk not a dvd

---

### Post by Pand5461 on 2011-05-26
Right-click -> "Open with archive mounter"?

---

### Post by tgm4883 on 2011-05-26
> **Pand5461 said:**
> Right-click -> "Open with archive mounter"?

+1. Why does everyone want to do it the hard way?

---

### Post by Grenage on 2011-05-26
> **gudurukarthik said:**
> hey but it replays this way 
karthik@karthik-laptop:~$ sudo mkdir /media/iso
[sudo] password for karthik: 
mkdir: cannot create directory `/media/iso': File exists
karthik@karthik-laptop:~$ 

fyi: im trying to extract from my hard disk not a dvd

Since the folder exists, you can skip that command.

> **tgm4883 said:**
> +1. Why does everyone want to do it the hard way?

Because that doesn't list it as a usable drive? Extracting an ISO is not mounting an ISO.

---

### Post by tgm4883 on 2011-05-26
> **Grenage said:**
> Because that doesn't list it as a usable drive? Extracting an ISO is not mounting an ISO.

Please don't guess, what I suggested does. Thanks for playing. [http://askubuntu.com/questions/43469/how-can-i-graphically-mount-isos](http://askubuntu.com/questions/43469/how-can-i-graphically-mount-isos)

---

### Post by Grenage on 2011-05-26
> **tgm4883 said:**
> Please don't guess, what I suggested does. Thanks for playing. [http://askubuntu.com/questions/43469/how-can-i-graphically-mount-isos](http://askubuntu.com/questions/43469/how-can-i-graphically-mount-isos)

Hah, you have my apologies; I read you post as 'archive manager'.  I didn't even realise that feature existed.

P.S: Thanks for playing? Are you ten?

---

### Post by oldos2er on 2011-05-26
> **Pand5461 said:**
> Right-click -> "Open with archive mounter"?

vlc, not Archive Mounter. Sorry I don't use Gnome, I forget the steps needed. If vlc is not listed in the open with menu, there should be an option for you to type in a program name.

---

### Post by tgm4883 on 2011-05-26
> **grenage said:**
> hah, you have my apologies; i read you post as 'archive manager'.  I didn't even realise that feature existed.

P.s: Thanks for playing? Are you ten?

tl;dr

---

### Post by sffvba[e0rt on 2011-05-26
> **tgm4883 said:**
> tl;dr

Hehe


404

---

### Post by Prince Valiant on 2011-05-26
open VLC.  
Go to Media --> Open file
Select the iso.

Now play the iso.  That's how I've done it many times in the past.  

Have fun!

-Val

---

### Post by nothingspecial on 2011-05-26
```
mplayer /path/to/iso.iso
```

```
vlc /path/to/iso.iso
```

Double clicking it works also.

Maybe there is something wrong with the concert you downloaded.

---

