---
title: "How do i install antivirus software?"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by taylor8 on 2009-03-04
Hi everyone. Totally new to this Ubuntu thing but so far am enjoying it. I had heard that Ubuntu was safe from virus attacks etc. but advised to get some antivirus anyway just to be safe. So i downloaded Avast for free but i haven't got a clue how to install it. I double click on it as i would in Windows but it opens some Archive prog and then displays an error message with the following:

End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/ian/Desktop/setupeng.exe or
          /home/ian/Desktop/setupeng.exe.zip, and cannot find /home/ian/Desktop/setupeng.exe.ZIP, period

Can someone please point me in the right direction. Massive thanks in advance to all.

---

### Post by kanikilu on 2009-03-04
The debate about anti-virus on *nix aside, it looks like you downloaded the installation for Windows. You want the .deb package from here:

[http://www.avast.com/eng/download-avast-for-linux-edition.html](http://www.avast.com/eng/download-avast-for-linux-edition.html)

---

### Post by mlentink on 2009-03-04
> **taylor8 said:**
> ...I had heard that Ubuntu was safe from virus attacks etc. but advised to get some antivirus anyway just to be safe. So i downloaded Avast for free but i haven't got a clue how to install it. I double click on it as i would in Windows but it opens some Archive prog and then displays an error message with the following:...
zipinfo:  cannot find zipfile directory in one of /home/ian/Desktop/setupeng.exe or
          /home/ian/Desktop/setupeng.exe.zip, and cannot find /home/ian/Desktop/setupeng.exe.ZIP, period


Ehh, where did you download this version of avast from? Did you search for antivirus in the Synaptic Package Manager?

I get the impression that you downloaded a Windows version of avast, which obviously won't work. Search for ClamAV in Add/Remove Programs or Synaptic. 
The antivirus you install, is only for the benefit of Windows-using collegues or relatives. Ubuntu itself will install malware only with your explicit consent.

---

### Post by stchman on 2009-03-04
AV is un-necessary in Linux.

---

### Post by HermanAB on 2009-03-04
Uhmmm...

First note that you do not need to add anything to a default Ubuntu system to protect it.  It is perfectly secure.  Relax and enjoy your new found freedom.

If you would modify Ubuntu and install a mail or file server and provide services to other Windows machines, then you should consider adding some programs to protect the Windows machines against themselves.  That is what Linux anti-virus programs do.

Now as for that program you downloaded, Linux cannot run Windows programs.  At least not without jumping through a large number of hoops.

Cheers,

Herman

---

### Post by taylor8 on 2009-03-04
To kanikilu;
Used the link and it worked perfectly so thanks very much my friend. And thanks to the other guys

---

