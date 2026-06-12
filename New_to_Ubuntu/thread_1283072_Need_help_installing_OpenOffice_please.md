---
title: "Need help installing OpenOffice please"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by pgar23 on 2009-10-05
Hi,
I am trying to install open office onto my machine but am having some difficulty.
I have been following [A HREF="http://www.openoffice.org/dev_docs/instructions.html#linux"]these [/A]instructions and I am stuck on direction number ;     
     4. This should create a directory "OOo_1.1x_LinuxIntel_install". 
    ("x" in this sense is a suffix to version 1.1 that will depend on the version you downloaded.)

My terminal looks something like this;

```

[pgar23@python ~]$ su
Password: 
[root@python pgar23]# mv /home/pgar23/Desktop/OOo_3.1.1rc2_20090820_LinuxIntel_install_ar.tar.gz /tmp
[root@python pgar23]# cd /tmp
[root@python tmp]# ls
OOo_3.1.1rc2_20090820_LinuxIntel_install_ar.tar.gz  orbit-gdm  orbit-root  pulse-53c4748lRsQn
[root@python tmp]# tar -zxvf OOo_3.1.1rc2_20090820_LinuxIntel_install_ar.tar.gzOo_3.1
tar: OOo_3.1.1rc2_20090820_LinuxIntel_install_ar.tar.gzOo_3.1: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
[root@python tmp]# tar -zxvf OOo_3.1.1rc2_20090820_LinuxIntel_install_ar.tar.gz
OOO310_m19_native_packed-1_ar.9420/
OOO310_m19_native_packed-1_ar.9420/readmes/
OOO310_m19_native_packed-1_ar.9420/readmes/README_ar.html
OOO310_m19_native_packed-1_ar.9420/readmes/README_ar
OOO310_m19_native_packed-1_ar.9420/update
OOO310_m19_native_packed-1_ar.9420/RPMS/
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-graphicfilter-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/openoffice.org3-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-ar-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/openoffice.org3-dict-fr-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-ar-help-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-ar-calc-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-core07-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-ar-base-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-ooolinguistic-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-ooofonts-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-math-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/openoffice.org3-math-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/openoffice.org-ure-1.5.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-core03-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-kde-integration-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-core04-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/openoffice.org3-ar-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/openoffice.org3-dict-es-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-ar-draw-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-oooimprovement-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/openoffice.org3-writer-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-ar-impress-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-testtool-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-gnome-integration-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/desktop-integration/
OOO310_m19_native_packed-1_ar.9420/RPMS/desktop-integration/openoffice.org3.1-freedesktop-menus-3.1-9420.noarch.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/desktop-integration/openoffice.org3.1-slackware-menus-3.1-noarch-9420.tgz
OOO310_m19_native_packed-1_ar.9420/RPMS/desktop-integration/openoffice.org3.1-suse-menus-3.1-9420.noarch.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/desktop-integration/openoffice.org3.1-debian-menus_3.1-9420_all.deb
OOO310_m19_native_packed-1_ar.9420/RPMS/desktop-integration/openoffice.org3.1-mandriva-menus-3.1-9420.noarch.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/desktop-integration/openoffice.org3.1-redhat-menus-3.1-9420.noarch.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-onlineupdate-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-ar-binfilter-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-pyuno-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-ar-writer-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-impress-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/openoffice.org3-impress-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-writer-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/openoffice.org3-draw-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-draw-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-core01-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-binfilter-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-core06-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-images-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-ar-math-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-xsltfilter-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-base-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/openoffice.org3-calc-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-calc-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/openoffice.org3-base-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/openoffice.org3-dict-en-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-core05-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-ar-res-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-core02-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/RPMS/ooobasis3.1-javafilter-3.1.1-9420.i586.rpm
OOO310_m19_native_packed-1_ar.9420/licenses/
OOO310_m19_native_packed-1_ar.9420/licenses/LICENSE_ar
OOO310_m19_native_packed-1_ar.9420/licenses/LICENSE_ar.html
[root@python tmp]# cat OOO310_m19_native_packed-1_ar.9420
cat: OOO310_m19_native_packed-1_ar.9420: Is a directory
[root@python tmp]# cd ./OO
OOO310_m19_native_packed-1_ar.9420/                 OOo_3.1.1rc2_20090820_LinuxIntel_install_ar.tar.gz
[root@python tmp]# cd ./OOO310_m19_native_packed-1_ar.9420/
[root@python OOO310_m19_native_packed-1_ar.9420]# ls
licenses  readmes  RPMS  update
[root@python OOO310_m19_native_packed-1_ar.9420]# cd ./RPMS
[root@python RPMS]# ls
desktop-integration                                ooobasis3.1-impress-3.1.1-9420.i586.rpm
ooobasis3.1-ar-3.1.1-9420.i586.rpm                 ooobasis3.1-javafilter-3.1.1-9420.i586.rpm
ooobasis3.1-ar-base-3.1.1-9420.i586.rpm            ooobasis3.1-kde-integration-3.1.1-9420.i586.rpm
ooobasis3.1-ar-binfilter-3.1.1-9420.i586.rpm       ooobasis3.1-math-3.1.1-9420.i586.rpm
ooobasis3.1-ar-calc-3.1.1-9420.i586.rpm            ooobasis3.1-onlineupdate-3.1.1-9420.i586.rpm
ooobasis3.1-ar-draw-3.1.1-9420.i586.rpm            ooobasis3.1-ooofonts-3.1.1-9420.i586.rpm
ooobasis3.1-ar-help-3.1.1-9420.i586.rpm            ooobasis3.1-oooimprovement-3.1.1-9420.i586.rpm
ooobasis3.1-ar-impress-3.1.1-9420.i586.rpm         ooobasis3.1-ooolinguistic-3.1.1-9420.i586.rpm
ooobasis3.1-ar-math-3.1.1-9420.i586.rpm            ooobasis3.1-pyuno-3.1.1-9420.i586.rpm
ooobasis3.1-ar-res-3.1.1-9420.i586.rpm             ooobasis3.1-testtool-3.1.1-9420.i586.rpm
ooobasis3.1-ar-writer-3.1.1-9420.i586.rpm          ooobasis3.1-writer-3.1.1-9420.i586.rpm
ooobasis3.1-base-3.1.1-9420.i586.rpm               ooobasis3.1-xsltfilter-3.1.1-9420.i586.rpm
ooobasis3.1-binfilter-3.1.1-9420.i586.rpm          openoffice.org3-3.1.1-9420.i586.rpm
ooobasis3.1-calc-3.1.1-9420.i586.rpm               openoffice.org3-ar-3.1.1-9420.i586.rpm
ooobasis3.1-core01-3.1.1-9420.i586.rpm             openoffice.org3-base-3.1.1-9420.i586.rpm
ooobasis3.1-core02-3.1.1-9420.i586.rpm             openoffice.org3-calc-3.1.1-9420.i586.rpm
ooobasis3.1-core03-3.1.1-9420.i586.rpm             openoffice.org3-dict-en-3.1.1-9420.i586.rpm
ooobasis3.1-core04-3.1.1-9420.i586.rpm             openoffice.org3-dict-es-3.1.1-9420.i586.rpm
ooobasis3.1-core05-3.1.1-9420.i586.rpm             openoffice.org3-dict-fr-3.1.1-9420.i586.rpm
ooobasis3.1-core06-3.1.1-9420.i586.rpm             openoffice.org3-draw-3.1.1-9420.i586.rpm
ooobasis3.1-core07-3.1.1-9420.i586.rpm             openoffice.org3-impress-3.1.1-9420.i586.rpm
ooobasis3.1-draw-3.1.1-9420.i586.rpm               openoffice.org3-math-3.1.1-9420.i586.rpm
ooobasis3.1-gnome-integration-3.1.1-9420.i586.rpm  openoffice.org3-writer-3.1.1-9420.i586.rpm
ooobasis3.1-graphicfilter-3.1.1-9420.i586.rpm      openoffice.org-ure-1.5.1-9420.i586.rpm
ooobasis3.1-images-3.1.1-9420.i586.rpm
[root@python RPMS]# 

```Any help is appreciated.

