---
title: "So I'm currently dual booting using wubi..."
date: 2009-05-13
forum: New to Ubuntu
---

### Post by catatonic on 2009-05-13
I seemed to have gotten stuck with the 32bit version of Ubuntu when I installed using wubi. Would there be any advantages of ditching wubi and making separate partions for each vista and ubuntu? Any difference in running x64 compared to 32bit?
It took me quite a while to get ubuntu setup like I wanted too on here, due to having problems with my integrated ATI graphics and working on a limited bandwidth satellite connection (200MB/24HR).

---

### Post by skymera on 2009-05-13
You'd probably get a nice performance increase when installing on a seperate partition :)

Try it :D

---

### Post by djyoung4 on 2009-05-13
You should definately set up different partitions.  I used to run ubuntu in a virtual machine and the performance was terrible.  I got it installed on a seperate partition but I allowed it to access all of my windows files.  it runs 100x better now

---

### Post by catatonic on 2009-05-13
> **skymera said:**
> You'd probably get a nice performance increase when installing on a seperate partition :)

Try it :D

You're gonna make tomorrow night a LONG night for me then :P

---

### Post by catatonic on 2009-05-13
> **djyoung4 said:**
> You should definately set up different partitions.  I used to run ubuntu in a virtual machine and the performance was terrible.  I got it installed on a seperate partition but I allowed it to access all of my windows files.  it runs 100x better now

My performace isn't too bad, I know its not up to what Ubuntu is really capable of, but still not too bad. I'm not running it in a virtual machine, I ran wubi which installs Ubuntu as a program, but still runs separate from windows.

---

### Post by Peter09 on 2009-05-13
The main disadvantage, as I see it, is that with wubi, if windows is down the lot is down.

---

### Post by djyoung4 on 2009-05-13
what peter said is what i meant to say.  I hated how it ate my ram up and when windows crashed so did ubuntu

---

### Post by catatonic on 2009-05-13
> **Peter09 said:**
> The main disadvantage, as I see it, is that with wubi, if windows is down the lot is down.

Good point, I've been lucky and vista hasn't had a problem yet... (Knock on wood.)

---

### Post by presence1960 on 2009-05-13
I don't like the idea of wubi. Yeah, yeah I know it gives some the opportunity to "try" Ubuntu without partitioning. Which by the way is not that difficult if one does some reading & studying prior to attempting it. The reason I don't like it is the host (in this case Windows) should be more stable than the guest (Ubuntu). Now isn't that a joke. Save yourself some headaches in the long run and set Ubuntu up on it's own partition. That way Ubuntu is not dependent on Windows. I believe that is the whole reason for trying Ubuntu- because Windows is not satisfactory in one way or another. Why make Ubuntu dependent on the thing that is not up to par?

P.S. Of course this is strictly my opinion about wubi.

---

### Post by thechanklybore on 2009-05-13
There is no reliance on any "Host" system in Wubi. It simply uses a file on an NTFS filesystem as a virtual disk-image which gets mounted as root.

In my testing I get only a very small increase in disk speed from having full EXT3 filesystem as opposed to NTFS-mounted EXT3.

So - to answer the original post, you can choose to install 64-Bit Ubuntu in 32-Bit Wubi simply by selecting it from the drop-down list.

On the other hand, partitioning is neater and you don't have to worry about "dirty" bit being set on the NTFS disk (requires you to force mount) - but that's only an issue if you use Windows ;-)

So, to reiterate, Wubi is NOT a virtual machine, it is NOT (apart from the installer) a Windows-based App, it is just a different boot method.

Also - the "if Windows is down Ubuntu is down" is just plain wrong! You don't need to be able to boot into Windows for Ubuntu to continue operating. As mentioned above, the worst thing that can happen is that you force a mount on a "dirty" NTFS filesystem.

---

### Post by catatonic on 2009-05-13
I guess I'll leave wubi alone for a bit. I really want to get a desktop since my laptop is my only functional computer at the moment. Once that happens I'll probably go Ubuntu only on this machine.

---

### Post by catatonic on 2009-05-16
Changed my mind, stayed up all night getting Ubuntu 9.04 x64. Now that I have the .iso and I'm about ready to burn and load it, I've run into a snag. Vista will only let me get 1GB of space to shrink my HDD. I've searched the web and did all the recommended things to clear up space with no avail. Can anybody chime in and give me a hint on how to fix this problem?

---

