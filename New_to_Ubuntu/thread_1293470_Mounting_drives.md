---
title: "Mounting drives"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by impatientboi on 2009-10-17
sorry i meant MOUNTING. couldnt help myself but a couple of questions   when i set up a dual boot on my machine the existing xp installation was already partitioned 80g and i couldn't change that.  i set aside 30g to play around with on ubuntu and the remaining 50g is a partition in the windows file format so i won't be using it, but it appears as media. I think I can mount the two so they appear as one, thus removing clutter (I'm using UNR. . .) what do i need to punch into the command line to mount them? I think i need  to use the /dev3 or something like that??  UNZIPPING i've found installing easy through the built in interface, and i've used apt-get install but i have downloaded a tar.gz file and i've tried to use the archive manager but i've only managed to extract the folder to the same directory the tar.gz file is in (in my case the desktop). Being a tar.gz file does that mean i can only extract the folder and then locate the executable to run the program and 'create a link' in the main menu? Or Can i use the command line to automate and have it just appear like when you use apt-get install or the  package manager?   CHANGING POSITIONS speaking of the command how do i navigate my way very basically like in dos change director cd/ can anybody link to a good resource?

---

### Post by Paqman on 2009-10-17
First of all, using some punctuation and paragraphs will make your posts a lot easier to read in future.

> **impatientboi said:**
> I think I can mount the two so they appear as one, thus removing clutter (I'm using UNR. . .) what do i need to punch into the command line to mount them?


You can mount them by simply clicking on them. If you want to have them mount permanently you can install ntfs-config to set that up. I'm not sure that you can mount two partitions as one file, sorry.

> 
i have downloaded a tar.gz file


Tar.gz is just an archive file, like the Windows .zip. It could contain literally anything. If it's an app you're trying to install, there's probably an easier way. What is it you're trying to install?

> how do i navigate my way very basically like in dos change director cd/ can anybody link to a good resource?

Exactly the same: cd. 

[Command line basics]("http://www.itk.ntnu.no/ansatte/Hendseth_Sverre/bash/basics.html")

---

