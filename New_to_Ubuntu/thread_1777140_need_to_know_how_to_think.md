---
title: "need to know how to think"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by msuser on 2011-06-07
i am a windowws guy 25 years... first time ubuntu user just checking out seamed to install fine 
i tried to download flash..  insted of downloading its asking me for an application? I dont understand what im to do... what should i know already? what application ftp? i see no offered list ? how much bitch is thius to completely install i dont have time im 55. every time i want to do something will it ask me to know something i dont know? i just wanted to download a file from adobe their link  what dont i understand about this ubuntu

---

### Post by iclestu on 2011-06-07
> **msuser said:**
> i am a windowws guy 25 years... first time ubuntu user just checking out seamed to install fine 
i tried to download flash..  insted of downloading its asking me for an application? I dont understand what im to do... what should i know already? what application ftp? i see no offered list ? how much bitch is thius to completely install i dont have time im 55. every time i want to do something will it ask me to know something i dont know? i just wanted to download a file from adobe their link  what dont i understand about this ubuntu


did you add the restriced formats?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by mike555 on 2011-06-07
In Ubuntu you should only get things from the package manager (not web sites) ,also be sure Firefox is closed when you install Flash.

---

### Post by nothingspecial on 2011-06-07
You're asking the right question.

You have to stop thinking like a windows user.

99.9% of the time you do not have to download stuff from a web page.

Use the software center

Open it up and install the flash plugin from there.

---

### Post by Random_Dude on 2011-06-07
I don't know if installing the ubuntu-restricted-extras will solve the problem, but it will definitely be handy in the future anyway.
You can do this by opening Synaptic Package Manager and typing ubuntu-restricted-extras and installing it, or by typing in the terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

Press Enter, type your password and press Enter again.

Cheers :cool:

---

### Post by msuser on 2011-06-07
thank you for quick reply ... igue3ss you hit on what i am missing retricted formats?? what is that im real new here.. i believe i was trying to download flask a exe file to install on ubuntu... through the link supplied from adobe web site. I am use to things just downloading and asking where i should put it like desktop... i dont see anything that will show me things like c:\   d:\  drives etc... things seem removed from user... where is command line etc things i need to know to fully configure this op sys, they all do the same services just how do i need to think. the term restricted formats ???? to down load a binary file... come on what app is missing andhow am i to know its name? there has to be a common theme here to do things.

---

### Post by msuser on 2011-06-07
so i did get an error it should have not asked me for an app.???.. that is how new i am i did not know that is an error... so ubuntu should just do as win dose just download it correct? to be asked for an app = error ???

---

### Post by iclestu on 2011-06-07
> **msuser said:**
> thank you for quick reply ... igue3ss you hit on what i am missing retricted formats?? what is that im real new here.. i believe i was trying to download flask a exe file to install on ubuntu... through the link supplied from adobe web site. I am use to things just downloading and asking where i should put it like desktop... i dont see anything that will show me things like c:\   d:\  drives etc... things seem removed from user... where is command line etc things i need to know to fully configure this op sys, they all do the same services just how do i need to think. the term restricted formats ???? to down load a binary file... come on what app is missing andhow am i to know its name? there has to be a common theme here to do things.

The truth is we are guessing that restricted formats is the missing link for that one particular issue.

It is a step change from windows. You dont generally install software via a weblink. As the previous poster suggested, 99% of the time you install it using the package manager from ubuntu. If that seems like a disadvantage think of all the cluter and crap that ends up on windows... pop ups with updates to everything. With ubuntu YOU control what hits your harddrive. That is no bad thing IMHO

Bear with it, it DOES need learning. It DOES need time to adjust from windows but it really is worth it.

---

### Post by iclestu on 2011-06-07
> **msuser said:**
> so i did get an error it should have not asked me for an app.???.. that is how new i am i did not know that is an error... so ubuntu should just do as win dose just download it correct? to be asked for an app = error ???

im stuggling to understand whats happening. Hit the print scrn button and show us some screenshots? might clarify

---

