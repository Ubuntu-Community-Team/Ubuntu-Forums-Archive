---
title: "Jaunty locked up due to upgrade"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by joneseyrocks on 2009-05-16
[FONT=Lucida Console]i recently attempted to update my video driver to optimize 3d mmorpg gameplay and now i cant even log on to my computer as the password page will not allow me to type i have an Intel 82865G video card. also is there a way to rollback to ubuntu8.10 without losing my saved files ? someone plz help this is my second call for help[/FONT]

---

### Post by guywithcable on 2009-05-16
> **joneseyrocks said:**
> [FONT=Lucida Console]i recently attempted to update my video driver to optimize 3d mmorpg gameplay and now i cant even log on to my computer as the password page will not allow me to type i have an Intel 82865G video card. also is there a way to rollback to ubuntu8.10 without losing my saved files ? someone plz help this is my second call for help[/FONT]

Have you tried using an external keyboard?

If that doesn't work, there should be a backup of your xorg.conf file in /etc/X11. You need to boot into an Ubuntu CD, go to your drive from the Places menu, once it is mounted, run:

```
gksu nautilus
```This will get you an administrator nautilus window. Go to your disk (not the current filesystem. probably /media/disk), then go to etc, then X11. In that folder, rename xorg.conf to xorg.conf.broken. Now look for a backup of xorg.conf (probably named xorg.conf.backup). Copy the most recent backup file and rename the copy to xorg.conf. Try rebooting your computer back into Ubuntu.

If this doesn't fix it, I can help you reinstall without losing your data. Let me know.

---

### Post by joneseyrocks on 2009-05-18
i tried unsuccessfully if you could walk me through the reinstall of 8.10 without losing files i would appreciate it thanks

---

### Post by gashcr on 2009-05-18
is your /home folder in a separate partition?

---

### Post by guywithcable on 2009-05-18
This is how you would reinstall without losing your data:

[LIST=1]
[*]Go to the live CD
[*]Mount the Ubuntu partition
[*]Run "gksu nautilus"
[*]From nautilus, go to the Ubuntu drive and create a new folder in it called "broken-system"
[*]Move everything but the home folder into that new folder
[*]Rename the home folder to "home-old"
[*]Close everything and unmount the disk
[*]Open the installer from the desktop
[*]When you get to the partitioner, choose manual partitioning
[*]Select the Ubuntu partition and choose to use it as ext3 with a mountpoint of /
[*]DO **NOT** FORMAT IT!
[*]It will tell you that it is going to overwrite any system folders. That's ok because you moved all the system folders.
[*]Be sure you use the same username as before
[*]Let it install, then choose to keep using the live CD
[*]Mount the partition again
[*]Run "gksu nautilus" again
[*]Go to the drive, and rename the new home folder to "home-empty"
[*]Rename the home-old folder to "home"
[*]Close everything and reboot
[*]Once you're in the system, you need to reinstall all your packages, but all your settings and files should be there.
[*]If you changed any config files in /etc you can bring them back from /broken-system/etc
[/LIST]
Hope that helps. :grin:

---

### Post by joneseyrocks on 2009-05-18
i dont know much about these partitions and mounting things so i think i will just reinstal 8.10 from scratch and deal with the lost files if i could just remove the updates that caused this mishap then i would be able to save my files to flash drive and then reinstall 8.10 is that possible?

---

### Post by guywithcable on 2009-05-18
If you go into a live CD, your Ubuntu partition will be listed under the Places menu. It will probably be labeled as the size of the partition (XX GB Media), unless you specified a label when you originally partitioned it. To mount it, all you have to do is click on that entry in the menu. From there, you should find your home folder, and inside that will be a folder for your user. That folder should contain all your files (Ubuntu doesn't let you save files elsewhere, unless you specify an administrator password.) You can copy that folder to a flash drive, or burn it to a CD. Whatever you like, but that's where all your stuff is. :) After you copy all your files and verify that they copied correctly (which is important), you can reinstall Ubuntu, and copy your files into your new Home Folder.

PS: It's not a good idea to copy your files to a Windows (NTFS) formatted flash drive, because they won't maintain their permissions, which could cause unpredictable things to happen.

---

### Post by guywithcable on 2009-05-18
All the software you've installed with Wine should be in that folder too. So once you reinstall Wine (if you're using it), you can copy that folder back and all your software will still be there (and should still work.)

The wine folder is hidden, because its name begins with a period. It is located in your user's home folder and called ".wine"

If you want to see hidden files while browsing a directory, go to the View menu, and click "Show Hidden Files"

---

### Post by joneseyrocks on 2009-05-19
so i got tired of everything freezing on me and reinstalled 8.10 and ran the updates. i refuse to go back to 9.04 i then reinstalled the game i am playing and now have issues with the add on things necessary to play in wine. the directions are not designed for someone who has no clue how to run the technical aspect of a linux system. they read as follows "
**Regedit configuration:**     
[I]Add "Direct3D" key to HKEY_CURRENT_USR -> Software -> Wine                     
[/I]*Add the following String Values to the Direct3D key:*




[I]DirectDrawRenderer                           "opengl"                                                 
Nonpower2Mode[/I]*                                "repack"*     
*OffscreenRenderingMode*[I]                       "fbo"                                                                                                         
PixelShaderMode[/I]*                               "enabled"*     
*RenderTargetLockMode*[I]                       "auto"                                                                                                           "
I am not sure how to do all of this if they had more of an IDIOTS GUIDE walk through i might get it the next step is pretty easy it is installing directx9 through wine trix but if you can offer any help with the regedit part i would be very grateful.
[/I]

---

### Post by guywithcable on 2009-05-19
> **joneseyrocks said:**
> so i got tired of everything freezing on me and reinstalled 8.10 and ran the updates. i refuse to go back to 9.04 i then reinstalled the game i am playing and now have issues with the add on things necessary to play in wine. the directions are not designed for someone who has no clue how to run the technical aspect of a linux system. they read as follows "
**Regedit configuration:**     
[I]Add "Direct3D" key to HKEY_CURRENT_USR -> Software -> Wine                     
[/I]*Add the following String Values to the Direct3D key:*




[I]DirectDrawRenderer                           "opengl"                                                 
Nonpower2Mode[/I]*                                "repack"*     
*OffscreenRenderingMode*[I]                       "fbo"                                                                                                         
PixelShaderMode[/I]*                               "enabled"*     
*RenderTargetLockMode*[I]                       "auto"                                                                                                           "
I am not sure how to do all of this if they had more of an IDIOTS GUIDE walk through i might get it the next step is pretty easy it is installing directx9 through wine trix but if you can offer any help with the regedit part i would be very grateful.
[/I]

To get into the registry editor in wine, run "wine regedit". Then you go to that folder "HKEY_CURRENT_USR/Software/Wine" then right click in the right side, and go to New -> Key, go into that folder, then New -> String Value.

---

### Post by joneseyrocks on 2009-05-19
everytime i go to the registry and try to add a new key it says invalid handel what does this mean?
i hate being soo close to done and unable to fix it myself

---

### Post by joneseyrocks on 2009-05-19
everytime i go to the registry and try to add a new key it says invalid handel what does this mean?
i hate being soo close to done and unable to fix it myself

---

### Post by guywithcable on 2009-05-19
I don't know. It's working on mine. :(

---

### Post by joneseyrocks on 2009-05-20
does it matter that my comp is a dell with an Intel 82856G video driver and that neither dell nor Intel support ubuntu on this machine?

---

### Post by guywithcable on 2009-05-20
I think if it's happening in Wine, it's probably a Wine issue.

---

