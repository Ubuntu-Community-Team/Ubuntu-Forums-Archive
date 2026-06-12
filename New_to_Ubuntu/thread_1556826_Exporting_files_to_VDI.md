---
title: "Exporting files to VDI"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by BomWatchOut on 2010-08-20
Hi,

New member asking maybe a noob question? :p

is it possible to export/compress/convert files or folders into VDI format to be later used in VirtualBox? i Have a triple boot system and want to use those folders in a virtual machine so that i only have to boot into Ubuntu. If i am able to do that then i won't need the triple boot... (which is what i want)

thanks in advance...

---

### Post by jonnywombat on 2010-08-22
Hi there...

What you need to do is install guest additions into your virtual box.

Now in ubuntu create a folder into which you are going to use to share things between ubuntu and virtualbox.

Once you have this done fire up virtual box again, and start your virtual machine.

Click on devices and then shared folders. 

On the window that opens click the top icon on the right marked add a new folder then in the dialogue box select other on the drop down menu and then navigate your way to the shared folder you created before. Select the make permanent option, and then click ok

Once you have done that you can map your "drive" so it appears in my computer automatically.

To do this in your virtual machine click on My Computer, the from the menu bar select tools and map network drive.

In the dialouge box select a letter for your drive, and then click on browse then navigate to virtual box shared folders.

Click ok and then finish.

Hth

---

