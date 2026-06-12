---
title: "Virtualization for a nervous Nelly"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by ibexslam on 2008-12-08
I'm going to try to set up two new computers, for my colleague (Nelly) and myself.  The new machines come with that Vista thing, which we don't want at all, at least not now.  We're getting legit copies of XP, which we will need quite a bit for our legacy applications.  But we both want to have Ubuntu installed, too, because we're all about open source and we don't like corporate baloney.

The thing is, Nelly doesn't want to have to reboot to switch from one OS to another.  Doesn't bother me, but for Nelly, the fewer complicated computer thingies to deal with, the better.  Know the type?

So, it seems virtualization is the way to go.  Is it better to run windows inside of ubuntu, or the other way around?

My choices are...uh...VMware, VirtualBox...Parallels?  Any tips there?  I'm leaning toward VirtualBox, but I'm ignorant at this point.

Just to show how ignorant I am, let me pose a question:  if linux is running as a guest inside windows, then, if the windows system were to become compromised and burdened by various malwares, would that affect the linux end of things?  Or would the linux be unaffected, as it would be if it were booting totally separately?

Any suggestions regarding EZ OS-switching and nervous Nellies are much appreciated.

I.

---

### Post by ibexslam on 2008-12-08
Or maybe Wubi is the way to go.  Is a Wubi installation persistent -- does it save my settings from one session to the next?  It sounds interesting.

I.

---

### Post by Dedoimedo on 2008-12-08
Hello,

If you use a Linux host and Windows guest, the chances of malware propagation are low. Still, do not get infected. And remember that virtualization is NOT about security.

Either VMware or VirtualBox, both good choices.

Dedoimedo

---

### Post by nhasian on 2008-12-08
use the virtualbox from their website instead of the Open Source Edition in the ubuntu repositories.  You can wipe the drive and just install ubuntu and then use virtualbox to install XP or Vista or both :)  I should caution you however that you in your virtual OS you wont have access to all the bells & whistles of your 3d graphics card.  if you want to run games or the like then dual booting is your best bet.  Vista comes with its own partition shrinking tool so you can shrink the vista partition to make room for the ubuntu installation.

---

### Post by 3rdalbum on 2008-12-08
I'd say run XP as the guest OS and Ubuntu as the host OS. (the host OS is the one that's running on the hardware, the guest is the one running inside the VM).

Reasoning: If XP is the host and it gets slow and bogged down, then the guest is going to get slow as well due to XP's ancient scheduler. Linux has a good scheduler and is less likely to get bogged down with cruft, so using it as the host will ensure that enough CPU power gets to the XP guest.

---

### Post by ibexslam on 2008-12-08
> **Dedoimedo said:**
> remember that virtualization is NOT about security.

I'm definitely starting to think Wubi is the way to go.  I read...somewhere...that it's not a virtual thing, and that windows isn't happening while ubuntu is running under wubi.  Requires a reboot--right?

Let me know if I've said anything dangerous or ignorant.  Much appreciated.

ibexslam

---

### Post by bwang on 2008-12-08
Yes, Wubi requires a reboot to switch between OSes.

---

### Post by handydan918 on 2008-12-08
> **bwang said:**
> Yes, Wubi requires a reboot to switch between OSes.

And it even has it's own dedicated section here on the forums. I would recommend anything else.

---

### Post by ibexslam on 2008-12-08
> **handydan918 said:**
> I would recommend anything else.

Dan, I have to say I'm not quite sure what you mean by that.

---

### Post by handydan918 on 2008-12-08
> **ibexslam said:**
> Dan, I have to say I'm not quite sure what you mean by that.

Anything besides Wubi. It looks like a good idea IF used for the purpose of "testing" Ubu without partitioning and all that drama. In practice, it seems that people are using it as an alternative to a "real" installation, a task for which I do not believe it is adequate.

If you are going to have to tolerate a dual boot, just do a conventional dual boot. 
Because it works.
If you don't want a dual boot, virtualize. vbox rox! It is not without it's limitations, but it is a huge step forward for running multiple O/S's.

---

### Post by wolfen69 on 2008-12-09
> **handydan918 said:**
> Anything besides Wubi. It looks like a good idea IF used for the purpose of "testing" Ubu without partitioning and all that drama. In practice, it seems that people are using it as an alternative to a "real" installation, a task for which I do not believe it is adequate.

If you are going to have to tolerate a dual boot, just do a conventional dual boot. 
Because it works.
If you don't want a dual boot, virtualize. vbox rox! It is not without it's limitations, but it is a huge step forward for running multiple O/S's.

although i would not run ubuntu with wubi myself, i installed ubuntu using wubi for someone else and it ran great. if you did not know it was wubi, you would have thought it was a seperate install.

---

### Post by Sorivenul on 2008-12-09
My vote goes to running XP virtually in VirtualBox, and as stated earlier, the version from the VirtualBox website as opposed to the version available in the repositories.

---

### Post by handydan918 on 2008-12-09
> **wolfen69 said:**
> although i would not run ubuntu with wubi myself, i installed ubuntu using wubi for someone else and it ran great. if you did not know it was wubi, you would have thought it was a seperate install.
 Don't misunderstand. I am not saying Wubi never works or that it has no place in the grand scheme of things. It's just that it is often mis-applied by noobs. It is NOT as fully functional as a "real" installation in all cases, and there is a reason for the existence of partitions. 
Using a proper partitioning scheme can avoid all manner of evils down the road, and this is never likely to happen with a wubi install.

---

### Post by ibexslam on 2008-12-10
Thanks for your help, folks.

I.

---

