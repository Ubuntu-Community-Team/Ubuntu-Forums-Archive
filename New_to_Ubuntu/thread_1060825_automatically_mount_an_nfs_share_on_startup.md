---
title: "automatically mount an nfs share on startup"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by leemajors on 2009-02-05
hi there,

i have a NAS sitting on my fridge using NFS.

every time i boot my machine up i have to run  sudo mount -t nfs 192.x.x.x:/mnt/nas /media/nas

or else i can't access the NAS from my machine.

how do i run this command automatically from booting up?

---

### Post by Voland on 2009-02-05
1 minute of googling:
[How to fstab ](http://ubuntuforums.org/showthread.php?t=283131)
[Ubuntu Wiki : fstab](https://help.ubuntu.com/community/Fstab)
[Mount Network File systems (NFS,Samba) in Ubuntu]("http://www.ubuntugeek.com/mount-network-file-systems-nfssamba-in-ubuntu.html")

---

### Post by leemajors on 2009-02-05
nice, thanks.

i did do some googling, and searching of the forum, but if you don't know to search for "fstab" then how do you find what you're looking for?

after looking through those links, i'm still none the wiser. it may be because i'm tired, i'll carry on reading over them tomorrow.

---

### Post by xopher_mc on 2009-02-05
you could also install autofs

sudo apt-get install autofs

Then it will automatically (when set up) mount nfs.

you need to edit the /etc/auto.master

sudo gedit /etc/auto.master

change the line

#/net	/etc/auto.net

to 

/net /etc/auto.net

Then make a directory called 

/net

sudo mkdir /net

now it should automagicaly mount your nfs.

---

### Post by cornish12 on 2009-02-08
Hi

I have a NAS and had the same problem. 

I solved it by creating a launcher that points to a location. The location being my NAS. Then I replaced the icon that looks like a spring thing with my own icon that looks like my NAS. Now I have an icon on start up that I can click and go straight to my NAS. This may not be elegant but it solves my problem without editing files etc.

---

### Post by Jose Catre-Vandis on 2009-02-08
As follows:

install a couple of things on your ubuntu PC
```
sudo apt-get install portmap nfs-common
```
create a directory for the share
```
sudo mkdir /media/myNAS
```
write down the IP address (for this example: 192.168.0.10) of your NAS and the full path of the folder being shared (for this example: /files)
edit your fstab file
```
sudo nano /etc/fstab
```
add the following to your fstab at the bottom
```
#NAS share
192.168.0.10:/files /media/myNAS  nfs rsize=8192,wsize=8192,timeo=14,intr,bg
```
save out and run the following command in a terminal
```
sudo mount -a
```
your NAS share should now be found at /media/myNAS

Note: you may need to adjust the settings after the "nfs" in fstab for peak performance

---

### Post by leemajors on 2009-04-27
well, Jose, that did beautifully. However, now when I boot up I still have to type "sudo mount -a" instead of 192.x.x.x:/blah, but it's getting closer.

any way to automatically do "sudo mount -a" on boot?

---

