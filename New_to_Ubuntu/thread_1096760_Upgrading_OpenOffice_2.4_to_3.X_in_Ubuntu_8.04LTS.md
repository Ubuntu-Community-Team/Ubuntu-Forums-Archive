---
title: "Upgrading OpenOffice 2.4 to 3.X in Ubuntu 8.04LTS"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by suomalainen on 2009-03-15
Ubunteros,

Is it possible to upgrade OpenOffice 2.4 to 3.x under Ubuntu 8.04LTS???

I looked in Synaptic Package Manager for OpenOffice 3 but nothing was available.

What can be done?

Thanks!

P.S. Why doesn't OpenOffice in Ubuntu have an upgarde button like OpenOffice has in WIndows XP???????????

---

### Post by .nedberg on 2009-03-15
I have not tried this myself, but add the repos from this page:
[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)
(remember to change the drop down to hardy)

then you can follow this how-to:
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

The upgrade button is removed because Ubuntu handles the updating of OOo

---

### Post by cotcot on 2009-03-15
EDIT : solution deleted. The solution above is better as the poster below wrote.

---

### Post by vanadium on 2009-03-15
.nedberg's advice is the better option. That way, you are installing OOo 3.0 the regular way, i.e. using Synaptic. You also get updates automatically in the usual way.

I have done the upgrade because I had a nasty pdf export bug in the regular version. It works very well.

---

### Post by sydbat on 2009-03-15
Yes, follow .nedberg's advice. This worked without a problem for me. 

The only thing I had to do was reinstall the dictionaries because it is a different extension with 3.0...one of the links above has the instructions for this...I believe.

---

### Post by suomalainen on 2009-03-15
Thanks everyone for the advice! Now for the dumb question. I'm not too sure how to get started. Do I open up terminal and copy the commands there or what exactl?

---

### Post by fooman on 2009-03-15
this should explain it pretty easily (and yes,  just copy and paste the commands into a terminal):

[http://ubuntuforums.org/showpost.php?p=6210799&postcount=1](http://ubuntuforums.org/showpost.php?p=6210799&postcount=1)

---

### Post by vanadium on 2009-03-15
See [https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories), which in turn links also to the related Ubuntu help page: [https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html](https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html)

---

### Post by presence1960 on 2009-03-15
> **suomalainen said:**
> Ubunteros,

Is it possible to upgrade OpenOffice 2.4 to 3.x under Ubuntu 8.04LTS???

I looked in Synaptic Package Manager for OpenOffice 3 but nothing was available.

What can be done?

Thanks!

P.S. Why doesn't OpenOffice in Ubuntu have an upgarde button like OpenOffice has in WIndows XP???????????

Here is a link : [http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

Note : Just make sure to edit the commands so that the correct filename shows. I did this in Mint 5 (which is Hardy) and Intrepid.  To install menus though I had to figure out to double click the openoffice.org3.0-debian-menus_3.0-9376_all.deb file in desktop-integration folder. For some reason the command on the web page didn't work.

---

### Post by suomalainen on 2009-03-15
Fooman,

As you can see since the time of your last post to me.... The process you pointed me to went real smoothly and I'm finished and upgraded to 3.0!!!!

Thank's very much for pointing me to this tutorial. It was easy to undetstand, read and implement!

Everything worked perfectly!!!!!

Thanks Again!!!!!

---

### Post by fooman on 2009-03-15
glad it helped.  :)

---

