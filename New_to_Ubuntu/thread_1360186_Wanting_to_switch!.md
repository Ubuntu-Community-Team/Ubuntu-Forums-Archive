---
title: "Wanting to switch!"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by UnknownFear on 2009-12-20
I currently dual-boot Vista and Ubuntu 9.10. Now, I got thinking, I don't normally game on my PC anymore, and I found out there are a bunch of games for Linux already, such as Duke Nukem 3D. Now, here is what I thought about doing. I was thinking of doing a fresh install of Ubuntu 9.10. Once that is done, I was going to uninstall all my games and programs I don't need on Vista, but keep IM, all my music and stuff on it so I can access it on Ubuntu without wasting space on Ubuntu by copying it all on it. Does this sound like a good thing to do?

---

### Post by Merk42 on 2009-12-20
If you say fresh install are you saying you won't use Vista anymore? 
Or are you going to reinstall 9.10 but still dual boot?

---

### Post by UnknownFear on 2009-12-20
> **Merk42 said:**
> If you say fresh install are you saying you won't use Vista anymore? 
Or are you going to reinstall 9.10 but still dual boot?

Fresh install meaning I would uninstall and reinstall Ubuntu 9.10, and only use Vista if I really need it.

---

### Post by Merk42 on 2009-12-20
What, if anything, do you use Vista for now?

I think you can do what you want, but it may run into some issues like where programs look in ~/Music for music and if you want to have the same chatlogs across both OSs.

Those are solvable with stuff like symlinks, but just saying maybe those are issues you hadn't thought of.

---

### Post by UnknownFear on 2009-12-20
> **Merk42 said:**
> What, if anything, do you use Vista for now?

I think you can do what you want, but it may run into some issues like where programs look in ~/Music for music and if you want to have the same chatlogs across both OSs.

Well, I downloaded a few songs/videos in Ubuntu and I put them in host/Users/<name>/Music & Videos and I could access them in Windows just fine.

---

### Post by Merk42 on 2009-12-20
> **UnknownFear said:**
> Well, I downloaded a few songs/videos in Ubuntu and I put them in host/Users/<name>/Music & Videos and I could access them in Windows just fine.

Yeah I was talking about if things scan ~/Music that's all.
Like Rhythmbox or Banshee might look in ~/Music for your songs, but they're really in host/Users/<name>/Music & Videos on the Vista partition.

---

### Post by UnknownFear on 2009-12-20
> **Merk42 said:**
> Yeah I was talking about if things scan ~/Music that's all.
Like Rhythmbox or Banshee might look in ~/Music for your songs, but they're really in host/Users/<name>/Music & Videos on the Vista partition.

Oh no, I know how to change the scan to go to the folder with all the music, etc. in it. Also, I am installing via Wubi with the maximum space being 30 GB. I can change this to a higher number with gParted and it shouldn't mess up anything, right?

---

### Post by Merk42 on 2009-12-20
> **UnknownFear said:**
> Oh no, I know how to change the scan to go to the folder with all the music, etc. in it. Also, I am installing via Wubi with the maximum space being 30 GB. I can change this to a higher number with gParted and it shouldn't mess up anything, right?

I wouldn't install through WUBI if possible.
It doesn't perform as well as a regular partition and if you ever want to get rid of Vista you'd end up getting rid of Ubuntu too.


Again, I ask, what are you still using Vista for?

---

### Post by UnknownFear on 2009-12-20
I'm still using Vista mainly for a few games. I also will keep Vista for college use as I am going for Computer Programming.

EDIT: I don't have any DVDs. Can I still burn it to a CD+R and install?

---

### Post by Merk42 on 2009-12-20
Oh, games, I was going to suggest a Virtual Machine for Vista, but I guess that won't do.

Yes you can use a CD or even a USB drive to install Ubuntu

---

### Post by UnknownFear on 2009-12-20
OK, I found a DVD and I am downloading the .iso for Ubuntu 9.10. When I install it, I will make it so Ubuntu has most of the space, but I will have Vista keep at least 50 GB just to be safe.

---

### Post by Merk42 on 2009-12-20
> **UnknownFear said:**
> OK, I found a DVD and I am downloading the .iso for Ubuntu 9.10. When I install it, I will make it so Ubuntu has most of the space, but I will have Vista keep at least 50 GB just to be safe.

Just make sure you don't overwrite Vista.
You may want to back up important files just in case.

If you can't shrink your Vista partition, then just go with WUBI

---

### Post by Cypher1101 on 2009-12-20
> **UnknownFear said:**
> I'm still using Vista mainly for a few games. I also will keep Vista for college use as I am going for Computer Programming.

EDIT: I don't have any DVDs. Can I still burn it to a CD+R and install?

Funny, I always found being a windows user a disadvantage while I was getting my degree in programming.

---

### Post by mybodymyself on 2009-12-20
[FONT=Trebuchet MS]Good for you.  Basically, decided just totally uninstall Microsoft Windows Vista since I hardly used the other features.  Besides Internet and Email.  [/FONT]Installed Ubuntu.  Anyway, I requested a free cd from Ubuntu which was approved and got it a few days ago.

Think this is it.

---

### Post by Yvan300 on 2009-12-20
Don't use gparted. Use vista's built in partitioner to shrink the partitions and don't forget to defrag before you start the process.

---

### Post by audiomick on 2009-12-20
> **Yvan300 said:**
> Don't use gparted. Use vista's built in partitioner to shrink the partitions and don't forget to defrag before you start the process.

I have often read that if the windows install is a bit older, it pays to defrag a couple of times.

Also, and important, start your windows a couple of times after resizing the partition, and let it do any file system checking it feels it needs to do before you do the Ubuntu install.

---

### Post by UnknownFear on 2009-12-21
> **mybodymyself said:**
> [FONT=Trebuchet MS]Good for you.  Basically, decided just totally uninstall Microsoft Windows Vista since I hardly used the other features.  Besides Internet and Email.  [/FONT]Installed Ubuntu.  Anyway, I requested a free cd from Ubuntu which was approved and got it a few days ago.

Think this is it.

Awesome!!!

Also, I decided to just get rid of Windows and do a full, complete install of Ubuntu 9.10. No more Windows for me! Now, when I get to college, however, I have a feeling I'll need to install Windows just for the program I am going into (Computer Programmer), but the awesome thing is, I read that I will be on Windows, IBM, and Linux throughout my program, so that's pretty cool! :D

---

