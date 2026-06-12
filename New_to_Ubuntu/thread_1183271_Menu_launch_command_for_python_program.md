---
title: "Menu launch command for python program"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by Chilli Bob on 2009-06-09
Hi all,

I have installed a python program called kabikaboo.py.  It is located in the folder /home/rob/kabikaboo/code/.  I can currently start it by opening a terminal, navigating to the folder and running ```
python kabikaboo.py
```.

I would like to add it to the application menu (under office), but can't work out what to put in the "command" slot in the launcher dialogue box.  I have tried....

```
python ~/kabikaboo/code/kabikaboo.py
``````
python ~/kabikaboo/code kabikaboo.py
``````
python home/rob/kabikaboo/code kabikaboo.py
``````
python /home/rob/kabikaboo/code kabikaboo.py
``````
python /home/rob/kabikaboo/code/kabikaboo.py
```.... plus several other permutations, none of which worked.  I realise that I am revealing my Linux illiteracy, but if someone could tell me the correct way to write this command, I'd be most grateful.

Thanks in advance, Rob.

---

### Post by Viva on 2009-06-09
python /home/rob/kabikaboo/code/kabikaboo.py should work.

---

### Post by Chilli Bob on 2009-06-09
> **Viva said:**
> python /home/rob/kabikaboo/code/kabikaboo.py should work.


I would have thought so, but nothing happens when I select this from the menu.

Note: I just tried running the above command in a terminal and got this error.

```
Traceback (most recent call last):
  File "/home/rob/kabikaboo/code/kabikaboo.py", line 1110, in <module>
    editor = KabikabooMainWindow()
  File "/home/rob/kabikaboo/code/kabikaboo.py", line 40, in __init__
    self.builder.add_from_file("forms/main.xml") 
glib.GError: Failed to open file 'forms/main.xml': No such file or directory

```

Now, the folder /home/rob/kabikaboo/code/ does contain a folder /forms, which does contain the file "main.xml".  So it seems that the problem is caused by not starting the program from the right folder, so it can't find the file in the subfolder.  

Is it possible to change to the correct folder, THEN run the python program, in a single line, that can be used in the launcher???

---

### Post by Chilli Bob on 2009-06-10
After a bit of reading, I tried this...

```
cd /home/rob/kabikaboo/code; python kabikaboo.py
```but got this error...

```
**Could not launch 'Kabikaboo'**

Failed to execute child process "cd" (No such file or directory)
```Any suggestions?

---

### Post by jyaan on 2009-06-10
You could try putting a little bash script in /usr/local/bin with those cd and python commands in it. And then just have your shortcut use that script as the command instead. Make sure the script has exec permissions though.

---

### Post by aidave on 2009-08-19
Yes a bash script would be the way to go here.
Unfortunately Python will try to run in a different directory where the Kabikaboo program will fail to find the right files.  So you have to "cd" to it first.

But dont worry because there is a Kabikaboo installer out now to handle it for you: [https://launchpad.net/kabikaboo](https://launchpad.net/kabikaboo)

cheers :)

---

