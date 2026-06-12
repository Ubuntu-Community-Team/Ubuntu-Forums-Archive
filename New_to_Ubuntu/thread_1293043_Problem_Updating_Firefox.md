---
title: "Problem Updating Firefox"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by bwagner330 on 2009-10-16
After installing 9.04 I tried to upgrade firefox to version 3.5 from the pre-installed 3.0.  When I did so it installed version 3.5 prerelease shiretoko, the firefox icon has changed and the program shows up as Shiretoko. While the program runs fine its somewhat annoying how can i fix this to update to the current version of firefox???

---

### Post by fooman on 2009-10-16
if you are looking to change the name/icon/links to firefox 3.5...see this:

[http://ubuntuforums.org/showthread.php?t=1225754&highlight=firefox+branding](http://ubuntuforums.org/showthread.php?t=1225754&highlight=firefox+branding)

hope thats what your looking for.

---

### Post by wojox on 2009-10-16
An even easier way is to download the version from their site.

---

### Post by bwagner330 on 2009-10-16
When I download the package from Mozilla how do i get it to install? It just unpacks it but wheres the install file, installing from the terminal using apt-get install just caused the problem I have now.

---

### Post by wojox on 2009-10-16
Okay to unpack:

```
tar -jxf firefox-<version>.tar.bz2
```

Then move it:

```
sudo mv firefox /usr/local
```

Change ownership:

```
chown -R root:root /usr/local/firefox
```

Now open System > Preferences > Main Menu

Left side select Internet 

Now select +New Item

Name: Firefox-3.5
Command: /usr/local/firefox/firefox
Icon: /usr/local/firefox/icons/firefox.svg

Close it up and look in your menu.

---

### Post by fooman on 2009-10-16
theres nothing to install....just unpack it and click on "firefox" that is in the folder it creates.

---

### Post by kansasnoob on 2009-10-16
I personally like using Ubuntuzilla:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

It's supported here at the forums:

[http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)

---

### Post by bwagner330 on 2009-10-16
> **wojox said:**
> Okay to unpack:

```
tar -jxf firefox-<version>.tar.bz2
```Then move it:

```
sudo mv firefox /usr/local
```Change ownership:

```
chown -R root:root /usr/local/firefox
```Now open System > Preferences > Main Menu

Left side select Internet 

Now select +New Item

Name: Firefox-3.5
Command: /usr/local/firefox/firefox
Icon: /usr/local/firefox/icons/firefox.svg

Close it up and look in your menu.

Thanks that worked!

and I will check out ubuntuzilla

---

