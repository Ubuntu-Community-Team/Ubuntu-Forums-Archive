---
title: "i need help with playing music and movies throughout the network?"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by beginningGimp on 2010-12-24
1.  I have a usb stick with 2 GB of music.  I don't know how to import it to Rythm Box.  I selected **scan removable media** and it will not scan my usb for music files.  How do I import music from removable media to Rythm Box.

2. Should I use Rythm Box or another program?  I have a computer in the bedroom with music files.  I also have a computer in the living room connected to a stereo system.  I would like to be able to play music in the bedroom and living room at the same time.  So when i walk from the bed room to the living room, the music is synchronized.  I would also like to play a movie in the bedroom computer and have it play in the living room as well.  So I ask again, should I be using Rythm Box or another program?

3.

---

### Post by nothingspecial on 2010-12-24
Do all these computers use Ubuntu? Or even linux.

If so, this is very easy.

If not, I`m the wrong person to show you.

---

### Post by beginningGimp on 2010-12-24
I will  be going to all ubuntu system, computer in bedroom has ubuntu 10.4 and with in an hour the computer in the living room should be running ubuntu.

---

### Post by t4thfavor on 2010-12-24
I use Ubuntu with samba to share out the music files, that way my Wife who prefers Win7 can still access them without too much extra trouble/setup.

It's really easy to setup, as the stuff you need to get started is almost already setup as soon as you install the packages.

EDIT: 

Oh, and if your not brave enough yet, there's a pretty competent gui.

---

### Post by beginningGimp on 2010-12-26
I have ubuntu 10.4 installed in the bedroom computer, and ubuntu 10.4 installed in the living room computer.  My music files are stored on my bedroom computer.  I am using Rythm Box for playing music. What is the next step?

---

### Post by t4thfavor on 2010-12-27
Install some type of file sharing utility as recommended above. Try samba, or nfs.

If you have windows, use Samba as it is easier to connect to from windows.

NFS is probably easier to install for linux only networks though.

---

### Post by beginningGimp on 2010-12-28
Ok, I installed samba (SMB/CIFS) through the ubuntu software center on my bedroom computer.  What is next? :confused:

---

### Post by t4thfavor on 2010-12-29
You'll need to get a little dirty to make this work. That said, you now need to edit your /etc/samba/smb.conf file.

relavent portions will look like this
```

[disk]
path = /media/300
available = yes
browsable = yes
public = yes
writable = yes

```

You will also need a user that is able to access the disk.

```

sudo service smbd restart
sudo smbpasswd yourusername

```
Pick a password, then from the other PC, if the username/password is the same, you should not need to enter it.

From the Places menu. pick network, and you should see the server you just setup.


If you look up how to add an automount to your /etc/fstab for a cifs mount, you will be able to access the share like a regular directory somewhere on your disk.

Oh, and you need to do some digging on this stuff, this thread has been solved hundreds of times. Not everybody is as nice as I am, and once you get a few more posts, people wont spoon feed you as often.

---