---

### Post by pgar23 on 2009-10-05
Instructions from the instruction source page.

```

[LIST=1]
[*]Make sure you are root
[*]Download the tarball from OpenOffice.org (the download can be done from any user account and then moved), and extract the tarball (.tar.gz file) to a temporary directory. 
"/tmp" is a good place for example. For the purpose of this example, I will assume you have downloaded the tarball to your /tmp directory.
[*]Open a terminal, such as xterm or konsole. 
    To extract the tarball, change to the /tmp directory: cd /tmp 
    and extract the tarball: "tar -zxvf [tarball name]".
[*]This should create a directory "OOo_1.1x_LinuxIntel_install". 
    ("x" in this sense is a suffix to version 1.1 that will depend on the version you downloaded.)
[*] Change into this directory: cd OOo_1.1x_LinuxIntel_install.
[*]Execute the setup script for a "network" installation.
    This is done with the following command: "./setup -net" 
This is a friendly installation process which will prompt you for a destination directory and other OpenOffice installation options. When the setup is finished, you should have a complete "network" installation installed in the destination directory you specified. Tips on installing OpenOffice.org with an NFS setup can be found on our [nfs tips]("http://www.openoffice.org/dev_docs/nfs_tips.html") page.      **Note:**It is NOT advisable to install over an existing OpenOffice installation. If you want to use the same destination as an existing version of OpenOffice, delete the contents of the existing directory!
[*] Part of the installation process includes telling OpenOffice about your Java installation. Normally this can be automatically found or you may need to supply it, or install the JRE supplied with OpenOffice if you don't already have it installed. (But see Prerequisites for more control over this.)
[*]Each user on your system should then execute the user-setup for OpenOffice.org.
    To do so, login as a regular user, then change into the program directory where you installed OpenOffice.org: 
    cd /opt/OpenOffice.org1.1.0, for example
    and execute the following command:
"./setup"
The user portion of setup will now execute. Tell setup to perform a Workstation installation (should copy about 1.4 MB of files to your home directory) and typically let it default to the directory it recommends for storage of the local files in your user directory.
    Example: "/home/billg/OpenOffice.org1.1.0"
    Follow the instructions and fill in your contact details.     If your users have been previously running an older version of OpenOffice, they should delete the current version of .sversionrc before starting up the newly installed version. This will reinitialize the version information for the new setup.
[*]That's it! If you use GNOME or KDE (provided your distro keeps the KDE user files in ~/.kde2), you will find that OpenOffice.org is fully integrated in your environment. If you use a different Windowmanager, you can start OpenOffice.org by typing ~/OpenOffice.org1.1.0/soffice
[*]You may remove the install files in /tmp, if you are done installing. (thanks to Henrik Eismark for pointing this out)
[/LIST]
 Have Fun!
 
```

