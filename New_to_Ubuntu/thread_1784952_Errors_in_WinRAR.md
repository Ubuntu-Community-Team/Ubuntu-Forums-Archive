---
title: "Errors in WinRAR"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by Coffeh! on 2011-06-17
Whenever I try to extract files in WinRAR, it gives me this error: "The program WinRAR.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience." than it goes on to say something about program deficiency's." I installed winRAR through the Synaptic Package Manager. Any help would be appreciated (i have 11.04) thanks.

---

### Post by DirtyPC on 2011-06-17
Use 7-zip instead. Found in software center.

---

### Post by ruffEdgz on 2011-06-17
> **harrylucas1 said:**
> Use 7-zip instead. Found in software center.

I like 7zip as well but I also installed both 'rar' and 'unrar-free' from the repo as well which work for me:
```

apt-get install rar unrar-free

```

---

### Post by DirtyPC on 2011-06-17
I don't like having lots of separates. I like just having one that does it all, but thats just my bean :D

---

### Post by mister_playboy on 2011-06-17
The only way to run WinRAR on Linux is through Wine... it's not available from the Software Center or Synaptic.

On Linux we just have access to the command line tools.  You can install unrar from the Software Center if you only need to extract .RARs... it will automatically work with File-Roller.

The rar package that allows creation of RARs requires a WinRAR/RAR license.

---

### Post by User3k on 2011-06-17
All you need to do is right click the file and extract. You won't need to open 7zip, unrar, etc separately. As long as they are installed that is all that is needed.

---

### Post by DirtyPC on 2011-06-17
> **User3k said:**
> All you need to do is right click the file and extract. You won't need to open 7zip, unrar, etc separately. As long as they are installed that is all that is needed.
I'm pretty sure you can right click with 7z?

---

### Post by goldshirt9 on 2011-06-17
> **harrylucas1 said:**
> I'm pretty sure you can right click with 7z?
you can i use it in linux and windoze 7 

nice bit of kit :p

---

### Post by User3k on 2011-06-17
> **harrylucas1 said:**
> I'm pretty sure you can right click with 7z?

I have unrar and 7zip installed. When I have a file that needs to be extracted all I do is right click and click "extract." I don't have to open and specific program.

---

### Post by Coffeh! on 2011-06-17
Hmm, I'm running WinRAR through wine currently. The extract works, but some files are connected to others, and it prompts me to enter the disk with the necessary data to continue. (I have all the files, i just can't extract the ones that are connected.)

---

### Post by mister_playboy on 2011-06-17
> **Coffeh! said:**
> Hmm, I'm running WinRAR through wine currently. The extract works, but some files are connected to others, and it prompts me to enter the disk with the necessary data to continue. (I have all the files, i just can't extract the ones that are connected.)

Are the files properly named?  x.rar.001, x.rar.002, etc.

Have you tried extracting with File-Roller? (i.e. right-click the file in Nautilus and extract)

---

### Post by Coffeh! on 2011-06-17
The files are properly named. When I do alt+F2 and type in file-roller, I get something called archive manager. It doesn't do anything... =/

---

### Post by jtarin on 2011-06-17
Post the names of the files that need extraction including their file extension if any.

---

### Post by Coffeh! on 2011-06-19
I got it figured out, was entering in the wrong file name (I felt stupid) for the extension. Thanks for helping a first time ubuntu user =).

---

### Post by jtarin on 2011-06-19
Great no problem we get confused compressed filers here all the time.:p 
Mark this thread solved if you will.

---

