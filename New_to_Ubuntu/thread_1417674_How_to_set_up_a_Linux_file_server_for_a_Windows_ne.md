---
title: "How to set up a Linux file server for a Windows network?"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by todbr on 2010-02-27
Hi folks, I have a newbie question that I'm sure there's a how-to for it somewhere, but I couldn't find exactly what I wanted. In sum, I need to set up a Linux file server for a Windows network to bypass Windows' 10 concurrent connections limit. 

Now the long story. I'm a system administrator of a Windows network in a small enterprise (about 20 machines). Things have been runnning well with a Ubuntu virtualized on top of a Windows server, but now the server machine must be upgraded for performance reasons and I'd like to mantain the same setup.

I am expert with Windows, but totally newbie with Linux. So, things I will have to deal with:
1. Install Ubuntu Server inside VMWare on top of a Windows Server 2008 machine (have to check if it's 64-bit).
2. Make file sharing work from the Windows host to the Linux guest
3. Share files from Linux guest to the network (Samba, right?)
4. Configure user permissions (some shares must be accessible only by some users)
5. All that preferably on terminal, for performance. I'm comfortable dealing with CLI, I just need to know the commands.

No Active Directory (it's a workgroup), no print server, no web server, just that. Shouldn't be too hard.

Any help appreciated - maybe a link to the relevant how-to. Thanks.

---

### Post by bumanie on 2010-02-27
Suggest you follow the official [samba tutorial]("http://www.samba.org/samba/what_is_samba.html") and then post back if with specific issues if something is not going to plan.

---

### Post by todbr on 2010-03-02
Ok, will try, but can I install Ubuntu normally, with GUI, and then when finished configuring everything just "turn off" the GUI and remain with CLI, for performance? How to do it?

---

