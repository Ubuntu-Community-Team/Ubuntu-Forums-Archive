---
title: "Is it possible to use both nfs and samba together?"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by Unewbeginner on 2011-01-13
I have a network with about 100 clients. They are with different OS. Some of them only run Ubuntu, Windows 7 or Apple OS X. Some of them might have two systems and they need to switch between the systems occasionally. I searched on the web and found that NFS is better than samba in the case to share folders among all unix-only machines. Is this true? If so, how could I setup the network to untilize the NFS advantage for those unix-only machines?

---

### Post by papibe on 2011-01-13
It is very possible to share even the same folder using both nfs and samba. As for which one is "better" it may be end up in a debate. In my experience nfs is around 30% faster while copying files. 

There's a no-cost [Micorsoft nfs add-on]("http://www.microsoft.com/downloads/en/details.aspx?FamilyID=dc03485b-629b-49a6-b5ef-18617d1a9804&displaylang=en"), but only available for some Windows 7 versions (I believe professional and up).

To get started with nfs read [this]("https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html").

I hope it helps.

---

### Post by Unewbeginner on 2011-01-13
Thanks Papibe for your fast reply. For the Microsoft nfs add-on, do you mean in my case(All Microsoft OS are windows 7) I could use NFS for all machines? If so, that would help me a lot.

---

### Post by papibe on 2011-01-13
Which version of Windows 7 are using your clients? It seems that the Microsoft add-onn in only available for enterprise and up:

From the previous link:
> Supported Operating Systems:Windows 7 Enterprise;Windows 7 Ultimate;Windows 7 Ultimate 64-bit;Windows Server 2008 R2
Regards.

---

