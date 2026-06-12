---
title: "Best way to get rid of Windows?"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by Kevinlittleton on 2010-01-02
I'm ready to make the switch from Windows to Ubuntu and I was wondering what the best way would be to get rid of XP on my computer. 

I'm dual booting Ubuntu Remix 9.10 and XP. I would just run the installer again and overwrite the whole drive but I have a lot of settings in Ubuntu and it took me forever to get wireless working right. Is there a way to save what I have and do a reinstall?

---

### Post by Exadrid on 2010-01-02
You can install gparted from repos and delete windows.

sudo apt-get install gparted
sudo gparted

and delete the ntfs partition, dont forget to save anything you might need on there!

---

### Post by J V on 2010-01-02
First, backup your /home... (Just archive them and stick them on a usb stick)

Then you can delete the windows partition (system > admin > disk utility) and add it to the ubuntu partition... Not sure *exactly* how this goes in palimpset, but after deleting the windows one you should be able to "enlarge" the ubuntu one.

If not, install the gparted program and you can do it from there...

---

### Post by Paqman on 2010-01-02
> **Exadrid said:**
> 
sudo gparted


You should always use gksu for graphical apps, not sudo. So to launch gparted from the command line it would be:
```
gksu gparted
```

Or simply go to System > Admin > Gparted.

---

### Post by J V on 2010-01-02
> **Paqman said:**
> You should always use gksu for graphical apps.*cough* *cough* gksudo *cough*

---

### Post by Cheesemill on 2010-01-02
Your going to have to boot from a Live CD as you can't resize mounted partitions.

When your running the Live CD go to System > Administration > Gparted then delete the Windows partition and resize your / partition to take up the available space.

Feel free to post screenshots of gparted before you make any changes if your not sure how to do this.

PS - It's recommended to have a backup of your system before making any partition changes, I've used gparted 100's of times without any issues but there's always a small chance of it messing up your disk.

---

### Post by Paqman on 2010-01-02
> **J V said:**
> *cough* *cough* gksudo *cough*

Same same.

---

### Post by Kevinlittleton on 2010-01-02
I'm using the bootable usb stick, does that work instead of the live cd?

---

### Post by Cheesemill on 2010-01-02
Yep, should be fine.

---

### Post by vvfrn on 2010-01-02
Use Gparted and delete the Windows partition.

---

### Post by Paqman on 2010-01-02
> **Kevinlittleton said:**
> I'm using the bootable usb stick, does that work instead of the live cd?

Yes. One thing to watch out for. The live session will automatically mount any available swap partitions (to improve performance). That has the effect of locking any other partitions contained within the same extended partition.

To solve this, in Gparted: right click on swap > swapoff.

---

### Post by Kevinlittleton on 2010-01-02
Ok, this is what I'm looking at. What do? And does that all look right?

---

### Post by Paqman on 2010-01-02
> **Kevinlittleton said:**
> Ok, this is what I'm looking at. What do? And does that all look right?

That's not Gparted, so even if you did use it to delete that partition, you wouldn't be able to give all the space you'd just freed up to Ubuntu. Hence why people were directing you to Gparted.

Try System > Admin > Gparted (or it might be called Partition Editor, depending on what version you've got...)

---

### Post by J V on 2010-01-02
ok, assuming you've backed up, first delete the "104GB filesystem"

Then in gparted, resize the extended partition to take up all available space, and the 54GB filesystem to take up all available space inside that...

You're done :)

---

### Post by nifty542 on 2010-01-02
Hi
Just a humble suggestion.You could google dban and make a clean install.It takes a while, but it's secure and it gives you all the options if you change your mind. You need to boot from a floppy disc or cd to do it, though
Regards
Nifty:)

---

### Post by Kevinlittleton on 2010-01-02
Ok, yeah my bad I wasn't booted from the usb drive yet but now I am and the gparted app is there. So delete the ntfs part?

---

### Post by J V on 2010-01-02
delete ntfs then enlarge extended and the 50 gig (50 gig is *in* extended so do extended first) then hit apply

Make sure you backup first...

---

### Post by Cheesemill on 2010-01-02
1 - Right-click on sda and select swapoff
2 - Delete sda1
3 - Resize sda2 all the way to the left
4 - Resize sda5 all the way to the left
5 - Click on the green tick to apply changes

---

### Post by J V on 2010-01-02
why don't they call logicals sda21 and sda22 hmm?

---

### Post by Cheesemill on 2010-01-02
> **J V said:**
> why don't they call logicals sda21 and sda22 hmm?

Is there really any reason to?

---

### Post by Kevinlittleton on 2010-01-02
> **Cheesemill said:**
> 1 - Right-click on sda and select swapoff
2 - Delete sda1
3 - Resize sda2 all the way to the left
4 - Resize sda5 all the way to the left
5 - Click on the green tick to apply changes

Followed said steps and it's 40 minutes away from applying all changes. Thanks so much everyone! I'll let you know if all is well in a little bit. Can't wait!

---

### Post by Kevinlittleton on 2010-01-02
Done! How do I get rid of grub?

---

### Post by Cheesemill on 2010-01-02
You don't. You need grub to boot Ubuntu.

Do you just want to remove the Windows menu entry?

---

### Post by Kevinlittleton on 2010-01-02
Oh I see, I just wanted to not have that grub screen pop up with all those entries. But alas if it needs to exist I will settle for that Windows Vista loader entry's death. :)

---

### Post by Cheesemill on 2010-01-02
Open a terminal and type:
```
sudo update-grub
```

This will remove the Windows entry and also set grub to hide the menu.

---

### Post by Kevinlittleton on 2010-01-02
It got rid of windows but the grub window still displays.

---

### Post by Cheesemill on 2010-01-02
Are you using 9.10 or 9.04 ?

---

### Post by Kevinlittleton on 2010-01-02
I'm using 9.10 remix on an Hp mini 110.

---

### Post by Cheesemill on 2010-01-02
You can get rid of the menu like this:
```
gksudo gedit /etc/default/grub
```To edit the grub config file.


Change the line
```
# GRUB_HIDDEN_TIMEOUT=0
```to
```
GRUB_HIDDEN_TIMEOUT=0
```save the file then update grub again:
```
sudo update-grub
```


See [here]("http://ubuntuforums.org/showthread.php?t=1302743") for more info if you need it.

---

### Post by Kevinlittleton on 2010-01-02
Epic! Thanks a million!  :guitar:

---

