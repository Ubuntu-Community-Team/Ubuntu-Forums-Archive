---
title: "Confusion with internal hard drives"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by glock30 on 2010-04-08
[FONT=Arial]I have finally built my first machine that has no trace of windows on it, and have a question about the way that the system detects the hard drives.  When I installed Ubuntu, I installed 3 hard drives.  2 160 GB hard drives, and one 1TB hard drives.  When I did the install, they were listed as follows:

sda: 160 GB mounted as /
sdb: 1 TB drive mounted as extra space
sdc: 160 GB mounted as /home

This works fine and dandy, but there is one little problem... it may just be me being OCD, but I want to plug the drives in so that sdb is for /home, and sdc is the extra space.  Would Ubuntu figure it out automatically if I switch the cables around?  I can't see any performance gain out of this... I searched around and could not find any solid answer to my question.  I know that in [/FONT][FONT=Courier New][FONT=Arial]/etc/fstab all the drives are identified by the UUID, so I THINK that I can do this without harming anything, but I am still a little fresh with Linux and don't want to kill what I already have going.  I know that the sdX is determined by the way that everything is plugged in, but please correct me if I am wrong.  Sorry if this is a simple question, but it is beginners talk after all. :D  Thanks.[/FONT]
[/FONT]

---

### Post by srs5694 on 2010-04-08
In theory, the change should work fine; however, there's an old saying:

"If it ain't broke, don't fix it."

Your current configuration ain't broke.

---

### Post by sisco311 on 2010-04-08
> **srs5694 said:**
> In theory, the change should work fine; however, there's an old saying:

"If it ain't broke, don't fix it."

Your current configuration ain't broke.

+1

Also, device names (sdX) are assigned at boot time, so they can change between system boots.

[uhelp]community/UsingUUID[/uhelp]

---

### Post by codemaniac on 2010-04-08
>  I know that the sdX is determined by the way that everything is plugged in

you can always create custom udev rules to name your devices as per your wish...

---

### Post by oldfred on 2010-04-08
While I have to agree 100% with srs5694 and sisco311, part of the reason I enjoy linux and the forums is that it is like one giant puzzle and we are working to solve it ( or help others solve it).

I do not intentionally break things but sometimes like to experiment and that leads to major breakage. Part of the learning then is to figure out how to fix it without the easy solution of a new install.

I have two 160GB and a 640GB. The order sda etc seems to be the order physically plugged into the SATA ports. In BIOS I cannot tell my 160s apart and have in the past had to try to boot one and if it did not work boot the other. Back then I only had one set up to boot. Now all three drive will boot something.

If your fstab uses UUIDs you probably could change. If you have boot loaders in any of the other drives you probably would have to reinstall.
Have good backups, several liveCD and/or emergency boot USB keys set up and you can experiment at your own risk.

---

### Post by glock30 on 2010-04-08
WOW.  Thanks for all the great advice so quickly.  If I get adventurous I might just try it, but the consensus seems to be that it is safer not to.  It is a fresh install, so I would not be loosing much.  Once again though, thanks a lot everyone. :smile:

---

