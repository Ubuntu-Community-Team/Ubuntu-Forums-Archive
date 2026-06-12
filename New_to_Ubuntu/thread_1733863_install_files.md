---
title: "install files"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by weezyrider on 2011-04-19
I am trying to install ESET AV. I've got to the point where there is a package icon sitting on the desktop and it has a lock on it.
If i right click it says its installing by getdeb or software center. Trouble is, it isn't installing. Another right click said extract here, now i have a folder on the desktop with the extracted bits and pieces I have no idea what to do with. 
It was installed, but I had to delete and download a new version and now I can't reinstall it. What else do I do?

If there is anyone in the CS, CO area please message me. Thanks

---

### Post by ttshivers on 2011-04-19
What is the file extension on the file that you downloaded? Ex. .deb, .rpm?

---

### Post by weezyrider on 2011-04-19
> **ttshivers said:**
> What is the file extension on the file that you downloaded? Ex. .deb, .rpm?

 The original download came in as esets.amd64.deb.bin I messed around with some commands I found in another post here and by using apt-get got it to open - mostly the Eula and TOS. 

Then something about install (y/n) typed in Y. Got some gibberish about not finding the file.  Looked at the stuff in terminal again something like -i dpkg esets-3.0.22.amd64.deb.  That is the name of the package type icon on the desktop that has a lock symbol on it. esets-3.0.22.amd64.deb. It simply won't install. 

I did see some remarks in terminal about destination, but none of the advice in the forums or books says anything about any destination of what goes where. They just say use package installer or apt-get.  A right click on the package said to extract here. So now I have the extract folder on the desktop and no program running in the system.  

Thanks,  W

---

### Post by K_45 on 2011-04-19
You don't need any AV on Linux, unless you share files with windows, and even then it depends on the type of files.

---

### Post by mörgæs on 2011-04-19
You need to post your exact commands and the exact error messages, if anyone should be able to help you.

But as posted above: Are you sure that you need antivirus?

---

### Post by weezyrider on 2011-04-20
Yes, I need an antivirus. I download for 2 offline XP boxes. 1 runs special software that has had a hard enough time with upgrades to Vista and now 7. It is only made for windows, there is no linux equivalent and it won't run under wine. So Ubuntu has to check files.

And the AV has also caught files that were not infected but caused problems. 

Some of you sound like IT specialists. I had one of the first programmable sewing machines, went to a tech and his question was "you want to do what with what? He got the program running and kept coming over to check as he didn't believe you could do this with a sewing machine. It's a fairly large business, but specialized. So I download updates and certain files from the sites. Some of the updates are exe files and I'd rather be safe than sorry.

---

### Post by weezyrider on 2011-04-20
I followed half of these instructions. Ignored stuff about fonts. 
[http://ubuntuforums.org/showthread.php?t=1086653&highlight=installing+bin+files](http://ubuntuforums.org/showthread.php?t=1086653&highlight=installing+bin+files)

Got to desktop, and then used apt-get.

---

### Post by weezyrider on 2011-04-20
Install says eset is installed, software center says eset is installed. It isn't running so I suspect it should be somewhere else besides the desktop.
 Trying to attach pics. Both are sitting on the desktop

---

