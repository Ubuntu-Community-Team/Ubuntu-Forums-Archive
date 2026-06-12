---
title: "How To Install"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by Flirtilizer on 2008-12-04
I need to know how to install a file that I don't get via the package manager.

Someone told me to click on the executable.  I hate being this green all over again.....

LOL

What is an executable.  I tried to log into the software's forum and they seem to be having issues with there CAPTCHA.....  Somethings is preventing me for registering.  What, I'm not sure.

I even went to the extreme of reading the manual, nothing there as far as I saw.

The package I'm trying to install is here:  [http://www.rawtherapee.com/?mitem=3](http://www.rawtherapee.com/?mitem=3)

The file downloaded is archived.  I unzipped it but I don't know what is executable in Linux. 

thanks for the help.

---

### Post by Riffer on 2008-12-04
It was answered in your other thread.  I believe it was the file named rt.

---

### Post by cyfur01 on 2008-12-04
For the long answer....

You can do this either graphically, or from the command line.

Graphically:
If you extracted the folder to your desktop and this should open a file browser window. The executable files will have a gear-like icon, like rt and rtstart in the attached screen-cap. Double click on rt and it should launch it for you. 

You can create a launcher to this on your desktop too. Right-click on an open part of your desktop and select "Create Launcher...". Click "Browse" and navigate to the executable, then click ok. Give it a name, and then hit the OK button and it should create a launcher that you can double click.

This all works fine and dandy provided you don't encounter any problems. If you do, you can try launching it in a terminal and it will spew out a bunch of error messages that can potentially help solve the problem.

Command Line:
Launch a terminal (Alt+F2, type "gnome-terminal"), and then, assuming the folder is on your desktop, execute the following:
```

cd Dekstop/RawTherapee24b2/
ls
./rt

```
The first command switches your present working directory to the folder you want to look at. The second command should list all the contents of the folder. Executable files will be coloured green. The last command would execute "rt". The dot-slash indicates that the executable command to be launched is rooted in the current directory.

---

### Post by Flirtilizer on 2008-12-04
Thanks.  I figured I was missing the obvious.  :)

So I can copy this pretty much any place I want then create a launcher to it?

/bin seems like a good place for it?

I don't like it on the desktop.  


Thanks very much for the help.

---

### Post by gjoellee on 2008-12-04
Maybe you can CD into the folder and run:```
./rwz_sdk.so
```

---

