---
title: "Installing/running the Eclipse platform on Ubuntu"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by gemm on 2009-05-14
Hi,

I have problems with installing/running the Eclipse platform on my Ubuntu. At least, it is not what I think it should be. Here are the problems:

I have first installed Eclipse from Add/Remove programs. The version, which was installed, however, was the old Eclipse 3.2. I have seen what packages there are in Synaptic Package Manager, but the latest, which I managed to find (see) was Eclipse 3.2.2. Therefore, I downloaded the last version from the Eclipse web site: Eclipse 3.4.2 (Ganymede) as .tar.gz file. I unpacked the file and I was able to run eclipse by clicking "eclipse" form the File Browser. However, I cannot run it from the console, because I think that it is not installed in the real sense on ubuntu:

-- when (being in the untarred Eclipse directory) I try to run Eclipse from the console, typing:
> eclipse &
I get the following message:  The program 'eclipse' is currently not installed.  You can install it by typing:
sudo apt-get install eclipse
bash: eclipse: command not found

So, I type:
> sudo apt-get install eclipse
then I am prompted to type my password, and I get

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  eclipse-gcj eclipse-jdt eclipse-jdt-gcj eclipse-pde eclipse-pde-gcj eclipse-platform eclipse-platform-gcj eclipse-rcp
  eclipse-rcp-gcj eclipse-source
The following NEW packages will be installed:
  eclipse eclipse-gcj eclipse-jdt eclipse-jdt-gcj eclipse-pde eclipse-pde-gcj eclipse-platform eclipse-platform-gcj
  eclipse-rcp eclipse-rcp-gcj eclipse-source
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 105MB of archives.
After this operation, 195MB of additional disk space will be used.
Do you want to continue [Y/n]? 

By typing "Y", files from [http://de.archive.ubuntu.com/ubuntu/pool/universe/e/eclipse/](http://de.archive.ubuntu.com/ubuntu/pool/universe/e/eclipse/) are tried to be fetched. For example, eclipse-rcp_3.2.2-5ubuntu2_i386.deb. As you can see this is again the old version of Eclipse. 

So, my question is: is there a way to install the latest Eclipse package, which I have downloaded as .tar.gz file, so that Eclipse is installed on Ubuntu and I am able to start it from the menu (Applications --> Programming --> Eclipse) or from the console (by typing eclipse &) as I can do is I install it using the package manager? 

Also, I assume that this will be a problem with other software packages, which I download as .tag.gz files. What is the general correct way to install packages from .tar.gz files? I will need to do this, if there is no specific .deb file for Ubuntu or if (as in this case) there is no newer version available. On other linux platforms I have done this with:
make
make install 
Is this the way for such packages on Ubuntu?

Thank you in advance!

---

### Post by jespdj on 2009-05-14
Instead of typing "eclipse" when you are in the Eclipse directory, type "./eclipse".

Make sure you have Sun Java 6 installed:
```
sudo apt-get install sun-java6-jdk
sudo update-java-alternatives -s java-6-sun
```

---

### Post by MaindotC on 2009-05-14
When you downloaded the compressed eclipse package, it uncompresses to show the compiled binary.  Their site offers the same thing for Windows - it's a zip file that includes a .exe and there's no installation process.  In my experience, this is not how you typically install a program but a binary is a binary so I'm not sure what the big difference is.  If anything it could be helpful in the sense that it comes with everything you need and if there's a problem you can just delete the file instead of going through caches and library directories to remove lingering parts.

Tar.gz files typically do come with a configure, make, and make install script which execute when you type "configure, make, make install".

My professor wanted us to use 3.2 because of some sort of compatability issue w/ Eclipse and the java packages we had to install in Windoze.  As you can tell by [this thread](http://ubuntuforums.org/showthread.php?t=1048046) he was also paranoid about me using Eclipse on my Linux platform instead of in Windoze, but it still worked fine (except we had to use msdb files).

Installing programs from Synaptic is usually the best way to install them because from the Ubuntu repos they are supported, and typically other users who host [a personal repository for others](http://ppa.launchpad.net/) have tested the packages on the distribution you need.

I don't really know the difference between apt and synaptic but I do know that Synaptic usually auto-fixes any compatability issues with versions of .deb's.

As for installing the latest version of Eclipse, I'd check the PPA link and see if any of them have the latest eclipse packages you need.  However, I advise you that if the Ubuntu repos only offer 3.2 it may be for a reason.

---

### Post by gemm on 2009-05-14
When I try typing: 

sudo apt-get install sun-java6-jdk

I get the following messages:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

and I am unable to install it. What does it mean?

---

### Post by whelanh on 2009-05-14
That message means that you have some other program open/running that is also able to install programs.  It is likely you have synaptic (ubuntu) or adept (kubuntu) open.  If you shut them down and re-submit your console command, it should work.

---

### Post by kpkeerthi on 2009-05-14
[https://wiki.ubuntu.com/UbuntuBackports]("https://wiki.ubuntu.com/UbuntuBackports"). You can read from this wiki link why packages are not always up-to-date in ubuntu repository.

You only need to make, make install if you want to compile and install a program from source bundle. And not all tar.gz are source bundles. 

As for eclipse, you can just download the archive off eclipse's website (if you want the latest version), extract it to your home folder, cd to it and run **./eclipse**. There is no need to make and make install since eclipse is Java based. You can even add a shortcut to it by right-clicking on Application -> Edit Menus. And yes, be sure you have [sun-jdk or open-jdk installed and selected as default]("https://help.ubuntu.com/community/Java").

---

### Post by kpkeerthi on 2009-05-14
How to compile from source: [https://help.ubuntu.com/community/CompilingSoftware]("https://help.ubuntu.com/community/CompilingSoftware")

Create a deb: [https://help.ubuntu.com/community/CheckInstall]("https://help.ubuntu.com/community/CheckInstall")

---

### Post by Trebaruna on 2009-05-14
The reason you can't start eclipse from the terminal, gemm, is that the terminal looks in a standard set of directories for the file you're trying to run. If it can't find it, it will --in this case-- search its list of software and determine eclipse can be found in some package or other.

So: what you do is, you make sure the binary you want to run is in one of those directories! Copy or move the file into /usr/local/bin/ using root, and make sure the file is world readable and executable (chmod go=rx). Now, wherever you are, typing eclipse will start that program.

---

### Post by gemm on 2009-05-14
> **Trebaruna said:**
> 
So: what you do is, you make sure the binary you want to run is in one of those directories! Copy or move the file into /usr/local/bin/ using root, and make sure the file is world readable and executable (chmod go=rx). Now, wherever you are, typing eclipse will start that program.

Hi,

in my home eclipse directory (where the executable file "eclipse" is) I have typed:
> chmod go=rx eclipse
then
> sudo cp eclipse /usr/local/bin/ 

However, when I try to run eclipse from other directory (and in the current directory without ./) I get a pop-up window, which says:
"The Eclipse executable launcher was unable to locate its companion shared library."

In the unpacked eclipse directory there are other files and directories except the executable "eclipse" file. Should I copy all/some of them to /usr/local/bin/ , too?

---

### Post by MaindotC on 2009-05-14
Instead of doing that just run Eclipse from the folder which you downloaded.  I have the same issue with Second Life - there's no installable client for Linux so you have download this folder and run the executable from the folder.

---

