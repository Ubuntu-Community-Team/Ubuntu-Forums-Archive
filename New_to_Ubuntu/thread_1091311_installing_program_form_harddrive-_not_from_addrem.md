---
title: "installing program form harddrive- not from add/remove"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by ave2 on 2009-03-09
I have a program on my hard drive- (blender 64 bit) that I downloaded from the internet. It comes in a .tar.bz2 file- when I uncompress it, I end up with a folder that contains the executable file- if I run it, I can use the program.

I notice that you can select the program in add/remove, but dont want to have to download it again, but rather install it from my home folder- how do I go about doing this?

---

### Post by bmj2728 on 2009-03-09
What you've done is the equivalent of installing the program. You've extracted the neccesary files as well as the executable to it's own directory. I'm not sure I understand your question. Are you asking how to create a desktop icon or menu item to launch the program?

---

### Post by ave2 on 2009-03-09
I wasnt sure if there is something that differentiates installed programs from programs you run as I have done-
however there are 3 things I can think of that I would like to set up: 
1) I would like to keep it neat- put the folder where all the other programs are installed, 
2) create an applications/graphics menu item
3) link the .blend files to the program, which is blenders native file format-(just like .doc is ms words) so that when I click a .blend file, it launches blender

---

### Post by bmj2728 on 2009-03-09
> **ave2 said:**
> I wasnt sure if there is something that differentiates installed programs from programs you run as I have done-
however there are 3 things I can think of that I would like to set up: 
1) I would like to keep it neat- put the folder where all the other programs are installed, 
2) create an applications/graphics menu item
3) link the .blend files to the program, which is blenders native file format-(just like .doc is ms words) so that when I click a .blend file, it launches blender

This can be a little confusing at first coming from Windows. After a while though, you'll start to think of installing software the Windows way as the strange way(only took me a couple of weeks). 

These are certainly all do-able requests.(based on your question, I'm assuming you've got a decent knowledge-base in computers)

It's a simple matter of copying the directory you created when you extracted Blender into the directory where you keep your programs. You can do this in the Nautilus file manager or from the command line. 

When you right-click the desktop you should see an option to create launcher. It's pretty straightforward.

As far as assigning the file types to Blender, they may already be assigned that way. I've only played around with Blender a little bit(waaaayyy beyond the scope of my abilities) so I'm not sure how saved .blend files will react if just opened. You can check System --> Preferences --> Preferred Programs(or something like that, sorry I'm doing this from my Windows machine at work) you may be able to set the association there.

---

### Post by ave2 on 2009-03-09
thanks for the help- where are programs normally installed in ubuntu- windows has the program files directory- is there a similar file in ubuntu

---

### Post by Dougie187 on 2009-03-09
If you want it installed where other programs are installed I would suggest using a package manager to install it. That way if you want to remove it then you can remove it using a package manager, and you can help keep things neat. If you install it manually and you decide you want to remove it, then you will have to go around everywhere and remove the files. 

If you **REALLY** don't want to redownload it, then I would suggest just renaming the blender folder, for example lets say the name is "blender", then you should rename it to ".blender" this will make it a hidden folder, and then you can simply make a launcher on your desktop, just make the command
```
/home/**username**/.blender/**exec_name**
```
Here you will need to replace username, with your username, and exec_name with the name of the executable name. Also .blender will need to be replaced with the actual directory name.

For future reference however, when a program gets installed to your computer, the executables are typically stored in /usr/bin, /usr/local/bin, or /usr/sbin. Typically sbin is restricted to programs that require sudo to run. If I were going to install this application, and I didn't want it in my home directory, I would probably put it in /usr/local.

---

### Post by LowSky on 2009-03-09
not really, this is because of Linux's idea of application security. for instance a program executible will be stores in the /usr folder, yet the settings will be in the /home folder.
Now I'm not saying you need to use synaptic or add/remove but it will actually install the program correctly with ubuntu support built in, which is nice oin my opinion.

If downloading 16MB takes too much time for you (I guessing dial up) then using it the way you are is just fine. The best place to install the file in my opinion is the /home folder if you are the only user. if you need just create your own launcher for the menu or panel or desktop, which ever makes it easy for you.

---

### Post by ave2 on 2009-03-09
maybe I should just reload it then- bandwidth is a bit expensive where I come from, so thought I would try find a work around first before downloading the file twice
thanks for the help

---

### Post by ave2 on 2009-03-09
hmm just downloaded blender using the add/remove programs- and its not the latest version- looks like I will have to install it myself

---

### Post by earthpigg on 2009-03-09
hold on ave2!

[http://www.getdeb.net/app/Blender](http://www.getdeb.net/app/Blender)

edit: editing now. just wanted to post that quickly to save you money on bandwidth, if possible. 

a **.tar.bz2 **is usually used if developers dont want to take the effort to package the linux software for each specific distro. it does not truly 'install' itself, but it will run on nearly any distro with no problems.

a **.deb **file (aka Debian Package) is software specifically packaged for Debian linux, or its children - such as Ubuntu. it will install properly, and be uninstallable via synaptic or 'sudo apt-get remove *programname*'

if you see something you want, but it is only available from the developers in .tar.bz2 format... find someone that repackaged it into a .deb :)

[http://www.getdeb.net/](http://www.getdeb.net/) is usually the first place i go to look for such a .deb.

---

### Post by ave2 on 2009-03-09
thanks earthpigg! I will check getdeb out- what are the risks of downloading deb files from other sources- is there a potential for malware to get installed?

---

