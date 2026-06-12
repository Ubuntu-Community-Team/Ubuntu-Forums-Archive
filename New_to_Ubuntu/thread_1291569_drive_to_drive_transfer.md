---
title: "drive to drive transfer?"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by meamjw on 2009-10-14
I have a machine with Windows XP Home that is refusing to boot. Today I have been getting acquainted with Ubuntu in the hope it would help me fix Windows. So far haven't found it to be any help with that because it won't open the files I think I need to access. Now, I have decided my best option is probably to move all files except Windows from my "C" partition to an external drive then reformat "C" and install Windows 7. My question is: how can I use Ubuntu to transfer those files? Is it possible for Ubuntu to use Windows Easy Transfer? Is there some other app that will do the job? I have another computer with Vista that is only three feet away, so maybe it needs to play a part in the transfer? I'm dumb as a rock when it comes to command line so please don't suggest any of that.               Thanks for any help.

---

### Post by tuxxy on 2009-10-14
If you can then you could plug the windows drive into a spare slot in your Ubuntu machine and then boot Ubuntu and simply mount the windows drives using nautilus and copy the files over using drag and drop

---

### Post by Paqman on 2009-10-14
> **meamjw said:**
> it won't open the files I think I need to access.

If that's the crux of your problem, maybe we can help.

So, can you get the Windows drive mounted and navigate through its contents? It should show up in the Places menu, but won't be mounted until you click on it.

---

### Post by zeroseven0183 on 2009-10-14
You could probably use your Ubuntu LiveCD. Boot using that liveCD to your computer with Windows, plug your external hard drive and transfer the files from there.

---

### Post by meamjw on 2009-10-15
Yes, I can see the files on the dead machine when Ubuntu is running. What is nautilus that you mention,tuxxy? I find no such thing in Ubuntu.
Ubuntu can't see my external drive. It is connected to the XP machine by SATA cable. Don't know if that has any bearing. As for drag and drop, I have never tried place to place transfer that way. Can I drag and drop an entire folder? I have thousands of files I want to keep on "C" drive. Doing them one at a time would be hopeless.

---

### Post by nothingspecial on 2009-10-15
Nautilus is the default ubuntu file browser (the window that opens up with all those little file pictures in it).

Yes you can drag and drop entire directories with it.

---

### Post by The Cog on 2009-10-15
The external drive should be visible in the **Places** menu as something like **120G Media**. Or in the file explorer (called nautilus) click the Computer icon. If the external drive doesn't show up there then we will have to do some debugging, or perhaps find a USB external drive instead.

You need two instances of nautilus running - one looking at your Windows disk and one looking at the external disk. Then just drag/drop folders between the two. Provided that the two windows are looking  at different drives then drag/drop will copy folders rather than just moving them. 

After all the drag/drop is finished, you must right-click their icons on the desktop and unmount them before unplugging the external drive - this is the equivalent of windows "safely remove" hardware. Or shut the machine down before unplugging.

---

### Post by meamjw on 2009-10-15
I just tried again to find my external drive with Ubuntu. It does not show it. 
Ubuntu reports a 132.4GB Media, 31.5GB Media and a "local disk" for which it gives a properties option. Properties says that is 24.4GB. It also shows an "image" drive but gives no size and no properties option for that.
What I actually have on that computer is a 160GB Maxtor with partitions of "C" and "D". That, of course is where Windows lives (or did live. It now lies in repose) There is also an 80GB Seagate with partitions "H" and "I".
I believe Ubuntu is reporting the free space as the capacity and that what it calls "local disk" is the "H" partition and what it calls "image" is the "I" partition.
All the foregoing babble simply means I have had a bit of trouble figuring out what it is actually showing. It definitely does not show my 500GB external.
 
Another idea has occured to me, but I'm not sure it would work. Since most, or all, you guys are much more computer savvy than I, you tell me if it is worth a try: Maybe I wouldn't even need Ubuntu, Windows, or other OS if I can just unhook the IDE cable from the drive containing Windows corpse and hook whatever adapter cable I need to the Vista machine, which is three feet away. Power could still come from the XP machine to run the drive. The Vista machine should think it has acquired a new drive. Then if I hook the external to the Vista machine, that machine should be able to handle all the transfer. Right or wrong?

---

### Post by LewRockwell on 2009-10-15
learn and use Clonezilla

[http://clonezilla.org/](http://clonezilla.org/)

Clonezilla is also included in the utility suite of Parted Magic LiveCD:

[http://partedmagic.com/](http://partedmagic.com/)

.

---

### Post by az on 2009-10-15
> **meamjw said:**
> Maybe I wouldn't even need Ubuntu, Windows, or other OS if I can just unhook the IDE cable from the drive containing Windows corpse and hook whatever adapter cable I need to the Vista machine, which is three feet away. Power could still come from the XP machine to run the drive. The Vista machine should think it has acquired a new drive. Then if I hook the external to the Vista machine, that machine should be able to handle all the transfer. 

Yup.  Should work fine.  What kid of cable are you going to use?

---

### Post by meamjw on 2009-10-15
Don't know yet. The drives in the XP use IDE, but I havent had the Vista apart, so don't know what it uses.

---

### Post by meamjw on 2009-10-15
Az, I tried to give you a quick reply a couple hours ago, but it seems to have lost it's way. It said, "I don't know yet. The XP machine has IDE cables but I have never had the Vista machine apart, so don't know what kind it has.

---

### Post by The Cog on 2009-10-15
I think it's a bad idea to try to power a drive from one machine while the IDE cable is connected to the other. You may run into electrical earthing issues. If possible, move the drive completely to the Vista machine.

The vista machine may only have SATA disk connectors, which would scupper that plan. Otherwise it should work fine.

---

### Post by az on 2009-10-15
> **The Cog said:**
> I think it's a bad idea to try to power a drive from one machine while the IDE cable is connected to the other. You may run into electrical earthing issues. If possible, move the drive completely to the Vista machine.



I've run drives like that lots of times.  Obviously, don't touch anything together than can cause a short, but the IDE bus doesn't care about the power source.  And the power source supplying the motherboard doesn't have to be the same that is supplying the drive.

---

