---
title: "UnifiedLinuxDriver.tar.gz"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by wstay on 2009-03-01
Can someone please show me how I can install the UnifiedLinuxDriver.tar.gz file which I downloaded from [www.samsungprinter.com](www.samsungprinter.com). I cannot attach this .tar.gz file here because the file is bigger than 976.6 KB which is not allowed. Therefore I take a screenshot (please see attachment) of the contents after I had extracted it to a folder called 'Samsung Unified Linux Driver installer'. Inside this folder is a folder called 'cdroot'. This 'cdroot' folder contains a 'Linux' folder, the contents of which are shown on Screenshot.png.zip. The 'cdroot' folder also contains an 'autorun' file with the following command:
#! /bin/sh
BASE=`dirname $0`
exec sh $BASE/Linux/install.sh

But when I double click on the 'autorun' file and choose Run, nothing happens - it won't run the installation.

---

### Post by taurus on 2009-03-01
Try running it from a terminal.  Open a terminal and post the output of this command.

```
cd ~/Desktop/"Samsung Unified Linux Driver installer"/cdroot/Linux
```

---

### Post by wstay on 2009-03-02
> **taurus said:**
> Try running it from a terminal.  Open a terminal and post the output of this command.

```
cd ~/Desktop/"Samsung Unified Linux Driver installer"/cdroot/Linux
```

I tried it on the Desktop by opening a terminal and also using the terminal from Ctrl+Alt+F1, but it still won't run the installation.
Is there any other or alternative way to get it to run the installation?

---

### Post by hyperyoda on 2009-03-02
> **wstay said:**
> I tried it on the Desktop by opening a terminal and also using the terminal from Ctrl+Alt+F1, but it still won't run the installation.
Is there any other or alternative way to get it to run the installation?

Hi,

Try this:

$ tar zxvf UnifiedLinuxDriver.tar.gz
$ cd cdroot/Linux
$ chmod +x install.sh
$ sudo ./install.sh

Zach

---

### Post by wstay on 2009-03-03
> **hyperyoda said:**
> Hi,

Try this:

$ tar zxvf UnifiedLinuxDriver.tar.gz
$ cd cdroot/Linux
$ chmod +x install.sh
$ sudo ./install.sh

Zach

I am now able to install with these commands. Thanks.
I installed without switching on my printer. And it installed the printer model as Samsung CLP-300splc as the default printer. But my printer model is Samsung SCX-4725F. I find that I cannot change the list of printer to my printer model. So I have to uninstall and to reinstall UnifiedLinuxDriver.tar.gz with my printer switch on to see whether it can detect on printer model.
But I don't know how to uninstall the UnifiedLinuxDriver.

---

### Post by wstay on 2009-03-04
> **hyperyoda said:**
> Hi,

Try this:

$ tar zxvf UnifiedLinuxDriver.tar.gz
$ cd cdroot/Linux
$ chmod +x install.sh
$ sudo ./install.sh

Zach

I found the installed UnifiedLinuxDriver under the Application menu with an uninstall icon called  Uninstall Samsung Unified Driver. When I click on this uninstall icon, it say I need root privilege. But using the terminal under root, I don't know where this uninstall icon is located and also what command to type?
Hope you can advise me on this.

---

### Post by markusf21 on 2009-03-04
right click the icon and set a launcher for the desktop. then right click the launcher and hit properties. find where it has the command to run. and edit it so it says sudo before the command. then exit properties and double click the launcher

---

### Post by wstay on 2009-03-04
> **markusf21 said:**
> right click the icon and set a launcher for the desktop. then right click the launcher and hit properties. find where it has the command to run. and edit it so it says sudo before the command. then exit properties and double click the launcher

I edit the command as: sudo/opt/Samsung/mfp/uninstall/uninstall.sh and then exit properties and double click the launcher on the Desktop. A message box appears as follow:"There was an error launching the application. Details: Failed to execute child process "sudo/opt/Samsung/mfp/uninstall/uninstall.sh" (No such file or directory)"
Is there any other option I can try?

---

### Post by Zack McCool on 2009-03-04
you can try using a space after sudo.

---

### Post by markusf21 on 2009-03-04
i guess i should have mentioned that space after sudo is required. sorry

---

