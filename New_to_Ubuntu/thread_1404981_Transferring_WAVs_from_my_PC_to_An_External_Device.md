---
title: "Transferring WAVs from my PC to An External Device"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by nosleep333 on 2010-02-12
[SIZE=3]**Hello Ubuntu Community. I am new to the Ubuntu OS as of tonight after having been a windows user all of my life and I have to say that I'm pretty impressed thus far. The overall functionality of my machine is now much more improved in many ways but I'm just having some minor trouble when attempting to do certain things. This brings me to my issue. I have a Roland MV-8000 that I run into my PC via USB. It's a sequencer/sampler with it's own internal hard drive designed to hold your sound libraries. I also have an external hard drive also run into the PC via USB. When attempting to drag a series of samples on to the MV-8000 hard drive from my external hard drive I receive an error message stating that the destination is read-only. I'm sure there's a way to simply copy and paste files from one drive to the other but for the life of me I can't figure it out. It'd be greatly appreciated if someone could explain a lil bit to me. I have a paying audio gig and am worried that I now won't have the user ability I need to get things done. This is moving so smoothly thus far that I'd really like to rely solely on this OS rather than splitting the drive between windows and Ubuntu. I do really like the way this OS looks and the simplicity of it all. Please help!!!**[/SIZE]

---

### Post by Eredeath on 2010-02-14
Find the path to the drive and change the permissions on it. 
To give full read/write permissions to all users use: ```
sudo chmod 777 'path to drive'
```

---

