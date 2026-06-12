---
title: "downloads going astray?"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by iggy pop on 2010-01-13
I am running Ubuntu 9.10 (Karmic Koala) and have almost got everything to my liking except that i have configured Firefox to place any downloads into the "Downloads" folder but the downloads always end up in the /tmp folder?

While i'm here i may as well ask if anyone could point me to an easy to follow tutorial which covers how to unwrap/open and install .tar.gz files.

Thanks for any and all help as it is really appreciated.

---

### Post by Paqman on 2010-01-13
> **iggy pop said:**
> I am running Ubuntu 9.10 (Karmic Koala) and have almost got everything to my liking except that i have configured Firefox to place any downloads into the "Downloads" folder but the downloads always end up in the /tmp folder?

That's odd. So you've set Firefox to download them to /home/username/Downloads? Are you sure they've finished downloading?

> While i'm here i may as well ask if anyone could point me to an easy to follow tutorial which covers how to unwrap/open and install .tar.gz files.

If you're just trying to install software, that's the hard way of doing it. The easy way is to go to Applications > Ubuntu Software Centre. There's also a more in depth tool at System > Admin > Synaptic. If you can't find a suitable package through these tools then try and find a .deb file of it to download, or a PPA or other 3rd party repository to connect to. Installing manually from a tarball or other archive is the absolute last resort.

---

### Post by iggy pop on 2010-01-13
The downloads have finished because a pop-up appears telling me so. 

When i try to download a .deb file i go through the process of downloading only to find that the .deb file in question doesn't exist on my computer?

I have looked in the repositories but there's no sign of the software i want (Opera Browser 10.10). I have also checked out the Ubuntu Software Center but no matter how many times i click on the link it produces no response?

---

### Post by Paqman on 2010-01-13
OK, let's try and get your downloads problem sorted first, that should allow you to get the proper .deb file for Opera.

In Firefox, try going to Edit > Prefs > Main, select "Always ask me where to save files" and try downloading Opera to your desktop (for example).

---

### Post by iggy pop on 2010-01-13
Don't know what's going on here. I have tried what you have suggest quite a few times before and had no luck. Now today you suggested that i set it to download to the Desktop and hey presto it worked.

I now have a file called:
opera_10.10.4742.gcc4.qt3_i386.deb sitting on my Desktop.

What next please

---

### Post by audiomick on 2010-01-13
right click on it. it should offer you "open with gdebi"
do that
(or maybe it is "install with gdebi")

> Don't know what's going on here. the box is probably just looking for attention...;)

---

### Post by iggy pop on 2010-01-13
I right-clicked on the package and then selected "open with GDebi Package Installer" as suggested but nothing happens?

---

### Post by audiomick on 2010-01-13
sure?
no new entries in your applications menu?
I don't think there is all that much to see when gdebi does it's stuff...

---

### Post by iggy pop on 2010-01-13
No new entries in the Application menu.
What if i used: dpkg -i opera_10.10.4742.gcc4.qt3_i386.deb?

---

### Post by iggy pop on 2010-01-13
Took a chance and used sudo dpkg -i package.deb in a terminal and the output was

Errors were detected?

---

### Post by audiomick on 2010-01-14
Hallo iggy pop,
Have you got this sorted out yet?

I went and got the deb packet you mentioned, although mine got itself a amd64 version, which is correct. Right click, open with gdebi, a window appeared and it installed.

As far as I can tell from reading 
```
man dpkg
```
your command should have worked.

You could try downloading again. Maybe the download is corrupted?

---

