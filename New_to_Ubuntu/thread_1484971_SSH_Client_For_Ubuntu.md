---
title: "SSH Client For Ubuntu"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by walkerchuckwalker on 2010-05-16
Are there any SSH Clients I can use for Ubuntu? I need one that is not command line (puttySSH). I have tried to install it using WINE but it won't do it saying:

The file '/home/username/Downloads/winscp427setup.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

Can anybody reccommend a fix to this, a source I can add to the Software Center, or an already available program in the Software Center?

---

### Post by Kobalt on 2010-05-16
If you want to transfer files over SSH, you can do this with the built-in nautilus client "Connect to a server..." 
If you're looking for a connection manager like Putty, then you can try *secpanel* (it's in the repos I think).

---

### Post by _0R10N on 2010-05-16
if your primary task is file transfer, you could try filezilla. If you use to perform other kind of tasks, instead, you should think in getting access via VNC.

---

### Post by onecsguy on 2011-02-04
> **walkerchuckwalker said:**
> Are there any SSH Clients I can use for Ubuntu? I need one that is not command line (puttySSH). I have tried to install it using WINE but it won't do it saying:

The file '/home/username/Downloads/winscp427setup.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

Can anybody reccommend a fix to this, a source I can add to the Software Center, or an already available program in the Software Center?

Looks like no one read your post, Putty should work with WINE, but i think they have a linux version as of now.  Your issue is that linux doesnt like to get Viruses from the internet, to run anything 'executable' you have to explicitly allow the file to execute in the files properties there is a check box to "Allow Executing File as Program"

[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

 Putty for unix has to be built from source, it should work in Linux Im trying it now, I needed SSH terminal access and came across this post.

I wish people would read posts before commenting, it would make message boards and support forums vastly more useful and searchable =\

---

