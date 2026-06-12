---
title: "Cannot mount network drive from command line"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by stepheny on 2008-10-14
I have bought a Iomega Home Network Hard Drive and installed it. It is reachable from my wife's XP laptop and from my Ubuntu (Gnome) machine via Places-Connect to Server-Windows Share.

I would like to include it in my fstab but I cannot seem to be able to mount the drive. I have tried the following from the command line (with and without username and password):-
```

sudo mount -t cifs //192.168.0.2/public /media/share
```

but sometimes I get the error "mount error 11 = Resource temporarily unavailable" and other times it appears to work but there is nothing in /media/share and when I do:- 
```

sudo umount /media/share
```

I get the error "umount: /media/share: not mounted"

Any help gratefully received.

---

### Post by madmaxnj on 2009-01-02
352 views and no replies.  I have the same network drive that I'm trying to get working with Intrepid.  I've 'heard' about the great linux online community and support.  Now that I'm entrenched I don't really see it.  A lot of people have problems, very few people have help.

---

### Post by kevindt on 2009-01-02
I have had the same problem with mounting my Buffalo NAS on 192/168.0.147, but have just solved it by the following steps:

1.  sudo mkdir /media/share.

2.  I needed to install smbfs (done via synaptics) which includes the mount.cifs command.

3.  Then it mounted perfectly with the command "sudo mount.cifs //192.168.0.147/share /media/share"

Kevin.

---

### Post by kevindt on 2009-01-02
I have had the same problem with mounting my Buffalo NAS on 192/168.0.147, but have just solved it by the following steps:

1.  sudo mkdir /media/share.

2.  I needed to install smbfs (done via synaptics) which includes the mount.cifs command.

3.  Then it mounted perfectly with the command "sudo mount.cifs //192.168.0.147/share /media/share"

Kevin.

---

### Post by kevindt on 2009-01-02
Sorry about double post - I hit a "server busy" and it loaded without seeing it do so the first time :)

---

### Post by madmaxnj on 2009-01-03
Kevin,
Thanks.  That sort-of worked for me.  I now have a /media/share drive (which wasn't there before), but its empty.  I think this is a different issue that I'm having with the iomega home network drive.  When I can see it under Places-Network (I have to have my XP box on to see it, but thats another story), I can see the folders, but no contents.  Once I figure the other stuff out, I guess I can out how to put the "sudo mount.cifs //192.168.0.147/share /media/share" in a startup batch script (or the linux equivalent).

---

### Post by madmaxnj on 2009-01-03
Spoke too soon, nothing happened.  Momentary lapse of reason the first time around.  I now get a prompt for the password to the share (which is nothing), and when I hit enter at the prompt it just sits there and nothing happens.  It doesn't even return to the command line prompt, it just dies.

---

### Post by stepheny on 2009-01-12
This is a bug with samba-common and smbfs 3.0.28a.

I fixed the problem by downloading samba-common_3.0.26a-1ubuntu2.3_i386.deb and smbfs_3.0.26a-1ubuntu2.3_i386.deb from [http://apt.wikimedia.org/ubuntu/pool/main/s/samba/]("http://apt.wikimedia.org/ubuntu/pool/main/s/samba/") and then forcing a downgrade with:

```
sudo dpkg -i --force-downgrade samba-common_3.0.26a-1ubuntu2.3_i386.deb
sudo dpkg -i --force-downgrade smbfs_3.0.26a-1ubuntu2.3_i386.deb
```

I can now mount the network drive with: 

```
sudo mount.smbfs //192.168.0.2/public /media/share
```

I understand that there may be a security issue involved with this solution but as of now I cannot mount the drive any other way.

---

### Post by echelecopao on 2009-04-24
I had the same problem described in the first message on my Iomega Home Network Hard Drive.
After upgrading the NAS with the latest firmware the problem was fixed. I'm now able to mount using this line in /etc/fstab
//NAME/HomeBackup /media/HomeBackup    cifs    credentials=/root/.cifscredentials  0 0

firmware file: storcenter_home_firmware-k108w15-d31462802.bin
get it from iomegas website. under Support

---

### Post by bries on 2009-09-05
> **stepheny said:**
> This is a bug with samba-common and smbfs 3.0.28a.

I fixed the problem by downloading samba-common_3.0.26a-1ubuntu2.3_i386.deb and smbfs_3.0.26a-1ubuntu2.3_i386.deb from [http://apt.wikimedia.org/ubuntu/pool/main/s/samba/]("http://apt.wikimedia.org/ubuntu/pool/main/s/samba/") and then forcing a downgrade with:

```
sudo dpkg -i --force-downgrade samba-common_3.0.26a-1ubuntu2.3_i386.deb
sudo dpkg -i --force-downgrade smbfs_3.0.26a-1ubuntu2.3_i386.deb
```

I can now mount the network drive with: 

```
sudo mount.smbfs //192.168.0.2/public /media/share
```

I understand that there may be a security issue involved with this solution but as of now I cannot mount the drive any other way.

this is exactly what I was looking for. I downgraded to samba-common and smbfs 3.0.26a and I can access the shares on my Iomega Home Media Drive again. Thanx!

---

### Post by Keermalec on 2009-09-18
Weel I'm a noob who just spent a hell of a lot of time working this out too.

I believe I found an easier way, involving editting the boot script /etc/rc.local. Heres the procedure in detailled noob steps:


1. make urself root admin:

    sudo bash
    ******

2. create a mount point on Desktop:

    cd /home/marco/Bureau
    mkdir 'Fichiers Réseau'
    chmod o+w 'Fichiers Réseau'

3. install smbfs:

    sudo aptitude install smbfs

4. mount the network resource to mount point:

    mount -t cifs //192.168.1.34/Public -o username=yourusername,password=yourpassword /home/marco/Bureau/'Fichiers Réseau'

5. to auto mount drive at each startup, allow modification of rc.local

    cd /etc
    chmod o+w rc.local

6. add following line to /etc/rc.local, before 'exit 0'
    
    sudo aptitude install smbfs
    mount -t cifs //192.168.1.34/Public -o username=yourusername,password=yourpassword /home/marco/Bureau/'Fichiers Réseau'


Works for me :) :) :)

---

