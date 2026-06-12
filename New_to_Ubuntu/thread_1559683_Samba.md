---
title: "Samba"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by gavdari on 2010-08-23
I have a Windows 7 pc which I want to share files with using my Ubuntu laptop. I did a quick search and I found something called Samba. But there is a few problems with that:
1. From what I've found, Samba is mainly command based and there are a few GUI interfaces available. Which one do you suggest for an absolute network newbie who just needs a simple file and printer sharing?
2. The version available in synaptic is Samba 4 which is considered experimental and the last stable version is 3.5.4 available in tarball by their official website. Is there any .deb package available? should I just install it from source using ./configure, make, make install?

---

### Post by erilidon on 2010-08-23
If you are wanting to share files off of ubuntu to another computer all you have to do is right right click on the folder and goto "sharing options" set it up and it will auto configure samba.

If you need to change the workgorup i believe the file to edit is smb.conf - not sure of that though.

Shouldn't be any harder than that.

---

### Post by gavdari on 2010-08-23
I did that. But I got the following error:
You need to install the Windows networks sharing service in order to share your folders.
When I click Install Serivce I get the following:
Sharing service installation has failed. Would you like to retry the installation?
Retrying does not solve the problem.

---

### Post by spcwingo on 2010-08-23
The "Windows networks sharing service" it's talking about is Samba.  ;)

---

### Post by gavdari on 2010-08-24
> **spcwingo said:**
> The "Windows networks sharing service" it's talking about is Samba.  ;)

ok then, back to my first question: which GUI and which version?

---

### Post by sptrsn on 2010-08-24
I followed this tutorial and it worked great for me. Using W7 and several versions of Ubuntu. 
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)

I don't think you can get there completely with gui. But you only have to set this up once. After that it's all gui based drag/drop going both ways.

---

### Post by spcwingo on 2010-08-24
> **gavdari said:**
> ok then, back to my first question: which GUI and which version?

1) GUI = Nautilus (the default file manager)
2) which version = the one in the repositories

To install samba just open a terminal:

Applications>Accessories>Terminal

and input this command:

```
sudo apt-get install -y samba
```

You might also need the Samba File System protocol...to install it issue this command in a terminal:

```
sudo apt-get install -y smbfs
```

---

### Post by vlamnire on 2010-08-24
I recently over came that problem and I found a video that perfectly explains it: [http://www.youtube.com/watch?v=89hjWOb8qmY](http://www.youtube.com/watch?v=89hjWOb8qmY)

---