---

### Post by ankspo71 on 2009-10-05
Hi,
I see a possible problem coming up. It looks like you have an RPM based installer, and I don't know if it is even possible for Ubuntu to handle RPM packages (not without installing some rpm package management tools anyways). They have .deb based packages here [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html)
James

---

### Post by wildman4god on 2009-10-05
open office is already installed on your computer if you use ubuntu, if you're trying to upgrade it to the latest version download a program called ubuntu-tweak for [http://ubuntu-tweak.com](http://ubuntu-tweak.com)
 
this has a source editor that allows you to easily enable third-party repositories for various software like openoffice. So download and install the program and enable the openoffice repository and it will offer to update open office.

---

### Post by pgar23 on 2009-10-05
> **ankspo71 said:**
> Hi,
I see a possible problem coming up. It looks like you have an RPM based installer, and I don't know if it is even possible for Ubuntu to handle RPM packages (not without installing some rpm package management tools anyways). They have .deb based packages here [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html)
James
No,
I should have mentioned..I am using _**Fedora 11**_. I chose to post this in UbubtForums because I always get the quickest and most sensible responses from this forum.

---

### Post by LewRockwell on 2009-10-05
> **pgar23 said:**
> No,
I should have mentioned..I am using _**Fedora 11**_. I chose to post this in UbubtForums because I always get the quickest and most sensible responses from this forum.

[http://slash7.com/pages/vampires](http://slash7.com/pages/vampires)

[http://fedoraforum.org/forum/showthread.php?t=213101](http://fedoraforum.org/forum/showthread.php?t=213101)

[http://fedoraforum.org/](http://fedoraforum.org/)

.

---

### Post by scratman on 2009-10-05
You might struggle to find help for Fedora on an Ubuntu Forum.  If you install Ubuntu, however, this place will become much more helpful.  I have no idea how to install programmes on Fedora, having never used it.  Try a different tutorial?

---

### Post by pgar23 on 2009-10-05
> **LewRockwell said:**
> [http://slash7.com/pages/vampires](http://slash7.com/pages/vampires)

.

Thanks Lew, 

I'm not a "Vampire" tho. I posted this thread in the all variants because my problem does effect all variants. its a problem with installing Open Office on linux. I came to this forum because I kno that the community here is most helpful. Different from being a vampire. nice tho.

---

### Post by LewRockwell on 2009-10-05
> **pgar23 said:**
> Thanks Lew, 

I'm not a "Vampire" tho. I posted this thread in the all variants because my problem does effect all variants. its a problem with installing Open Office on linux. I came to this forum because I kno that the community here is most helpful. Different from being a vampire. nice tho.

it's all good

.

---

### Post by wildman4god on 2009-10-05
still fedora should have open office, most of the larger distros do, and to update it add a new repository for it. If fedora doesn't have openoffice by default then install it from fedora's package manager.

---

