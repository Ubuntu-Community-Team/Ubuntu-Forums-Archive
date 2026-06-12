---
title: "Grub wont boot"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by capnthommo on 2010-01-11
hi folks
yesterday, booted fine.  today, toshiba initial screen then get 
> GRUB loading stage 1.5
for about 0.5second then
>  [ Minimal BASH-like line editing is supported.  For the first word. TAB lists possible command completions/ Anywhere else TAB lists the possible completions of a device/filename. ] 

grub>
i think i remember a kernel update yesterday (could be wrong) but it booted okay after that a couple of times, i am sure.
has anybody got a suggestion?  i have tried googling and looked at the ubuntu pages, but nothinb seems to suggest.
any help appreciated.
thanks v much
capnthommo

---

### Post by sxmaxchine on 2010-01-11
i dont know to much about the grub but this program should be able to fix the grub [http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/") hope this helps

---

### Post by capnthommo on 2010-01-11
hi sxmaxchine and thanks.
not having a lot of luck with the link you posted because the machine i'm accessing web on is an old windows pc and has no disk burner.
i have managed to get on my real machine using my old 8.10 live disk but that doesn't get me very far.  all i can think is that i have somehow lost the kernel but i can't be sure.  i have certainly done nothing and just don't understand what's gone wrong.
any further help anyone can offer is gratefully received.
oh, and i shall certainly download the brub assist s'ware when i get this solved.
thanks again
capnthommo

---

### Post by audiomick on 2010-01-11
Hi Thommo,
Have a look here.
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
If you can boot into a live cd, you should be able to follow the instructions there to find out what state your machine is in. If you can't make any sense out of the output, post it back here.

It sounds like you are using an older Ubuntu, or an updated one. If so, it will be using grub legacy (version number 0.96 or something, anyway less than 1.0). If it was a fresh install of 9.10, it will be Grub2 (version number 1.97, I think, in any case greater than 1.0)

There is documentation about grub legacy here
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

and grub2 here
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

I've got some things to do right now, but I'll look back in a few hours to see how you are going.

---

### Post by capnthommo on 2010-01-11
hi audiomick
thanks.  i was previously using 9.10, but that is where the problem seems to lie.  i am just unable to access my laptop except with my 8.10 live disk as i have (foolishly) just upgraded the last two times so that is the most up to date disk i have.  of course this means that all i can see is what is on the disk, not what is on my hard drive (i hope!).  this leaves me at a wall.  i don't want to install 8.10 again as i feel i will lose everything (mostly data) that i have at present.  i know, i should have backed up to my ext hd drive, and i usually do but i have a couple of files that i haven't done so with and...
anyway, i could start at 8.10 and go through the upgrade processes to get back where i was but i think that would be counter productive.  and even with the help pages i am still very much in the dark and everything seems to rely on having a karmik live disk which i don't have as i upgraded.
as to the kernel, i believe i was using 2.6.31-18 afaik, but could be wrong.
sorry to be so negative, but i am really lost here, and worst of all, under time pressure too.
thanks again
cheers
capnthommo
p.s.  obviously i can't download a karmic disk as i need to keep the 8.10 disk in the drive but would it help if i used the 8.10 to upgrade the system to 9.10 ie would it lose my data files?

---

### Post by audiomick on 2010-01-11
Hallo again.
You shouldn't need to re-install your Ubuntu. Maybe you'll need to re-install grub. You will have legacy grub, if you have only updated and not done a fresh install.

I assume you can access the internet when you are booted into the 8.10 live cd. You should be able to.

Go to the boot info script link
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
follow the instructions there, and post the RESULTS.TXT here.

---

### Post by capnthommo on 2010-01-11
hi audiomick
firstly, thanks for the reply.  however, i have now re-installed 8.10 and gone through the upgrade processes to get back to karmic.  i can now boot and operate as normal, though this has left me with the original / and /nigel partitions with, fortunately, all the system apparently intact.  so i shall now look into amalgamating the 2 so as to get back to where i was.  i will think about this one before acting because maybe i will decide to just run with the new install (having made sure i have a live-disk and keep more regular back-ups of course), because quite frankly the set up was beginning to get a little cluttered anyway.  i just want to make sure i don't chuck the baby out with the bathwater.
i guess the re-install must have put grub back along with everything else.
thanks for the help, i would have stuck with this one a bit longer but with the annual accounts needing to be submitted pretty soon i couldn't afford to hang around all that long.
fortunately everything is still there so no loss, just wonder why it happened as i don't mess around with things i don't understand (honest, i don't)
cheers again

---

### Post by audiomick on 2010-01-11
Hallo.
Glad you got going again.

> so i shall now look into amalgamating the 2 so as to get back to where i was. i will think about this one before acting because maybe i will decide to just run with the new install
I would suggest leaving things alone, I you can, until 10.04 comes out. If your system is satisfactory at the moment, that will give you time to clean out the dross, inform yourself, get nicely prepared, and do a fresh install.
9.10 already has two major changes, i.e. that the boot loader is now Grub2, and that the default file system is now ext4. I know that the change to Grub2 doesn't take effect through an update, only through a fresh install, and I am pretty sure that this is the case for the file system as well.

9.10 seems to have (had) a few birthing problems, but 10.04 should be pretty solid, I have heard (read).

> i guess the re-install must have put grub back along with everything else.yes, it will have. For your info, it is also possible to just re-install grub.

> but with the annual accounts needing to be submitted pretty soonyou too, eh? Been putting that off for weeks...;)

---

