---
title: "Learning the command-line"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by iggy pop on 2010-05-03
Have been wanting to learn about using the command-line for quite a while and i happened to find in the Ubuntu forums a program that did just that. You can find it at:

[http://ubuntuforums.org/showthread.php?t=380978](http://ubuntuforums.org/showthread.php?t=380978)

It's called cmd_tutor-0.4

I downloaded the cmd_tutor package to my desktop.

I extracted and installed the program no problem and i now have a folder called cmd-tutor-0.4 sitting on my desktop and no idea how to run it.

I did open a terminal and typed: cmd-tutor-0.4 but all i got back was, command not found? 

Could someone help me please. Thanks

---

### Post by donkyhotay on 2010-05-03
just typing in the name of the program won't work by itself because the computer doesn't know where the program is located (do a google search on filename paths for more info on that). Assuming the name of the folder is "cmd-tutor-0.4", the folder is on your desktop and the name of the program inside the folder is also "cmd-tutor-0.4" then you would type the following into the CLI.
```

cd Desktop/cmd-tutor-0.4
./cmd-tutor-0.4

```
what this does is tell the computer "go into the folder called cmd-tutor-0.4 located in the folder called desktop" the second command tells the computer "run the program called cmd-tutor-0.4 that is located within the current directory". Be aware I've never used that program so I am making a number of assumptions here.

---

### Post by tgalati4 on 2010-05-03
Go into the directory an run the progam:

python cmd_tutor.py

---

### Post by wojox on 2010-05-03
Looking at the thread it should be:

```
./cmd_tutor
```

---

### Post by _0R10N on 2010-05-03
> **iggy pop said:**
> Have been wanting to learn about using the command-line for quite a while and i happened to find in the Ubuntu forums a program that did just that. You can find it at:

[http://ubuntuforums.org/showthread.php?t=380978](http://ubuntuforums.org/showthread.php?t=380978)

It's called cmd_tutor-0.4

I downloaded the cmd_tutor package to my desktop.

I extracted and installed the program no problem and i now have a folder called cmd-tutor-0.4 sitting on my desktop and no idea how to run it.

I did open a terminal and typed: cmd-tutor-0.4 but all i got back was, command not found? 

Could someone help me please. Thanks


Well, I'd never tried that program, but I'm giving the basics to execute any programs.
First, you have to move into that folder. Open a terminal and run
```
cd ~/Desktop/cmd-tutor-0.4
```
Then, you should look for a file (tipically a script) that will run your program. Frecuently this file is named after the program. You can also look for a README file, which should contain the instruction to execute the program properly.
Once you've located the file, you can execute it by running
```
./file_name
```
or
```
sh file_name
```

Kind regards!

---

### Post by oldos2er on 2010-05-03
> **iggy pop said:**
> 
I extracted and installed the program no problem and i now have a folder called cmd-tutor-0.4 sitting on my desktop and no idea how to run it.


Click the 'install' file for instructions.

---

### Post by carrarin on 2010-05-03
So, lets say you downloaded the tar.gz file to your desktop.
Extract the files by right clicking on the tar.gz file and then clicking Extract Here option. 

Open a terminal...
type the following commands:
cd ~/Desktop/cmd-tutor-0.4
sudo python install.py install

The application is now installed on your computer.
To run the application, open a terminal and type:
cmd-tutor

Follow the instructions. Good luck!

---

