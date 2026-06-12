---
title: "OpenOffice.org 3??????"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-03-25
I have OpenOffice.org on both my Ubuntu 8.10 O/S and my Windows Vista O/S.

A few months ago, I was prompted to install the new v3 of OpenOffice.org on my Windows O/S, and I thought it a bit odd that the MS version was released before the Linux version.

I've been waiting for Ubuntu to upgrade my OpenOffice.org but there's still nothing to suggest that v3 is ready. When I look for it in Synaptic, it says that I have the most recently available version - 2.4.1

So when should I expect to get v3?

Or, have I made a booboo by expecting it to be downloaded/installed through the normal update procedure?

---

### Post by gjoellee on 2009-03-25
You will not get OOo v3 in Intrepid...
But you can install it in other ways, just Google "how to install openoffice 3 in ubuntu"

---

### Post by Simian Man on 2009-03-25
Ubuntu doesn't update to new versions of packages.  The only updates you get are fixes to the same release.  If you want latests software, either install it manually or switch to a different distro.

---

### Post by kanikilu on 2009-03-25
If you want to update before the next Ubuntu release, there are a couple different ways, either manually from OO.org, or via the PPA:

[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

---

### Post by LowSky on 2009-03-25
Please remember that Ubuntu has 6 month release cycles, and during that cycle software is locked until the next version. they will do security update and patches, but no extensive version upgrades. Some do occur and can be accessed by allow the use of backports, but there is no guaantee that they will be done.

If you want the newest version use the kanililu gave you, thats one of your options.

Otherwise you can install OOo3 using the source files, or wait until 9.04 is released late next month

---

### Post by tom56 on 2009-03-25
What new features do you want? I think the only major change was the ability to open .docx files, and that has already been added through an update to 2.4 in Ubuntu.

---

### Post by Simian Man on 2009-03-25
> **tom56 said:**
> What new features do you want? I think the only major change was the ability to open .docx files, and that has already been added through an update to 2.4 in Ubuntu.

Not really.  [It is much better.]("http://www.openoffice.org/dev_docs/features/3.0/")

---

### Post by tom56 on 2009-03-25
> **Simian Man said:**
> Not really.  [It is much better.]("http://www.openoffice.org/dev_docs/features/3.0/")

Ok, fair enough that is quite a lot of changes. My point was more that sometimes you have to resist upgrade-itis! Unless you really NEED a particular new feature it's usually not worth the hassle.

EDIT: That said, I'm already running 9.04 so I'm not really one to talk :)

---

### Post by Jeff_Illingworth on 2009-03-25
Isn't OOo3 now available through Synpatic?

---

### Post by Paddy Landau on 2009-03-25
Nice 'n' easy...

First...

[LIST=1]
[*]System -> Administration -> Software Sources
[*]Settings -> Repositories -> Third Party Software -> +Add...
[*]*deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main*
[*]+Add Source... -> Close
[/LIST]
Then...

[LIST=1]
[*]System -> Administration -> Update Manager -> Check
[/LIST]
You should find OpenOffice 3 ready to update . I forget whether you need to uninstall OO 2 first.

---

### Post by sgosnell on 2009-03-25
Or you can just download the .deb from openoffice.org and install it.  V3 is in Jaunty, so if you wait until it comes out next month you can upgrade everything at once.

---

### Post by odinb on 2009-03-25
--== OpenOffice Repository howto ==--
Add the repository to your system's list of APT sources (System > Administration > software sources > Third Party software > Add):
*For Ubuntu 8.10 "Intrepid Ibex" users:
	deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

*For Ubuntu 9.04 "Jaunty Jackalope" users:
	deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) jaunty main

--== Issues with missing Public Keys? ==--
Enter this command, replacing 247D1CFF with your NO_PUBKEY-key last eight digits from the error-message to import the key:
gpg --keyserver keyserver.ubuntu.com --recv 247D1CFF

Then add the key to your software sources, again, replace 247d1cff with the keynumber used in above command:
gpg --export --armor 247D1CFF | sudo apt-key add -

Then update your software sources:
sudo apt-get update


And you do not have to uninstall the old version. With the above method, you will get all updates together with other updates of your system just as usual.

---

### Post by scottuss on 2009-03-25
Shameless plug: if you find yourself wanting the latest software as soon as it's available, try Arch Linux.

</end of shameless plug>

---