### Post by wstay on 2009-03-04
I put in a space after sudo: sudo /opt/Samsung/mfp/uninstall/uninstall.sh
I double click on the uninstall icon and also right click on the uninstall icon and select 'open' - the uninstall won't run.
It looks like the uninstall icon is blur-out on the Desktop and I can't see the uninstall icon in the terminal when I open the terminal and cd to the Desktop.
I try to use the terminal and cd to /opt/Samsung/mfp/uninstall and enter the command chmod +x uninstall.sh and then enter the command uninstall.sh and it gives an error message -'command not found'.

---

### Post by wstay on 2009-03-10
> **Zack McCool said:**
> you can try using a space after sudo.

Before I hit the Thanks button (and where can I find the button), could you please help me solve this problem:
I put in a space after sudo: sudo /opt/Samsung/mfp/uninstall/uninstall.sh
I double click on the uninstall icon and also right click on the uninstall icon and select 'open' - the uninstall won't run.
I try to use the terminal and cd to /opt/Samsung/mfp/uninstall and enter the command chmod +x uninstall.sh and then enter the command uninstall.sh and it gives an error message -'command not found'.

---

### Post by wstay on 2009-03-17
> **markusf21 said:**
> i guess i should have mentioned that space after sudo is required. sorry

I think putting a space after sudo does not help because it does not run the uninstall application.
Using sudo/opt/Samsung/mfp/uninstall/uninstall.sh without a space after sudo runs the application but it gives an error message as follows:
"There was an error launching the application. Details: Failed to execute child process "sudo/opt/Samsung/mfp/uninstall/uninstall.sh" (No such file or directory)"
What is this child process and why it says there is no such file or directory. Can we create such a file or directory?

---

### Post by pbpersson on 2009-03-17
> **wstay said:**
> 
I try to use the terminal and cd to /opt/Samsung/mfp/uninstall and enter the command chmod +x uninstall.sh and then enter the command uninstall.sh and it gives an error message -'command not found'.

At the very last step here when you are in the /opt/Samsung/mfp/uninstall directory and you enter the command uninstall.sh, please put a period and a forward slash before the filename so it looks like:

./uninstall.sh

and see if that works.

---

### Post by wstay on 2009-03-17
> **pbpersson said:**
> At the very last step here when you are in the /opt/Samsung/mfp/uninstall directory and you enter the command uninstall.sh, please put a period and a forward slash before the filename so it looks like:

./uninstall.sh


I try this very last step with the following error message:
root@ubuntu8:/opt/Samsung/mfp/uninstall# ./uninstall.sh 
Qt: Session management error: None of the authentication protocols specified are supported
Cannot mix incompatible Qt libraries
Aborted
root@ubuntu8:/opt/Samsung/mfp/uninstall# chmod +x ./uninstall.sh 
root@ubuntu8:/opt/Samsung/mfp/uninstall# ./uninstall.sh 
Qt: Session management error: None of the authentication protocols specified are supported
Cannot mix incompatible Qt libraries
Aborted
root@ubuntu8:/opt/Samsung/mfp/uninstall# 

Perhaps you can help to explain the meaning of this error message.

---

### Post by pbpersson on 2009-03-17
> **wstay said:**
> 
Qt: Session management error: None of the authentication protocols specified are supported
Cannot mix incompatible Qt libraries
Aborted
root@ubuntu8:/opt/Samsung/mfp/uninstall# 

Perhaps you can help to explain the meaning of this error message.

I Googled the error message and it means you have the Qt libraries installed in two places on your machine and it is confusing the uninstall script.  That is all I can tell you, you would need to get more information by either Googling the error message or going to the web site where you found the driver to see if they have a forum or support knowledgebase....unless someone here is familiar with this problem

---

### Post by gandaran on 2009-03-17
use the same package you installed to uninstall, that package  has an install and an uninstall script, just follow the same steps you took to install but only deference is to type uninstall instead install.

---

### Post by wstay on 2009-03-18
> **gandaran said:**
> use the same package you installed to uninstall, that package  has an install and an uninstall script, just follow the same steps you took to install but only deference is to type uninstall instead install.

Using the same package I installed to uninstall and following the same steps I took to install to uninstall, I got the following error message:

