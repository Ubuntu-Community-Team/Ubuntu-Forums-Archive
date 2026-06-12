---
title: "files will not open"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by psyk117 on 2009-11-10
I just upgraded to 9.10, and now my files will not open. I click on "documents" and it looks like it's going to open, but it doesn't.
help would be greatly appreciated.

---

### Post by Bodsda on 2009-11-10
> **psyk117 said:**
> I just upgraded to 9.10, and now my files will not open. I click on "documents" and it looks like it's going to open, but it doesn't.
help would be greatly appreciated.

Hi, could you please open a terminal by going to the Applications menu >> Accessories sub menu >> Terminal

Once this has opened could you please run the following command 
```

nautilus ~/Documents

```

This will open a file browser starting at your documents folder. The reason I am asking you to run this from the terminal is so that we can see any errors that are produced. These can then be pasted on here so that we can try and diagnose the problem.

Kind regards,
Bodsda

---

### Post by psyk117 on 2009-11-10
(nautilus:2627): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:2627): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2627): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2627): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Segmentation fault

---

### Post by philinux on 2009-11-10
Try removing the nautilus settings folder.

Open a terminal and copy this in

```
rm ~/.gconf/apps/nautilus
```

Then try Places again. The above folder will be recreated.

---

### Post by psyk117 on 2009-11-10
when I typed that it just said:

rm: cannot remove `/home/psyk117/.gconf/apps/nautilus': Is a directory

---

### Post by Terry of Astoria on 2009-11-10
That makes sense. To remove the whole directory (folder) you will have to do "rm -r" not just "rm". If you want to follow the previous directions, you could add the -r to the command right after rm, like 
```
rm -r ~/.gconf/apps/nautilus
```

---

### Post by psyk117 on 2009-11-10
well, I just tried that, and it didn't work =[
it didn't say anything afterwards.

---

### Post by jakon on 2009-11-10
This is okay. No output means everything worked fine.

Does nautilus start now?

---

### Post by psyk117 on 2009-11-10
nothing starts...
I still can't open anything.

---

### Post by psyk117 on 2009-11-11
help?
it's still not opening my folders in places..

---

### Post by MinionTech on 2011-01-05
> **philinux said:**
> Try removing the nautilus settings folder.

Open a terminal and copy this in

```
rm ~/.gconf/apps/nautilus
```

Then try Places again. The above folder will be recreated.


Thanks Philinux!  You just solved my file launching problem.

---

### Post by s1wood on 2011-01-06
deleted post - I just realised how old this thread is.

---

### Post by oksig3n on 2011-01-15
currently i have been this problem.. this is my output.. how to solve my frend

> fmzunimap@fmzunimap-desktop:~$ nautilus ~/Documents

(nautilus:8495): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

** (nautilus:8495): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:8495): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:8495): WARNING **: No marshaller for signature of signal 'ShareCreateError'
** Message: Initializing gksu extension...
Initializing nautilus-gdu extension
Segmentation fault
fmzunimap@fmzunimap-desktop:~$ rm ~/.gconf/apps/nautilus
rm: cannot remove `/home/fmzunimap/.gconf/apps/nautilus': No such file or directory
fmzunimap@fmzunimap-desktop:~$ rm -r ~/.gconf/apps/nautilus
rm: remove all arguments recursively? y
rm: cannot remove `/home/fmzunimap/.gconf/apps/nautilus': No such file or directory
fmzunimap@fmzunimap-desktop:~$ rm ~/.gconf/apps/nautilus
rm: cannot remove `/home/fmzunimap/.gconf/apps/nautilus': No such file or directory
fmzunimap@fmzunimap-desktop:~$ 

---

### Post by MinionTech on 2011-01-16
> **oksig3n said:**
> currently i have been this problem.. this is my output.. how to solve my frend

Hi Okaysig3n,


You were close!  Try this instead:

```

rm -rf ~/.gconf/apps/nautilus
nautilus -q

```


Best regards,

MinionTech

---

