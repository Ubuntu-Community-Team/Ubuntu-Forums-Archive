---
title: "0 Byte folders in windows"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by Elep.Repu on 2009-07-16
I copied music to an external NTFS from linux.

Copied alright, no errors originally. Win couldn't open it (I did a bunch of searches),
Moved back over to linux and it copied from the external just fine, even the 0 byte folders were copied like normal folders.

In windows I could *open* those folders, and even copy and *use* what was inside,
but automatically I couldn't copy the folder itself (which meant I would be going through a lot of stuff to fix it manually.)


Any ideas how this happened?
I ran a chdisk (which took forever like usual,) and it didn't do anything.
I'm in linux and moving everything over to an internal, 
hopefully this will solve the problem?

I read folders are nothing (in linux too) to windows, and it just looks at the MBR (linux looks at one of the superblocks, correct?)

So in that case, if the (cause I was getting the error "file not here" even on attempted deletion) MBR doesn't say the folder is there then it can't copy over I guess.

but the files are there still...idk..


But linux avoided the whole thing and still copied it over, which is strange to me.

---

### Post by jbrown96 on 2009-07-16
Is it a permission problem? In Windows, right click on a folder and go to properties; make sure you are allowed to copy the files. 

I've never had any problems transferring from Linux to Windows using NTFS. If they are music files, they are probably well under the 4GB/file limit, so you could also try FAT32.

---

### Post by Elep.Repu on 2009-07-16
> **jbrown96 said:**
> Is it a permission problem? In Windows, right click on a folder and go to properties; make sure you are allowed to copy the files. 

I've never had any problems transferring from Linux to Windows using NTFS. If they are music files, they are probably well under the 4GB/file limit, so you could also try FAT32.

It wasn't a permission problem. In windows I am administrator, I checked the permissions though.
It's the folder that reports itself as 0 bytes, regardless of having files in it that's the problem.
I'm moving them over right now in linux, but I'm still baffled this happened. And wondering why it works in linux but not in windows. >.>

---

### Post by fabioxxxx on 2009-08-24
Same problem here, all the folders in the ntfs partition are ok, just one that does not work under windows.

When i try enter the folder : this message is displayed.
"E:\folder not accessible."
"access denied" 
And show 0 bytes in windows properties. in linux i dont have problems with this particular folder.

I tried chmod 777 -R in the folder in the partition but still can get this single folder to work.

I have only installers of programs for windows  in the folder, cold be a virus ? cant scan the folder as well...

---

### Post by zeroseven0183 on 2009-08-25
Probably, a virus is causing it. Try moving the files (using Linux) from that folder to a new folder.
Then see if the contents are accessible in Windows. Or you might want to try accessing it on Safe Mode.

---

### Post by Elep.Repu on 2009-08-26
> **zeroseven0183 said:**
> Probably, a virus is causing it. Try moving the files (using Linux) from that folder to a new folder.
Then see if the contents are accessible in Windows. Or you might want to try accessing it on Safe Mode.

This happened a while ago, 
There was no virus. Files within my library were visible but couldn't be copied around. Full windows, not hacked.
The problem was never fixed. The only way I could copy them anywhere without moving out of the affected folders was within linux.

---

