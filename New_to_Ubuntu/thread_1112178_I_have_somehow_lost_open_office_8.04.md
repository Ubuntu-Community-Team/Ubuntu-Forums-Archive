---
title: "I have somehow lost open office 8.04"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by LeeHamo on 2009-03-31
Somehow I have lost openoffice, I say somehow but I have been screwing around trying to install version 3 and I think ive totalled the whole thing.

terminal had errors and I aint got any kind of openoffice stuff in my office tab.

Anyone care to help me please, I have a load of college stuff to print out for tomorrow night and I need an open office that can open .docx files.

Cheers,

Lee.

---

### Post by abn91c on 2009-03-31
reinstall 2.4 from synaptic then use this guide for 3.0 [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by LeeHamo on 2009-03-31
Thanks, can you tell me which one in synaptic I am to choose, I chose one and it said I had unresolved dependencies or something.

---

### Post by LeeHamo on 2009-03-31
please someone help me

---

### Post by Idaho Dan on 2009-03-31
LeeHamo,
try the Add/Remove Applications. Everything that starts with Openoffice.org.

---

### Post by kiridude on 2009-03-31
I would suggest from a terminal:

sudo aptitude remove open office

to clean up, then:

sudo aptitude install open office

that should fix it.

---

### Post by chinni.joy on 2009-03-31
hi 
[B]
Try below guide lines for openOffice 3.0[/B];-

  
Upgrading OpenOffice suite

    Open terminal and Type this command:
         sudo gedit /etc/apt/sources.list
 
and paste this below lines in that file:

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main

now close that file.

type this command:
   sudo apt-get update.

After completion of previous command type this commd:

  sudo synaptic

search for 'sun openOffice' and select checkboxs of openoffice.org and click -> apply button ->install

you dont need it to remove it or uninstall old one .

---

### Post by LeeHamo on 2009-04-17
> **chinni.joy said:**
> hi 
[B]
Try below guide lines for openOffice 3.0[/B];-

  
Upgrading OpenOffice suite

    Open terminal and Type this command:
         sudo gedit /etc/apt/sources.list
 
and paste this below lines in that file:

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main

now close that file.

type this command:
   sudo apt-get update.

After completion of previous command type this commd:

  sudo synaptic

search for 'sun openOffice' and select checkboxs of openoffice.org and click -> apply button ->install

you dont need it to remove it or uninstall old one .

Thanks for the replies guys, I did the above and got this message when I marked openoffice.org for installation:

Could not mark all packages for installation or upgrade

The following packages have unresolved dependencies.  Make sure all required repositories are added and enabled in the preferences.

openoffice.org:
 Depends: openoffice.org-core but it is not going to be installed
 Depends: openoffice.org-writer but it is not going to be installed
 Depends: openoffice.org-calc but it is not going to be installed
 Depends: openoffice.org-impress but it is not going to be installed
 Depends: openoffice.org-draw but it is not going to be installed
 Depends: openoffice.org-math but it is not going to be installed
 Depends: openoffice.org-base but it is not going to be installed
 Depends: openoffice.org-report-builder-bin but it is not going to be installed
 Depends: openoffice.org-officebean but it is not going to be installed
 Depends: openoffice.org-writer2latex but it is not going to be installed
 Depends: liblucene2-java but it is not going to be installed

---

### Post by LeeHamo on 2009-04-17
> **kiridude said:**
> I would suggest from a terminal:

sudo aptitude remove open office

to clean up, then:

sudo aptitude install open office

that should fix it.

Tried this one next, seemed to have worked but I cant open documents.

---

### Post by howefield on 2009-04-17
Which version of open office have you got installed now ?

---

### Post by LeeHamo on 2009-04-17
> **howefield said:**
> Which version of open office have you got installed now ?

Whichever one I got when I did this:

sudo aptitude remove open office

to clean up, then:

sudo aptitude install open office

But it doesnt work.

---

### Post by LeeHamo on 2009-04-19
I guess this is unsolvable, ah well it was my fault.

---

### Post by hesjnet on 2009-04-19
You say you can't open documents? Can you be a bit more precise?

Have you tried to open the appropriate Openoffice program (writer,calc,presentation) to try to open the document from inside the program? 
[LIST=1][*]Open Word Processor[*]Click on "File"[*]Click on "Open.."[*]Try to locate the file and open it.
[/LIST]

If this works, then it is not openoffice that is the problem, it is the file-associations. To fix this you have to right-click on the document that is not opening and click on the tab called "open with". Choose the appropriate openoffice program you want it to open in:popcorn:

Good luck.

---

### Post by LeeHamo on 2009-04-20
Ok so I right clicked a word document, created in openoffice before it broke, and selected open with, the only one related to openoffice is openoffice.org, clicked that and it loaded for a bit then dissapeared.

Another thing in update manager I have this:

[ATTACH]110396[/ATTACH]

Always been shaded out since I tried to update to 3.0 and broke the whole lot.

Cheers.

---

### Post by LeeHamo on 2009-04-21
anyone have any further help on this or is it a lost cause?

---

### Post by LeeHamo on 2009-04-22
Thanks for trying everybody, I didnt expect to fix this.

Lee.

---

