---
title: "Terminal file manager"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by CaptainMark on 2009-06-03
I would like to know the terminal command for moving the contents of a file as a group.
Eg. I have a folder 

/home/mark/documents/uni

And that folder contains lots of files
Assingment 1, project 1, assingnment 2, module 2 .... etc. 
If i wanted to move all of the contents of the file into another folder, say

/home/mark/documents/files/university

What terminal command would I use?

I know if i use```
 sudo mv documents/uni documents/files/university
```Then the folder would move but I want to leave the folder as it is just move the files inside
so I would find my files under
/home/mark/documents/files/university/Assignment 1 etc.
I know I could click and drag in this instance but this is just a made up example.
Thanks

---

### Post by SuperSonic4 on 2009-06-03
Do you mean move all the files and folders in the first directory (but not it's parent folder) to the new folder?

If you need to create the folder first: ```
mkdir -p /home/mark/documents/files/university
```

The p flag is for parents - ie: it will create any missing directory leading to that one.

```
mv -v /home/mark/documents/uni/* /home/mark/documents/files/university
```

The v flag means verbose and to tell you what's going on. Why you'd use sudo in your home directory I'm not sure - you'd only need that if root owned the documents themselves. You may also want to pass the u flag which is update only.

------------------

T flag doesn't seem too special. When I passed -T it moved it all including subfolders etc but I passed it on it's own

---

### Post by Locutus_of_Borg on 2009-06-03
mv folder/* new_folder/
will move the contents of folder into new_folder while still leaving the now empty folder in its place

is that what you are asking?

---

### Post by CaptainMark on 2009-06-04
Thats exactly what i was asking thank you very much.

---

