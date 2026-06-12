---
title: "Netgen"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by basilwatson on 2008-12-29
Hi all I need to install Netgen ( a meshing program ) 

I was up and running last week , installable as a .deb file ...

This week ( i reinstalled ubuntu 8.10 and all the dependency files are missing ... 

it starts with ,,Tk-dev , so you try and install that ... needs another and so on 

Whats the story here,  why was it all ok last week and not this week ,,

No I haven't upgraded just a reinstall with the same disk as last time ! 


Stephen

---

### Post by Michael.Godawski on 2008-12-29
When you install an applications via the terminal or Synaptic, you may have seen that additional packages were also installed with the actual package.

A package needs other packages to work -  it needs dependencies.

When you work with your system, and install new stuff you collect quite a bunch of additional dependencies. Some of them are used by one application, some of them are used by many other programs. 

Last week you did not have to install the dependencies for netgear, because you had them already installed.

Just install the needed packages and have fun. Report back if there are any problems.

See also:


[LIST]
[*] [htt]("https://help.ubuntu.com/community/InstallingSoftware#Package")[ps://help.ubuntu.com/community/InstallingSoftware#Package Dependencies]("ps://help.ubuntu.com/community/InstallingSoftware#Package%20Dependencies")
[/LIST]

---

### Post by basilwatson on 2008-12-29
Have tried that ,,,and when I got to lib x11-6 or something like that it stalled saying could not install ,,,and there are a lot of dependencies ...eleven of which 3 I could install ,,,they have to go in an order as one depends on the other ,,which order ,,

No there has been an update , or a change in the repositories which has caused this ,,, 

I have a customer comming on the third ,,and this hasnt made life easy ,,, 

Stephen

libx11-dev:
  Depends: libx11-6 (=2:1.1.5-2ubuntu1) but 2:1.1.5-2ubuntu1.1 is to be installed
 Depends: x11proto-input-dev but it is not going to be installed

and so on try to install one and it depends on the other,,,,,,,

---

