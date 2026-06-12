---
title: "Update blender."
date: 2011-05-01
forum: New to Ubuntu
---

### Post by abnordude on 2011-05-01
I installed blender from the ubuntu software centre.
But it is not latest version.
How do I get the latest version of blender.
WELL.....
Infact, how do I get the latest version of other stuff??
Like maybe eclipse.............and so on.

---

### Post by RedBird on 2011-05-01
It is known that Ubuntu Software Center only updates its repositories whenever security requires.

To always get the latest and greatest version of Blender, you should download it yourself from [this page]("http://www.blender.org/download/get-blender/").

How to install it, incase you don't know:

1. Download the latest version from [here]("http://www.blender.org/download/get-blender/") and choose carefully if you want the 32bit or 64bit version.
2. Extract it. Note: I always extract my programs in /usr/local/bin/ and let's assume that your download is in the Downloads folder and its the 32bit version.
```
sudo tar xvjf ~/Downloads/blender-2.57b-linux-glibc27-i686.tar.bz2 /usr/local/lib/
```
3. Insert the entry into desktop menu. Right click on the top bar of the desktop where it says: "Applications Places System" and choose Edit Menus.
4. Go to Graphics group on the left, then press on '+ New Item' button on the right.
5. Type the name 'Blender 2.57b' or whatever.
6. In the command blank space, click on Browse and choose the file 'blender' inside the folder of Blender that we just extracted so that the command becomes something like this:
/usr/local/bin/blender-2.57b-linux-glibc27-i686/blender
7. Optional: :p type in the comment: 'Create and edit 3D models and animations'
8. Optional: If you want to the icon of Blender for your just-created launcher you can get it from icons folder inside Bledner folder.
I choose the scalable icon in
/usr/local/bin/blender-2.57b-linux-glibc27-i686/icon/scalable/

That's it the same goes with every other application you want to install. Not to forget, eclipse is in tar.gz so the code to extract should be

```
tar -zxvf ~/Downloads/eclipse-SDK-3.6.2-linux-gtk.tar.gz /usr/local/bin/
```

---

### Post by abnordude on 2011-05-01
> **RedBird said:**
> It is known that Ubuntu Software Center only updates its repositories whenever security requires.

To always get the latest and greatest version of Blender, you should download it yourself from [this page]("http://www.blender.org/download/get-blender/").

How to install it, incase you don't know:

1. Download the latest version from [here]("http://www.blender.org/download/get-blender/") and choose carefully if you want the 32bit or 64bit version.
2. Extract it. Note: I always extract my programs in /usr/local/bin/ and let's assume that your download is in the Downloads folder and its the 32bit version.
```
sudo tar xvjf ~/Downloads/blender-2.57b-linux-glibc27-i686.tar.bz2 /usr/local/lib/
```3. Insert the entry into desktop menu. Right click on the top bar of the desktop where it says: "Applications Places System" and choose Edit Menus.
4. Go to Graphics group on the left, then press on '+ New Item' button on the right.
5. Type the name 'Blender 2.57b' or whatever.
6. In the command blank space, click on Browse and choose the file 'blender' inside the folder of Blender that we just extracted so that the command becomes something like this:
/usr/local/bin/blender-2.57b-linux-glibc27-i686/blender
7. Optional: :p type in the comment: 'Create and edit 3D models and animations'
8. Optional: If you want to the icon of Blender for your just-created launcher you can get it from icons folder inside Bledner folder.
I choose the scalable icon in
/usr/local/bin/blender-2.57b-linux-glibc27-i686/icon/scalable/

That's it the same goes with every other application you want to install. Not to forget, eclipse is in tar.gz so the code to extract should be

```
tar -zxvf ~/Downloads/eclipse-SDK-3.6.2-linux-gtk.tar.gz /usr/local/bin/
```


Ok. but I already have blender installed.
I just need to update it.
Isn't there any stable ppa's out there?

---

### Post by Lateralis on 2011-05-01
[This Ubuntu forums thread]("http://ubuntuforums.org/showthread.php?t=1184942") might be of interest.

---

