---
title: "Open Office 3.2.1 Installation"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by Ottawajoe on 2010-08-21
Open Office downloaded an update which is now on my desktop. It is a .tar.GZ file. How do I install it so that I may begin using this updated Openoffice suite?

thanks

---

### Post by kaldor on 2010-08-21
Ottawa ftw!

Anyway, this is Ubuntu. Ubuntu doesn't even use OpenOffice. It's a rebranded (though mislabled) version of GO-OO by Novell. 

The tar.gz you downloaded isn't really going to be much use. It's best to just use what you have; Ubuntu/Debian use repositories to manage software, and it's much easier to just stick with your current version. The newest versions eventually get ported and updated in Ubuntu anyway.

---

### Post by sikander3786 on 2010-08-21
> **Ottawajoe said:**
> Open Office downloaded an update which is now on my desktop. It is a .tar.GZ file. How do I install it so that I may begin using this updated Openoffice suite?

thanks

As kaldor said, it is better to use the update manager or

```

sudo apt-get update

sudo apt-get upgrade

```

It will look after all the updates that are ported to Ubuntu. And this way, your system will be much more stable.

Regards.

---

### Post by Paddy Landau on 2010-08-21
There are two ways to install OO.

The first is through the repository.

However, if you want the latest version, then this is how you go about it.

First, *completely* uninstall the existing OpenOffice.

[LIST=1]
[*]Go to Synaptic Package Manager, find *all* installed instances of OpenOffice, and Mark for Complete Removal.
[*]Apply to uninstall.
[*]Recommended: Also delete the folder .openoffice.org in your home directory.
[/LIST]
Second, install the newest version.

[LIST=1]
[*]Go to OpenOffice's website and download the Linux DEB file (it's actually a tar file, so I think you already downloaded it).
[*]Extract the contents (right-click the tar file and select Extract Here). It should create its own folder.
[*]Now you have to open a terminal (Accessories > Terminal).
[*]Change directory to the new folder ([FONT=Courier New]cd ~/<foldername>[/FONT]). You should see a folder called DEBS.
[*]Enter the following command:
```
sudo dpkg -Ri DEBS
```
[/LIST]
Voilà!

Thanks (as usual) to Hagar de l'Est in his [Ubuntu OO tutorial]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68"), which is worth a read.

---

### Post by Paddy Landau on 2010-08-21
> **sikander3786 said:**
> And this way, your system will be much more stable.
Unfortunately, with OO, I've not always found the Ubuntu version to be the most stable.

---

### Post by sikander3786 on 2010-08-21
> **Paddy Landau said:**
> Unfortunately, with OO, I've not always found the Ubuntu version to be the most stable.

But it has been very much stable for me after every update. I've never had any issues regarding OO ever.

---

### Post by KegHead on 2010-08-21
Hi!

I just typed in the terminal:

sudo apt-get install openoffice.org

Worked great after;

sudo apt-get update

sudo apt-get upgrade

Hope this helps!

KegHead

---

