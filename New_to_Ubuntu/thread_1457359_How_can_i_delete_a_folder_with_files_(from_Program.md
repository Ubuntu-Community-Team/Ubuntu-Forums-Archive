---
title: "How can i delete a folder with files (from Program)"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by souraklis on 2010-04-18
I have installed wrongly a program in the path \use\local\...
I want to delete all the files there but i cant find any accurate way. Can anyone help???

---

### Post by WinterRain on 2010-04-18
```
gksu nautilus
```
will give you permission (graphically) to delete things as you wish. Just be careful.

---

### Post by jaco223 on 2010-04-18
> **souraklis said:**
> I have installed wrongly a program in the path \use\local\...
I want to delete all the files there but i cant find any accurate way. Can anyone help???


Open a terminal window and navigate to where the files are you want to remove.
And type:

```
sudo** rm **(filename)
```

 The **rm -rf** command will remove any directory you specify.

Hope this helps.

Jaco

---

### Post by barney385 on 2010-04-18
I believe you can do an apt-get purge *pkg* also...

---

### Post by souraklis on 2010-04-18
jaco223 &#921; started yesterday to do exactly what you told but the folder had 3000 files and it was nt very practical. So i ve just tried to remove the files from nautilus. I ve erased them normally but when i went to filesystem to see the free space i noticed that it is the same with the free space before(the delete).

---

### Post by quadproc on 2010-04-18
> **souraklis said:**
> jaco223 &#921; started yesterday to do exactly what you told but the folder had 3000 files and it was nt very practical. So i ve just tried to remove the files from nautilus. I ve erased them normally but when i went to filesystem to see the free space i noticed that it is the same with the free space before(the delete).
Did you actually remove the files rather than moving them to Trash?  If moved to Trash then they are still there just in another place.

I don't know what your unwanted file names have in common but this might be an ideal place to use a regular expression which is a little more sophisticated than "*".  Or, perhaps the "find" command could be targeted to the files that you wish to remove.

Whatever you use, please be careful.

quadproc

---

### Post by souraklis on 2010-04-18
ok i removed them firstly to the trash but when i went to see them the trash bin was empty!!!??

---

### Post by eltonw on 2010-04-18
> **souraklis said:**
> ok i removed them firstly to the trash but when i went to see them the trash bin was empty!!!??

The trash bin may appear to be empty, but perhaps these are hidden files? ... that would explain why you have not recovered space on your HD, they may be just 'marked for / as deleted' but not actually purged from the HD.

If you enable show hidden files, you will see more directories.  Nautilus: View--> Show Hidden files. If you enable this you would see that there ARE files and folders in the trash.
 
[COLOR="Red"][FONT="Comic Sans MS"]CAVEAT: BE CAREFUL what you delete among the hidden folders!!! [/FONT][/COLOR]

These directories will have a dot before the name, e.g. .newprogram. **FYI**, to create a hidden folder in linux you MUST place a dot before the name.

HTH...

---

### Post by Paqman on 2010-04-18
> **souraklis said:**
> ok i removed them firstly to the trash but when i went to see them the trash bin was empty!!!??

If you deleted them as root, then they'll be in root's trash bin, not yours.

---

### Post by souraklis on 2010-04-18
eltonw I cant open from nautilus the trash bin i got:

"The folder contents could not be displayed"
Operation not supported

---

### Post by quadproc on 2010-04-18
> **souraklis said:**
> eltonw I cant open from nautilus the trash bin i got:

"The folder contents could not be displayed"
Operation not supported
Did you do this as a privileged user?  If so, it should have worked.  You can run the Places utility with privilege by
```
gksudo nautilis
```But please be careful - you can make your system unusable and lose all of your programs and data due to simple mistakes made in this mode.

quadproc

---

### Post by souraklis on 2010-04-20
Just nothing i tried to deleted as a root user with sudo but the same i couldnt find the files.

---

