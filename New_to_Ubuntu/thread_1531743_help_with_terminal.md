---
title: "help with terminal"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by Chad Olson on 2010-07-15
I installed some emerald theams and the only way I can get them to work is to run Terminal>.  emerald --replace     I tried to put in in startup applications but all it does is open the terminal after startup and I have to type in in I would like it to run the command auto and also in the background so I don't have it on my task-bar.  


I put this in the wrong prefix couldn't figure out how to move it in edit mode would like to know how to do tat also.

---

### Post by tom.swartz07 on 2010-07-15
> **Chad Olson said:**
> I installed some emerald theams and the only way I can get them to work is to run Terminal>.  emerald --replace     I tried to put in in startup applications but all it does is open the terminal after startup and I have to type in in I would like it to run the command auto and also in the background so I don't have it on my task-bar.  


I put this in the wrong prefix couldn't figure out how to move it in edit mode would like to know how to do tat also.

Hiya Chad.

This should be a relatively simple fix. You have 2 options;
1) Create a small script (dont panic, Ill help) that would automatically run the commands on startup

or 

2) Just use the ALT + F2 command menu to run the emerald theme.




I would suggest the first one, as it will save you trouble of doing it every time you log in.

To write the script, You should first open a plain-text editor, such as g-edit. You could find it under Applications,Accessories,gedit


Now we write the meat of the program, its fairly simple, so no problems here;

Let me explain what goes into it, then you could see the code. 
All bash (the language used in the terminal) programs need a line called a 'shebang' Its usually #!/bin/bash or !#/bin/sh.
That tells the terminal what programming language you are using.

Next is the working part of the code;

 Lets have the program wait for a few seconds until your desktop is fully loaded, otherwise you might run into some problems (i'd suggest 50 seconds, but if your computer is fast you could shave off a few)
Then we just type the command and we are set!


```
#!/bin/bash
sleep 50 && metacity --replace;

```

Enter this into the text editor and save it as a .sh file (metacity_start.sh for example). Just as long as the extension is .sh you should be fine.

Now, Right click on the file, go to properties and make sure the box is checked that says it has permissions to execute as a program

Now go into the startup programs and add that script, reboot and youre done!

---

### Post by Chad Olson on 2010-07-15
I found out how to do it their is a setting in compiz.
compizconfig settings manager> effects> window decorations> in the command box /usr/bin/emerald --replace

---

