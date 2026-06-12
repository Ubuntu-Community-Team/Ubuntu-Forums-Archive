---
title: "Could I Triple Share a /mount/data/ Partiton?"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by mikodo on 2011-04-28
HI everyone,

I not asking how ... nor am I going to try to do this now ... but I am asking ... will I be able to Triple Share a /mount/data/ Partition between Xubuntu, Arch Linux and Crunchbang?

I have Ubuntu Lucid as my only OS now, but will be going to Xubuntu with the Xfce desktop, probably at Xubuntu 12.04, when Gnome2 is dead. [I]

I want to triple-boot with a common /mount/data partition with:

Xubuntu

Arch Linux

Crunchbang

Use the Xfce desktop with each.

I want to use Arch Linux and Crunchbang to experiment with and learn the CLI with bash/dash and the linux filesystems and not worry when I break them, because I would still have my smooth running 'buntu, to use as my production distro.

[/I]*Am I dreaming in Technicolor; Or will I be able to set this up?*
[I]
Thanks and goodnite.

:)



  
[/I]

---

### Post by jtarin on 2011-04-28
As long as the filesystem is compatible with all three. I can't see any reason why not......I'm I missing something here???

---

### Post by seenthelite on 2011-04-28
Yes, that is the best way to set up a multi boot system.

---

### Post by coffeecat on 2011-04-28
Basically, yes. Create one data partition and create appropriate mount lines in the /etc/fstab files of Xubuntu, Arch and Crunchbang. Each distro will be able to see and access the file.[B]

BIG HOWEVER[/B]. If you create a data partition with a Linux filesystem, you may run into permissions problems. All the *buntu family set up the first user with a UID of 1000. I can't remember what Arch does and I've never used Crunchbang. Some distros (such as Fedora) set up the first user with a UID of 500, so if a file is saved with ownership of UID=500, there may be a permission issue when you try to access it from the distro where your account has a UID of 1000.

Fairly easily worked around if you know how to set up special groups or do some judicious chmodding, but it can be a nuisance.

The other way would be to have a NTFS filesystem on the shared partition. Since NTFS doesn't support Linux permissions, you won't have the problem. But don't do this if you don't have Windows. You need Windows' chkdsk if you ever suffer filesystem corruption in a NTFS partition.

---

### Post by mikodo on 2011-04-28
> **jtarin said:**
>  I can't see any reason why not......I'm I missing something here???

Maybe, that this the Absolute Beginner Talk section and i am a Noob! 

:razz:

---

### Post by mikodo on 2011-04-28
> **seenthelite said:**
> Yes, that is the best way to set up a multi boot system.

Thanks.

:P

---

### Post by mikodo on 2011-04-28
> **coffeecat said:**
> Basically, yes. Create one data partition and create appropriate mount lines in the /etc/fstab files of Xubuntu, Arch and Crunchbang. Each distro will be able to see and access the file.[B]

BIG HOWEVER[/B]. If you create a data partition with a Linux filesystem, you may run into permissions problems. All the *buntu family set up the first user with a UID of 1000. I can't remember what Arch does and I've never used Crunchbang. Some distros (such as Fedora) set up the first user with a UID of 500, so if a file is saved with ownership of UID=500, there may be a permission issue when you try to access it from the distro where your account has a UID of 1000.

Fairly easily worked around if you know how to set up special groups or do some judicious chmodding, but it can be a nuisance.

The other way would be to have a NTFS filesystem on the shared partition. Since NTFS doesn't support Linux permissions, you won't have the problem. But don't do this if you don't have Windows. You need Windows' chkdsk if you ever suffer filesystem corruption in a NTFS partition.

Thanks for the information and the the warning about the Fedora's first users UID being 500; I have read about that before; but luckily, I am not intending to use Fedora. For a prepackaged system, I'm sticking with Ubuntu. I don't use Windows, so no problem there. I'll read about the first users UID's of Arch Linux and Crunchbang and make sure that the first user has similar UID's, so the perms are not a problem. I have also read that one should use a different group and username with each distro. I am not sure why? I'll read about that too!

Thanks!

:P

---

### Post by coffeecat on 2011-04-28
> **mikodo said:**
> I'll read about the first users UID's of Arch Linux and Crunchbang and make sure that the first user has similar UID's, so the perms are not a problem.

If you open a terminal and run "id" you get listed your UID and all the groups you belong to together with the GIDs for each group. That *should* work in any distro because id is a standard gnu utility.

> **mikodo said:**
>  I have also read that one should use a different group and username with each distro. I am not sure why? I'll read about that too!

I'm not sure either. Or there could be some confusion there. I do remember seeing some advice that if you share a home partition - as distinct from a data partition - then you need to set up different UID accounts in the various distros if they use different versions of gnome or whatever. This to avoid conflicting configuration files. I'm not sure that's entirely necessary, but that is what you may have come across.

However, setting different usernames may not work. Let's take the case of three distros each setting a UID of 1000 for the first created user. You set up account Andy in distro A, Bill in distro B and Charlie in distro C. Three different usernames, but they'll each have the same UID. In consequence distro B's Bill account will see distro's C Charlie files as belonging to itself.

Something to think about. :) It's the UID (and GID) that matters.

---

### Post by mikodo on 2011-04-28
Thanks Coffeecat!

I was over here and there reading about this and that!

Thanks for the advice again.

Mike

---

### Post by ~Plue on 2011-04-28
just a litte something to add: in the fedora installer, theres an option to change the uid to whatever you want and useradd on arch would start from a a uid of 1000

---

### Post by mikodo on 2011-04-28
> **~Plue said:**
> just a litte something to add: in the fedora installer, theres an option to change the uid to whatever you want and useradd on arch would start from a a uid of 1000

Hey, very good to know ...

Down the road, I might want to see what all the fuss is about, with Red Hat and Fedora, and their excellent reputation, as well packaged systems!


EDIT: Thanks also, for the information about the user add (group add too?) Arch Linux starting with UID/GID = 1000.

Thank you.

:P

---

### Post by oldfred on 2011-04-28
Coffeecat may have covered it all, but just to add my 2 cents.

I posted this in another thread which I did not save the link.

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition.

Shared /data -see post #4 oldfred
[http://ubuntuforums.org/showthread.p...hlight=%2Fdata](http://ubuntuforums.org/showthread.p...hlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

---

### Post by mikodo on 2011-04-29
Thanks oldfred, 

How do you find all these great threads that you continually present to us?

You are so spot on, on what I am going to need to know when I start setting up the separate /mount/data/ partition and the sharing within the distros ... etc.

I really really appreciate you spending your time and effort helping me out!!!

I love ya ...

If you are worrying about that last statement don't ... 

I'm on my second wife ...

:P

---

