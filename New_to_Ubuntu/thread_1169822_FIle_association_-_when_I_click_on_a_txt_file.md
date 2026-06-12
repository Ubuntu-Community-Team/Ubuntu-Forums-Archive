---
title: "FIle association - when I click on a txt file"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by cwmoser on 2009-05-25
When I double click on a text file wanting to open it in a text edit, nothing happens.  I have to right click on the file and select "Open With" to select an editor to open the file.  

The next time I double click on an txt file, still nothing happens.  I can double click on certain files like *.ods, *.xls, etc and they open in Open Office.

How do I associate a program to run to open a txt file like in Windows?

Carl

---

### Post by MrWES on 2009-05-25
> **cwmoser said:**
> When I double click on a text file wanting to open it in a text edit, nothing happens.  I have to right click on the file and select "Open With" to select an editor to open the file.  

The next time I double click on an txt file, still nothing happens.  I can double click on certain files like *.ods, *.xls, etc and they open in Open Office.

How do I associate a program to run to open a txt file like in Windows?

Carl

Right click on the file; Properties and then the Open With tab. Change the program association -- now it will be permanent.

Bill

---

### Post by Didius Falco on 2009-05-25
> **cwmoser said:**
> When I double click on a text file wanting to open it in a text edit, nothing happens.  I have to right click on the file and select "Open With" to select an editor to open the file.  

The next time I double click on an txt file, still nothing happens.  I can double click on certain files like *.ods, *.xls, etc and they open in Open Office.

How do I associate a program to run to open a txt file like in Windows?

Carl

Hi,

Right click a .txt file, then select **Properties **and the **Open With** tab, select what you want to open it with by default.

Regards,

Didius

---

### Post by camper365 on 2009-05-25
As Didius Falco said, right click on the file like you would in Windows, select open with and select the Text Editor Button. If there isn't one, click Add, then expand the custom command option. Type gedit (all lowercase).

---

### Post by cwmoser on 2009-05-25
The thing is I can right click on an *.txt file and select Open With and it opens.  Later, if I just double click on the same file, nothing happens.  I have to go back to right clicking and dealing with Open With.

Other file types like *.odt will open in an application when you double click on them.  Why not *.txt files????

Carl

---

### Post by CatKiller on 2009-05-25
> **cwmoser said:**
> The thing is I can right click on an *.txt file and select Open With and it opens.  Later, if I just double click on the same file, nothing happens.  I have to go back to right clicking and dealing with Open With.

No you don't. Read the responses from MrWES and Didius Falco again.

---

### Post by cwmoser on 2009-05-25
> **CatKiller said:**
> No you don't. Read the responses from MrWES and Didius Falco again.


I reread them.  Still cannot get an association to stick for *.txt files.

I can open them by right clicking and Open With.
Cannot get the file to open by simply left double clicking the *.txt file.

Carl

---

### Post by cwmoser on 2009-05-25
I found out why my *.txt files would not open -- they had 777 permissions.
I changed them to 666 and now they do take file associations.

i.e. I used this command on my *.txt files:  chmod  666  *.txt


Carl

---

### Post by asmoore82 on 2009-05-25
**Step 1:**
right-click any txt file and select "**Properties**"
click the **"Open With" tab** *inside* of "**Properties**"
hit the "Reset" button and/or select the text editor of your choice

**Step 2:**
check your settings for executable txt files:
in any Nautilus "File Browser" window, open "Edit -> Preferences"
click the **"Behavior" tab** and
make sure that "Run executable txt files ..." is **_not_ selected**.

see attached images.

EDIT: it's probably a really good idea to turn off silently running
executable txt's even though you've already solved the real problem;
Much kudos to you for taking the time to properly fix your file permissions.

---

### Post by cwmoser on 2009-05-26
Thanks guys, I learn something everyday.  Really like Ubuntu.

Carl

---

