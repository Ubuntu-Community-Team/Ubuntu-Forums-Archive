---
title: "Manual installation of Deb files and Update Manager problem"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by chandru155 on 2009-08-25
Yesterday:
   Yesterday i freshly installed Ubuntu and updated it using Update manager. It downloaded around 160MB of files. I took back up of them(.deb files) from archieves folder. 
Today:
   Inorder to test my backup files are working or not, i again freshly installed Ubuntu 9.04 and tried those DEB files. Most of them are installed correctly. 
But some(say X) asked to install the Dependency (Say Y) to install. So i tried Y. But again, Y asked me to install X. So i couldnt install both of them. They are asking one another to install for their installation. So i couldnt install(Its like DeadLock).

   Then, I Checked with update manager. But the update Manager shown me some list of available updates which i already installed using my Backup deb files. (one of the update is acpid_1.0.6-9ubuntu4.9.04.3_i386). So i try to install again the deb file, it asked me for the Reinstall only. What is going wrong? why The Update Manager is showing acpid_1.0.6-9ubuntu4.9.04.3_i386 as not installed and asking for the installation(though i installed it manaually using the Deb files)

Still i am getting that X-Y dead lock, that i exaplained above. I dont want to install using Update Manager. I want to install them manually. because, in future if i dont have internet connection means, i cant use Update Manager. Thats why i am asking. Help me with brief procedure, since i am newbie to Ubuntu.

---

### Post by zvacet on 2009-08-25
One way is to put backed packages in var/cache/apt/archives and then in **synaptic>mark all updates**.Second way is also from var/cache/apt/archives but you have to be inside.Type in terminal

```
cd /var/cache/apt/archives
```

and then 

```
sudo dpkg -i *deb
```

To solve dependency problem simply install them together

```
sudo dpkg -i X Y
```

---

### Post by chandru155 on 2009-08-25
So you are saying that Since the Installed deb files are not in Archives folder, the update manager is showing them as not installed? (Why update manager is checking like this) Or i understood wrongly?

---

### Post by mcduck on 2009-08-25
> **chandru155 said:**
> So you are saying that Since the Installed deb files are not in Archives folder, the update manager is showing them as not installed? (Why update manager is checking like this) Or i understood wrongly?

No, he's telling you that to install packages that depend on each other you simply need to install them both at the same time.

update Manager probably offers you updates because, like you said, you didn't install all of them yet.

---

### Post by chandru155 on 2009-08-25
Thanks. i followed the second method. It worked. Again i checked with the Update Manager, it shows the system is updated one. Thanks for the help. One doubt. Is it must to copy those DEB files to the Archieves folder or can we install them from any directory?

---

### Post by matthewbpt on 2009-08-25
If you copy the deb files to the archive folder then you can install program like how you normally would and they wouldn't need to be downloaded. For example say you downloaded vlc in your previous installation and backed up the cached archives. If you make a new install and then place those backed up debs in the archive folder, then typing 'sudo apt-get install vlc' in the command line will install from the debs in the archive folder and not have to download them (unless a newer version of the file is now available in the repos), because apt searches the archive folder to see if you already have the file. So the most practical thing to do is to copy those files to the archive folder.

Note: this doesn't work with just any deb file, they have to be deb files listed in one of your repositories.

---

### Post by mcduck on 2009-08-25
> **chandru155 said:**
> Thanks. i followed the second method. It worked. Again i checked with the Update Manager, it shows the system is updated one. Thanks for the help. One doubt. Is it must to copy those DEB files to the Archieves folder or can we install them from any directory?

You can install them from anywhere.

If you put them to the archives directory then graphical tools like Synaptic and Update Manager will use them instead of downloading the same package again from repositories, but usually just installing the packages directly will give exactly the same result with less work. :)

---

### Post by zvacet on 2009-08-25
> Is it must to copy those DEB files to the Archieves folder or can we install them from any directory?

I think **mcduck** and **matthewbpt** give you answer,but few words from me.All packages you install via apt-get,aptitude or synaptic goes to the var/cache/apt/archives.If you back them up and later want them install again,most logical move ( for me) is to put them into the place where they were by default.You can even use [APTonCD]("http://aptoncd.sourceforge.net/") to do that.Yoz will find it in synaptic.

---

