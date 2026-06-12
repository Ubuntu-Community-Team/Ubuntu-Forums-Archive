---
title: "won't boot anymore 9.04 HELP"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by sneakyB on 2009-05-04
hi all,

had some probs with the new ubuntu... no video driver, ni wifi driver etc...
have been trying a couple of recommended solutions, and now my ubuntu 9.04 won't start anymore.

I still get the loading screen, but right before the page where you have to enter username and pasw, the screens goes black, flashes a couple of times, and that's it!

this is on my work pc, so real bad :s. is there a way to boot anyhow? (tried safe mode etc, but same thing)

if not, can I access the files somehow from my pc? (mainly mails etc). please help,

thanks

---

### Post by sneakyB on 2009-05-04
or if I would re install, do I still get all my mails etc in evolution and other files stored on the disk?

do I have to re install the same version, or can I go back to the 8.10, which seemed to be working a lot better on my machine...

thanks a lot

---

### Post by Didius Falco on 2009-05-04
Hi,

You need to give a lot more information:

In the thread title, you say it won't boot "any more". When did you start having problems?

Was it right after you tried some of the "recommended solutions"?

Were they recommended to you or did you just read them in a thread somewhere?

Do you remember what they were?

Did you still have access to the internet?

Do you have a separate Home partition?

What are the hardware specs on your pc, including the video card? If we can get you back into a graphical environment, we can start working on the other problems.

Are you wanting to try and fix 9.04 or just go back to 8.10?

Enquiring minds want to know!! :?:

---

### Post by sneakyB on 2009-05-04
Hi didius Falco,

thanks for the quick reply.

I started having the problem after installing some from the package installer, that was recommended on someone else's, similar problem. Unfortunately, I don't remember the exact name, and can't look it up as I can only work from the windows part of my pc.

unless there is a way to boot somehow, no internet on the ubuntu. (used to work before, no wireless though)

