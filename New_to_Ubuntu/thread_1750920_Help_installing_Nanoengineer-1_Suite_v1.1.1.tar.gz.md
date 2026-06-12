---
title: "Help installing Nanoengineer-1 Suite v1.1.1.tar.gz with Ubu 10.04"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by joelorenzo on 2011-05-06
Hi all,

I've downloaded a program called [NanoEngineer-1]("http://nanoengineer-1.com/content/index.php?option=com_docman&task=cat_view&gid=22&&Itemid=52") but it came as a tar.gz. I have been searching through forums for the past couple of days and I'm completely stumped. I have tried the tar -xvzf pkg.tar.gz command but all that does is sprinkle the contents in my /home folder. Any help would be GREATLY appreciated. 

Thanks,
Joe

---

### Post by technologiclee on 2011-05-06
Hi,

I have tried installing Nanoengineer-1 and succeeded a few time, although not on the newest version of Ubuntu.

Where did you download NE-1 from? Nanorex? I have heard that it has been recently packaged for Fedora.

I eventually asked for NE-1 to be packaged for ubuntu. As far as I know it still has a status of "wishlist"

Here are some of my notes on installation. There is a link at the bottom to more detailed notes.

[http://ubuntuforums.org/showthread.php?t=1080172]("http://ubuntuforums.org/showthread.php?t=1080172")

Basically you have to install several dependencies then you can run NE-1. Some of these programs that it relies on are now no longer in the Ubuntu repositories because there are newer versions. It is necessary to download them from their host websites. The software is worth the effort. I never did get the simulator to run in Linux, but that is a matter of moving one file (correctly).

I have used NE-1 on other platforms and there is nothing else that I have seen that does the job as well.

If you have any questions, I will try to help. Also check the wiki. There is also a development group to continue work on NE-1.


nanoengineer-dev.googlegroups.com

Please keep me posted on your progress or any NE-1 related news.

Thanks,
Lee

---

### Post by Fraoch on 2011-05-06
> **technologiclee said:**
> I have heard that it has been recently packaged for Fedora.

If that's the case, alien can repackage it into a .deb that Ubuntu uses.  It worked the few times I tried it for other packages.

alien is in the Ubuntu repos.

---

### Post by technologiclee on 2011-05-06
I have heard of Alien and would like to try it. Here is where I saw a mention of a Fedora package.

[http://groups.google.com/group/nanoengineer-dev/browse_thread/thread/5a4c50cec04425a0/3e048149efabab49?lnk=gst&q=+When+I+packaged+NE1+for+Fedora+I+added+a+patch+#3e048149efabab49]("http://groups.google.com/group/nanoengineer-dev/browse_thread/thread/5a4c50cec04425a0/3e048149efabab49?lnk=gst&q=+When+I+packaged+NE1+for+Fedora+I+added+a+patch+#3e048149efabab49")

Here is the packaging thread for Fedora...
[https://bugzilla.redhat.com/show_bug.cgi?id=541765]("https://bugzilla.redhat.com/show_bug.cgi?id=541765")

Here is my request for packaging:
[https://bugs.launchpad.net/ubuntu/+bug/357053]("https://bugs.launchpad.net/ubuntu/+bug/357053")

Please let me know if you find a NE-1.deb or .rpm

Thanks,
Lee

---

### Post by joelorenzo on 2011-05-07
Ok great, 
I will on it and I will get back to you.
Thanks for the help.
-Joe

---

### Post by Pinkeye on 2011-06-25
I recently tried to compile NanoEngineer on Maverick ..i got partial functionality, but had to do alot of work.  I found that the source code needs to be upgraded to work with ubuntu10.10.  I will post somthing more thorough later, but here's what i did. 

i began my library package dependency hunt with NanoEngineer's outdated build page. This is a good place to see what is gonna be needed, but it is outdated. 
 [http://nanoengineer-1.net/mediawiki/index.php?title=Building_NanoEngineer-1_on_Linux](http://nanoengineer-1.net/mediawiki/index.php?title=Building_NanoEngineer-1_on_Linux)

**List of Packages: **
  *note- this may not be a complete list ...i had to try a lot of different packages... if you try all of these and get errors be sure to install any dev files. 
      -look for 'strange-but-related libraries' with cmd   ' * apt-cache search package* '...this will usually spit out lists of dependent libraries.... ex.  apt-cache search qt4
      - *dpkg -l | grep package*   ..to see what you already have installed 

python 2.6        ..its a good idea to run python -v to see what version you have ...some libraries only work with certain python versions

idle ..not idle3..idle works with python 2.6 ..idle3 works with python3   ...this took forever

python-qt4
python-qt4-dev
python-qt-dev
libqt4-dev
qt4-dev-tools
qt4-qtconfig
python-qt4-gl
libqt4-opengl
libqt4-opengl-dev

sip4
python-sip
python-sip-dev

pyqt-tools
pyqt4-dev-tools


python-numpy

python-numeric
python-numeric-ext

python-ctypeslib

libgle3
libgle3-dev

python-imaging
python-imaging-tk

libdb4.8
libdb-dev
*may try 4.7 ..also these were a pain.  I have more Berkley Database software than i can list (ie stuff that has libdb, db4.8, is all Berkley Databse software) I think these are right, but may not be all of it. 

freeglut3             *not sure if these are neccessary
freeglut3-dev

python-pyrex  *not sure about this one either

openbabel
python-openbabel

gnuplot
python-gnuplot

Source Code alterations:

**Change 1**: [http://diyhpl.us/cgit/nanoengineer-theirix/commit/?id=549a7d50411e64cddef0df8a4b2cc335a333e3bc](http://diyhpl.us/cgit/nanoengineer-theirix/commit/?id=549a7d50411e64cddef0df8a4b2cc335a333e3bc)

 alter cad/src/files/mmp/files_mmp.py  in whatever directory you untared nanoengineer  (..its around line 927)
  You need to change some lines in files_mmp.py due to changes in python. Go to link, 
 and change the lines in red to say what is in green.  You need to change a variable    called 'as' to 'atomset' ....'as' is now a reserved word in python ..or something of that nature. im not sure. 

 _The code was..._
 as = AtomSet(self.assy, list1) # create atom set and set props 
as.name = name
 as.color = col
 self.addmember(as)

_ change it too..._

 atomset = AtomSet(self.assy, list1) # create atom set and set props
 atomset.name = name
 atomset.color = col
 self.addmember(atomset)


**Change 2**: [http://osdir.com/ml/fedora-package-review/2010-03/msg03387.html](http://osdir.com/ml/fedora-package-review/2010-03/msg03387.html)

this is a 'fix' for fedora, but it worked in maverick too.  a compile error complains about not being able to find where a gui button is located. Comments in the code tell the size of the button needed ..so i may just use gimp and make my own....i think this 'fix' causes other problems...but anyways; change this file in the directory where you unpacked NanoEngineer
 cad/src/ne1_ui/toolbars/FlyoutToolbar.py
line 72 is the offending line.  
 > extension_button = self.getExtensionButton()
             if extension_button:  <--------------add this line
                         extension_button.setIcon(geticon(...thats all i have, i will try to post more when i have time


to run NanoEngineer, open a terminal and cd to directory where NanoEngineer has been untared, then in the terminal

 cd  NanoEngineer/cad/src               <--- change directory to the cad/src directory of NanoEngineer where main.py is located
 python main.py                                           <--- run main.py    ....i spent a while looking for something to ./configure , and the make install.   Thats not needed here, lol.

---

