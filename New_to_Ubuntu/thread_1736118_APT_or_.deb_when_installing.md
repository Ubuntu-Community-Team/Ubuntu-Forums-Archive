---
title: "APT or .deb when installing?"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by SandJ on 2011-04-22
When being offered options for installing software,which is the correct one to choose?  For example, when going to install the Adobe Flash Player the choices are:

[FONT=Courier New]- YUM[/FONT] (it can't be that)
[FONT=Courier New]- .tar.gz[/FONT] (Ubuntu is easier than installing apps from a compressed file, I know that much)
[FONT=Courier New]- .rpm[/FONT] (something to do with Package Manager so sounds right)
[FONT=Courier New]- .deb[/FONT] (hmm it might be that; Ubuntu is something to do with Debian)
[FONT=Courier New]- APT[/FONT] for Ubuntu 9.04+ (seems obvious but doesn't work for me)

So, in order of 'correctness', which option should a Ubuntu user use?  :confused:

TIA.

---

### Post by jtarin on 2011-04-22
Menu>System>Administration>Synaptic........in the search box enter "flashplugin-installer". It will then use "apt" to download and install.
Quit thinking Windows way of installing . Use Synaptic.....why leave home searching for software. :)

---

### Post by frup on 2011-04-22
.deb is the correct version for you. .deb is like the file format. Apt is like the mechanism for installing, it uses debs still. 

APT is to .deb as YUM is to .rpm.

I think what the apt link is for apt url. For that to work you will need to be using the default firefox I think. 

If you're in the command line you would type sudo apt-get install packagename

apt-get pulls the deb for packagename and installs it for you.

---

### Post by SandJ on 2011-04-22
> **jtarin said:**
> Menu>System>Administration>Synaptic........in the search box enter "flashplugin-installer". It will then use "apt" to download and install.
 Quit thinking Windows way of installing . Use Synaptic.....why leave home searching for software. :)That is not actually helpful advice to a new user; you just made everything more obfuscated and been smug while doing so.  Also, you did not answer my question.

> **frup said:**
> .deb is the correct version for you. .deb is like the file format. Apt is like the mechanism for installing, it uses debs still. 

APT is to .deb as YUM is to .rpm.

I think what the apt link is for apt url. For that to work you will need to be using the default firefox I think. 

If you're in the command line you would type sudo apt-get install packagename

apt-get pulls the deb for packagename and installs it for you.Thank you.

So:
- last resort is "apt-get" the ".deb" file at the command line which downloads and installs the package;
- better is to select the .deb file from the Adobe menu which will download and install the package;
- better again is to select the APT which will automate the installation.

---

### Post by el_koraco on 2011-04-22
You really have little use for downloading files from the internet and installing them. Linux is built around "repositories", or large software containers, where all the software packages are stored. Apt is one of the tools which accesses and manipulates the packages in the repositories. It is the command line tool for handling dpkg, or the program which does the actual work. 

The GUI front ends for apt are the Ubuntu Software Center and Synaptic Package Manager. You can search either of these two for a package named ubuntu-restricted-extras, which contains the flash plugin, MS fonts, and all the codecs.

---

### Post by frup on 2011-04-22
Well in Ubuntu you want to be using the repositories to install most of your software.

The repositories are like an app store or market place database. You can find out more about this if you want to.

Apt-get is the system that accesses the repositories. .debs are the types of files stored in the repositories. 

The synaptic method the other member gave you is a very good GUI for doing things with Apt-get. Another method which is favoured now is software centre, it works similar but is the officially supported method for Ubuntu.

You don't want to install software from websites if you don't have to or know why you want to. Always check the repositories first.

So to install flash you use a program like Apt-get (in the command line), Synaptic (Very powerful) or Software Centre (nice and easy). You search for flash or for "restricted extras" and install that.

When asking for advice on the forums and searching the net you will always get more than one way to do things as there are more than one way. Everyone has their preferred version. Most of us prefer the command line to give information to others. While it may seem odd or hard to you think about this:

With the command line we can give you the exact information you need for you to copy and paste. It is really fast and we all know exactly what is going on, less room for error. If we try get you to do things GUI, there is a lot of room for mistakes and it is much more difficult to explain.

People don't help you in their free time because they want to be smug, they help because they are trying to help you. Be thankful they are trying.

---

### Post by el_koraco on 2011-04-22
[https://help.ubuntu.com/10.04/serverguide/C/package-management.html]("https://help.ubuntu.com/10.04/serverguide/C/package-management.html")

[https://help.ubuntu.com/community/AptGet/Howto]("https://help.ubuntu.com/community/AptGet/Howto")

[https://help.ubuntu.com/community/SynapticHowto]("https://help.ubuntu.com/community/SynapticHowto")

---

### Post by SandJ on 2011-04-22
> **frup said:**
> Well in Ubuntu you want to be using the repositories to install most of your software.  The repositories are like an app store or market place database.

Apt-get is the system that accesses the repositories. .debs are the types of files stored in the repositories.  The synaptic method the other member gave you is a very good GUI for doing things with Apt-get. Another method which is favoured now is software centre, it works similar but is the officially supported method for Ubuntu.An excellent explanation.  Thank you.

> **frup said:**
> You don't want to install software from websites if you don't have to or know why you want to.<insert jaw-dropping smiley here>  That is a change of philosophy!

It doesn't help then when the very first time I go to install something (Adobe's Flash Player), the software supplier lists Ubuntu as an option as a target system.  That did nothing to point me in the right direction!

> **frup said:**
> Always check the repositories first.

So to install flash you use a program like Apt-get (in the command line), Synaptic (Very powerful) or Software Centre (nice and easy). You search for flash or for "restricted extras" and install that.Got the message.  I'll remember that.  (It could do with being printed on the install CD I used!)

> **frup said:**
> When asking for advice on the forums and searching the net you will always get more than one way to do things as there are more than one way. Everyone has their preferred version. Most of us prefer the command line to give information to others. While it may seem odd or hard to you think about this:

With the command line we can give you the exact information you need for you to copy and paste. It is really fast and we all know exactly what is going on, less room for error. If we try get you to do things GUI, there is a lot of room for mistakes and it is much more difficult to explain.

People don't help you in their free time because they want to be smug, they help because they are trying to help you. Be thankful they are trying.'kay.  :oops:  A combination of not having something work, trying to find a solution for myself, finding lots of conflicting advice, then getting flamed in a newbie site for being confused does not make for a happy experience.

---

### Post by jtarin on 2011-04-22
> **SandJ said:**
> That is not actually helpful advice to a new user; you just made everything more obfuscated and been smug while doing so.  Also, you did not answer my question.
Thank you.

That advice was the most direct way to obtain your file and accomplish what you wanted....your the one that obfuscated your own request by not searching before asking. And what would you know about giving advice to anyone. Your the one that asked. If you don't like it don't follow it. The smugness is of your own paranoid imagination.Your one of those guys that should write your own manual on how people should deal with you....and let us download it before we help you.We would be so much wiser.....your welcome.And I never flamed you in my first post......just a short sweet and direct to the point.

---

