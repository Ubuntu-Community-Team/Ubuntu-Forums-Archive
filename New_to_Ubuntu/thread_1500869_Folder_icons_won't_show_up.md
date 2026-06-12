---
title: "Folder icons won't show up"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by lanetherif on 2010-06-03
Hi,

I am not able to use the newly installed icon packs, at least not  wholly. 
I've downloaded a few icon packs from package manager and two manually. I  am trying to use G-Flat SVG icon pack. It seems to work fine with  navigation buttons both in Gnome and in programs such as Firefox. Yet,  folder icons somehow fall back to default Gnome icon theme. 
I've read a post in a blog which tells adding another folder in icon's  directory named /places and editing index.theme respectively has solved  the problem. I did it, it didn't worked. I copied the icon theme  directory to /usr/share/icons, it was a desperate attempt and as I  expected it also didn't work.
This is the index.theme file the icon theme uses:
     > # The Flat icon theme for GNOME
# Flat icons that are the work of Danny Allen (danny@dannyallen.co.uk) have been used with permission from the author.
# Original Flat icon conversion by Exdaix
# Stock gnome icons, emblems, misc applications, and gnome specific enhancements added 12/05 by poptones
# Versioning for this GNOME port does not explicitly follow the versioning of the original KDE icon set 
# as this set has become more completely gnome-centric and so does not include most kde applications.

[Icon Theme]
Name=G-Flat SVG 0.99

inherits=gnome
Directories=scalable/apps,scalable/mimetypes,scalable/emblems,scalable/devices,scalable/stock,scalable/stock/media,scalable/stock/net,24x24/stock,24x24/stock/media,24x24/stock/net,scalable/places
Example=gnome-theme-preview.svg

[scalable/actions]
MinSize=1
Size=48
MaxSize=256
Context=Actions
Type=scalable

[scalable/apps]
MinSize=1
Size=48
MaxSize=256
Context=Applications
Type=scalable

[scalable/devices]
MinSize=1
Size=48
MaxSize=256
Context=Devices
Type=scalable

[scalable/emblems]
Size=72
Context=Emblems
Type=Scalable

[scalable/places]
MinSize=1
Size=48
Maxsize=128
Context=Places
Type=Scalable

[scalable/mimetypes]
MinSize=1
Size=48
MaxSize=128
Context=MimeTypes
Type=Scalable

[scalable/stock]
MinSize=1
Size=48
MaxSize=128
Context=Stock
Type=scalable

[scalable/stock/net]
MinSize=1
Size=48
MaxSize=128
Context=Stock
Type=scalable

[scalable/stock/media]
MinSize=1
Size=48
MaxSize=128
Context=Stock
Type=scalable

[scalable/stock/navigation]
MinSize=1
Size=48
MaxSize=128
Context=Stock
Type=scalable


[24x24/stock]
MinSize=1
Size=128
MaxSize=24
Context=Stock
Type=24x24

[24x24/stock/net]
MinSize=1
Size=128
MaxSize=24
Context=Stock
Type=24x24

[24x24/stock/media]
MinSize=1
Size=128
MaxSize=24
Context=Stock
Type=24x24

[24x24/stock/navigation]
MinSize=1
Size=128
MaxSize=24
Context=Stock
Type=24x24

Any help will be appreciated.

---

### Post by U DON on 2010-06-03
I have a similar problem, except all of the "Places" icons would display correctly (for instance, the Music folder would have the corresponding "folder-music" icon) except for Downloads. I'd like to know the solution to this as well as this is annoying me...

---

### Post by lanetherif on 2010-06-04
Bump?

---

### Post by lanetherif on 2010-06-07
Isn't there anybody who uses customized icon pack out there? :D

---

### Post by lanetherif on 2010-06-09
Bump!

---

### Post by lanetherif on 2010-06-13
I give up... :D

---

### Post by lanetherif on 2010-06-23
One more chance...

---

### Post by GrouchyGaijin on 2010-10-09
> **U DON said:**
> I have a similar problem, except all of the "Places" icons would display correctly (for instance, the Music folder would have the corresponding "folder-music" icon) except for Downloads. I'd like to know the solution to this as well as this is annoying me...I have a similar problem as well.  In some icon sets for example Dropline Nuovo the new folder icons work however in most they default to Gnome.

---

### Post by lanetherif on 2010-10-22
> **GrouchyGaijin said:**
> I have a similar problem as well.  In some icon sets for example Dropline Nuovo the new folder icons work however in most they default to Gnome.

Still... bump.

---

### Post by maxwellcom on 2010-10-22
> **lanetherif said:**
> Still... bump.

I too like the Dropline Nuovo custom icon theme, which is included in the Maverick repo. It does not, however, display properly when installed and applied.  The majority of the icons, including the basic folder icon, display the default GDM icon instead.

Have the system names for icons changed, so that an older icon theme (like Dropline Nuovo) doesn't provide the correct names in the theme config files (and so  Ubuntu just defaults to GDM)?

---

