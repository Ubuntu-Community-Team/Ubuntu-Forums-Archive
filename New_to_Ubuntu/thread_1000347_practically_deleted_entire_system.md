---
title: "practically deleted entire system"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by crabclaw on 2008-12-02
I am fairly ubuntly challenged and here's the proof. I couldn't get dreamweaver to uninstall so I uninstalled wine and used deborphan to practically wipe out half the programs on my computer. I could deal with it by reinstalling the more important programs but it seems that in the meantime I managed to delete some other bits and pieces that i can't exactly begin to describe. Is there a way of restoring my system to the way it was yesterday?

Shedloads of karma for any answers you can provide.

---

### Post by handydan918 on 2008-12-02
> **crabclaw said:**
>  Is there a way of restoring my system to the way it was yesterday?

 Sure! Just use your backup! 



What? No backup? 




Oh. Sorry.....







No. There is no "Restore Point" a la Windows, or any such nonsense. The strength of a linux system is that it does exactly what it's told. Including self-destruct. Fortunately, reinstalling is fairly simple.

---

### Post by dondad on 2008-12-02
> **crabclaw said:**
> I am fairly ubuntly challenged and here's the proof. I couldn't get dreamweaver to uninstall so I uninstalled wine and used deborphan to practically wipe out half the programs on my computer. I could deal with it by reinstalling the more important programs but it seems that in the meantime I managed to delete some other bits and pieces that i can't exactly begin to describe. Is there a way of restoring my system to the way it was yesterday?

Shedloads of karma for any answers you can provide.

Unfortunately, there is no way without a backup. It might be easier to reinstall if most stuff was lost. If you do not have one, you might want to think about a separate partition for /home. That can save a lot of problems when you bork your system. (how well I know ;-))

---

### Post by luckydeveloper on 2008-12-02
Reinstall the system, if you dont have a backup. thats the only choice.

---

### Post by mapes12 on 2008-12-03
The following is a post I made earlier. You need to have a robust backup policy. Also check out the link in my sig file to the Pschocats website and have a read of the tutorials:

The first thing to consider is making sure you have "/" and /home on separate partitions. /home contains all your files, settings bookmarks and anything else to do with your look & feel of your system. "/" contains your system and application software.

Here's how to split them apart: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

There are many ways to backup the separate partitions. For example try this for your "/" system partition: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) and then use some of the other suggestions on this thread to backup /home. You can even just copy everything to external media and reinstall /home in case of a catastophe.

For your "/" system files another method is to keep regular backups of your updates and applied applications using aptoncd (search for it in Synaptic Pacakage Manager and Google for its home page). Then, if your system crashes just reinstall Ubu from your regular install CD then just restore the aptoncd image to get your system back the way things were before it went wrong.

---

### Post by Paqman on 2008-12-03
As long as the package management system is still intact, you should be able to restore deleted packages reasonably easily.

In Linux, packages have dependencies. In order to install one package, others will need to be present. If not, they will be installed to satisfy the dependency.

You can see how that works for a nice user-facing package like [ubuntu-desktop]("http://packages.ubuntu.com/intrepid/ubuntu-desktop"). In fact, ALL this package does is depend on other packages (what's known as a meta-package) So if you try to install it, it will check to see that all those dependencies are satisfied, and they will check to make sure their own dependencies are met, and so on and so on.

So as long as your package manager is still intact and working, installing a package like ubuntu-desktop should restore a lot of the important packages you might be missing (including major systems like pulseaudio, alsa and xorg) Not only that, but it will also reinstall any missing parts of those packages, all the way down the line.

---

### Post by philinux on 2008-12-03
> **crabclaw said:**
> I am fairly ubuntly challenged and here's the proof. I couldn't get dreamweaver to uninstall so I uninstalled wine and used deborphan to practically wipe out half the programs on my computer. I could deal with it by reinstalling the more important programs but it seems that in the meantime I managed to delete some other bits and pieces that i can't exactly begin to describe. Is there a way of restoring my system to the way it was yesterday?

Shedloads of karma for any answers you can provide.

The question is, does your system still boot and run? If the answer is yes then just install the programs that are missing.

---

### Post by loomsen on 2008-12-03
If you consider to reinstall, and as well expect to basically remove many/most pkges after install anyway, you might want to go the other way round.

Create an image on [www.instalinux.com](www.instalinux.com)
the file created will be about 10MB if you chose just a basic Intrepid system, without pulling any metapackage in. Then, after install, choose to install ubuntu-minimal or ubuntu-standard and gnome-core or gnome-common. (sorted by size, ascending--> ubuntu-minimal will provide fewest dependencies of these 4 metas, gnome-common the most, if I remember right)

That way you won't have to waste several hours dealing with apps you act want to remove, but can use the time to consider what you WANT to install.

Another very nice app, one of my favourites, is
[unetbootin. Basically provides the same as instalinux, but has a lot more distros/options to chose from.](https://sourceforge.net/project/showfiles.php?group_id=222386)

---

