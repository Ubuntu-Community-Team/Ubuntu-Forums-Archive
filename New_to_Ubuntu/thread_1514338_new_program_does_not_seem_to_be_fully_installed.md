---
title: "new program does not seem to be fully installed"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by cetacean on 2010-06-20
I downloaded qCAD with Synaptic Package Manager, along with its help and manual. It seemed to work OK, but it does not show up under Applications.

I can type "qcad" in the terminal and it will run, but says it can't find help and manual.

How do I get the program, and its parts, to show up in Applications properly integrated?

thanks

---

### Post by MooPi on 2010-06-20
You can create a launcher by right clicking on the desktop. The drop down menu should give you a choice to configure a launcher. Fill in the categories and you should be on your way. I'm not certain but I believe you can copy this file to /usr/share/applications and if you filled in all the spaces for the launcher it should show up in your menu. As I don't use Gnome desktop regularly I'm not certain. Sorry for the disclaimer :-(

---

### Post by marshmallow1304 on 2010-06-20
It appears that the documentation is provided in a separate package: [qcad-doc]("apt://qcad-doc").

---

### Post by BrianV on 2010-11-07
I am having similar problems. There seem to be two parts: 1. Getting the qcad application to show in the Applications menu, and 2. getting the Help function to work in qcad.

Problem 1. seems to have been adequately addressed in the posts; the work-around does the job.

Problem 2. is still open. I installed all the qcad related packages using Ubuntu Software Center (10.04) and applied the work-around to get qcad to launch. When I select Help > Manual (or hit F1) a message shows up in qcad "File does not exist: /qcaddoc.adp (Package qcad-doc installed?) Profile '/qcaddoc.adp' does not exist." I un-installed, then re-installed the qcad-doc package, to no effect. Checking via a terminal the contents of /usr/share/doc/qcad-doc it shows only the copyright and changelog.Debian.gz files. /usr/share/doc/qcad/html contains a file qcaddoc.adp.gz. I wonder if there is a bug in the install process?

Any suggestions to get Help working?

---

### Post by Dakshinamurti on 2011-01-23
Hi!

Here is a solution I just discoverd. There are two steps needed.
1. unpack qcaddoc.afp.gz in /usr/share/doc/qcad/html
  ```
 cd /usr/share/doc/qcad/html
 sudo gunzip qcaddoc.adp.gz
```2. link this directory into the install-directory of qcad on lynx
   ```
cd /usr/share/qcad
 sudo ln -s /usr/share/doc/qcad/html doc
```That's it. Restart qcad and enjoy the manual.

---

### Post by BrianV on 2011-01-23
Thank you, Dakshinamurti, I tried your solution and it worked like a charm!:D

---

### Post by heyup on 2011-10-13
> **Dakshinamurti said:**
> Hi!

Here is a solution I just discoverd. There are two steps needed.
1. unpack qcaddoc.afp.gz in /usr/share/doc/qcad/html
  ```
 cd /usr/share/doc/qcad/html
 sudo gunzip qcaddoc.adp.gz
```2. link this directory into the install-directory of qcad on lynx
   ```
cd /usr/share/qcad
 sudo ln -s /usr/share/doc/qcad/html doc
```That's it. Restart qcad and enjoy the manual.

Is the code in step 2 correct? 

I'm using Lucid and there is no directory /usr/share/qcad 

The QCad executable is at /usr/bin/qcad

I have the same problem as the OP and BrianV, i.e. I cannot access the QCad HELP Manual.

---

### Post by heyup on 2011-10-16
> **heyup said:**
> 
I'm using Lucid and there is no directory /usr/share/qcad 


Something must have changed in the installation files of QCad. Terminal reports:

> :~$ cd /usr/share/qcad
bash: cd: /usr/share/qcad: No such file or directory


I've unpacked qcaddoc.adp.gz in /usr/share/doc/qcad/html ,but what directory do I link it to?

Can anyone solve this?

---

### Post by brawd on 2011-11-05
I had this problem too. I didn't do all that tar stuff I just downloaded from the repositories. I've also had this problem with other draughting programs such as geda.

Your problem is probably no more than finding the right path to the documentation, as mine was.

If you go to Synaptic package manager and enter qcad into the Quick search box it should show the Qcad doc as being installed. If not install it.

Select the file and right click with your mouse. From the box that comes up select Properties. Next select Installed files. Look down the list and you should be able to figure out the correct path to use in the solution offered above. You can always follow the path given to the file and trigger it from there. They are usually HTML files.

regards,

brawd.

---

### Post by andi11 on 2012-01-07
for me the following solution was successful (Lucid 10.04) to get the manual with the F1 button in qcad 2.0.5.0

1) repositories install: qcad / qcad-doc / qcad-data / libcad0-dev 

2) commandline:
sudo gunzip /usr/share/doc/qcad/html/qcaddoc.adp.gz
sudo ln -s /usr/share/doc/qcad/html /usr/share/qcad/doc

3) start qcad and press F1 button ;)

---

### Post by heyup on 2012-01-07
> **andi11 said:**
> for me the following solution was successful (Lucid 10.04) to get the manual with the F1 button in qcad 2.0.5.0

1) repositories install: qcad / qcad-doc / qcad-data / libcad0-dev 

2) commandline:
sudo gunzip /usr/share/doc/qcad/html/qcaddoc.adp.gz
sudo ln -s /usr/share/doc/qcad/html /usr/share/qcad/doc

3) start qcad and press F1 button ;)

This now works for me after adding repositories:

qcad-data 
libcad0-dev 

and then reinstalling all the qcad packages. 

I kept getting this error when trying to make the symlink:

> ln: creating symbolic link `/usr/share/qcad/doc': No such file or directory

Now sorted.

Thanks for your help.

---

