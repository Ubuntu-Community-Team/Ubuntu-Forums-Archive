---
title: "Can see second harddrive, Cannot DO anything on it."
date: 2010-02-03
forum: New to Ubuntu
---

### Post by ismene on 2010-02-03
Hello - 

I'm really starting to feel like a complete idiot. I have installed a second HD on my Karmic Koala Machine. I couldn't figure out how to mount it, so after browsing the forums, I downloaded the Storage Device Manager and now it mounts on boot up. BUT,  I cannot write or read anything on it. and if I try to click on the one directory "Lost+Found" it says that I do not have permission to display this folder. 

I've read through the FAQs, the forums, and I'm not quite sure what to do. 

Help!

---

### Post by nothingspecial on 2010-02-03
```
ls /media
```

find out the name of your drive.

```
sudo chown -R username:username /media/drive
```

substitute both usernames for your username and drive for the name of your drive.

---

### Post by Cabs21 on 2010-02-03
you have to give your user permission to access write read change and other stuff to the drive/folder that is your second HDD.  In terminal you need to change to root user then access the drive and change the permissions on it.  GUI way would be

```
 sudo -i
(enter password if needed)
nautilus
```

then navigate to the drive (usually in folder /media/your drive here)
right click it and go to permissions tab.  then change them to what you want and say ok and close the terminal.

I know there are other ways to do this but this is the only one i can remember right now.

---

### Post by Muskegman on 2010-02-03
Hi in Karmic you should be able to select , system / administration / disk utility and then click on your second hard drive, marked either sdb or whatever you named it such as "my space" and then you are prompted to type in your password which will then place your second hard drive on your desktop. You should then be able to clcik on it and then drag and drop files into it. 

This new disk utility included in Karmic makes it very easy to give you full permission to read and write to your second HD

---

### Post by ismene on 2010-02-03
Thank you for the suggestion - I didn't do this because I wasn't sure quite what my username was. I'm really feeling like a twit.

---

### Post by ismene on 2010-02-03
> **Muskegman said:**
> Hi in Karmic you should be able to select , system / administration / disk utility and then click on your second hard drive, marked either sdb or whatever you named it such as "my space" and then you are prompted to type in your password which will then place your second hard drive on your desktop. You should then be able to clcik on it and then drag and drop files into it. 

This new disk utility included in Karmic makes it very easy to give you full permission to read and write to your second HD
This didn't work for me - Disk Utility didn't give any permissions options. :S

---

### Post by ismene on 2010-02-03
> ```
 sudo -i
(enter password if needed)
nautilus
```then navigate to the drive (usually in folder /media/your drive here)
right click it and go to permissions tab.  then change them to what you want and say ok and close the terminal.



Thank you! This worked! I was able to read / write a file!

THANKS!

---

### Post by Cabs21 on 2010-02-04
Word. and enjoy

---

