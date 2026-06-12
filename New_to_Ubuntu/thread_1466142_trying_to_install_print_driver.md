---
title: "trying to install print driver"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by noworldorder on 2010-04-30
ubuntu 9.10

total newbie

I have been trying to install a samsung ml-1915 printer for a few weeks with no luck.  The driver seems to require root privilages.  The instructions for installing are as follows:
**Linux**

                                                  You need to download Linux software packages from the Samsung website to install the printer software. 
           Follow the steps below to install the software.
                                                                           **Installing the Unified Linux Driver**

                 
               
             
                            
[LIST=1]
[*]                   Make sure that the machine is connected to your computer and powered on.
[*]                   When the Administrator Login window appears, type in root in the Login field and enter the system password.
                                                                                                                   [IMG]http://downloadcenter.samsung.com/content/UM/200911/20091119182011250/EN/common/note.png[/IMG]                                                  
                                                                                                 You must log in as a super user (root) to install the machine software. If you are not a super user, ask your system administrator.
[*]                   From the Samsung website, download the Unified Linux Driver package to your computer.
[*]                   Right click the Unified Linux Driver package and extract the package
[*]                   Double click cdroot > autorun.
[*]                   When the welcome screen appears, click Next.
[*]                   When the installation is complete, click Finish.
[/LIST]
                          It is not working.  I need to be in root but I don't know how to get those privilages in the GUI.  I made a new user account with administrator privileges but no luck.  The driver can be run normally or in terminal. When I run it in terminal it says there are no root privilages even in the new user account I made.


I thought of running it from terminal and using sudo but I can't get to the desktop where the driver is.  cd /Desktop cd ~Desktop cd desktop none of it works.


newbie needs help
thanks ~ chirs

---

### Post by Chronon on 2010-04-30
It seems that you need to run this "autorun" script/program with root privileges to install.  

In the terminal "cd" (the change directories program) to the directory containing "autorun".  The desktop is located at ~/Desktop.  (~ is a link to /home/*username*/)  Also, the bash shell is case sensitive, so you can do
```
cd Desktop
```from your home directory but 
```
cd desktop
```will complain about no such directory.

EDIT: Just to clarify that once you have navigated to the directory containing "autorun", you will want to do this:
```
sudo ./autorun
```

---

### Post by Vined Adobo on 2010-04-30
c

---

### Post by swoll1980 on 2010-04-30
nvrmnd

---

### Post by noworldorder on 2010-04-30
solved - it was just a matter of finding Desktop.  I was going to root then trying to find desktop which never worked.  So I wnt to desktop straight from home and it was ok.  I had to type ./ in frot of the script to run it.

Finally I can print.

thanks ~c

---

### Post by cuberts on 2010-04-30
> **noworldorder said:**
> ubuntu 9.10

total newbie

I have been trying to install a samsung ml-1915 printer for a few weeks with no luck.  The driver seems to require root privilages.  The instructions for installing are as follows:
**Linux**

                                                  You need to download Linux software packages from the Samsung website to install the printer software. 
           Follow the steps below to install the software.
                                                                           **Installing the Unified Linux Driver**

                 
               
             
                            
[LIST=1]
[*]                   Make sure that the machine is connected to your computer and powered on.
[*]                   When the Administrator Login window appears, type in root in the Login field and enter the system password.
                                                                                                                   [IMG]http://downloadcenter.samsung.com/content/UM/200911/20091119182011250/EN/common/note.png[/IMG]                                                  
                                                                                                 You must log in as a super user (root) to install the machine software. If you are not a super user, ask your system administrator.
[*]                   From the Samsung website, download the Unified Linux Driver package to your computer.
[*]                   Right click the Unified Linux Driver package and extract the package
[*]                   Double click cdroot > autorun.
[*]                   When the welcome screen appears, click Next.
[*]                   When the installation is complete, click Finish.
[/LIST]
                          It is not working.  I need to be in root but I don't know how to get those privilages in the GUI.  I made a new user account with administrator privileges but no luck.  The driver can be run normally or in terminal. When I run it in terminal it says there are no root privilages even in the new user account I made.


I thought of running it from terminal and using sudo but I can't get to the desktop where the driver is.  cd /Desktop cd ~Desktop cd desktop none of it works.


newbie needs help
thanks ~ chirsit seems that you have to actually connect the printer through CUPS

---

### Post by Chronon on 2010-04-30
Good to hear.  :)
Can you mark your thread as solved?

---

### Post by noworldorder on 2010-04-30
and ....    :oops:  how do I mark my thread 'solved'...

---

### Post by Chronon on 2010-04-30
Try the "Thread tools" link in your original post.  ;)

---

