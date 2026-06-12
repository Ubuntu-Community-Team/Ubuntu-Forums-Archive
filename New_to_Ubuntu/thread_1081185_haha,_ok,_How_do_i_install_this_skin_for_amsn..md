---
title: "haha, ok, How do i install this skin for amsn."
date: 2009-02-26
forum: New to Ubuntu
---

### Post by negative: on 2009-02-26
Well, here i go again.another question lol. 


I downloaded this skin right for amsn, and the instructions say... 

Linux

To install a skin just download it, and extract the files for the .zip file (.zip, .tar.gz, or similar). Then copy the extracted skin folder to one of the following locations:

 /usr/share/amsn/skins
 $HOME/.amsn/skins

The skin should appear in the skins selector dialog. 

Does this mean use terminal somehow, cause if it does, i no idea what to put in to install it.

Because i tried just cutting and pasting the file, but i do not have access, and i can't change the permissions. 

by the way i extracted it to my desktop first so it's just in a folder called Dark Matter.

stuck.. lol. :mad:

---

### Post by BOZG on 2009-02-26
Try these in the terminal:

```
sudo mv ~/Desktop/Dark\ Matter /usr/share/amsn/skins
```

or

```
sudo mv ~/Desktop/Dark\ Matter ~/.amsn/skins
```

---

### Post by overlord.gaurav on 2009-02-26
Well, you might not have the permissions[write] to /usr/share/amsn/skins but you do have permission[write] to  the other folder
The folder ".amsn" is a hidden folder in your home directory.
According to instructions:
Copy the skin file. Then go to your home folder. Press "Ctrl + H" and you'll find a folder named ".amsn" Go to this folder and paste the skin inside the sub-folder named "skins".

---

### Post by negative: on 2009-03-09
thankyouu, :)

i forgot which one worked, but it did lol. 


:D

---

