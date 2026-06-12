---
title: "Some fail are extracted fail"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by Sir.Lock.Homes on 2010-07-15
hi mates im new here
here's the situation im trying to extract a winrar file but some files are failed to be extracted. i search the google a while a go and they are pointing to use file roller but it seems that, its hard to install file roller can any one help me with this im ussing ubuntu 9.10
 

by the way im new in linux OS :p 
Thanks

---

### Post by 3rdalbum on 2010-07-15
File Roller comes preinstalled with Ubuntu, under the name "Archive Manager".

Are you sure these are RAR files? File Roller/Archive Manager can deal with RAR, no problems. If the files are actually 7zip (.7z) then you'll need to install the 7z package from Synaptic, and then File Roller can work with 7zip files.

---

### Post by Sir.Lock.Homes on 2010-07-15
> **3rdalbum said:**
> File Roller comes preinstalled with Ubuntu, under the name "Archive Manager".

Are you sure these are RAR files? File Roller/Archive Manager can deal with RAR, no problems. If the files are actually 7zip (.7z) then you'll need to install the 7z package from Synaptic, and then File Roller can work with 7zip files.


actualy its a set of files i compress it in winrar and split it in7parts then when i unzip it in ubuntu with unrar some files fail from being unzip but still the process is still on going

i realy dont know if it is the unziping issue or there are some files in my ubuntu OS that he cant ready i didnt yet fully configure the OS

---

### Post by belkinsa on 2010-07-15
> **3rdalbum said:**
> File Roller comes preinstalled with Ubuntu, under the name "Archive Manager".

Are you sure these are RAR files? File Roller/Archive Manager can deal with RAR, no problems. If the files are actually 7zip (.7z) then you'll need to install the 7z package from Synaptic, and then File Roller can work with 7zip files.

The 7Zip program that allows File Roller to work with them is also in the Software Center

---

### Post by jrothwell97 on 2010-07-15
You might need to install ubuntu-restricted-extras to allow File Roller to handle RAR files.

To do this, you can, if you wish, use the Synaptic Package Manager to install the package manually. However, since we know the package name we're looking for, it is usually quicker and easier to open Terminal (in Applications/Accessories) and enter:

```
sudo apt-get install ubuntu-restricted-extras
```

You will be asked for your password, but as you type nothing will appear on the screen: don't worry, this is normal, the password is still going in.

Once it's finished (the prompt will reappear) try again. Good luck.

---

