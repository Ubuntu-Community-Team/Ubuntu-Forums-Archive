---
title: "Irritating permissions problem"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by Charlie Chick on 2009-11-22
Hello Everybody,

I have an irritating permissions problem. I have just formatted an external USB drive to ext4 using G Parted and I now can't copy anything to it because I'm told that I don't have the necessary permissions. I just created it - shouldn't that automatically give me permission to use my own drive? 

How do I make it useable? Right clicking and selecting PROPERTIES says that "permissions cannot be determined". This drive is currently unuseable.

Thanks,

Charlie

---

### Post by dragos_iliescu_2005 on 2009-11-22
It sound to me like the drive is not mounted.

---

### Post by Charlie Chick on 2009-11-22
Yes, the drive is mounted.

---

### Post by dragos_iliescu_2005 on 2009-11-22
In this case I have no other idea. Sorry.

---

### Post by Charlie Chick on 2009-11-22
Can anybody else help me please?

---

### Post by Puzzled Guy on 2009-11-22
did you create the drive in the extended partition?

did you use gparted? if so, did you install it or did you do it from the live cd?

---

### Post by Charlie Chick on 2009-11-22
I used G Parted within Ubuntu. I formatted it to ext4 and now it's unuseable. Should I have booted from a CD version of G Parted and done it that way? Surely, as I did it from within my own Ubuntu I should have permissions over it?

---

### Post by Elfy on 2009-11-22
Change the permissions so you own it and not root.

```
sudo chown user.user /path/todrive
sudo chmod 770 /path/todrive
```

eg - if the external is mounted on /media/disc use that above

Where user is your user name, I tend ot give myslef full rights - hence the chmod 770 command

[https://help.ubuntu.com/community/FilePermissions#Changing%20the%20File%20Owner%20and%20Group](https://help.ubuntu.com/community/FilePermissions#Changing%20the%20File%20Owner%20and%20Group)

---

### Post by Charlie Chick on 2009-11-22
Is there any way of doing this without using the command line? I'm not sure how to find the path.

---

### Post by Z652 on 2009-11-22
This might help?

[http://ubuntuforums.org/showpost.php?p=8317399&postcount=2](http://ubuntuforums.org/showpost.php?p=8317399&postcount=2)

---

### Post by Charlie Chick on 2009-11-22
I tried the information in the link but got an error message:

(nautilus:3881): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

** (nautilus:3881): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3881): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3881): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Also, right clicking the drive in file browser doesn't have properties.

---

### Post by Charlie Chick on 2009-11-22
> **Z652 said:**
> This might help?

[http://ubuntuforums.org/showpost.php?p=8317399&postcount=2](http://ubuntuforums.org/showpost.php?p=8317399&postcount=2)

Thank you, it worked! I couldn't get permissions by right clicking the drive itself; it simply didn't appear. However, there was a 'lost & found' folder and I right clicked that, selected permissions and gave myself read & write permissions. That seems to have done the trick.

Thanks very much for your help (and to everybody else who responded)

Charlie

---