### Post by el_koraco on 2011-06-07
> **msuser said:**
> thank you for quick reply ... igue3ss you hit on what i am missing retricted formats?? what is that im real new here.. i believe i was trying to download flask a exe file to install on ubuntu... through the link supplied from adobe web site. I am use to things just downloading and asking where i should put it like desktop... i dont see anything that will show me things like c:\   d:\  drives etc... things seem removed from user... where is command line etc things i need to know to fully configure this op sys, they all do the same services just how do i need to think. the term restricted formats ???? to down load a binary file... come on what app is missing andhow am i to know its name? there has to be a common theme here to do things.

If you insist on installing things from the web, look for files with the .deb extension, not the .exe one. Adobe will even let you look for the flash plugin for Ubuntu. 

There's no c: and d: drive. The filesystem is different in Linux.

---

### Post by Sylos on 2011-06-07
Hello.

The 'restricted extras' packages give you a variety of tools to allow you to access things in restricted formats. As ubuntu is open source it would not be legal in some countries to bundle in the necesarry stuff to allow you to open mp3's or some other media formats as the code is under restrictive licence - hence you need to install a package to give you these things.

As for some of the other bits you raised:
 Ubuntu and linux in general is different to windows and so things a re arranged differently and often called different things. You wont have a C drive because the way drives are mounted is different - but you can access your 'home' folder and all your other locations using the tools provided (nautilus is the equivalent to windows explorer for example).
The command line can be accessed from Applications > Accessories > Terminal (i think thats right - not at my ubuntu PC at the moment) and you can enter all of your commands from here. Obviously the commands will be different to anything you used on windows as the OS is very different. For the most part  a basic user can avoid the Terminal and do most things from the GUI.

I suppose the best answer to your questions is to say that you will only get the hang of the new OS layout and how to go about things by exploring and trying things out. Try going through the task bar and use the different programs and utilities and see what they do. Once you get past the initial confusion of not knowing what things are called and where they are found I think you'll find that, on the face of it, the way you do everyday tasks is not that different from windows - just more stable and more readily configurable to your own needs.

Good Luck

---

### Post by msuser on 2011-06-07
Im sorry people, I am really new, to new to even ask newbe questions... I need to take the advise above and just put in the time and figure this out.... i really dont know even how to ask a question.... I was looking for something like all admin and application control is in the bla bla, command prompt is located ..... I am just lost i know what i want to do but am lost in un know to me  icons. I want config sys and autoecec.bat edlin i can understant this i hate hunting through unknown icons that usually keep the user from doing exactly what they want. I know dos /windows from beginning ever herd of cpm or mmmost they were os too.... but comand line function, easy to0 look up commands you had a list of commands, unix u can link them its teasy no gui.... Ill be back later when i can phrase a question....

---

### Post by msuser on 2011-06-07
SORRY and THANK YOU ALL..... i hate users   ID10T error

---

### Post by collisionystm on 2011-06-07
> **msuser said:**
> i am a windowws guy 25 years... first time ubuntu user just checking out seamed to install fine 
i tried to download flash..  insted of downloading its asking me for an application? I dont understand what im to do... what should i know already? what application ftp? i see no offered list ? how much bitch is thius to completely install i dont have time im 55. every time i want to do something will it ask me to know something i dont know? i just wanted to download a file from adobe their link  what dont i understand about this ubuntu


Install the firefox addon FLASHAID

It will choose the correct flash for your system. 64 or 32

---

### Post by Random_Dude on 2011-06-07
It takes a while to get used to Ubuntu, you should take things easy and learn as you go along.
You might want to take a look at a manual first, like this one: [http://ubuntu-manual.org/](http://ubuntu-manual.org/)
It is the manual for the old version of Ubuntu, so _the user interface explained in the manual is different._ However, you might want to read the chapters about installing software, and them you'll be able to formulate the questions better. ;)

Cheers :cool:

---

### Post by nothingspecial on 2011-06-07
If you want a command line, just press Ctrl-Alt-T

I think that's what you are asking for ???????

---

### Post by aytech on 2011-06-07
Hi msuser!
Please try to find the time to read the [Ubuntu guide]("http://ubuntuguide.org/wiki/Ubuntu:Maverick"), it helped me a lot when I was in your shoes..

---

### Post by Zill on 2011-06-07
msuser:  You might find the following link helpful...

[Linux is Not Windows]("http://linux.oneandoneis2.org/LNW.htm")

---

