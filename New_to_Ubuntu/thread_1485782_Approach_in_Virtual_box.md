---
title: "Approach in Virtual box"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by Vege 4wd on 2010-05-17
Hi all I have a bit of an obscure problem I'm hoping you can help me with.:confused:

I am new to Ubuntu. (Lucid). Love it. My main data base is with approach. After much searching of forum I found the best way to use Lotus Approach and Organiser is by using Virtual box. Loaded with no problems at all. Lotus Approach and organise also installed with no problem on an xp guest machine. I burnt my database onto a disc but I can not open it Approach. It does not seem to be able to detect it. The Organise files work well. 

Anyone had this problem?? or know a work around?

Thanks in advance.

---

### Post by lkraemer on 2010-05-17
Run VirtualBox, Click on STORAGE.  Under your controller type click on
the DVD/CDR Drive in the AREA titled Storage Tree.  Then look to the right
under ATTRIBUTES, and to CD/DVD Device.  Click on the Pulldown Arrow.
See if Guest Additions is selected or if the DVD/CD Drive is selected.
Select the DVD/CD Drive and then check PASSTHROUGH, then OK.

Now START Windows and after it is up and running insert your DVD/CD in
the drive and see if you can access it.  It should work to copy your data.

One other option you have is to create a SHARED Folder for WinDOUGH's.
Just make a subdirectory in /home/user named Windows_XP_Shared.
Put your Data there in a Folder named Data.  

Run VirtualBox again and scroll down to Shared Folders.  In the Folders
List Window look to the right to find ACCESS, then to the right to find
the + and click on it, and browse for the Folder you just created.
Then click OK.

Start XP, and when it is all booted, click on My Network Places,
Entire Network, VirtualBox Shared Folders, vboxsvr, vboxsvr\Windows_XP_Shared 
and select your subdirectory/folder to copy.
Bi-Directional......

The manual explains this well.......might be a benefit to download
the PDF and give it a quick read......

lk

---

### Post by Vege 4wd on 2010-05-18
My problem is a little different. I have a shared folder and have no problems opening anything in accept Approach files.:confused::confused:

---

### Post by Paresh on 2010-05-18
If you can read anything else, it sounds like there may be a problem with the Approach file itself. I don't know much about Approach files, but at least you can eliminate a corrupt file if you can read it back on the original (non-ubuntu) machine?

---

### Post by Vege 4wd on 2010-05-18
Hi yes, it was a problem with Approach. I put the files with .APR ext in shared box but apparently it need .PBR or similiar ext as well. Copied to share folder and it opened straight away.

---