wstay@ubuntu8:~/Desktop/UnifiedLinuxDriver/cdroot/Linux$ chmod +x uninstall.sh 
wstay@ubuntu8:~/Desktop/UnifiedLinuxDriver/cdroot/Linux$ sudo ./uninstall.sh 
[sudo] password for wstay: 
Failed to load widget from </home/wstay/Desktop/UnifiedLinuxDriver/cdroot/Linux/i386/share/ui/uninstalldialogbase.ui>
QMutex::unlock: unlock from different thread than locker
                was locked by 0, unlock attempt from -1223563584
wstay@ubuntu8:~/Desktop/UnifiedLinuxDriver/cdroot/Linux$ 

It says 'Failed to load widget from </home/wstay/Desktop/UnifiedLinuxDriver/cdroot/Linux/i386/share/ui/uninstalldialogbase.ui>'. And I do not see any directory or file name ui/uninstalldialogbase.ui. even with the Show Hidden Files check box checked in my File Browser.

---

### Post by gandaran on 2009-03-18
I'm sorry my post didn't work, just one question about this qoute
> root@ubuntu8:/opt/Samsung/mfp/uninstall# ./uninstall.sh 
are you in the right directory, is there actually an uninstall folder or just an uninstall.sh file? 
as a last resort you can delete every installed folder or file, open the install.sh or uninstall.sh file with gedit to find out where it installs every file.

---

### Post by wstay on 2009-03-19
> **gandaran said:**
>  
just one question about this qoute: 
root@ubuntu8:/opt/Samsung/mfp/uninstall# ./uninstall.sh 

are you in the right directory, is there actually an uninstall folder or just an uninstall.sh file? 

Yes, there is actually an uninstall folder and the uninstall.sh file is in this folder.

> 
wstay@ubuntu8:~/Desktop/UnifiedLinuxDriver/cdroot/Linux$ chmod +x uninstall.sh
wstay@ubuntu8:~/Desktop/UnifiedLinuxDriver/cdroot/Linux$ sudo ./uninstall.sh
[sudo] password for wstay:
Failed to load widget from </home/wstay/Desktop/UnifiedLinuxDriver/cdroot/Linux/i386/share/ui/uninstalldialogbase.ui>


There is no ui/uninstalldialogbase.ui. directory/file in the /home/wstay/Desktop/UnifiedLinuxDriver/cdroot/Linux/i386/share folder from where I had originally installed the printer driver.
The ui/uninstalldialogbase.ui. file is only found in the folder /opt/Samsung/mfp/share/ui under the root folder.

And running uninstall from the wstay@ubuntu8:/opt/Samsung/mfp/uninstall folder gives the following error message:
wstay@ubuntu8:/opt/Samsung/mfp/uninstall$ sudo ./uninstall.sh 
Cannot mix incompatible Qt libraries
Aborted
wstay@ubuntu8:/opt/Samsung/mfp/uninstall$ 

And running uninstall from (as root) root@ubuntu8:/opt/Samsung/mfp/uninstall gives the following error message:
wstay@ubuntu8:~$ su
Password: 
root@ubuntu8:/home/wstay# cd /opt/Samsung/mfp/uninstall
root@ubuntu8:/opt/Samsung/mfp/uninstall# chmod +x uninstall.sh 
root@ubuntu8:/opt/Samsung/mfp/uninstall# ./uninstall.sh 
Qt: Session management error: None of the authentication protocols specified are supported
Cannot mix incompatible Qt libraries
Aborted
root@ubuntu8:/opt/Samsung/mfp/uninstall#

So where can the uninstall problem be?

---

### Post by braigetori on 2009-04-29
ok, i was having the exact same problem as you (but with 9.04).

this is how i solved it: 

copy all the files in the i386 share directory (from opt; except for the images folder, b/c it is already there) into the original folder you used to install the driver (cdroot/Linux/i386)

then sudo the uninstall.sh in the origional folder and it worked, driver is gone.

this driver was causing problems with apt updates.

:b

---

### Post by testmiss123 on 2009-11-26
in the autorun script change the line to use bash instead of sh

Change this line:  exec sh $BASE/Linux/install.sh

To:  exec bash $BASE/Linux/install.sh

If that does not work change the 

#! /bin/sh  line in the install.sh script to #! /bin/bash as well and it should work.

---

