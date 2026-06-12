---
title: "Install Blender? (&quot;sudo apt-get install blender&quot; doesn't work)"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by Hellot on 2010-11-21
I'm trying to install blender. I downloaded it from the site, but don't understand how to actually install most things in Linux after I've downloaded them. I tried "sudo apt-get install blender" through the terminal and looked in Synaptic Package Manager with no luck.

I appreciate any help,
thanks

---

### Post by beew on 2010-11-21
In Linux you don't need to download most things from the sites. It is easier and better to install from the repository through the Software Center or Synaptic package manager (Under System > Administration) These are prepackaged versions for Ubuntu so they are mauntained regularly through Ubuntu's packaging system. The only catch is that the stable version in the Ubuntu repositories can be quite outdated. But you can get more updated versions by adding ppas (third party maintained repository) and once they are added you can download and install software from them through the SC or Synaptic (or the cli with sudo apt-get) like you would from the official Ubuntu repositories.

"sudo apt-get install whatever" is the command line that would install the package "whatever" from the repositories (The same as SC and Synaptic but without the GUI)   

So your command, when executed would have actually installed blender, but not the package you downloaded, rather, the one from the Ubuntu repo. The Ubuntu version is a bit old (2.4X?), if you don't mind trying a beta you can get a daily updated build by adding the blender ppa to your sources.
see here. [URL="http://www.webupd8.org/2010/07/blender-253-beta-3d-graphics.html"]http://www.webupd8.org/2010/07/blender-253-beta-3d-graphics.html

[/URL]

---

