---
title: "New, and lost.. Looking for a shortcut here (2 questions)"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by omnisource on 2010-05-22
Alright I am new to Linux but not computers or programming. And I have to questions

First is more of a ease-of-use question. The first program I downloaded was GIMP. I ran terminal and navigated to its directory and ran it using the command 'gimp'. Do I have to run most programs this way or is there a short cut method to run from the desktop.


Second question, I am eager to learn Python, I already know C/C++ and BASIC. But I don't know how to move my saved script files into the python directory, Ubuntu says I dont have the permissions to copy the file into my usr/local/lib and usr/local/bin. 

What do I need to do to be able to write to these folders ( I already fooled around in User Maintenance ) I can log in as root in terminal but not as the Desktop user. Or Do I just need to tell Python where my file is instead of moving the file to my Python directory.

oh and P.S. I love this OS, I already uninstalled Windows and gave my whole drive to Linux!

---

### Post by Kafubie on 2010-05-22
> **omnisource said:**
> Alright I am new to Linux but not computers or programming. And I have to questions

First is more of a ease-of-use question. The first program I downloaded was GIMP. I ran terminal and navigated to its directory and ran it using the command 'gimp'. Do I have to run most programs this way or is there a short cut method to run from the desktop.


Second question, I am eager to learn Python, I already know C/C++ and BASIC. But I don't know how to move my saved script files into the python directory, Ubuntu says I dont have the permissions to copy the file into my usr/local/lib and usr/local/bin. 

What do I need to do to be able to write to these folders ( I already fooled around in User Maintenance ) I can log in as root in terminal but not as the Desktop user. Or Do I just need to tell Python where my file is instead of moving the file to my Python directory.

oh and P.S. I love this OS, I already uninstalled Windows and gave my whole drive to Linux!

Hello!
Linux is **AWESOME!**

1.  You can go to Applications -> Graphics -> then click and drag GIMP on one of your panels.

The last 2, i am learning myself.  lol
But the third one has to do with using "chmod" in the terminal to give writing permissions to the the script.

---

### Post by SlidingHorn on 2010-05-22
> **omnisource said:**
> Second question, I am eager to learn Python, I already know C/C++ and BASIC. But I don't know how to move my saved script files into the python directory, Ubuntu says I dont have the permissions to copy the file into my usr/local/lib and usr/local/bin. 

What do I need to do to be able to write to these folders ( I already fooled around in User Maintenance ) I can log in as root in terminal but not as the Desktop user. Or Do I just need to tell Python where my file is instead of moving the file to my Python directory.

```
sudo mv /original/file/location /new/file/location
```

---

### Post by omnisource on 2010-05-22
Well when i goto usr/lib64/gimp/2.0 i just see 4 directories, I assumed I would see a gimp executable or something considering that typing 'gimp' in the terminal in this directory boots the program.

When I click on Applications -> Graphics -> there is no GIMP program listed just some shipped software.

hmm puzzling because when I installed WINE it appeared under Applications.

---

### Post by Darkness Des on 2010-05-22
You don't have to navigate to the GIMP directory. All you have to do is type "gimp". Same for all other programs.

---

### Post by amauk on 2010-05-22
When you say you downloaded the Gimp,
did you use the software repositories, or get gimp off of the internet?

Just checking...

---

### Post by oldfred on 2010-05-22
And to add to amauk's question.

You mentioned wine. Did you install the windows version in wine?

---

### Post by omnisource on 2010-05-22
> **Darkness Des said:**
> You don't have to navigate to the GIMP directory. All you have to do is type "gimp". Same for all other programs.

Thanks!


and to answer the other questions, I installed GIMP from Ubuntu Software Center, WINE was just something I planned to mess with later.

---

### Post by sydbat on 2010-05-22
You should be able to right click on the menu area (Applications, Places, System) and get a drop down that has "Edit Menus". From there you can choose what you want to show up in your menus (Applications and System). Gimp should be under "Graphics".

---

### Post by omnisource on 2010-05-22
> **sydbat said:**
> You should be able to right click on the menu area (Applications, Places, System) and get a drop down that has "Edit Menus". From there you can choose what you want to show up in your menus (Applications and System). Gimp should be under "Graphics".


Worked like a dream. GIMP was already selected to show but when I closed out it showed right up!


Thanks to everyone for the prompt response. Not too many forums are this helpful to new users!

p.s. I moved the .py file using that 'sudo mv source dest' command and it imported correctly. Kudos to SlidingHorn for the quick help!

---

