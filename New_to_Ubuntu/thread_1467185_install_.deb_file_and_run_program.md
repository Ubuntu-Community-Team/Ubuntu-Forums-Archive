---
title: "install .deb file and run program"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by manhattanLIN on 2010-04-30
:popcorn:Hi,
 
I am trying to run a .deb file i installed. I am still new to ubuntu. I got the .deb file to install, but how do i run the program? I searched the file directory, and clicked on several icons, but nothing happens. . There is no icon on my desktop. I found the package and clicked 'Properties'. That's all I can do. Help
 
Thanks

---

### Post by hackb0y294 on 2010-04-30
Double-click it, or right click and click Open With Gdebi Package Installer.

Oh, by the way, this is an installer, not a standalone program, so you have to install it first using the steps above.

---

### Post by jrothwell97 on 2010-04-30
Welcome to Ubuntu!

Firstly, what program are you trying to install? You might find it more convenient (and safer) to install it from the Ubuntu Software Centre. In that case, you're certain to get a menu item for it.

---

### Post by no2498 on 2010-04-30
look in applications
i have not seen any program load a icon to the desktop

---

### Post by manhattanLIN on 2010-05-06
Thanks for the replies. I think the .deb file is installed, i double-clicked the file, and it said it installed..but then it doesn't bring up the app. I don't know how to run the program after I double-click on it.  
 
I don't see the name of the program in applications
 
If it helps, this is software written for lindows. I'm not even sure if this would work with ubuntu.

---

### Post by NT_CRASH on 2010-05-06
If you press ALT+F2 this will open the "Run Application" dialog box. Type the name of the program you installed. If in fact it is installed you should be able to run it for from here.

---

### Post by manhattanLIN on 2010-05-11
Thanks NT_Crash,
 
I don't see the app under add/remove programs, or when i press alt-f2.  I can only see it under 'Synaptic package manager'.  When I try to double-click to run the program, nothing happens.  I don't even get an error message.

---

### Post by themusicalduck on 2010-05-11
What is the program that you installed? Not all .deb files will make a menu entry, it totally depends on what kind of program it is.

For e.g., a panel applet would be under Add to panel when right clicking on the panel.

---

### Post by no2498 on 2010-05-12
does not sound like its installed
is the small box green in Synaptic package manager
close Synaptic package manager if yes

if yes open a terminal type the name of it in click enter

---

### Post by manhattanLIN on 2010-05-15
Ok, I checked synaptic package manager, and the green box is next to the program.  This is for a dial-up internet company's web connect software.  
 
I went to the program directory, and try typing the name of the exe file in terminal, nothing happened.  I did the same thing with alt-f2, but it didn't work.  
 
I did some looking, and the files are under my /opt directory.  
I double-click on the executable file but nothing happens.  Shouldn't I get some kind of error message?
 
Thanks

---

### Post by Paddy Landau on 2010-05-15
In Synaptic, if you right-click and select Properties > Installed Files, you'll get a list of installed files. That will help you to find what you're looking for.

> **manhattanLIN said:**
> I double-click on the executable file but nothing happens.  Shouldn't I get some kind of error message?
That depends entirely on how the program was written. If it's a terminal program, then you don't want to double-click, but instead to open a terminal and run it from there.

I'm a bit puzzled, though. Ubuntu comes with dial-up built in. Why would the company give you a deb file to install for dial-up?

---

