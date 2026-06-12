---
title: "Adding more pictures to the Cosmos screensaver"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by brallan on 2010-05-24
thanks zabuch! Those wanting an easy premade solution should download zabuch's gnome [hubble telecope pictures]("http://techblog.zabuchy.net/wp-content/uploads/2010/07/gnome-screensaver-hubble_0.1_all.deb") screensaver and then activate it within System>Preferences>Screensavers.

thanks grekhss! those wanting to make a screensaver with their own jpgs should copy them to /usr/share/backgrounds/cosmos and run grekhss's script. read on below...

In Karmic, the path for the cosmos screensaver folder is:

/usr/share/backgrounds/cosmos

just add more pictures to this folder and you can get them both as a screensaver and as a desktop background slideshow. I only can recommend adding JPGs, other formats might crash your system...

the package gnome-screensaver-cosmos-extras will misinstall them in another folder:

/usr/share/pixmaps/backgrounds/cosmos

---

### Post by brallan on 2010-05-24
ooops, i just discovered that the desktop background will not get updated with the new pictures unless you edit (painstakingly) the file:

background-1.xml

anyone know of an easy way to generate an updated version of this xml file from the pictures in the folder?

---

### Post by grekhss on 2010-06-08
> **brallan said:**
> ooops, i just discovered that the desktop background will not get updated with the new pictures unless you edit (painstakingly) the file:

background-1.xml

anyone know of an easy way to generate an updated version of this xml file from the pictures in the folder?

The following scripts create background-1.xml for all .jpg files in the current folder.
**IMPORTANT! What the files do:**
1) create_xml_file.sh creates text file names.txt, makes a backup of background-1.xml and launches names.py
2) names.py takes the file names.txt and creates new file background-1.xml
3) **VERY IMPORTANT!** It is supposed that contents of the folder where you create background-1.xml and the contents of /usr/share/backgrounds/cosmos are the same. Otherwise, there is a risk that your desktop background will be simply black. Thus, please, do not forget to copy all .jpg files into cosmos source folder (/usr/share/backgrounds/cosmos)

*Launch create_xml_file.sh to create background-1.xml.*
Of course, it is supposed that python is installed on your PC. =)

**Update!**
It seems that my xml file is a bit incorrect. However, I did not find any sufficient differences, it is better to not use it until I fix the bug.
**Update #2!**
I have found the source of the trouble and fixed it. Moreover, I made some improvements and now your jpg files will stay the same - only xml file will be created. Hope that creation of a new file will not damage anything. =) Anyway your old 'background-1.xml' will be backuped.

---

### Post by zabuch on 2010-07-10
You can also create your own .deb package with your own images to be displayed, see [http://techblog.zabuchy.net/2010/how-to-create-simple-theme-for-gnome-screensaver/](http://techblog.zabuchy.net/2010/how-to-create-simple-theme-for-gnome-screensaver/) . I have created a template for the package - you can get it at [http://techblog.zabuchy.net/wp-content/uploads/2010/07/screensaver-template.tar.gz](http://techblog.zabuchy.net/wp-content/uploads/2010/07/screensaver-template.tar.gz) . It contains simple shell script that will generate .xml file.

---

