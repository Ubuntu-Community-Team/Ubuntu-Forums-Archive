---
title: "3D Kitchen Design Software"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by jamiehendrich on 2009-09-03
Does anyone know a good FREE 3D kitchen design software for Linux where I can drag and drop appliances, cabinets, etc?    I am running Jaunty.  Thank you for any suggestions.

Jamie

PS  A SIMPLE 3D kitchen design software!

---

### Post by zeroseven0183 on 2009-09-03
Sweet Home 3D[U]
[/U][http://www.sweethome3d.eu]("http://www.sweethome3d.eu/")
[URL="http://www.sweethome3d.eu"] 
[/URL]Here's where you can download that application: [http://prdownloads.sourceforge.net/sweethome3d/SweetHome3D-2.0-linux-x86.tgz](http://prdownloads.sourceforge.net/sweethome3d/SweetHome3D-2.0-linux-x86.tgz)

---

### Post by cool_fp on 2009-09-03
> **zeroseven0183 said:**
> Sweet Home 3D[U]
[/U][http://www.sweethome3d.eu]("http://www.sweethome3d.eu/")
[URL="http://www.sweethome3d.eu"] 
[/URL]Here's where you can download that application: [http://prdownloads.sourceforge.net/sweethome3d/SweetHome3D-2.0-linux-x86.tgz](http://prdownloads.sourceforge.net/sweethome3d/SweetHome3D-2.0-linux-x86.tgz)

Thanks for sharing this here as I have already used this for one of my client but I found this very good at graphics and other features but for this case I think this software need many modifications also so before you going to use this change the things whatever you can change Thanks!

---

### Post by jamiehendrich on 2009-09-04
thank you very much!

Jamie

---

### Post by jamiehendrich on 2009-09-04
I now have /home/jamie/Desktop/SweetHome3D-2.0-linux-x86.tgz
on my desktop and I selected "extract" from Archive manage and then there is an orange folder on my desktop that is SweetHome3D-2.0.

Now I don't know how to run the program.  I tried to research how to go into a terminal and type in tar xzvf with the file name and then tar.gz or tgz at the end, to no avail.  I know nothing about computers.  What am I doing wrong?

jamie

---

### Post by mlentink on 2009-09-04
A bit of googling resulted in e.g. [this]("http://amitech.50webs.com/installing/index.php.html").

Try using the following search terms: ubuntu help installing software in Google.

---

### Post by jamiehendrich on 2009-09-04
I had already googled it and have instructions.   I just don't understand it.  There was something about installing it now and then running it.  I typed in those commands at my terminal and, naturally neither of them worked properly.

I finally figured out how to unzip the tar file.  I didn't know you had to type in "CD Desktop" prior to the "tar" command.  I just don't know how to make it run, where the icon is, where the files are, etc.    I assumed once I unzipped it and saw all that stuff scrolling down my computer that it was "unzipping," that it would automatically put the icon on my desktop.  I could click on it and it would open.....like automatically.  Oh, well.

Jamie

PS  It's not fun being technologically challenged.  

PS/PS  Thank you anyway.

---

### Post by Regenweald on 2009-09-04
> **jamiehendrich said:**
> I had already googled it and have instructions.   I just don't understand it.  There was something about installing it now and then running it.  I typed in those commands at my terminal and, naturally neither of them worked properly.

I finally figured out how to unzip the tar file.  I didn't know you had to type in "CD Desktop" prior to the "tar" command.  I just don't know how to make it run, where the icon is, where the files are, etc.    I assumed once I unzipped it and saw all that stuff scrolling down my computer that it was "unzipping," that it would automatically put the icon on my desktop.  I could click on it and it would open.....like automatically.  Oh, well.

Jamie

PS  It's not fun being technologically challenged.  

PS/PS  Thank you anyway.

From the site : 
```

Under Linux:	Uncompress the downloaded file and run SweetHome3D application found in the uncompressed directory. To install Sweet Home 3D, move the uncompressed directory in the one of your choice.

```

you have already uncompressed the file and it should have a folder on the desktop.

---

### Post by jamiehendrich on 2009-09-05
I am on a different computer now.  I just downloaded the software on this computer with Jaunty, and then I "extracted" it and it is now in a folder on my desktop; and if I click on the folder, it lists all the items there.  I don't know if "extract" is the same as "unzipping" or not.

What I don't know how to do is run it.  I googled that yesterday and it gave some command like apt-get install or run or something and the error message was "are you root."  

If you get a moment, please let me know what you think I'm doing wrong.  

     A.  Is "extract" the same as "unzip?"

     B.  Now that I have extracted and it's on my desktop, do I have to also unzip at terminal?

     C.  Once I unzip, is there a command at terminal to make it run?

Thank you so much.

Jamie

---

### Post by halitech on 2009-09-05
A. yes

B. no

C. no, just open the folder and double click on SweetHome3D

Linux files don't rely on file extensions like windows does so don't look for an .exe file to run. I'm actually surprised there are no instructions in the tar file on running it.

---

### Post by eath on 2009-09-05
Hey, is there a way to install it so my wife and I can both run it?  (We use different logins and she is blocked from my home directory)

---

### Post by halitech on 2009-09-05
you could copy the folder to a thumb drive and then she could copy it to her Desktop

you could also copy it to /opt and then you could both make a launcher on your desktop (you'll need to copy it with gksudo nautilus)

---

### Post by bear24rw on 2009-09-05
Thats a actually a really cool program, thanks

---

### Post by jamiehendrich on 2009-09-07
thank you sooooooo much.  I just opened it as you said and clicked on HomeSweetHome3D and it said "run in terminal" or "run" and I clicked "run" and it opened up perfectly.  I cannot believe it was that simple.
This is terrific.  Thank you, everyone!

Jamie

---

### Post by eath on 2009-09-10
> **halitech said:**
> 
you could also copy it to /opt and then you could both make a launcher on your desktop (you'll need to copy it with gksudo nautilus)


Thanks.  I always wondered what to do with the /opt directory.  It worked quite well.

---

