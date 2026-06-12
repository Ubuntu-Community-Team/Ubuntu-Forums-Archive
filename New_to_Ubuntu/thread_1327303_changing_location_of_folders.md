---
title: "changing location of folders"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by vikman on 2009-11-15
I can do the following in windows.....
within my main user folder I can change the location of my various folders- documents, music, pictures etc....
for example....
my main user folder can be in c:\users\user_name
           in that my pictures folder can be located in d:\pictures
                          music can be located in d:\media\music

How can I achieve this in ubuntu?

---

### Post by BDNiner on 2009-11-15
One suggestion would be to use short cuts. I don't know of another way to change the path that a folder in your home folder points to like you can in windows by changing the registry.

I don't know if creating a symbolic link would acheive what you are trying to accomplish.

---

### Post by Jon Monreal on 2009-11-15
I'm not exactly sure why you would want to do this, and you can find a pretty good explanation of how the home folder works [here]("https://help.ubuntu.com/community/HomeFolder").

Are you trying to share files between Ubuntu and another Operating System? Or is there some reason for wanting separate partitions (with Windows, C:\, D:\ and so on)?

---

### Post by vikman on 2009-11-15
> **Jon Monreal said:**
> I'm not exactly sure why you would want to do this, and you can find a pretty good explanation of how the home folder works [here]("https://help.ubuntu.com/community/HomeFolder").

Are you trying to share files between Ubuntu and another Operating System? Or is there some reason for wanting separate partitions (with Windows, C:\, D:\ and so on)?

yes... I am trying to share it with windows... not yet ready to make full switch to ubuntu since rest of family is not prepared....
I want the music, documents and pictures to be accessible from both Operating systems....

---

### Post by vikman on 2009-11-15
> **BDNiner said:**
> One suggestion would be to use short cuts. I don't know of another way to change the path that a folder in your home folder points to like you can in windows by changing the registry.

I don't know if creating a symbolic link would acheive what you are trying to accomplish.

In windows I don't even go to the registry... I just right click on the folder click properties and changes the folder location to where I want it to point to.....

---

### Post by Jon Monreal on 2009-11-15
Somebody else just started a [thread on the exact same thing]("http://ubuntuforums.org/showthread.php?t=1327286") a little while ago.

Hope that helps you.

---

### Post by halitech on 2009-11-15
your /home folder has to be on an native linux partition. You can use ntfs-config to mount the windows drive and create shortcuts in nautilus to point to those locations.

---

### Post by BDNiner on 2009-11-15
> **vikman said:**
> In windows I don't even go to the registry... I just right click on the folder click properties and changes the folder location to where I want it to point to.....

Ok, I didn't know that the right click option was present. I have always done it through group policy on a domain. Thanks for that info.

Anyways, since you are trying to share files between windows and Ubuntu I would suggest that you leave everything on the windows partition. Ubuntu can read NTFS pretty well. I cannot say the same for Windows reading EXT3 or EXT4. You would then have to create an entry in your /etc/fstab file to mount the windows partition on boot up, otherwise you would have to remember to mount it every time you log into Ubuntu. You would then have to create a symbolic link to the path of you folders on the windows partition to replace the ones in your home folder, and change the icons to your liking. There isn't a right-click/change location option in Ubuntu that I am aware of, so this would be the method that I would accomplish was you are trying to do. I hope this helps.

---

