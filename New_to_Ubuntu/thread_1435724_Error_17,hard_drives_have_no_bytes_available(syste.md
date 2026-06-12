---
title: "Error 17,hard drives have no bytes available(system monitor)"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by MisFitt on 2010-03-21
"have no bytes available" is in error and I can't change it
Oh I've really done it this time!
Dual booting XPpro(32 bit) and Jaunty(64 bit)
On bootup I get 
Error 17.
XP wasn't recognising the HD Jaunty's installed on so I added a label(F:) and was doing some chkdsk and defrag because,well,Beta Lucid that I downloaded and was looking at alerted me to "imminent" failure of one hard drive and various problems with what I had thought was my perfectly fine 500GiB.
 EDIT-Somewhere whilst executing the attempt at repair/checking the hard drivesin XP,I've wiped my Jaunty installation somehow and now the problem is that I want to reinstal it and also 
how do I get into XP?I'd hate to have to reinstal everything if I don't have to
Thanks(oh pleeease!)

---

### Post by Ozymandias_117 on 2010-03-21
> XP wasn't recognising the HD Jaunty's installed on so I added a label(F:) and was doing some chkdsk and defrag because,well,Beta Lucid that I downloaded and was looking at alerted me to "imminent" failure of one hard drive and various problems with what I had thought was my perfectly fine 500GiB.
I can't access any files anywhere,not mounting?
Jaunty's in the small partition called 160Gib btw,/sda2 has all my media and files.
I do also have an external HD which is almost full.
excuse the mess!
BIOS looks ok though I'm not 100% sure,anyway,I'm praying and would be grateful for access,AGAIN, to this huge knowledge base,thanks in advance

Windows can't see Linux partitions unless you have special software on it.

Um, you most likely broke it by running chkdsk and defrag on it... They are windows programs designed to work on fat, fat32 and ntfs... not a Linux filesystem of Ext4 :P If there is a way to recover from that, I don't know of it. (Well, I mean recover your data, you can always reformat if there wasn't anything important).

BTW: Unix derivatives (Which Linux is) don't need to be de-fragmented, They are smarter than windows and just don't fragment your data in the first place ;)

edit: Forgot the exit /quote ;)

---

### Post by MisFitt on 2010-03-21
Thanks.
I actually read to do that re "failing" or suspect hard drives here and on another linux forum,wish I had waited until this morning!
Oh dear,I'd only just done a full install of both.Anyway,It seems I need to buy new hard drives,ouch.
Back to the old drawing board unless I can find a way to keep the xp(which would be great,sick of the sight of it but my significant other "needs it"

---

### Post by Ozymandias_117 on 2010-03-21
> **MisFitt said:**
> Thanks.
I actually read to do that re "failing" or suspect hard drives here and on another linux forum,wish I had waited until this morning!
If you remember the url, I'd like to visit and see if there is something I'm unaware of.
> **MisFitt said:**
> 
Oh dear,I'd only just done a full install of both.Anyway,It seems I need to buy new hard drives,ouch.

I doubt you did physical damage, you will just have to install again
> **MisFitt said:**
> 
Back to the old drawing board unless I can find a way to keep the xp(which would be great,sick of the sight of it but my significant other "needs it"
I don't understand what you mean "unless I can find a way to keep the xp" I was under the impression that you were only having problems with the Linux partitions?

---

### Post by Ozymandias_117 on 2010-03-21
Oh... I think I see, since your Linux partition is broken... GRUB won't load... so now you don't have an MBR... If you want both, just reinstall Linux to where it was.

If you only want Windows, boot to it's disk, press "R" for recovery mode. then type FIXMBR and FIXBOOT (You shouldn't need the second, but just in case.)

---

### Post by MisFitt on 2010-03-21
The URL would be in the history of firefox in Jaunty.
My XP pro for whatever reason doesn't have the repair function "R"(and it's a proper,full bought separately version)
BUT,I've just booted into the Lucid disk and I can see 5+GiB used where my Jaunty should be so it's likely a grub issue(hope,hope),AND btw it's not screaming about the hard drive health,at this point,anyway.
So,the question is can the GRUB be fixed(and how?) seeing it appears to be there????
Thanks so much for your time,it's much appreciated.
My mistake,it wasn't one of the forums I'd googled it was from Lucid,see the thumbnails.
I can barely wait for the final release,looks and is amazing.
The video programs hopefully will make it the perfect system for many more,myself included,big time.
Great move Canonical!THANKS!

---

### Post by Ozymandias_117 on 2010-03-21
If you want to try to just fix GRUB and see what happens, boot to your LiveCD. Click on "Places" then the filesystem with the size of your Linux partition. Once it is mounted, open a terminal and type ```
mount | tail -1 
``` which should output something like this ```
/dev/sda2 on /media/0d104aff-ec8c-44c8-b811-92b993823444
``` Plus some other stuff... make note of the /dev/*something* then in the terminal type ```
sudo grub-install --root-directory=/media/*type_in_the_first_few_letters_of_that_thing_you_saw_earlier_then_press_tab* /dev/*What_you_Made_the_note_of*
```

It should then install grub, reboot and see if it works. (If that didn't make sense tell me and I'll try to make it simpler :P)

---

### Post by Ozymandias_117 on 2010-03-21
> **MisFitt said:**
> The URL would be in the history of firefox in Jaunty.
My XP pro for whatever reason doesn't have the repair function "R"(and it's a proper,full bought separately version)
BUT,I've just booted into the Lucid disk and I can see 5+GiB used where my Jaunty should be so it's likely a grub issue(hope,hope),AND btw it's not screaming about the hard drive health,at this point,anyway.
So,the question is can the GRUB be fixed(and how?) seeing it appears to be there????
Thanks so much for your time,it's much appreciated.
My mistake,it wasn't one of the forums I'd googled it was from Lucid

Those aren't your Linux partitions it's telling you to run a chkdsk on, those are your windows partitions.

---

### Post by Ozymandias_117 on 2010-03-21
By the way, if you really did damage the Ubuntu Partition, that most likely won't work. But you can still try re-installing Ubuntu on that Partition which should get GRUB working and fix your problems.

---

### Post by MisFitt on 2010-03-21
I tried with several variations to do the GRUB but it was obviously beyond me,if I could take you up on your offer(smile)
I didn't quite understand but I'm trying,VERY hard!
I'm having flashes of all the tweaks I had to make on that install...........
However,I'm taking your advice and reinstalling jaunty 64.
I cannot wait for the final release of Lucid,it is absolutely gorgeous and has so many appealing features,love it-but I'm waiting,
new hard drive for it!
Thankyou again
-EDIT-have installed Jaunty again,all systems go,xp where I left it,GRUB fine.

---

### Post by Ozymandias_117 on 2010-03-21
First thing I would do, is boot to the LiveCD, and try to mount your Linux Partition (If you aren't sure which one it is, just mount them all.) Try to browse it. (There should be folders like /bin, /home, /sbin, /usr, /tmp, /var on your Linux Partition) If you can find a partition with those on it, we may have a chance :). (Also, if you do find it, make a note of which one it is.)

edit: When I say "We may have a chance" I mean of fixing your computer without reinstalling your OS ;)

---

### Post by MisFitt on 2010-03-22
Thanks but I had found it had been wiped so I did an install anyway.
I know I will need another hard drive before the LTS comes out which means learning how to keep my home and whatever other important data I have to pop back in.
Do you have any comments on hard drive health that's reported by 9.10 and 10.04 beta?
I pasted the 2 screenshots from Lucid live cd though the text's not too clear.

---

