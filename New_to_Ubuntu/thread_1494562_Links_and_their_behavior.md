---
title: "Links and their behavior"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by TheUnwiseman on 2010-05-27
Hey forum.  So I'm developing a small program with releases in both Linux and Windows environments, but they both use the same source code (just two different executables, naturally).  I'm making it available on SourceForge, and I'm keeping two separate zip/tar.gz files for each platform.  Locally, I have them separated into two folders so that each time I update the code, I can just create an archive out of the folder and upload it to my project page.  But I don't want to have to copy and paste every time I change a file that has a copy of itself in the other folder.  How would I make proper links from the Windows files to the Linux files?  If I do make them links, will they compress properly into an archive, with the actual file they link to in tact?  Thanks in advance for the help.

---

### Post by sanguinoso on 2010-05-27
Are you referring to symbolic links when you say links? Because in that case there is no way I no of to have a symbolic link compress like that. The compression compresses the symbolic link and not the file the link refers to.

---

### Post by TheUnwiseman on 2010-05-27
> **sanguinoso said:**
> Are you referring to symbolic links when you say links?

See, there's the thing--I don't know which kind I'm talking about.  All I want is a file in one folder that stays consistent with the contents of another file in a different folder.

---

### Post by sanguinoso on 2010-05-27
Are you adverse to version control? And when do you want this synchronization to happen? I ask because there are a few ways that came to mind to solve this problem. There is a command called rsync that will synchronize two folders and it will only modify changed files. But this again is similar to copying and pasting. However, like I said you could use a version control system like git to maintain all the files and write a script to create the zips/tar.gzs.

---

### Post by TheUnwiseman on 2010-05-27
I'm very new to version control, so I don't even really know the basics about it.  I'm also unfamiliar with zipping/taring from the command line.

---

### Post by sanguinoso on 2010-05-27
Well very simply you can run 
```
tar czvf myfolder.tar.gz abcfolder/
```
and similarly
```
zip archivefile1 doc1 doc2 doc3
```

So if you had one folder where all your files are under lets call it top and inside the top folder you have win and linux folders. Is that accurate to your setup? You could have a folder that contains all the files that are the same on both platforms, and then leave the platform specific code inside each separate folder. Then when you want to do a build you could use a little script to create platform specific packages. Does that sound like what you want?

---

### Post by TheUnwiseman on 2010-05-27
Yes, sanguinoso, that's exactly what I want!  Thanks a lot!

---

