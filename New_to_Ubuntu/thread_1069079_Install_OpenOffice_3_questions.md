---
title: "Install OpenOffice 3 questions"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by NewJack on 2009-02-13
Here is my situation so far:

-I am using Ubuntu Intrepid.
-I uninstalled OOo 2.x and installed OOo 3.0 using the instructions on Tombuntu's blog (Here: [http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)).
-No problems with OOo 3 to date.

Now.....

I would like to update to OOo 3.1 .  Do I just grab the .deb from the OOo site and install over my existing OOo 3.0 or do I have to completely uninstall v 3.0 first?  Or, can I put the OOo PPA in my sources.list, update and should OOo update it

---

### Post by BDNiner on 2009-02-13
I have the exact same question. With my experience from upgrading from kde4.1 to kde4.2, i just had to add the new repository and I was prompted to upgrade by software manager. But since i installed it using tombuntu's guide i have no idea.

I think i will uninstall OOo 3.0 first.

---

### Post by Meow27 on 2009-02-13
fr om my own experience with windows the answer is the same with linux; you have to the latest intallation files, using the updating feature in linux will simply download the latest DEB installation files 

i personally like [http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

but your link will do as well

edit- play it safe and remove your old version of openoffice before installing the new one

---

### Post by howefield on 2009-02-13
If you use a repository, you are more likely to get updates.

Try the link here

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by gjoellee on 2009-02-13
You can download the DEBS from [www.openoffice.org]("http://www.openoffice.org") extract the folder. Then use the following command:
```
cd /path/to/OOo3.1/folder/DEBS
```then use the following command:
```
sudo dpkg -i *.deb
```then:
```
cd desk*
```then again:
```
sudo dpkg -i *.deb
```

---

### Post by spcwingo on 2009-02-13
I just downloaded from Sun and used the included update script.

---

### Post by BDNiner on 2009-02-13
Thank you for the softpedia link. I will add that link tonight. If i add the link will ubuntu determine that i already have OOo 3 install and prompt me to upgrade or am i better off uninstalling it and using the repo to reinstall the newer version?

---

### Post by howefield on 2009-02-13
The first paragraph in the link explains that it will be an upgrade.

---

### Post by BDNiner on 2009-02-13
Sorry, the site is blocked at my job so i can't check the link until i get home.

---

### Post by NewJack on 2009-02-13
Thanks for the responses.  It turns out that when I posted this, the update option wasn't working for some reason.  I just decided to give another go at it and now it is updating.

---

