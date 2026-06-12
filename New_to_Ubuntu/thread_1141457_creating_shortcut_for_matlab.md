---
title: "creating shortcut for matlab"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by alexeyhurricane on 2009-04-28
ok i just installed matlab program to ```
/usr/local/matlabR2009a
```

and im trying to put link to this program on desktop ,pls help!

thank you very much!

---

### Post by hesjnet on 2009-04-28
what do you do to open the program? If you just write matlab in the terminal, then you'll right click on the desktop and choose new starter

Type in matlab in every textbox.

---

### Post by alexeyhurricane on 2009-04-28
doesnt work like that terminal says matlab not found if i click matlab it starts! if i click right click option is not availabale for me to create link!

---

### Post by Nepherte on 2009-04-28
If the matlab commando doesn't show up, it's probably because it's not in your PATH. All of that doesn't really matter if you want to create a starter on your desktop.

1. Right click on your desktop and pick create starter (not sure of the exact english term).

2. Fill in the details. Most important one is the path to the binary executable. This is probably where it is located in your case:
```
/usr/local/matlabR2009a/bin/matlab
```
If you want to startup the gui of matlab, you have to add the -desktop switch to it. Like this:
```
/usr/local/matlabR2009a/bin/matlab -desktop
```

---

### Post by apocalypse80 on 2009-04-28
Just to add that matlab offers to create symlinks during installation (apparently you rejected it).
You can just create them manually;

sudo ln -s /usr/local/matlabR2009a/bin/matlab /usr/local/bin/matlab
sudo ln -s /usr/local/matlabR2009a/bin/mbuild /usr/local/bin/mbuild
sudo ln -s /usr/local/matlabR2009a/bin/mcc /usr/local/bin/mcc
sudo ln -s /usr/local/matlabR2009a/bin/mex /usr/local/bin/mex

Those are the symlinks my matlab installation created.
Mine is version 2008a not sure if 2009a is any different but I doubt it.

After that matlab should run from the terminal.

---

### Post by alexeyhurricane on 2009-04-28
ok now window shows for a few seconds and disappears and nothing happening after that!

---

### Post by Jazzy_Jeff on 2009-04-28
One way you can do it is by going to the top and right click on Applications and then Edit Menus. Choose where you want to put a launcher, (as an example Applications), then click new item. Put in the information it asks for and when you are done, go back into your menu and right click on your new entry and put it on desktop.

---

### Post by alexeyhurricane on 2009-04-28
same problem shows up for few seconds then goes away and nothing!

---

### Post by Jazzy_Jeff on 2009-04-28
Go to Places at the top and click on Desktop and see if the launcher shows up in there. I had a problem before with things not showing up until I did that.

---

### Post by alexeyhurricane on 2009-04-28
i mean that i think link works ok , but program just loads for a few seconds then disappears!

---

### Post by Nepherte on 2009-04-28
If you only see the splash screen and nothing afterwards, you probably left out the -desktop part in
```
matlab -desktop
```
That's the behavior I get too when I leave that out.

---

### Post by TideMan on 2009-04-28
The problem is you need to start the licence manager using lmstart.

I solved the problem by going to:
System/Preferences/Sessions/Startup Programs
and adding a new program called Matlab Licence Manager Startup or something similar and inserting the following into the command window:
/usr/share/matlab/etc/lmstart
You may need to adjust this for the location of your lmstart

This will start the licence manager everytime you boot up.

---

### Post by alexeyhurricane on 2009-04-29
i tried matlab -desktop, but it kind of starts matlab program! but  doesnt ppalce anything on desktop! i tried to put licence ill check what's goin on

---

### Post by alexeyhurricane on 2009-04-29
doesnt work anything still same thing happening !

---

### Post by Nepherte on 2009-05-01
What happens if you run matlab from the console? Does it give any errors?

---

### Post by freeburn on 2009-05-01
is it possible to run matlab in ubuntu? can anyone pls explain it to me?i thought i can not convert to ubuntu only bcz of MATLAB.

---

### Post by Nepherte on 2009-05-01
Yes it is possible to run matlab on linux on the condition that you bought the unix/linux version of matlab.

---

### Post by robertrej on 2009-05-01
Sorry to ask but not sure where to put this question.
I am trying to create a shortcut to:    /home/bob/Desktop/
in terminal and just can not sort out the process.
there is a icon shortcut but it takes me to: bob@bob-desktop:~$ 
not Desktop upper case D ! 

And no I am not lazy I goto that directory a lot during my day
and typing   cd /home/bob/Desktop/          gets boring.


                               Please help
                               Bob

---

### Post by TideMan on 2009-05-03
> **freeburn said:**
> is it possible to run matlab in ubuntu? can anyone pls explain it to me?i thought i can not convert to ubuntu only bcz of MATLAB.

If you ask the supplier of your Windows version, they will supply (for free!!) a copy for Linux.  At least that's what happened for me.

Once you have your Linux CD, you need to carefully follow the instructions on the CD, especially with regard to licencing.  It will never work unless you have a personal number which TMW supplies by email when you order your Linux version.

---

### Post by Claus7 on 2010-10-23
Hello,

> **Nepherte said:**
> 
If you want to startup the gui of matlab, you have to add the -desktop switch to it. Like this:
```
/usr/local/matlabR2009a/bin/matlab -desktop
```

thanks a lot! And I was looking for this for a long time!

Regards!

---

### Post by DrImago on 2011-01-24
> **alexeyhurricane said:**
> i mean that i think link works ok , but program just loads for a few seconds then disappears!

The way I did it was:

Right click the applications menu (top left)

Edit menus

New Item

I selected for the Type -> Application in terminal

Browsed to the path of the matlab launcher

Gave it the name Matlab

And that was it.

Now I can launch Matlab from the Applications menu with no problem.

Hope it works for you too!

---

### Post by wlane on 2011-06-17
I've got MATLAB installed correctly and it runs great if I open the Terminal and type
```
matlab
```or
```
matlab -desktop
```however I want it to work from a menu icon without a terminal.

I tried creating a new icon using these details:
Command: matlab
Command: matlab -desktop
Command: /usr/local/MATLAB/R2011a/bin/matlab
Command: /usr/local/MATLAB/R2011a/bin/matlab -desktop

None of the above commands work, any ideas?

Thanks guys!

Edit:
Turned out I mixed up my directories, this command worked
Command: /usr/share/MATLAB/R2011a/bin/matlab -desktop

---

