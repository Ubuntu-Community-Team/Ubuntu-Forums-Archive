---
title: "A Beginner understanding Directories and Users"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by ugly_duckling492 on 2009-01-21
Here I am, a complete beginner to Ubuntu and Linux in general. I'm just getting into installing files and I'm having trouble understanding two concepts:

The types of users and their different privileges.
&
How the directory work.

(Being a windows de-convert, I'm finding installing files isn't as easy as clicking &#8220;next&#8221;, &#8220;accept Terms and Agreements&#8221;, &#8220;next&#8221; again, then &#8220;finish&#8221;.)

Can someone explain the different types of users, what their privileges are, and how to gain access to them? Specific commands would be helpful. :)

A brief explanation on directories would be nice too. For example, if I were installing &#8220;Java&#8221;, where would I...direct it? And what are all the other directories used for?

A more specific question, on the User Topic, is how can I gain access to the root user? Do I need to be the root user to install applications into the directory: usr/local (cause that's what the Java installation  instructions are telling me.) Any help is appreciated. :)****

---

### Post by LowSky on 2009-01-21
Ok first things first the directory is a little differnet but not hard to understand. Linux doesn't use letters for partitions or drives, rather it uses descriptions and label names.

so a hard drive wll be called sda. the drectory is set up with the root being the main directory, root is displaed as:  / 

files install the /usr directory and personall settings to /home

user works just like windows. but with more options. two biggest ooptions in Ubuntu Linux are users with admin rights and those without. admin rights is called sudo, (meaning super user do) it is a short cut to a root user as other Linux distro use.

Ubuntu make installing software easy with a program called Synaptic. It located under the System> Admin menu you can install many applicatinos, like java, flash, and mp3 codec, by just checking a box and clicking install. Much easier then windows, hunt for package, then click 5 times to make your point and hope it works. All packages in Syanptic will work, there is no guess work....

But if that wasn't enought you could install progrmas by typing the commands, or using the even easier Add/Remove application that makes synaptic look old a basic.

---

### Post by Ender Black on 2009-01-21
Here is a good tutorial on Folders: [http://tinyurl.com/ypceql](http://tinyurl.com/ypceql)

You don't need to log in to root to install applications.  In fact, in Ubuntu you have a two or three step process to even allow root log ins.  Instead, you have to use your SUDO password to install applications or change configuration files.

---

### Post by Titan8990 on 2009-01-21
First off, program installation in Debian based Linux (Ubuntu) is easier than in Windows. This does not apply to all Linux Distros.


You should be installing all your programs, including java, through the Synaptic Package Manager. This is found in System -> Administration.


Users and groups are what you define them as. The only user group you start with is the 'admin' group. This allows a user to use escalated privileges. There are other users and groups that are used my services, but these should not be changed.


You can get a Users and Groups GUI from System -> Administartion, or you can use these CLI tools:

adduser

cat /etc/group

cat /etc/passwd


To see more information on the adduser command:

man adduser



Linux directory structure: [http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)



Finding a program:

```
jordan@einstein:~$ which gedit
/usr/bin/gedit
```

```
jordan@einstein:~$ whereis gedit
gedit: /usr/bin/gedit /usr/share/man/man1/gedit.1.gz
```



> A more specific question, on the User Topic, is how can I gain access to the root user?


A) Use a different distro that allows direct access to the root user

B) Use sudo -i from the command line

C) Read the following here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)



And lastly, yes, you need to have privs to install to the /usr dir. Also note that what you have typed:

usr/local

is a "relative path". What this means is that it only applies to the directory you are currently in. In order for that path to be correct you would have to currently be in the / directory. The correct absolute path is:

/usr/local

This is because in Linux all absolute paths start with /


The equivalent in Windows:


Relative: "Program Files\notepad"

Absolute: "C:\Program Files\notepad"

---

### Post by oldos2er on 2009-01-21
"if I were installing &#8220;Java&#8221;, where would I...direct it?"

 Let the package manager handle it. Please read [https://help.ubuntu.com/8.10/add-applications/C/index.html](https://help.ubuntu.com/8.10/add-applications/C/index.html)

---

### Post by ugly_duckling492 on 2009-01-22
Yay! My questions are getting answered... all it took was a little looking. Anyways...

I got logged in as root user, and I'm trying to install an application. The rpm file, whatever that is (a quick mention of what it is would be nice), is downloaded to my desktop...

The install instructions are telling me that I need to "change the permission of the file you downloaded to be executable" then they instruct me to type the file name along with "chmod a+x" in front (is that part called a command? I'm new to all this... you were at my level at one point too!) 

Now, when I do so, it says that that file/directory doesn't exist... 

So confused!

---

### Post by oldos2er on 2009-01-22
RPM files are for Red Hat and its derivatives. Ubuntu uses packages called *.deb . What exactly are you trying to install? And why aren't you using one of the package managers? e.g. Synaptic, or Add/Remove.

---

### Post by cariboo on 2009-01-22
Before you try to install that .rpm file search System-->Administration-->Synaptic Package Manager for the program. If you still insist on installing that .rpm package, leave Synaptic open, as you are going to need to install a program to convert the .rpm to a .deb.

To convert .rpm's to .deb's you need a program called Alien. You didn't say which version of Ubuntu you are using, so I'll give you genaeral instructions. Click the search icon in Synaptic and type **alien** in the search box. Once the program has found alien right click on the package and select **mark for installation**, next click the mark button on the window that pops up, as you will notice there is a list of other packages that will be installed. Next click **Apply** then click **Apply** again on the window that pops up, this will start the download and installation process.

Once the package have been installed, you can close synaptic. Open an Apllications-->Accessories-->Termianl and type:

```
sudo alien -d ~/Desktop/<packagename>
```

The above command assumes that the rpm package is on your desktop. You will have to type the name of the package exactly in place of <packagename>. Once alien has done it conversion, you will need to install the package. To install the .deb package you can do it 2 ways, just double-click on the .deb file on your desktop and gdebi will automagically install it and any dependencies it needs, if it needs any and they are availabe. the second way is in the same terminal type:

```
sudo dpkg -i <packagename>
```

In this case rpelace <packagename> with the name of the .deb package.

As you can see in Linux there is always at least two ways to do anything.

Jim

---

### Post by hyper_ch on 2009-01-22
have a read here: [http://www.psychocats.net](http://www.psychocats.net)

---

