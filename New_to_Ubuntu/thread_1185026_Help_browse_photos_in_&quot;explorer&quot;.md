---
title: "Help browse photos in &quot;explorer&quot;"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by netjens on 2009-06-11
Hey there I am new to ubuntu. I have a quick question. I try to see photos explorer or file viewer so to say, all I see is a symbol for a photo but not the photo itself, is there a setting for this?

---

### Post by st33med on 2009-06-11
You mean nautilus? That is the name for the file manager, or 'explorer'. 

It should show it by default.  What extension are these photos?

---

### Post by netjens on 2009-06-11
I dont know what the name is, but where you view your files on the computer in ubuntu. I have mapped a NAS drive, and it works fine, but I can not see the photos, just a icon that represent the photo if you understand what I mean. The photos are JPG, nothing special

---

### Post by st33med on 2009-06-11
Does a little pull down menu near the top right say Icon View? If not, change it to that.

---

### Post by netjens on 2009-06-11
Nope, but I found out a weird thing just now, if I copy a photo from the NAS and put it on my HD under pictures, I can see the photo as thumpnail. Here is the really weird part, when I use gimp, and browse my picture on the NAS, I can see the photos as thumpnails, but not in the file view in ubuntu.

---

### Post by ethoxyethaan on 2009-06-11
open a terminal

cd /media/YOUR_DRIVE_NAME/PICTURE_FOLDER/

ls -l 

If the Read permissions are wrong it wont be able to form a **thumbnail**. 

you can post the output here if you are unsure.

---

### Post by asmoore82 on 2009-06-11
under any Nautilus "File Browser" Window,
Open "Edit -> Preferences" go to the "Preview" tab
and set your desired settings.

The default is to preview "Local files only."

---

### Post by nandemonai on 2009-06-11
> **asmoore82 said:**
> under any Nautilus "File Browser" Window,
Open "Edit -> Preferences" go to the "Preview" tab
and set your desired settings.

The default is to preview "Local files only."

+1 The problem is it's a remote file system. You'll have to set the thumbnails bit to 'always' to generate previews for remote shares.

---

### Post by netjens on 2009-06-12
Thanks everyone, it works great now after I made the settings so it should show not only local files :-)

---

