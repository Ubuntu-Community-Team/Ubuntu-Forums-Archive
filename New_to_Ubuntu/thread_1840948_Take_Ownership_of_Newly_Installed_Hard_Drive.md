---
title: "Take Ownership of Newly Installed Hard Drive"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by ai4kn on 2011-09-08
I recently installed a new 2.0 TB hard drive on by Ubuntu 11.04 system. I have visibility of the drive on Nautilus, but can't write to it. Owner shows as "root". How do I take ownership of this drive?

---

### Post by howefield on 2011-09-08
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

```
sudo chown -R USERNAME:USERNAME /media/mynewdrive
```

replace USERNAME with your user name and mynewdrive with the name of the drive.

---

### Post by JohnPta on 2011-09-24
> **howefield said:**
> [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

```
sudo chown -R USERNAME:USERNAME /media/mynewdrive
```

replace USERNAME with your user name and mynewdrive with the name of the drive.

Ok I did as your suggested with "ai4kn" but this is my result: 

root@jan-desktop:~# sudo chown -R USERNAME:Jan /media/Samsung
chown: invalid user: `USERNAME:Jan'
root@jan-desktop:~# sudo chown -R Jan: /media/Samsung
chown: invalid spec: `Jan:'
root@jan-desktop:~# sudo chown -R Jan. /media/Samsung
chown: invalid user: `Jan.'
root@jan-desktop:~# sudo chown -R Group:Jan /media/Samsung
chown: invalid user: `Group:Jan'
root@jan-desktop:~# 

Regards Jan

---

### Post by Elfy on 2011-09-24
Try jan - not Jan

Linux is cAse sensitive

If not logout of the root session and use whatever it says at the prompt - eg

hobgoblin@hobgoblin

mines hobgoblin

---

### Post by coffeecat on 2011-09-24
One useful little shortcut that doesn't seem to be well known. If you omit the group name, but leave a trailing colon, as in:

```
sudo chown -R yourusername: /media/mountpoint
```

... the chown command will apply whichever your default group is. Saves a few keystrokes and it works with chmod too.

---

### Post by JohnPta on 2011-09-24
> **coffeecat said:**
> One useful little shortcut that doesn't seem to be well known. If you omit the group name, but leave a trailing colon, as in:

```
sudo chown -R yourusername: /media/mountpoint
```

... the chown command will apply whichever your default group is. Saves a few keystrokes and it works with chmod too.

Thanks, that works however when I switch of or reboot the computer I have to go through that whole exercise again. Is there no way that one can change this to a permanent situation/setup.

Thanks.

---

### Post by coffeecat on 2011-09-24
> **JohnPta said:**
> Thanks, that works however when I switch of or reboot the computer I have to go through that whole exercise again. Is there no way that one can change this to a permanent situation/setup.

Thanks.

Interesting. It sounds as though the -R (recursive) option may not be affecting the ownership of the root of the filesystem in the external drive - just all the folders and files in it. 

Whenever I want to own a Linux filesystem on an external drive or an internal partition, I run the chown command without the -R switch. Although this might appear to be chowning the mountpoint, it doesn't - it takes ownership of the filesystem itself. And it sticks. So try:

```
sudo chown yourusername: /media/mountpoint
```

Substituting *yourusername* and *mountpoint* as appropriate.

---

### Post by Leppie on 2011-09-24
Nesxt time try the following, it should be just copy & paste:
```
sudo chown -R $USER: /media/Samsung
```

What filesystem is the drive?

---

### Post by user sam on 2011-09-24
Um, this may be a stupid suggestion, but why not just start Nautilus as root using gksu and then browse to your hard drive, right click, go to properties and change the permissions from there?
```
gksu nautilus
```

---

### Post by JohnPta on 2011-09-24
> **coffeecat said:**
> Interesting. It sounds as though the -R (recursive) option may not be affecting the ownership of the root of the filesystem in the external drive - just all the folders and files in it. 

Whenever I want to own a Linux filesystem on an external drive or an internal partition, I run the chown command without the -R switch. Although this might appear to be chowning the mountpoint, it doesn't - it takes ownership of the filesystem itself. And it sticks. So try:

```
sudo chown yourusername: /media/mountpoint
```

Substituting *yourusername* and *mountpoint* as appropriate.

Yes you are right. When I take the mount point as "/media" it sticks, thanks anyway.:biggrin:
My wife asks me why I am still fighting with Linux instead of planting roses at my age. Well I told her because it is there and it keeps my brain busy. ;)

---

### Post by coffeecat on 2011-09-24
> **JohnPta said:**
> 
My wife asks me why I am still fighting with Linux instead of planting roses at my age. Well I told her because it is there and it keeps my brain busy. ;)

And Linux doesn't impale you with thorns! Well - only metaphorical ones. :)

Good luck!

---

