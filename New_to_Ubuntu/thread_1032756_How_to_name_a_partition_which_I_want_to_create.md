---
title: "How to name a partition which I want to create?"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by kramer65 on 2009-01-06
I want to make a new partition using gparted. The last one I made had no name and was always displaying as "Media of GB 200". 

When I make a new partition in Gparted however, I can't give it a label or name it. How would I be able to do this?

---

### Post by theinnercityhippy on 2009-01-06
> **kramer65 said:**
> I want to make a new partition using gparted. The last one I made had no name and was always displaying as "Media of GB 200". 

When I make a new partition in Gparted however, I can't give it a label or name it. How would I be able to do this?

When it has been created, open a terminal from the Accessories menu and do the following

```
e2label device [newlabel]
```

Where the device is the information for that particular partition (eg /dev/sda3). You can find this out from gparted. The new label should take effect after a reboot.

Hope this helps

-JimDog*-

---

### Post by Michael.Godawski on 2009-01-06
A great how to on labeling wrote once bodhi.zazen.

Have a look into his fstab guide:


[LIST]
[*][http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[/LIST]

---

### Post by kramer65 on 2009-01-06
Thanks for those tips. I used the code you suggested (e2label device [newlabel]) and rebooted and it now seems to be renamed. When I click it however, I get an error saying (freely translated from Dutch):

Can't mount volume '**Opslag**' ("Opslag" is the name I gave it)
And that only root can mount /dev/sda1 to /media/**Data**.

"Data" was the name that the partition had before. But because "Data" never worked properly I deleted the partition and recreated it to rename it to "Opslag".

Do you know how I can get rid of that old name "Data"?

---

### Post by Titan8990 on 2009-01-06
Do the following:

sudo mkdir /media/opslag
sudo mount /dev/sda1 /media/opslag

Then to make it accessible to your user:


sudo chown -R yourusername /media/opslag


In order for it to mount on boot you will have to edit /etc/fstab: [http://ubuntuforums.org/showthread.php?t=283131&highlight=fstab](http://ubuntuforums.org/showthread.php?t=283131&highlight=fstab)

---

### Post by kramer65 on 2009-01-06
One step further.. It now opens but I have no rights to it. I am not sure but can I then do this:

sudo chmod 777 /media/opslag

?

- edit -
Alroght! Thanks for that! I can now use it!!

I will find out how to automatically mount it now then!

Thank you so much again!

ps. I thought I had learned something by now that rights are always done with chmod, but I had never heared of chown.. Well, I can always learn.. :)

---

### Post by Titan8990 on 2009-01-06
Yes, but you would want it to do:


sudo chmod -R 777 /media/opslag


Neither commands will work if the drive is not in a Linux format such as EXT2/3 or XFS.

---

### Post by kramer65 on 2009-01-06
Alright. But what is then the difference between chmod and chown?

---

### Post by Titan8990 on 2009-01-06
chmod changes permissions and chown changes the owner of the file/folder.

---

### Post by kramer65 on 2009-01-06
Ah Alright, that makes sense. Thanks!

I just got into a little confusion. I now have two things in media: "Opslag" and "opslag" (with and without a capital letter "O").
In Places it shows one with a capital letter but when I click it I get to the one without capital letter. What did I do wrong here..?


-edit-
ps. I also just read that whole file about fstab, but I totally don't get how to mount automatically. I read this: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

I got this file (/etc/fstab) open but I don't know what I need to write under <options>..

---

### Post by logos34 on 2009-01-06
the mount name is apparently lower case o, but the volume label is capital.  Relabel it

---

### Post by kramer65 on 2009-01-07
Ok. So how can I rename the mount name to a name with a capital letter O?

---

### Post by logos34 on 2009-01-07
sudo mkdir /media/Opslag

edit fstab entry

---

