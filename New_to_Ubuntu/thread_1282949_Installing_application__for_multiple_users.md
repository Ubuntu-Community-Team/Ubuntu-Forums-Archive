---
title: "Installing application  for multiple users?"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by PhysicsBrown on 2009-10-05
Is there a particular location that I should use to install an application that should be accessible to multiple users? I tried installing in /usr/share because it looked like a lot of shared apps were there, but the system says I don't have write access (even though I have administrative rights).
 
As you can probably tell by now, I'm a total beginner to Ubuntu. I have finally figured out how to install Java and Flash (I gave up on Ubuntu 8.04 and moved to 9.04, where it was easy!). Now I'm ready to install an application (a set of physics simulations called PhET) that uses those tools. This application is installed from a .bin file (that was a chore to find out how to install that, but I finally know how now). Now I just need to know where to install it so my students can access the application without giving them administrative rights.
 
Thanks in advance to anyone who can point me in the right direction!

---

### Post by tom.swartz07 on 2009-10-05
Ive only briefly heard of the PhET programs in my Physics classes. They seem really interesting! 

Although I dont know what method you are using to install the applications, I would assume that you are using the terminal, in which case you could just use ```
sudo **command**
``` and it should allow you to copy the programs to the share file.

Alternatively, if you are unable to do a *Hard Install* on the system, you might be able to find the programs hosted online here: [http://phet.colorado.edu/simulations/index.php?cat=Featured_Sims]("http://phet.colorado.edu/simulations/index.php?cat=Featured_Sims")

Let us know what happens!

---

### Post by wojox on 2009-10-05
Step 1: You need to navigate to the .bin file.

Step 2: Leave the .bin file in an easy to install location - I recommend the Desktop, but any location will work. Open the Terminal by navigating to Applications > Accessories > Terminal.

Step 3: CD to the folder you have the .bin file located. To do this, type cd + location . So, for example, if you have the .bin file download to the Desktop, type cd Desktop.

You should now have the word Desktop added to the Terminal code - name@name:~$ Desktop.

Now, type ls and hit ENTER so you don't have to switch between Terminal and Desktop to see the file name.

Type sudo chmod +x filename.bin to turn the .bin file into something that Ubuntu will install. Nothing will appear to happen, don't worry. Now, type ./filename.bin. This will start the installation file from within the Terminal. Don't freak out at the code that appears. If it pauses, read what the bottom says and read the instructions. Usually, it's telling you the file size of the program it's going to install, and requesting that you type Y for yes and hit ENTER.

Them just go to System > Administration > Users and Groups to set permissions.

---

### Post by PhysicsBrown on 2009-10-05
Thanks, but I have already succeeded in installing the app. The question is: How do I install it in the proper location so that other users can access it? 
 
Here's what happens now: My user name is physics, so the PhET application installs by default in a folder called /home/physics/PhET.  It runs fine when I'm logged on under the physics user name. But when I create another user name for my students, without administration priveleges, and then log on using the student user name, I am unable to run the application. I'm assuming that's because it's installed in the location that's only accessible by the physics user?
 
So I'm wondering if there is a "common area" where I can install the application, so that it will be accessible for any user that logs on? Or is it necessary for me to install the application separately for each user that I create? That would seem redundant, because then it would install a second copy of the application in a folder called /home/student/PhET. 
 
I know nothing about linux, but I noticed that there is a folder called /usr/share that seems to contain a lot of apps. So I was guessing that this might be the "common area" that I should install my to-be-shared apps into. But when I try to install it there I get an error message that says I don't have write access to that area.
 
Thanks to everyone for your patience with this absolute beginner.

---

### Post by tom.swartz07 on 2009-10-05
Follow wojox's guide for installing the programs under the student profile. 

If you run into any permissions problems during the install, just enter sudo before the command. It will prompt you for the admin password (the one you use for the Physics login) and then things will proceed as normal.

MOST programs will be installed correctly for all profiles when running the binary file, but some are hastily put together and sometimes skip this step. 

If you install it on the 'student' profile, you could be certain that it will be there, and that it wont be lost in translation between the several users.

Just remember to set the permissions of the program after its installed!

---

### Post by PhysicsBrown on 2009-10-05
Thanks again ... well, some of this makes sense, I think.  Feels like I'm on another planet. 
 
The good news: I think I may have solved the problem that I set out to solve. The secret seemed to be for me to right-click on the PhET folder, and to share that folder and adjust the permissions of that folder. After enough adjustments, it seemed to do the trick. I logged on as the student user, and then it was able to run it OK. So far it seems good.
 
I'm not sure exactly how to set the permissions of an application, but I'll fiddle around with that. But maybe it's not necessary since it seemed to fix the problem by adjusting the permissions of the folder containing the application. (Is any of this making sense? It's hard to go from speaking Windows to speaking Linux.)

---

### Post by tom.swartz07 on 2009-10-05
I totally understand the transition between Windows and Linux. You'll get the hang of it as you go along! :)

Im glad that you were able to get the programs to work! For future reference, that same operation could be completed by using the command ```
sudo chmod 555 /filepath/to/folder
``` under any user profile.

Hope you have fun with Physics and Linux - the 2 greatest things in the world!!

---

### Post by aesis05401 on 2009-10-05
I understand the confusion of other respondents due to the way your original post was worded. 

Provided your original installation is in a directory that will be available to the other users when they are logged in you should be able to :
```

# Add group physapps to local machine
sudo addgroup physapps

# Add desired applications to group physapps
sudo chgrp -v physapps <application-executable>

# Change group permissions to read and execute
sudo chmod -v g+rx <application-executable>

# Lock out users not of proper group
sudo chmod -v o-rwx <application-executable>

# Add existing users to the physapps group
sudo adduser <existing-user> physapps

```

I know that /usr/share is useful as an installation location for manually installed programs, but if you install with apt-get or synaptic you should be able to :
```

sudo find / -name <app-name>

```

to locate the files and simply add them to your physapps group. 

Does this make sense?  You actually have very very fine grained control over the permissions which is where the complexity comes in.  This is a brief overview of chmod and chgrp that is a little friendlier than the man [pages:http://www.tuxfiles.org/linuxhelp/fileowner.html]("http://www.tuxfiles.org/linuxhelp/fileowner.html") (follow link at bottom of page to chmod from chown/chgrp).

---

### Post by PhysicsBrown on 2009-10-07
Thanks, Aesis and Tom! This looks like useful info. So far I've just been playing around with the menus and the Users and Groups administrative tool, but it looks like I've got some more studying to do (after I finish grading this mountain of papers someday). I spent a few minutes reading over the Tuxfiles links, and that material certainly seems clear and well-written. Thanks for the resources.

---

### Post by 3rdalbum on 2009-10-07
Your ordinary user account can't make modifications outside your home directory, which is why you were getting "permission denied" when you tried to install the program to /usr/share.

You'd need to run the installer as root in order to put that program there. (hint: Type in "sudo -i" into a terminal, type your password, and then drag the installer to the terminal to run it as root).

/usr/share is an acceptable location for it. /usr/local or /opt is traditionally the more appropriate place, but I'm not going to tell you how to run your system :-)

---