my video card, according to windows device manager is
mobile intel(r)965 express chipset family. (at least I hope this is what you're looking for) 
I'm having a dell vostro.

If I could get 9.04 work as good as 8.10, preferably 9.04, but either is ok... just want to have access to my data again, and if possible not have to use windows.

I have a separate home partition. (i did not change any setting while installing ubuntu 8.10, and left everything as it was recommended.

I hope this helps a bit more... (not very good with all this)

thanks again for the help

---

### Post by Didius Falco on 2009-05-04
If you do have a separate /Home partition, then reinstalling would be the easiest fix for it. If you have a Live CD or USB, I'd boot that first and open the Partition Manager to confirm that there is a separate /Home partition.

In any case, for any PC, but particularly for a mission-critical work PC, the three most important words I can tell you are: Backup, Backup and Backup. ;-)  

Were I you, I'd back up before reinstalling. You can backup just the Home partition (or Folder if you do not have a separate /Home partition). You can do this using the Live CD.

Unless there is some compelling reason for you to go with 9.04, I'd stick with 8.10, since you say it worked well for you, but that choice is up to you. If you do have a separate /Home partition, when you install again and it gets to the Partition Manager part, choose the **Manual (advanced)** option. Highlight the partition that Ubuntu was installed in and **Edit** the options to use it, set it as EXT3 type and set it to "/", which will make it Root. Tick the little box that says Format on the screen. Next,  highlight the /Home partition, set the options on it, but set it to /Home and do [COLOR=Red]**not**[/COLOR] tick the format box.

That way, your install will use it as /Home, but it won't overwrite your files, including your email and other settings. You will have to reinstall any programs that aren't paart of the base packages that come with Ubuntu, but when you reinstall them, they'll find their settings and use them.

If you decide you want to go the other route and fix the current install, I'll try and help out, and hopefully others will join in.

Good luck!

On Edit: rereading your post, it sounds like you used one of the default installs in Ubuntu. I'm not positive (I always do my own partitioning) but I don't think any of the defaults will make a separate /Home partition. Be sure and confirm that you do have one. If you don't, just be sure to back up the entire Home folder tree, including any hidden files. You can see them by hitting ctrl-h while in Nautilus (the file manager).

I'm not trying to be condescending, but I don't know your skill level, and I'd much rather tell you something you already know than omit something you need to know....

---

### Post by sneakyB on 2009-05-04
hi again,

thanks again for the explanation and effort.
I tried exactly as you said, but get a weird result :s

I reinstalled, being able to do everything as you suggested, with my 8.10 cd, (which I burned from an iso). during the installation I saw it importing old settings, documents etc, so seemed al fine.
however, when I try booting, I still get the 9.04 looking start up screen.  ... until it turns black, start doing some stuff, and than getting stuck with the error: 
enabling additional executable binary formats binfmt-support
FATAL: could not load /lib/modules/2.6.28-11-generic/modules.dep
update binfmts: warning: couldn't load the binfmt_misc module.

next comes: checking battery state, and that's where it gets stuck.

by doing ctr alt del, it shuts down, with the 8.10 look again... :s

from my windows, using diskinternals linux, I still can see the files that were on the linux disk though, so feels like everything is still there...

any suggestions? 
I really like ubuntu a lot, so hope I can (or you guys) figure something out!

cheers

---

### Post by Didius Falco on 2009-05-04
I'm still here...just doing a little research...will post again soon.

---

### Post by Didius Falco on 2009-05-04
You did have it format the Ubuntu Root partition?

---

### Post by sneakyB on 2009-05-04
yes, did so. perhaps I should give it another go...

---

### Post by Didius Falco on 2009-05-04
Yeah, the only really good way to downgrade is to just format and reinstall over the top of all of it, and then use your backups to recover your personal data. :( 

It wouldn't hurt. AAMOF, I'd use Gparted (the partition manager in the Live CD, not the one in the installer) and format it before you install it.

I also would NOT let it import settings. You can move all that later.

If you get the same result, You'd be better off to let it format both partitions and then use your backups to recover your emails, bookmarks, etc.

I'll stick around a while and see how it goes.

Good luck!

On Edit: What has me puzzled is that the usplash is located in the /usr/lib/usplash folder, which should definitely have been wiped by the format.  :-k

---

### Post by sneakyB on 2009-05-04
I just tried something else...

when my dell starts up, I get a few choices to boot from:
ubuntu 8.10 ... 2.6.28-11
ubuntu 8.10 ... 2.6.28-11 (recovery mode)
ubuntu 8.10 ... 2.6.27-11
same in recovery
ubuntu 2.6.27-7  <-- I ,managed to boot ubuntu from the last one. (with my windows background and another few, but minor strange things)

might it still be worth it to try the update to 9.04 from there, or will I most likely run into the same problems again?

either ways, got to get my mind on something else for an hour or so, but will hopefully find a way to get it running smooth again! 

when not having the live CD, I  best use the gparted from the installer right?

thanks again for all the help. very much appreciated!

---

### Post by Didius Falco on 2009-05-04
It might, but you run the risk of an install that is damaged in some way that might show up and bite you later.

Go and relax now. Ofttimes that is the best way to find a solution, by letting it percolate in your unconscious while you are doing something else.

Regards,

Didius

---

### Post by sneakyB on 2009-05-04
Good morning again!

did the install (9.04) from the live cd this time. working like a charm
... almost.
the wifi worked right after installing, which is the first time in my short ubuntu history :)
the only thing still not working is the compiz...

it looks installed when I open the package manager, but I can't find the settings anywhere. system/preferences/compiz is not there :s (tried reinstall etc)

I think 9.04 still has problems communicating with my graphics card.
minimizing windows is slow and ugly as well.  

any suggestions on that one?

gratias!

---

### Post by sneakyB on 2009-05-05
perhaps this helps:

bert@bert:~$ sudo lspci |more
[sudo] password for bert: 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controlle
r Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrat
ed Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Grap
hics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll
er #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll
er #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Control
ler #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller
 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (r
ev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (r
ev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (r
ev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll
er #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll
bert@bert:~$ 


thanks,

B

---

### Post by sneakyB on 2009-05-05
I figured it out with this forum [http://ubuntuforums.org/showpost.php?p=4202892&postcount=6](http://ubuntuforums.org/showpost.php?p=4202892&postcount=6)

everything working smooth now!!

thanks for all the help

---

### Post by Didius Falco on 2009-05-05
You are very welcome! Sorry I wasn't around to help with the video problem, but it's solved and that's the important part.

Regards,

Didius

P.S. Please mark this as solved. That way someone else may find it and it'll help them out too. You can mark it solved by editing your first post, hitting the **Go Advanced button**, clicking the front of the thread title and typing solved. Then save the post and you are done.

---

