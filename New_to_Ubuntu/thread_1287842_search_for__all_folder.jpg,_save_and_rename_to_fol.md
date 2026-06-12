---
title: "search for  all folder.jpg, save and rename to: folder 001,002,003 -- .jpg"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by skooter1121 on 2009-10-10
I have lots of folder.jpg files in my MUSIC folder and subs. Using 'earch in Nautilus' I can find them. When I hightlight them and copy, then try to paster them into another folder it warns me that that file already exists.

How can I select them in Nautilus and copy them to another folder and renaming them 001,002,003,004.... , (or even better named after the folder they were in: Movies folder.jpg, Books Folder.jpg, Jethro Tull Folder.jpg ,,,,,)

Any suggestions?

-Skooter

---

### Post by elvisd on 2009-10-21
search for some bash script or python to accomplis that...

---

### Post by pgar23 on 2009-10-21
```
sudo cp *.jpg
``` that code will copy any file that ends in the .jpg form.

For further assistance we will need a better description of what it is exactly that you would like to do. (i.e. move all .jpg files to /home/username/Pictures)

```
sudo cp /home/your_username_here/Music/*.jpg /home/your_username_here/Pictures
```
Will move all the files ending in .jpg form. It will move them from whatever location you input, to whatever location you want them TO BE in.

---

