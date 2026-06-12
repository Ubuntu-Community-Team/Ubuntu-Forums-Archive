---
title: "How to find mount point for ipod to use gtkpod"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by Colonel Forbin on 2010-02-19
I just got a new ipod touch, and can't seem to find  where it is mounting. When I plug it in, ubuntu sees it as a digital camera and wants to know if I want to run fspot. I need to find the mount point so I can use gtkpod. Or, ideally, to use amarok. How do I do that? I have looked at media, and it is not there, and it is also not showing in mnt. Any help is appreciated.

---

### Post by mikewhatever on 2010-02-19
Run 'mount' in Terminal to see all that's mounted.

---

### Post by Colonel Forbin on 2010-02-19
ok, I tried that, and it doesn't appear to be there. I'm confused why it comes up as ipod and a digi camera, but doesn't appear in mount of fdisk -l.

---

### Post by donkey24 on 2010-02-25
Im having the same problem. GTK doesnt have the 32 gig model to choose from when choosing the model. This really makes me upset with them holes at Apple for being so damn stuck up.

---

### Post by lamachine on 2010-06-19
apt-get install ifuse 
plug the ihpone via USB and
Command line:
ifuse /mnt/ipod 

Replace the "/mnt/ipod" with where ever you want to mount it 
The iphone / ipod file system will show up under your mounted point 

For amarok users =>  [http://lifehacker.com/388785/sync-your-iphone-wirelessly-in-linux](http://lifehacker.com/388785/sync-your-iphone-wirelessly-in-linux)

---

### Post by donovanh on 2010-06-22
I'm having trouble with this issue also.

I can see my music in Rhythmbox, but can't seem to work out how to set up gtkpod. There isn't any /media/ipod!

When trying the above, it says that the specified mount point doesn't exist. :(

---

### Post by lamachine on 2010-06-22
> **donovanh said:**
> I'm having trouble with this issue also.

I can see my music in Rhythmbox, but can't seem to work out how to set up gtkpod. There isn't any /media/ipod!

When trying the above, it says that the specified mount point doesn't exist. :(

Of coz the specified mount point doesn't exist if there isn't any /media/ipod
Run mkdir -p /media/ipod and repeat the procedure described in note               #[**5**]("http://ubuntuforums.org/showpost.php?p=9482812&postcount=5")

---

### Post by barracuda9000 on 2011-01-09
The mount point that nautilus uses for the iPhone 3GS in this case is  ~.gvfs (it will probably use that same location to mount an iPod touch  as well). This is a hidden directory (because of the dot in the name) so  you won't be able to navigate to it from a file browser window. You can  access it without having to use a command-line in 3 steps. First,  minimize all windows, click anywhere on your desktop, then hit the / key  and an "open location" window should appear. Second, type out the full  path name of the mount point (/home/<your_home_folder>/.gvfs) and  hit enter. Finally, when the nautilus window opens, you will see another  folder with the name of your device. Double click on it and there will  be all the media on that device available in other folders.
Let me know if you encounter any problems - good luck.

---

