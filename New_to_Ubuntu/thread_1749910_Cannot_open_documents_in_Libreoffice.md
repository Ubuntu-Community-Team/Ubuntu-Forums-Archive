---
title: "Cannot open documents in Libreoffice"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by hannaman on 2011-05-05
I cannot seem to open saved documents in Libreoffice writer on Ubuntu 11.04.  I've tried opening documents that have been saved in several formats such as .odt and .doc and none work.  I cannot even open a document that I created in the same version of Libreoffice two days before.  In all cases Libreoffice seems to hang once I select a document from the Open dialog and I have to kill the soffice.bin process.  I have tried restarting both Libreoffice and my computer, deleting the .libreoffice directory, and even reinstalling Libreoffice but nothing has helped.  If I try open a document from a terminal such as:
```
$ libreoffice /path/to/document.doc
```
Libreoffice just hangs at the splash screen and no errors are produced.
Any ideas?

---

### Post by wilee-nilee on 2011-05-05
> **hannaman said:**
> I cannot seem to open saved documents in Libreoffice writer on Ubuntu 11.04.  I've tried opening documents that have been saved in several formats such as .odt and .doc and none work.  I cannot even open a document that I created in the same version of Libreoffice two days before.  In all cases Libreoffice seems to hang once I select a document from the Open dialog and I have to kill the soffice.bin process.  I have tried restarting both Libreoffice and my computer, deleting the .libreoffice directory, and even reinstalling Libreoffice but nothing has helped.  If I try open a document from a terminal such as:
```
$ libreoffice /path/to/document.doc
```
Libreoffice just hangs at the splash screen and no errors are produced.
Any ideas?

I just got a update in libreoffice check if your updated.

You can also install abiword for now to get a word processor immediately. Abiword actually has some advantages you can copy and paste without the formatting attached. Like if you have a text set filled with other code.

---

### Post by jtarin on 2011-05-05
Are you using Sun Java or one of the open source java's?

---

### Post by Mario ROGER on 2011-05-05
Hello

I had some similar behaviour with openOffice some times ago

I propose following test

[LIST=1]
[*]Start an xterm
[*]Check you have no libre office process running ( *ps -aef | grep libre* ) and kill it (them) when exists ( *kill -9 xxxx* )
[*]move ** .java** directory (example *mv .java java_sav* )
[*]move** .libreoffice** directory (example *mv .libreoffice libreoffice_sav* )
[*]Start LibreOffice (* libreoffic*e* &* )
[/LIST]

Is this solution running ?

Hope this help : TuxMario

---

### Post by hannaman on 2011-05-05
@jtarin
I am sure I am using the SUN Java as, I believe, that is installed with the restricted extras package.
@Mario ROGER
Thanks for the advice.  I will try that when I get home tonight and report if it works or not.

I did not realize Libreoffice was so dependent on Java.
Thanks.

---

### Post by hannaman on 2011-05-05
Some more information.  On a brand new install of Ubuntu 11.04, I still cannot open my documents with Libreoffice.
Here's the wrinkle that I have discovered, though.  My documents are on a NAS mounted via NFS.  If I copy the documents to my local drive, Libreoffice works as expected.  If I try to access them from the NFS mount, I get the same results as described above.
No other programs seem to have any problems accessing data from this NFS mount, including Banshee, VLC, and Evince, so there doesn't seem to be a permissions problem.  I went so far as to install Abiword, which opened my documents from the NFS mount with no issues.  It just seems to be a problem with Libreoffice.
Any more ideas?

Thanks

---

### Post by Mario ROGER on 2011-05-07
Hello

So the issue is linked to NFS associated to LibreOffice.

I read some french thread about similar issue and the solution seems linked to NFS.

Libreoffice seems to add some locking info to opened files and this needs an NFS service managed by **lockd** deamon on NFS server

The french user changed the NFS server version. He switched from "NFS user space release" to "kernel release" then lockd deamon was available and everythings worked perfectly

Bye : Mario
NB : I have no NFS at home so I can't make the test

---

### Post by hannaman on 2011-05-07
Thanks for the updated info.  Since I am using a commercial NAS, I am at their mercy when it comes to NFS version.
I have found a potential workaround, however.  This post [http://ubuntuforums.org/showthread.php?t=1645957](http://ubuntuforums.org/showthread.php?t=1645957) got me looking at the soffice script.  I took a little more radical approach than that poster however and removed the script, then created a link to soffice.bin.  So far LibreOffice is behaving as I would expect.  At least I have a place to look if it acts up in the future.  I guess this can be marked solved.

---

