---
title: "Formatted hard drive Gparted now no access."
date: 2011-06-04
forum: New to Ubuntu
---

### Post by cheekymonky2010 on 2011-06-04
Hi guys, I've recently tried Gparted and formatted one of my hardrives.  Now it just has a "Lost and Found" folder and I can't create any other folders in there?  I wanted to format it so that I could store music and films on it and have it as a location for Ushare and the Xbox! any help much appreciated??

---

### Post by cheekymonky2010 on 2011-06-04
Hi guys, I've recently tried Gparted and formatted one of my hardrives. Now it just has a "Lost and Found" folder and I can't create any other folders in there? I wanted to format it so that I could store music and films on it and have it as a location for Ushare and the Xbox! any help much appreciated??

Apologies for double thread, had too many typos to make sense!

---

### Post by cheekymonky2010 on 2011-06-04
:KS Fixed it! Just reformatted the hardrive in Gparted to ext4 and formatted the hardrive from Computer in ubuntu to ext4.  Can now create folders inside it!  not sure if it will work with Ushare just yet but it's a step forward I guess.  think 2 days at the computer is enough for now! :guitar:

---

### Post by howefield on 2011-06-04
Duplicate threads merged.

---

### Post by leviathan8 on 2011-06-04
You can always change the permissions of the filesystem, assuming that you already have ubuntu and a user installed on one partition. 
To do this, you launch nautilus as root with [FONT="Fixedsys"]gksu nautilus[/FONT] , mount the desired filesystem, navigate to the /media directory, and once you see the name of the new partition, right click on it then go to permissions. Now set read/ write permissions on your user.

---

### Post by cheekymonky2010 on 2011-06-04
Thanks a lot guys :D

---

### Post by thahirkoya on 2012-01-09
thanks leviathan8  :D

---

