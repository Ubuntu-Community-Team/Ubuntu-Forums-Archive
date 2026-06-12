---
title: "I would like to make a full backup of my / and /home"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by slughappy1 on 2010-07-02
I would like to make a full backup of my / and /home partitions. I want to be able to install different versions of Ubuntu or distributions on my computer. Is this the best way to backup my / directory, [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087). Also, would I have to do anything different to backup my /home?

---

### Post by apb2390 on 2010-07-02
For an easy, full backup I would say that's the best way to do it. It's straightforward and simply works.

For backing up your /home Directory, instead of using the command:
```
cd /
```
you would use the command:
```
cd /home
```
and then execute the command:
```
tar cvpzf backup_home.tgz  --exclude=/backup_home.tgz
```
This would create a different file called backup_home.tgz in your /home directory.

Cheers,
apb

---

### Post by sam_delta on 2010-07-02
for home, deja-dup works awesome for me. Its fast and has an easy gui. you can backup either to a server, to a local folder or a usb. You can also make it backup at scheduled times and backups wont take long since it keeps a index of the changes made and only backups the changes.

sam

---

### Post by slughappy1 on 2010-07-03
Ok thanks. Also just to make sure. Since I have a seperate / and /home partitions. The backup of / wont backup my /home right?

EDIT: I take my question back. I started it and found out it will back up the /home partition when I use the command ```
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

```

---

### Post by philinux on 2010-07-03
> **slughappy1 said:**
> I would like to make a full backup of my / and /home partitions. I want to be able to install different versions of Ubuntu or distributions on my computer. Is this the best way to backup my / directory, [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087). Also, would I have to do anything different to backup my /home?

You could try this.

[http://geekconnection.org/remastersys/](http://geekconnection.org/remastersys/)

It has a limit of 4gig for the iso created. That's an iso standard limit not the project's.

---

### Post by oldfred on 2010-07-03
I am always less concerned about root as I would plan on reinstalling anyway and I totally reinstall with each new version now.

I make a list of all installed applications and a copy of sources and include that in /home so it gets backed up also. If I manually edit anything in /etc I make a copy and put that into /home. Since I link /data folders into /home I have a script for that. That does not leave much that would have to be manually reset as long as I have a good copy of /home. (Oldfred goes off to make backup of /home =P~)

sudo cp /etc/apt/sources.list ~/sources.list.backup
dpkg --get-selections > ubuntu-file

---

### Post by joedoe47 on 2010-07-03
The easiest I found was like "sam_delta" recommended, deja dup. It's simple to use as far as backing up you info into a nice zipped file you can upload it to a usb drive, backup hardrive, dvd it will even upload itself into a web server (you just need to go into the settings and select "preferences". COme on two buttons how easier can it get (oh and you have the option to encrypt your backup)?

However Remastersys is also good (you don't need to worry about configuring or stuff like that) plus it packages your information ready to be burned into a dvd (although like mention before by philinux there is a 4 gig limit). It's just a matter of dragging and dropping your files back where they belong.

to each his own I say it depends on how or rather where to plan to store your backup and how easy would you like your restore to be (lazy or easy?)

---

