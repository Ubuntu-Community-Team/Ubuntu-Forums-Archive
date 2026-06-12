---
title: "Nautilus Copy/Paste"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by desaivarun_104lts on 2011-03-01
Hi,

I am new guy to ubuntu.My problem is i am uanble to copy/paste any file from one folder to another folder.The same problem occurs when i insert an USB also.

If i enter this command in the terminal gksudo nautilus,i can do copy/paste either in usb or normal also.I dont know why i am unable to do copy/paste without using the command.Is there any way to do the copy/paste without using the command every time.When i use the command gksudo nautilus,my wallpaper also changes.

Note: Please,excuseme,if any spelling mistakes are there,and if this is the not thread for this type of quetions.

Waiting for the reply.

---

### Post by vivek.pandey on 2011-03-01
what error message do you get while copying?

---

### Post by nomko on 2011-03-01
Just tell us forst ffrom which file you want to copy/move files from.
As a "regular" user you don't have permissions in every folder.

---

### Post by desaivarun_104lts on 2011-03-01
> **neo_aryan said:**
> what error message do you get while copying?
when i select any folder to copy,it will be copied,when i try to paste it in any other folder,the paste option will  not be there..i tried to copy a folder called keucr from my Downloads folder to usr/src and to paste the folder there.but i am unable to do it.

When i am using USB also,two folders will open,one is USB0 and the other is New Volume,USB0 will open,if i want to copy any folder from the USB0,i cant do that.

---

### Post by vivek.pandey on 2011-03-01
> **desaivarun_104lts said:**
> when i select any folder to copy,it will be copied,when i try to paste it in any other folder,the paste option will  not be there..i tried to copy a folder called keucr from my Downloads folder to usr/src and to paste the folder there.but i am unable to do it.


you mean you tried to copy it in your usr/src ie the file system. obviously you cant do that
.you cant copy anything in your filesystem unless you are root user

---

### Post by desaivarun_104lts on 2011-03-10
> **neo_aryan said:**
> you mean you tried to copy it in your usr/src ie the file system. obviously you cant do that
.you cant copy anything in your filesystem unless you are root user
Hi,

The Problem is solved,just i removed an application called "usbmount" from the software center..It is the one which is not allowing me to do copy/paste,everytime when i insert an usb,without typing gksudo nautilus in terminal,i am unable to do copy/paste things.

After removing usbmount,i can do it now.

Thank you for your time :-)

---

### Post by vivek.pandey on 2011-03-10
so you mean to say you  copied a folder called keucr from my Downloads folder to usr/src and  pasted the folder there.??

---

### Post by desaivarun_104lts on 2011-03-10
> **neo_aryan said:**
> so you mean to say you  copied a folder called keucr from my Downloads folder to usr/src and  pasted the folder there.??
No,i am succesfull in copying the folders from my home folder to USB,few days back i am unable to do that, every time i have to open the terminal,and i have to give root permission,and i can do copy/paste things,which is a difficult one..

---

### Post by vivek.pandey on 2011-03-10
> **desaivarun_104lts said:**
> No,i am succesfull in copying the folders from my home folder to USB,few days back i am unable to do that, every time i have to open the terminal,and i have to give root permission,and i can do copy/paste things,which is a difficult one..

k thats fine .. but the example you gave  involved the /usr/src
so i thought that....
anyways congrats for your solution .that looks a good one. i ll keep a copy of it .it may be help to me if ever i get into same trouble ;-)

---

