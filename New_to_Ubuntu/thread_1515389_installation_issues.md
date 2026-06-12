---
title: "installation issues"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by FNDII on 2010-06-22
I am having problems getting Ubuntu to install. When I restart the computer it reads the CD and brings up the main "try or install" menu. When i select either of these I get an error

"unable to find medium containing a live file system"

---

### Post by ThesaurusRex on 2010-06-22
Since the computer did recognize that you had an Ubuntu CD, it sounds like the live CD might not have burned correctly. Possible corruption. I suggest burning another and trying again.

---

### Post by FNDII on 2010-06-22
I dont think thats the case. I just used the CD to install Ubuntu on my other computer and it worked fine.

---

### Post by FNDII on 2010-06-22
Noticed you can hit esc to see whats going on during the install

So before I get the
"unable to find medium containing a live file system"

I get about 50 of these
"mount:mounting /dev/sr0 on cdrom fail invalid argument"

---

### Post by FNDII on 2010-06-22
I did a bit of searching and found only one other instance of this error. They said that they did not know what was wrong but bypassed it by installing from a usb stick. I don't have one of those. Limited ubuntu skills of mine lead me to think its a CD ROM issue. Not sure how to troubleshoot the issue though.

---

### Post by FNDII on 2010-06-23
I tried switching out CD roms drives and still get the same error. Nnot sure what could be preventing me from the instalation at this point

used the CD to install on 2 different computers

took those cd drives out and tried them in this computer. install failed

---

### Post by Zeike on 2010-06-23
Please do not double (quadruple) post.

I suggest you check the integrity of the cd just to be safe.  For information on how to do this see: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)



EDIT: I've done some looking and it seems this problem might be caused by a video card for some reason.  What video card do you have?  If you are using a PCI card try temporarily unplugging it during installation (that is, if you have an onboard one as well).

---

### Post by FNDII on 2010-06-23
so i removed the card (geforce 8500gt) and got the same error on installation issues. not sure what else to try 

used 2 different ubuntu cd's that have worked on other computer installs

tried 2 different cd rom drives 

tried the installation with and without the video card

and I always get error
mount:mounting /dev/sr0 on cdrom fail invalid argument


A new error that i see
(process: 262): Glib warning** : getpwid_r():failed due to unknown user id

---

### Post by pxr on 2010-06-24
My best guess would be your motherboard BIOS is telling, or not telling, the CDROM to emulate/not emulate something.

I'd have a look in the BIOS and see if there was a setting on the CDROM you can change.

---

