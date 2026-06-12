---
title: "Backup Windows to Instal Ubuntu"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by PKcin on 2011-07-16
Hi,

I currently have a Dell latop running Windows Vista. It has been running slower and slower the hard drive is full and I use my mac most of the time because windows is annoying. As a result of this i decided that it was time i upgraded it to Ubuntu. Im am new at this and am nervous about wiping windows off my computer. I would like to backup my entire hard drive to an external one so that i will be the same as before if i decide to switch back. If I decide to create an image of it do i have access to specific files on it? If not should i create a seperate back up of the files i want to use on Ubuntu? (music, pictures,videos, software) I do not want to dual boot windows and Ubuntu because my hard drive is already full and the computer is running slow so i just want to start anew.

Thank you

---

### Post by amjjawad on 2011-07-16
> **PKcin said:**
> Hi,

I currently have a Dell latop running Windows Vista. It has been running slower and slower the hard drive is full and I use my mac most of the time because windows is annoying. As a result of this i decided that it was time i upgraded it to Ubuntu. Im am new at this and am nervous about wiping windows off my computer. I would like to backup my entire hard drive to an external one so that i will be the same as before if i decide to switch back. If I decide to create an image of it do i have access to specific files on it? If not should i create a seperate back up of the files i want to use on Ubuntu? (music, pictures,videos, software) I do not want to dual boot windows and Ubuntu because my hard drive is already full and the computer is running slow so i just want to start anew.

Thank you

Hello and Welcome :)

In case you'll create an image then you will NOT be able to access specific file(s).
The better way in your case is to have an external HDD which is equal in size of your internal HDD or more and just COPY your important files without copying System Files and Installed Programs.

After you're done with copying your data, format your HDD and install Ubuntu. Don't forget to TRY Ubuntu from the LiveCD or LiveUSB before installing to make sure everything will work just fine.

After installation, plug your external HDD and copy your files back to your HDD or just access whatever you need.

As simple as that :)

---

### Post by PKcin on 2011-07-16
Thanks for your very quick response.

I am currently creating a clone of my hard drive with software i found online. Im assuming that this way i will be able to access my personal files while also having the system files to run windows? If this is true i should be able to access the files i need AND have all the files required to reset my computer to its original setting..correct?

---

### Post by amjjawad on 2011-07-16
> **PKcin said:**
> Thanks for your very quick response.

I am currently creating a clone of my hard drive with software i found online. Im assuming that this way i will be able to access my personal files while also having the system files to run windows? If this is true i should be able to access the files i need AND have all the files required to reset my computer to its original setting..correct?

If that Software will create a compressed image file which can be restored later using the same software then it's not a good idea specially you want to format and get rid of Windows.

Vista is what you have right? when you go to your C Drive, there is a Folder called Users. ALL your personal Data should be stored there. Copy that folder to an external HDD. Check Drive C (or other drives if you have) whether there is any important folder/file you may need later. Copy that/these file(s) as well.

Clone Programs are useful if you're using the same OS.

---

### Post by PKcin on 2011-07-16
Ok thanks

Ill do both to make sure :D

---

### Post by amjjawad on 2011-07-16
> **PKcin said:**
> Ok thanks

Ill do both to make sure :D

You welcome and Good Luck with that :)

---

### Post by Jerry N on 2011-07-16
> **PKcin said:**
> If not should i create a seperate back up of the files i want to use on Ubuntu? (music, pictures,videos, software) 

Back on my soapbox:  You shouldn't have to ask whether or not to create a backup of your files.  You should **ALWAYS** have a current backup of your files, unless they are of no importance to you whatsoever. Hard drives do fail, you know.  

OK - off the soapbox.  Clonezilla is an excellent tool for creating an image of your hard drive.

Jerry

---

### Post by dFlyer on 2011-07-16
macrium reflect should be able to clone your vista drive. Here is a link:

[http://www.macrium.com/reflectfree.aspx](http://www.macrium.com/reflectfree.aspx)

---

### Post by Mark Phelps on 2011-07-16
In addition, MR (which can be downloaded for free) also has the ability to allow you to MOUNT the saved backup -- so you can retrieve individual files from it.

As far as I know, the Linux backup tool CloneZilla does NOT allow you to mount the backup images.

---

