---
title: "safe to manage windows partion?"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by robro on 2011-02-15
Hello commuinity,
well when i installed ubuntu i had no idea what a partion was, and i thought that the windows partion was the freespace, i reserved 86 gb's for it and left ubuntu with 47 gb's :| i am currently using 30 something gb's for windows, i was wondering if it was safe to shrink the windows partion to something aroung 40-50 gb's?

Thank you for your help :)

---

### Post by Mariane on 2011-02-15
Is your windows OS running OK? If yes it should continue to do so unless you fill it up (or it fills itself up). I just did the same thing only on a bigger disk. It had no idea how much space I should be leaving for windows so I gave Ubuntu 80% of the space. Then I tested windows and it was fine. 

Mariane

---

### Post by robro on 2011-02-15
Yeah it is running fine but i hate giving windows so much space and ubuntu so little :lolflag:

btw your signature is exactly what i do :lol:

---

### Post by Mariane on 2011-02-15
):P 

I will not advise about resizing the partitions, I'm not experienced enough. 

Mariane

---

### Post by BananaPeal on 2011-02-15
I've used gparted to resize a windows partition. Specifically, I've resized an XP partition (with all the stuff still on it) to make room for a win7 install so I could then move the files over more easily. After deleting the winXP partition, I made the win7 partition fill up the entire drive and it took a long time but it worked without hurting the data on it. 

It works fine, although like the disclaimer, no warranty! Make sure your power doesn't go out!

good luck!

---

### Post by robro on 2011-02-15
Thanks, ill make sure my power cord doesn't get cut in the process :lol:
but if i make the decision that windows is useless, will it hurt ubuntu if i completly delete my windows partion or for that matter make my computer only good as a boat anchor :lolflag:

---

### Post by BananaPeal on 2011-02-15
That's a question for your boot loader. If you've got a successful dual-boot right now I imagine you're using GRUB. I wanna say GRUB is robust enough to handle the missing os ... but try this thread:

[http://ubuntuforums.org/showthread.php?t=339973](http://ubuntuforums.org/showthread.php?t=339973)

every time i get grub to work it seems windows deletes it so i don't have enuf experience on this issue but according to that thread, seems to work nicely.

---

### Post by robro on 2011-02-15
ok but theres just one more thing im woried about, it says that i should backup all data on my hard drive, but the stupid piece of s*** windows dosn't recognize my 1.5 tb external hard drive :evil:
do you think its gonna go ok without problems?

---

### Post by PaulReaver on 2011-02-15
you could mount the windows partition from ubuntu and copy it across to the external disk???

if its xp... your pictures, videos, music, stuff'll be in c:/users/documents and settings/<user name>/

---

### Post by robro on 2011-02-15
*sigh* im thinking about getting windows out complely,
im going to install another OS on my system and all i have left is 17 gigs :(
but if i do, ill lose my antivirus on it, it was the last time i could install it and i dont want that to be wasted :(
is there anyway i could just backup that and delete windows?

---

### Post by BananaPeal on 2011-02-18
Hello,

Sorry I haven't been back in awhile, was pestering others with my installation problems  ... :confused: 

but to answer your question: My hdd was fullish, and I had no thumb drive. I was upgrading from xp to 7 on this box and I wanted both to exist briefly so that I could move the  old xp my docs etc over.

I used gparted because windows partition manager is still kinda cumbersome and doesn't let you do alot of things. and i think i had to boot live to be able to modify the partitions. 

Long story short, moved like 200gb when relocating the partition... i.e. it squeezed the partition to the back half of the disk and made a new ntfs for the front, moving files in the process (or something so the hdd light was on), took like 40-50 mins and all worked as promised!

Those disclaimers are precautionary... maybe just backup the really important stuff

---

### Post by BananaPeal on 2011-02-18
> **PaulReaver said:**
> you could mount the windows partition from ubuntu and copy it across to the external disk???

if its xp... your pictures, videos, music, stuff'll be in c:/users/documents and settings/<user name>/

you can mount ntfs in the new linuxes and read from ntfs (but not write in 9.10) but now apparently on liveCD 10.04, you can write to ntfs too... i just tried it!

---

### Post by robro on 2011-02-18
Well i finally got around to resizing my windows,
I am resizing it as i type this and to be frank, i realy dont care if it screws it up or not because i dont realy have anything important on there and it is just taking up space that i need for fedora.

:lolflag: it just finished but before i boot it up, is there anything i should do before so?

edit: well since no one posted again i guessed it was safe to boot, but sadly i was wrong :(










lol jk :lolflag: everything went fine and i now have enough space to install fedora :D thanks for your help everyone :)

---

