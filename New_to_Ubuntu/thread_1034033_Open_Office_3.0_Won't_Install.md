---
title: "Open Office 3.0 Won't Install"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by browndog on 2009-01-07
I've downloaded Open Office 3.0 from [www.openoffice.org](www.openoffice.org), but when I decompress and try to install it I get a message telling me that many dependent files are missing.  When I search for it in the Synaptic repositories (and yes, I have them all enabled) I find nothing.  Any ideas?

---

### Post by solitaire on 2009-01-07
First thing is to remove the current Open Office in Ubuntu using Synaptic (their is conflicts running both versions i think!)

Open up a terminal and go to the "OOO300_m9_native_packed-1_en-US.9358" folder (Thats the folder you extracted from teh tar.gz file) Then go in to the "DEBS" folder and run the following:
```

sudo dpkg -i *.deb

```
This installs all the debs in the correct order.
Then go in to the "desktop-integration" folder and install that .deb (it adds in the menu items).

you should now have Open Office 3 in your Applications menu :D

---

### Post by Wildgoosechaser on 2009-01-07
did you make sure you downloaded the .deb file? I made that maistake but realized it pretty quickly.

---

### Post by fooman on 2009-01-07
you could try it this way:

[http://ubuntuforums.org/showpost.php?p=6210799&postcount=1](http://ubuntuforums.org/showpost.php?p=6210799&postcount=1)

hope that helps. :)

---

### Post by razar45 on 2009-01-07
> **fooman said:**
> you could try it this way:

[http://ubuntuforums.org/showpost.php?p=6210799&postcount=1](http://ubuntuforums.org/showpost.php?p=6210799&postcount=1)

hope that helps. :)

Ya thats what i did =P

---

### Post by abn91c on 2009-01-07
have you tried this guide instead: [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by razar45 on 2009-01-07
that works?

---

### Post by beastrace91 on 2009-01-07
> **abn91c said:**
> have you tried this guide instead: [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

That guide works wonderfully.

~Jeff

---

### Post by hyper_ch on 2009-01-08
is there any reason why you must have the latest OOo version=?

---

### Post by jdelasalas on 2009-01-08
I downloaded the most recent version of Open Office and I made the mistake of trying to install it right off the bat.  I painstakingly removed all traces of Open Office through the package manager then installed all the .deb files.  In retrospect, all that work wasn't really worth it, but everything does look shinier.

---

### Post by Dumbestcrayon on 2009-01-08
I was told that this wouldn't work but I did it anyways and I have 3.0 now.


```
sudo apt-get remove openoffice.org
sudo apt-get update
sudo apt-get install openoffice.org
```

---

### Post by sauravghosh on 2009-01-08
> **Dumbestcrayon said:**
> I was told that this wouldn't work but I did it anyways and I have 3.0 now.


```
sudo apt-get remove openoffice.org
sudo apt-get update
sudo apt-get install openoffice.org
```

What repository are you using that has 3.0?  I just tried this using multiverse and I still have only 2.4...

---

### Post by browndog on 2009-01-08
> **hyper_ch said:**
> is there any reason why you must have the latest OOo version=?
For the same reason I always want the latest Ubuntu distro...I'm a free software freak and have love to be on the bleeding edge.

---

### Post by hyper_ch on 2009-01-09
why don't you then compile things from latest svn?

---

### Post by Firestem4 on 2009-01-09
scratch that -(erased wehat i previously wrote) I made a big booboo. I had to remove openoffice and it had broken packages so I have to rebuild its dependencies and probably revert back to 2.4, see if thats stable. And then try to upgrade to 3.0 afterwards or do manual install from the tar.gz file.

---

### Post by babloo75 on 2009-01-09
> **hyper_ch said:**
> is there any reason why you must have the latest OOo version=?

Yes dear, if you have MS Office 2007 installed on windows partition, as its default format is .docx. .docx files can be opened by older version of open office but while u scroll down any document- the computer hangs... and only way to get out of that mess is hard shut down (I m telling about my personal experience)

---

### Post by hyper_ch on 2009-01-09
I'm not your dear ;)

---

### Post by WitchCraft on 2009-01-09
> **solitaire said:**
> First thing is to remove the current Open Office in Ubuntu using Synaptic (their is conflicts running both versions i think!)


No there isn't! I run both and they work just fine.
Just move the desktop-integration folder out of the folder of all the .debs.

Then do "dpkg -i *.deb"
You meaybe have to repeat that up to 5 times.
Then it should work, and you can go to the desktop integration folder and do the same.
(i think desktop integration didn't work when I tried...)

You will then find openoffice3 in:
/opt/openoffice.org3
Then you can add a openoffice3 menu item to the gnome applications menu. Just copy the openoffice 2.4.

---

### Post by jrusso2 on 2009-01-09
[http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

This is what I used and it works perfect.  There is also a repo for 8.10.

---

### Post by 73ckn797 on 2009-01-09
> **browndog said:**
> I've downloaded Open Office 3.0 from [www.openoffice.org]("http://www.openoffice.org"), but when I decompress and try to install it I get a message telling me that many dependent files are missing.  When I search for it in the Synaptic repositories (and yes, I have them all enabled) I find nothing.  Any ideas?

Go to System/Administration/Software Sources/Third-Party Software/Add and paste this link in there: [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu)

That installs Oo3 via Synaptics. Worked perfectly for me.

---

