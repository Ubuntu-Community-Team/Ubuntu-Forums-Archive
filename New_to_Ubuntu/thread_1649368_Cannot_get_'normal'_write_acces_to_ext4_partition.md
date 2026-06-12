---
title: "Cannot get 'normal' write acces to ext4 partition"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by yozgoesdigital on 2010-12-20
Hi All,
Just installed a fresh lubuntu installation with a separate partition for all the data files. 
I edited the fstab file to let this partition be automounted to /home/flaptop/Data. Problem is that the partition is mounted, but I am not able to get write acces. If I try to write I get the message: 
> Error creating directory: Permission denied
Although it is possible to write things with a sudo command from the terminal (e.g. I could create a folder).

The fstab command:
```
/dev/sda6  /home/flaptop/Data  ext4  defaults 0  0 
```

Who can help/guide me with automounting this partition? I tried, but I do not get any further on my own.

Thanks!

---

### Post by Verbeck on 2010-12-20
try 
```

sudo chown -R username:usergroup /home/flaptop/Data

eg,
sudo chown -R flaptop:flaptop /home/flaptop/Data

```while it's mounted

---

### Post by slooow on 2010-12-20
It seems to me that you have to check who is owner of that partition. 
```
ls -la /home/flaptop/Data
```
If you find that you are not the owner of that directory, do
s```
udo chown -R user /home/flaptop/Data
```

By the way the second zero in fstab should probably be replaced with a 2. Read man fstab for more info.

---

### Post by lmarmisa on 2010-12-20
I recommend to modify a bit  your procedure.

1) Define a new directory for mounting your hard drive /media. For example:

```

sudo mkdir /media/DataHD

```2) Modify the line of file /etc/fstab

```

/dev/sda6  /media/DataHD  ext4  defaults 0  0

```3) Reboot the system or mount manually DataHD.

4) Create a new directory for Data in DataHD:

```

sudo mkdir /media/DataHD/Data

```5) Become the owner of the new directory Data:

```

sudo chown -R flapto:flaptop /media/DataHD/Data

```6) Finally define a symbolic link from your home directory to the Data dir (I suppose you have deleted your current folder /home/flaptop/Data) 

```

ln -s /media/DataHD/Data ~/Data

```

---

### Post by yozgoesdigital on 2010-12-20
Thanks for the quick replies.
When you freshly install, the user and usergroup are similar? 

I will directly try the suggested solutions, I will keep you informed.

---

### Post by lmarmisa on 2010-12-20
> **yozgoesdigital said:**
> Thanks for the quick replies.
When you freshly install, the user and usergroup are similar? 

I will directly try the suggested solutions, I will keep you informed.

The Ubuntu installation defines the same name for user and group. I suppose that this name is flaptop in your system.

---

### Post by yozgoesdigital on 2010-12-20
It worked thanks! The chown command apparently is the command which does the magic.

@ Imarmisa:

For my understanding: Is there a special reason to only change permissions/ownership of the folder Data on the Ext4 partition (= sda6/Data)? My preference would be to change ownership to the whole partition (=sda6), since it is the only OS which will be using this partition.

so step 5 would be: 
```
sudo chown -R flapto[COLOR="Red"]p[/COLOR]:flaptop /media/DataHD
```
p.s. (the red p was a typo in your post)

step 6 would become:
```
ln -s /media/DataHD ~/Data
```

Is there a disadvantage for this solution?

---

### Post by lmarmisa on 2010-12-20
> **yozgoesdigital said:**
> It worked thanks! The chown command apparently is the command which does the magic.

@ Imarmisa:

For my understanding: Is there a special reason to only change permissions/ownership of the folder Data on the Ext4 partition (= sda6/Data)? My preference would be to change ownership to the whole partition (=sda6), since it is the only OS which will be using this partition.

so step 5 would be: 
```
sudo chown -R flapto[COLOR=Red]p[/COLOR]:flaptop /media/DataHD
```p.s. (the red p was a typo in your post)

step 6 would become:
```
ln -s /media/DataHD ~/Data
```Is there a disadvantage for this solution?

Sorry by my mistake typing the command chown.

The solution I propose allows to define new folders in the new partition owned by other users. Other advantage is to maintain all the devices mounted in the same directory /media. This is more or less a standard in Debian / Ubuntu. I had some problems some time ago trying to change the owner of a whole partition too. These are my reasons.


A last comment: if you wish to have a trash folder in your new partition, you have to create in the root of this partition a folder named .Trash-1000 (really 1000 is your uid) owned by your user.

```

sudo mkdir /media/DataHD/.Trash-1000
sudo chown -R flaptop:flaptop /media/DataHD/.Trash-1000

```

---

### Post by yozgoesdigital on 2010-12-20
Thanks that explains the reasoning behind it.

Yoz

---

