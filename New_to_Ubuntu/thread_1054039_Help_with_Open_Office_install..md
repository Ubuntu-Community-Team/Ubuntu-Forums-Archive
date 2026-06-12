---
title: "Help with Open Office install."
date: 2009-01-29
forum: New to Ubuntu
---

### Post by Ross Leo on 2009-01-29
I am a relative newbie to Ubuntu and Linux.  I know some things and am learning as fast as I can.  I would like to convert to Ubuntu-OpenOffice entirely and move away from MS as far as is practical and realistic (in this world anyway).

I need help with Open Office.  I have already gotten 2.4 installed and working, but want to upgrade to 3.x.  I am assuming I must uninstall 2.4 and then install 3.x, but getting 3.0 to open and install is proving beyond my novice status.

Is 3.x available for Ubuntu or am I stuck with 2.4?
How do I get 3.x installed properly?

Would appreciate your wisdom and guidance to hasten my conversion.  Thx.

---

### Post by Sirron on 2009-01-29
OpenOffice 3.0.1 is officially available for Debian, which Ubuntu is based on.

Try this guide:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

I haven't tried that method myself, but it seems like a better way around.

---

### Post by HotShotDJ on 2009-01-29
> **Ross Leo said:**
> Is 3.x available for Ubuntu or am I stuck with 2.4?
How do I get 3.x installed properly?You didn't mention which version of Ubuntu you are using.  The link given by Sirron will give you the proper instructions for Intrepid (8.10) but they will not work with Hardy (8.04 LTS).  If you are using Hardy, you may need to use another (and sometimes painful if one is not careful) method.

EDIT:  After reading carlee's post below, I double checked... and YES, Scribblers finally DID do a Hardy (8.04 LTS) backport of OpenOffice 3.  So go ahead and use carlee's post as your guide on this.

---

### Post by Captain_tux on 2009-01-29
> **Sirron said:**
> 

Try this guide:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)



Please be attentive to the fact that these instructions are only good for Ubuntu 8.10 (Intrepid Ibex).

Hotshot: Good point with your signature!

---

### Post by sandyd on 2009-01-29
if your using ubuntu 8.04, replace

```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

with this
```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
```

if your using 8.10, just leave it.

---

### Post by Ben Page on 2009-01-29
Or you can do it in windows-ish way, download the package here:
[http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US), choose your language, and linux .deb sort of packaging ("installer"). Behind this link is a table witch is intuitively placed.
Then just install it, 
First open synaptic and search for openoffice and uninstall all.

Extract the downloaded file on your desktop (or where ever).
open terminal and be super user (sudo bash), then:
cd Desktop
cd NAME_of_the_OO3.0_FOLDER
cd DEBS
Or just drop the folder (gui way) to the terminal
then do in terminal

dpkg -i *.deb

to add oo3 to menus;

cd (go to) desktop-integration

dpkg -i *.deb

Log off or restart the OS if OO3 is not in menu.

Also, you can download SuperUbuntu - hacktolive.org edition of Ubuntu 8.10, and you'll have OO3 and many players and codecs and DVD burners etc. preinstalled.

---

### Post by XanTrax on 2009-01-29
> **Ben Page said:**
> Or you can do it in windows-ish way, download the package here:
[http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US), choose your language, and linux .deb sort of packaging ("installer"). Behind this link is a table witch is intuitively placed.
Then just install it, 
First open synaptic and search for openoffice and uninstall all.

Extract the downloaded file on your desktop (or where ever).
open terminal and be super user (sudo bash), then:
cd Desktop
cd NAME_of_the_OO3.0_FOLDER
cd DEBS
Or just drop the folder (gui way) to the terminal
then do in terminal

dpkg -i *.deb

to add oo3 to menus;

cd (go to) desktop-integration

dpkg -i *.deb

Log off or restart the OS if OO3 is not in menu.

Also, you can download SuperUbuntu - hacktolive.org edition of Ubuntu 8.10, and you'll have OO3 and many players and codecs and DVD burners etc. preinstalled.

My suggestion is to do it this way.  When I used the repo's, I didnt seem to get the entire package like I did when doing it this way.

---

### Post by SamNSane on 2009-01-29
> **XanTrax said:**
> My suggestion is to do it this way.  When I used the repo's, I didnt seem to get the entire package like I did when doing it this way.

I believe it's really a better idea to use repositories (at least if they're trusted ones) when possible. That way you will automatically get updates as they are added to the repos -- assuming they're being maintained. Those particular ones apparently are.

Not getting the "entire package" is fixable by searching Synaptic for the Open Office parts that you want that aren't installed. Sometimes, unfortunately, the descriptions of the packages aren't terribly helpful in figuring out what parts you want and what parts you don't.

---

### Post by XanTrax on 2009-01-29
> **SamNSane said:**
> I believe it's really a better idea to use repositories (at least if they're trusted ones) when possible. That way you will automatically get updates as they are added to the repos -- assuming they're being maintained. Those particular ones apparently are.

Not getting the "entire package" is fixable by searching Synaptic for the Open Office parts that you want that aren't installed. Sometimes, unfortunately, the descriptions of the packages aren't terribly helpful in figuring out what parts you want and what parts you don't.

I added the repos for Ooo3 and when I did the upgrade to Ooo2.4, it didnt install Draw, Math, and Base.  Using the download site, everything was installed.

---

### Post by SamNSane on 2009-01-29
> **XanTrax said:**
> I added the repos for Ooo3 and when I did the upgrade to Ooo2.4, it didnt install Draw, Math, and Base.  Using the download site, everything was installed.

I'm not sure what you meant. Did you install 2.4 after adding the repositories for Open Office 3? I'm not sure how you would do that?

For instance, in Hardy, I would either use the Synaptic dialogs to add the repositories or I would add these lines

```

deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main

```

to my /etc/apt/sources.list file. (I'd use a text editor running under administrative privileges, as in "gksu gedit /etc/apt/sources.list" issued from a gnome-terminal window.)

Then I'd open Synaptic, hit the reload button on the toolbar, and then search for OpenOffice using the Name filter. Of course that will shows me a LOT of stuff I don't want, too -- like menu / help support for other languages and dev docs and stuff. But I can find the packages I want, mark them, and install them.

Another way to accomplish the same thing is to do a standard Hardy installation, go into the Add/Remove Programs applet, choose all of the Open Office stuff (including base, calc, and actually the whole Open Office package which is, inexplicably to me, set off as a separate thing, but I guess it's that hand-holding interface thingy). Install it. Now I have the earlier version of Open Office under Ubuntu. Now I add the version 3 repositories, open Synaptic, use the reload button on the toolbar, and let Synaptic upgrade Open Office (all of it) to version 3.

I've done it both ways a number of times, and it has worked perfectly every time. I've got calc / formula / base / word processing / presentation -- the whole ball of wax. And this way, because it's supported by a maintained repository, I get the updates that come along -- at least if they get included in this repository which is NOT an official Ubuntu repository. But it looks pretty good, nonetheless.

---

### Post by XanTrax on 2009-01-30
2.4 Came installed on Intrepid.  I added the repos for Ooo3.  I did an upgrade to it and when I looked in the menus it was only Calc, Impress, and Write.  There was no Base, Math, or Draw.

---

### Post by SamNSane on 2009-01-30
Okay. Now I understand what happened to you. You're seeing the result of the fact that the standard Open Office installation does not include all of the applications. If you had gone into Add/Remove Applications first and added Base / Math / Draw (and the package that's called "Suite"), then you would have had all of them updated. The repos don't update what isn't already installed. You could still have got everything from the repos by going into Synaptic. I'm not sure how well the Add/Remove Applications applet would have worked for you at that point. Probably it would have worked just fine if you had added those items from the applet.

---

### Post by ugm6hr on 2009-01-30
> **Ross Leo said:**
> How do I get 3.x installed properly?


A resource that works for Hardy and Intrepid using the standard Sun downloads of OO.org:
[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

Includes cut & paste instructions for Terminal - all you need do is find the appropriate deb.tar.gz on the Sun website.

---

### Post by XanTrax on 2009-01-30
> **SamNSane said:**
> Okay. Now I understand what happened to you. You're seeing the result of the fact that the standard Open Office installation does not include all of the applications. If you had gone into Add/Remove Applications first and added Base / Math / Draw (and the package that's called "Suite"), then you would have had all of them updated. The repos don't update what isn't already installed. You could still have got everything from the repos by going into Synaptic. I'm not sure how well the Add/Remove Applications applet would have worked for you at that point. Probably it would have worked just fine if you had added those items from the applet.

Oh. Makes sense.  I thought that openoffice upgrade would have installed other aspects of the entire suite.

---

