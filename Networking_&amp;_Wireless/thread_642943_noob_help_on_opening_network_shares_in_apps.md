---
title: "noob help on opening network shares in apps"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by LAD29 on 2007-12-17
Hi all,

This maybe a very silly question but I just can't figure it out myself and cannot seem to find my way to a post with my 'problem'.  I'm running gutsy desktop on my laptop.

Basically I'm trying to burn a Ubuntu Server ISO image to CD where the image is stored on a Server shared network folder.

I can create a share to the folder which I can then access from the list under the Places menu no problem, but when I open an app (in this instance Nero) where do I navigate to to then find my network shared folder?

This got me thinking therefore, when I create these Network shared folders where and how in general can I get to them from any apps?

Cheers
J

---

### Post by d0nny2600 on 2007-12-17
Depends on how you would normally access the network. For example if the server folder you want is on the server myServ and the folder is called myFolder you would type

\\myServ\myFolder

---

### Post by LAD29 on 2007-12-17
Sorry, I'm not sure what you mean.  How can I get to the share from within the app browsing folders?

If I open Nero, then click on File>Open I see the list of local folders.  If I type in the server share path in the location box nothing happens.

So, I figured there must be a folder(s) to click through to access the share?

---

### Post by airtonix on 2007-12-17
If you using gnome desktop, then you'll be using the nautilus file browser....

now to access any remote share you have access to(within a file-chooser-dialouge box) it needs to listed within your favourties/bookmarks....

To bookmark your shares or a location within the hierachy of your shares, just make sure your sidebar is open(F9 toggles it) and change the view of the side bar to show bookmarks...then drag the desired folder to book mark....

I think you can also drag a piece of text that is a path to the place into this area and will also do the same thing...

once it is there, you can access that entry in any file-chooser dialouge box.

You may find that some apps dont allow you access to these 'bookmarks-of-remote-places', and in these cases, i would look at mounting remote file systems to local folders...which does a much better job for long term usages.

---

### Post by LAD29 on 2007-12-18
Thanks for your post.

Hmm... I can see favs/bokmarks of Network Shares in the file browser but not in a File Open Dialog in Nero.

I'll investigate mounting folders and see if that works.

Cheers.

---

