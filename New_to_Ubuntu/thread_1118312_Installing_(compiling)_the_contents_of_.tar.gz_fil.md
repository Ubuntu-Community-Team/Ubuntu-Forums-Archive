---
title: "Installing (compiling?) the contents of .tar.gz files?"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by jamesclish on 2009-04-06
Hi all!

I downloaded a theme for Ubuntu that came in a .tar.gz archive. I extracted the folder with no problems to my desktop. With a little bit of reading, I gather that I have to compile the contents of this folder?

I've tried lots of things, including cding to the directory and typing ./configure . (This seems to be the most common suggestion in the forums.) This just produces an error:

```
bash: ./configure: No such file or directory
```

Thanks in advance!

-James

---

### Post by batharoy on 2009-04-06
Themes dont need compiling.
Open up Appearance Preferences 
System>Preferences>Appearance

Then use the install button or Drag&Drop

---

### Post by oldos2er on 2009-04-06
A theme shouldn't need to be compiled; to install it you would just drag and drop it (as a tar.gz) into the Theme tab of System, Preferences, Appearance.

 If it's a theme engine, it's a different story. Can you tell us the name of the file, and where you downloaded it from?

---

### Post by snova on 2009-04-06
> **jamesclish said:**
> I downloaded a theme for Ubuntu that came in a .tar.gz archive. I extracted the folder with no problems to my desktop. With a little bit of reading, I gather that I have to compile the contents of this folder?

Often, but not always. What are the contents of the archive?

Also, I believe that some archives can be dragged onto the Themes window to install, or try the Install button from Appearance Settings.

---

### Post by pissedoffdude on 2009-04-06
Can you post a link to the theme you downloaded.  Also, check the extracted files for .sh extensions.  If you find something like autogen.sh, you should execute it by doing: ```
./autogen.sh

``` and then you'd run your normal ```
make
sudo make install
```

---

### Post by jamesclish on 2009-04-06
Thanks guys. Just a drag and drop job.

Have a good day!

---

### Post by qwertyuiop96 on 2009-04-06
Go to system>pref>appearance>install>chose your file>install(ok).  A box should come up asking if you would like to switch... hit yes.  You are ready to explore the wonders of ubuntu themes!;)

---

