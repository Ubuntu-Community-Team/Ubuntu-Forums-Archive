---
title: "Issues connecting fresh 19.10 install to a Windows network - permission denied"
date: 2020-03-28
forum: Networking &amp; Wireless
---

### Post by Sour Mash on 2020-03-28
Hi, I'm back after several years away - as most of the world is on lock down, it felt like a good time to get reacquainted with Ubuntu.

So, I've resurrected the old machine, updated it with a fresh install of Ubuntu 19.10 with a wired connection to my router and with my Windows machine also wired to the same router.
I did all this to salvage some media files off an old NAS drive - I've done that by direct connection of the drive to the motherboard, so v happy. 
However, the next stage was to connect the Ubuntu machine to the Widows network and share those salvaged files - I've come unstuck.

At the moment I can connect to the Windows machine, I can see disks, directories and even play music from the Windows machine on the Ubuntu machine.
I can't create a folder or delete a file on the Windows machine from the Ubuntu machine - "Permission Denied".
I cannot do anything the other way - I can't see the Ubuntu machine on the Windows machine at all.

I was in this same spot 5 years ago but it looks like user bab1 who was so helpful last time has ceased posting on here :-( they were v helpful.

So, in summary, I'm after a guru who could help me chase out the gremlins please?

Is there a step by step idiots guide anyone can point me at please?

Thanks

---

### Post by SeijiSensei on 2020-03-28
Not being able to create files and directories on the Windows share must be a Windows permission issue.  Are you connecting with your Windows username and password?  Do you have rights to create/delete files on those directories if you're on the Windows machine itself?  What if you're connected as a guest?

---

### Post by Sour Mash on 2020-03-30
Thanks for the reply, you're right - ish, I thought "it's gotta be a Windows permission thing" so I went and changed that and found I had red only permission, so I fixed that BUT why couldn't I see the Ubuntu machine from Windows?
I rebooted everything and now, I can See my Ubuntu machine in windows - sort of! In Network in file explorer, there is my Ubuntu machine, visible BUT when I try and click on it I get an error that the network path was not found.
I'm a bit stuck.

---

### Post by Sour Mash on 2020-03-30
Having fixed the permission in Windows I thought I'd try and do the same in Ubuntu
I figured that having corrected sharing permission on Windows and tested it on Ubuntu - I could create and delete files on the Windows folder, I would try the same logic the other way around.
Now I am thrashing around here but I thought my logic was good - I went to the the Ubuntu Home folder and tried to set the permissions to include my Windows account name as a user - I tried but am sure I didn't actually change anything.
I rebooted everything and now just get a purple screen on the Ubuntu machine (and it's disappeared off the Network view in Windows entirely). The purple screen doesn't respond to any mouse or keyboard input other than ctrl alt del and it reboots back there.

I'm was going to create a new thread for this new problem but the the Ubuntu machine came to life again! Maybe I was just being impatient but it did sit there for 5 mins plus.

Oh well, let's not dwell on that one too long. Back to the network issue!

---

### Post by Sour Mash on 2020-04-01
Hmm, I'm really not doing very well here, lost the ability to see my Windows machine :-( Windows does find my Ubuntu machine but doesn't let me do anything with it :-( I've set all the permissions I can find to allow this but nothing seems to work - other than going backwards!

---

