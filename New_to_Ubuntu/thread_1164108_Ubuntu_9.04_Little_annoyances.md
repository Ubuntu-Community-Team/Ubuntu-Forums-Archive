---
title: "Ubuntu 9.04 Little annoyances"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by matey3 on 2009-05-19
I really like the new jaunty 9.04 and I am NOT complaining at all, but I was rather surprised that upon installation it did not have any options for Upgrading (from 8.04)!?
(I really installed it to update my defunct 8.04 installation because it would not update/upgrade and/or nothing else bcs something was wrong with bacula!?
Not even apt-get install -f worked, it kept giving errors about bacula and mysql etc.?? and kick me out... so I upgraded...)

So I lost all my files and programs.
Now my tool-bars seem to be locked with no options to get them to unlock or move them to another location.(I prefer the bottom of screen)

Then I could not setup root password,(but I solved that so I could do some things).
Anyway, it seems like upon new install the newer OS should ask about root's password for the Old OS then let you go about your business as usual.
But I have not seen that in this or any previous versions either...

Anyway I know it is my lack of expertise in linux (Hence this is the "Absolute Beginners" forum), but I hope they improve on those points (mainly the installation) in the future. 

Thanks a lot!
):P

---

### Post by Ms_Angel_D on 2009-05-19
You can't upgrade from 8.04 to 9.04  you have to go  "8.04 -> 8.10 -> 9.04" it's the only way upgrading will work.

Not sure what to say about the toolbar issues.

---

### Post by lovinglinux on 2009-05-19
> **matey3 said:**
> I really like the new jaunty 9.04 and I am NOT complaining at all, but I was rather surprised that upon installation it did not have any options for Upgrading (from 8.04)!?

Hardy Heron 8.04 is a LTS release (Long Term Support). So it is supported until 2011 and can be upgraded directly to a new LTS release, or you can do the steps already mentioned.

> **matey3 said:**
> So I lost all my files and programs.

Before upgrading you can run a command to generate a lit of installed software and run another command to download and install them all at once again. Next time follow the instructions bellow:

> **lovinglinux said:**
> 
To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

```
dpkg --get-selections > ~/my-packages
```

This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```

It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository

To preserve your configurations and personal files, is recommended to create a [separate partition for /home](http://www.psychocats.net/ubuntu/separatehome). It will preserve most of your settings when you make a clean install.

> **matey3 said:**
> Now my tool-bars seem to be locked with no options to get them to unlock or move them to another location.(I prefer the bottom of screen)

Right-click on an empty space of the panel, select "Properties" and then select the "Orientation" option.

> **matey3 said:**
> Then I could not setup root password,(but I solved that so I could do some things).

Ubuntu comes without root password for security reasons. You shouldn't bypass this. Whenever you need root access, you should run the command with sudo in front of it. It will ask for your user password and if you are the administrative user (the default first user), then you will be able to do anything you need.

---

### Post by matey3 on 2009-05-19
> **Ms_Angel_D said:**
> You can't upgrade from 8.04 to 9.04  you have to go  "8.04 -> 8.10 -> 9.04" it's the only way upgrading will work.

Not sure what to say about the toolbar issues.

Thank you for the reply.
I did not realize that! I wished I had it that way, I could not run apt-get anything so I had to download the ISO to burn it on a CD so I just found 9.04, I wished I had asked before I did the upgrade.
Umm, learn something new every day :)
Thanks!

NOW If I could find out how to change my Monitor's driver in the GUI (I dont really want to mess up my xorg.conf) lol, then it would be great!

I googled it and found displayConfig-GTK but that has been obsolete in 9.04!?

---

### Post by matey3 on 2009-05-19
> **lovinglinux said:**
> Hardy Heron 8.04 is a LTS release (Long Term Support). So it is supported until 2011 and can be upgraded directly to a new LTS release, or you can do the steps already mentioned.





Thank You very much LovingLinux for a complete/thorough reply!
I copied the whole thing and I am going to email it to myself for future reference (cuz I dont trust saving it to this machine any more lol) :)
But I do appreciate it.

Regards;

---

### Post by Mark Phelps on 2009-05-20
Didn't notice whether you installed from the LiveCD or the alternate CD.  I'm guessing you installed from the LiveCd and reformatted your partitions -- which is why you lost everything.

The alternate CD gives you the option of manually partitioning and deciding which partitions to reformat.  If you partition with /home on its own partition, when you install using this method, you can tell it NOT to reformat /home, which will leave your files and data there intact.

Something to think about for future "upgrades".

---

