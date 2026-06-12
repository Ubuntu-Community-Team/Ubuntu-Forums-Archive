---
title: "/media exists but how do I find it?"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by Zo|oZ on 2011-03-28
I am running Ubuntu 10.10 (Moon OS) in a virtual machine on Mac OS X using VirtualBox. VirtualBox allows you to share folders with the host and I am doing this. The folders are mounted in /media.

What confuses me is that I cannot view /media from the Gnome file browser windows. When I am on the command line and type "ls -al /" the folder is not listed either. It is certainly there, in some way, because I can type "cd /media" and that works. I presume that this is standard but I am not accustomed to it. 

I'd like to be able to access /media from the file browser windows.

I'd also like to be able to see a full list of files and directories from the command line.

Would someone give me a pointer?

---

### Post by vanadium on 2011-03-28
First navigate to "File system". This shows the root partition (symbol: /). As the name "/media" indicates already, the folder "media" is straight in the root folder /.

---

### Post by mcduck on 2011-03-28
> **Zo|oZ said:**
> I am running Ubuntu 10.10 (Moon OS) in a virtual machine on Mac OS X using VirtualBox. VirtualBox allows you to share folders with the host and I am doing this. The folders are mounted in /media.

What confuses me is that I cannot view /media from the Gnome file browser windows. When I am on the command line and type "ls -al /" the folder is not listed either. It is certainly there, in some way, because I can type "cd /media" and that works. I presume that this is standard but I am not accustomed to it. 

I'd like to be able to access /media from the file browser windows.

I'd also like to be able to see a full list of files and directories from the command line.

Would someone give me a pointer?
You should probably be asking this in the [MoonOS forums]("http://moonos.org/forum"), while it's *based on* Ubuntu, it's not Ubuntu.

MoonOS has it's own filesystem hierarchy which doesn't follow the standard hierarchy used by Ubuntu and most other Linux distributions.

---

### Post by Zo|oZ on 2011-03-28
thanks McDuck. I didn't realise it was so different. I'll hop over to the Moon OS site and ask there.

---

