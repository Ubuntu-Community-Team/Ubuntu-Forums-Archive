---
title: "How do I remove Windows XP from a dual boot with Ubuntu"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by djokela1 on 2009-04-27
Hi,

I installed Ubuntu 8.10 to dual boot with Windows XP (and have since upgraded to 9.04). After spending some time with Ubuntu, I've decided I want to get rid of Windows 

All the forums on this topic instruct me to use GParted to delete the windows partition, but when I open GParted, I only see one partition, an NTFS partition.

Does that mean that Ubuntu is installed within the same partition as Windows? If so, how can I retain Ubuntu and all it's programs/settings while deleting the windows portion? Can I/do I have to move Ubuntu to its own partition (ext3, or something...), and then delete the NTFS partition? 

If I need to move Ubuntu to a separate partition before deleting NTFS, how do I do that? 

I'm quite a beginner, so maybe there's something obvious I'm missing or terminology I'm mixing up. I just want to get rid of Windows to free up space and remove all the junk that has accumulated over the years, then let Ubuntu purr. 

Thanks in advance for your help!

---

### Post by mikewhatever on 2009-04-27
You probably see the ntfs partition because you installed using wubi. Here is a quote from wubi FAQ: [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)
> 
Can I move my virtual disk file to a dedicated partition?

You can use LVPM to transfer your installation. A guide and support forum for LVPM is available here.


---

### Post by ssdt on 2009-04-27
Whatever you do, don't right click on my computer and then in the "manage" don't delete anything. It might delete everything if you do that.

---

### Post by sydbat on 2009-04-27
It sounds like you have a wubi install (meaning you installed Ubuntu as a program inside Windows).

My suggestion is this - backup EVERYTHING important from Ubuntu AND Windows (all your photos, documents, emails, everything) before doing anything else. Burn it all to CDs or DVDs or, if you have one available, move everything to a separate hard drive. 

Also, make a "backup" of installed applications you want to reinstall after you nuke everything by doing [this]("http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/").

Then, after you are sure you have everything backed up, boot up the Live CD and install Ubuntu, following the directions [here]("https://help.ubuntu.com/community/GraphicalInstall").

Alternately, you could try [this procedure]("http://ubuntuforums.org/showthread.php?t=438591"), but it leaves Windows intact on your box, and it sounds like you do not want that.

EDIT - almost forgot the most important thing...[this site]("http://psychocats.net/ubuntu/index.php") has some of the most thorough and best tutorials for Ubuntu!

---

### Post by ikisham on 2009-04-27
Also backup your important files (maybe your ubuntu folder - that's the way it's stored, isn't it?) before you resize the partition to create space for the ubuntu install.
After you have installed it to your hd you may format the Windows partition if you want.

EDIT. never mind, sydbat gave a more embracing response.

---

### Post by Johnsie on 2009-04-27
Just drink the kool aid and Windows will disappear forever

---

### Post by sydbat on 2009-04-27
> **Johnsie said:**
> Just drink the kool aid and Windows will disappear foreverMmmmm...kool aide...<insert Homer drooling here>...

ikisham - Thanks.

---

