---
title: "can't make a CD software file executable"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by al.adab on 2010-08-15
hello,

I need to install Pentax software (photo management of raw files). This is DOS/Windows executable (application/x-ms-dos-executable) stuff on a CD. I previously installed it (Ubuntu 9.04) through Wine no problem. Now (on 10.04) I can't. 

I initially get the following message:  

*The file '/media/S-SW74/Setup.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.*

If I right-click on the Setup-exe icon, go to Properties/Permissions, and try to make it executable, I get the following message: 

[I]The permission could not be changed. 
Sorry, could not change the permissions of "Setup.exe": Error setting permissions: Read-only file system[/I]

If I try to change from "Read-only" to "Read and write" (owner and group access) I get the same error message. 

What should I do? I kind of recall using a *chmod* command in terminal ages ago, but can't figure out how to do it. If I copy the content of the CD onto my hard disk I can make the file executable no problem, I know, but I'd like to avoid having to do that...

thanks

---

### Post by arochester on 2010-08-15
Have you tried the native Linux application called Rawstudio? It's in the Repositories. The website is [http://rawstudio.org/](http://rawstudio.org/)

---

### Post by al.adab on 2010-08-15
thanks arochester, I've just downloaded and tried it out...I'm shooting in JPEG monochrome (tried to shoot in RAW but it turns out to be too time consuming). I can get Rawstudio open JPEG files but not to restore information on colours in the photo...(but this is not the place to discuss this, I know!)

---

### Post by oldfred on 2010-08-15
Have you copied file into wine? ~/.wine/drive_c/Program Files

You cannot change settings on the CD, it is read only. But after you copy it into wine if it still is not executable you can change it.

---

### Post by al.adab on 2010-08-15
yes I did copy it into wine + installed it. Need to create a new post, though, as I get a wine program error (probably a bug).

---

