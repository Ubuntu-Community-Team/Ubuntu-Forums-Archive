---
title: "How to change the permissions on a .exe file in a cd, to install using WINE ?"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by swarup on 2010-09-09
I have a Windows program which I have installed many times in Ubuntu systems, using WINE. This is the first time I am trying to install it on a 10.04 Lucid system, and I am getting an error message saying I have no permission to treat the .exe file as an executable file. I went into the Properities -> Permissions for that very .exe file, and tried to check the box for "execute (allow executing as a program)", but it would not allow me to check the box, instead giving me an error message that I have no permission to check that box. So, how can I get permission to run this .exe file as an executable in WINE?

---

### Post by jtarin on 2010-09-09
FromWINE Docs.
> 7.12. I ran wine with sudo or as root. How do I fix my permission errors?

You need to fix the permissions on your ~/.wine directory, this is where all Wine state, configuration and any important data you might have such as installed programs, saved data within Wine programs, etc. are stored. Once you delete or fix the permssions on this directory, rerun Wine as a regular user always! Run the following to fix the permissions on your ~/.wine directory if it now has root permissions.

```
cd ~
sudo chown -R $USER:$USER .wine
```

---

### Post by Jesus_Valdez on 2010-09-09
copy the exe file to your Home folder and try from there, maybe that helps.

---

### Post by swarup on 2010-09-09
> **jtarin said:**
> Have you prefaced your command with sudo.

I did not write the command in a terminal window. There is a GUI-- by right-clicking on the .exe file, there comes the option to open "properties -> permission". And there, there is a box to click, to make the file executable. In the GUI, there is no place to put a command i.e. prefaced by "sudo", is there?

---

### Post by jtarin on 2010-09-09
Soeone's other fix....> I've noticed most people here installing the DVD version (which, in hindsight, I should have bought). When I ran the install shield wizard, it only installed the files from CD#1 and then ended normally, making me think that everything was okay and it would ask me to insert the other CDs later in the game. Unfortunately, it dies with a strange error if you do that. I found another article that said I had to copy all of the iwd files to ".wine/drive_c/Program Files/Activision/Call of Duty 2/main". Unfortunately, when I put in any of CDs 2 through 6, Ubuntu gave me a permissions error and refused to even display the files as a normal user. [COLOR="Red"]To get around this problem, I had to copy from the CD to the "/root" folder, where I could change the file permissions, and then copy from "/root" to the final destination.[/COLOR] After all the files were copied, the game started working perfectly, and deserves its gold or platinum ranking.

I'm using Ubuntu 8.04 on a Dell Precision M6300.


---

### Post by swarup on 2010-09-09
> **jtarin said:**
> FromWINE Docs.

I went to the .wine directory in my home folder and found that in "properities -> permissions" for that very "wine" directory, there is already permission for executable files. It is already set. But still, when I go to the .exe on the cd, it will not allow me to set it as executable. 

If I am to do this work in a terminal window as suggested by your post, then please kindly fill in the blanks in that prompt so I can understand what is meant to go there. For example, what does "USER" mean, or "R"-- it is not clear to me. For "USER", do I put in the name of the computer?

---

### Post by fiyer on 2010-09-09
> **Jesus_Valdez said:**
> copy the exe file to your Home folder and try from there, maybe that helps.

I'll second that as an easy fix.  Copy the contents of the cd, and change the properties of the exe once it is on the harddrive.

---

### Post by swarup on 2010-09-09
> **fiyer said:**
> I'll second that as an easy fix.  Copy the contents of the cd, and change the properties of the exe once it is on the harddrive.

Many thanks to you as well as to jtarin and Jesus_Valdez, who have given similar suggestions. I copied the contents of the entire cd into my home directory, and there I was immediately allowed to change the permissions on the .exe file. This is surely the simplest solution-- thank you. :)

---

### Post by mc4man on 2010-09-09
> This is surely the simplest solution
Simplest, no, this is another example of how poorly implemented  the new 'security policy' is.

There are 2 ways to permantly fix this and 1 simple 'workaround' 

Simple 'workaround'

Next time right click on the cd icon -> open. Browse the folder, find the Install.exe or Setup.exe, whatever and ...

Right click on the .exe -> open with -> other application -> Use a custom command. For the command just use 
wine

This only has to be done once, in the future a right click on any .exe -> open with you'll see a choice named just 'wine', pick that and you'll be ok.

---

