---
title: "Installing a .iso"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by MilSpec109 on 2009-03-02
hey all. im pretty new to this ubuntu thing and in all fairness, im not very good with it. i have NO skill with computers and i really never got a solid footing on this "linux" thing. but thats old news...my problem is ive got this application i wanted to install that is in the form of a .iso file. on windows i could install it by using something like DAEMON TOOLS or Alcohol 120 where it would auto run but i have no idea how to do so with ubuntu :confused: any help would be greatly appreciated!

---

### Post by avtolle on 2009-03-02
What application are you trying to install, i.e., the name of the app?

---

### Post by Panzor on 2009-03-02
If you're trying to mount the .iso image (which is one of DAEMON TOOLS's prime uses) then do this:

```
$sudo mkdir /mnt/cdimage/
$sudo mount -o loop /path/to/.iso /mnt/cdimage
```
That will mount the .iso to the cdimage directory you made in the first command. Remember, replace "/path/to/.iso" with the real value for that.

---

### Post by rustutzman on 2009-03-02
Gmount-iso can help with a GUI to help with the mounting.

Russ

---

### Post by RichardLinx on 2009-03-02
You might be able to mount the .iso but if it's a Windows app you might not be able to run  it, depending on what it is.

---

### Post by Cybie257 on 2009-03-02
The easiest way to mount an ISO in Ubuntu is to right click the .iso file, select Open With->Open With "Archive Mounter".

not much simpler than that. Have been able to do that with 8.10 and up to Alpha 5 Jaunty. 

-Cybie

---

### Post by MilSpec109 on 2009-03-02
it's supposed to be linux compatible. i can mount it using Gmount but thats about all i can do. it says theres a virtual disc there but it doesnt auto run

---

### Post by sgosnell on 2009-03-02
Why not just burn the .iso to a CD and run it from the CD drive?

---

### Post by sandyd on 2009-03-02
> **MilSpec109 said:**
> it's supposed to be linux compatible. i can mount it using Gmount but thats about all i can do. it says theres a virtual disc there but it doesnt auto run
linux, buddy does not have autorun

you have to go to the directory you mounted it to manually run it

---

### Post by Vantrax on 2009-03-02
If you followed the command earlier head to /mnt/cdimage and you will find the contents of your cd with something that looks like a setup.sh.


Good luck

---

### Post by MilSpec109 on 2009-03-03
okay so i got the iso mounted, i can see the virtual disc "thing". however, nothing happens... (excuse the coarse language, im not technical at all) i can view the files inside the iso. there's one that says AutoRun.inf and one that says Setup.exe

---

### Post by DBrocks on 2009-03-03
If it's an exe, you're trying to install a windows program. Try to use it with Wine.

---

### Post by MilSpec109 on 2009-03-04
ahh. thank you

---

### Post by mlentink on 2009-03-04
Please do not. 
Wine will run some Windows programs, but certainly not all of them.

Maybe we could help you better if you just told us what it was you wanted to achieve, i.e. what it was you wanted to run this windows program for

---

### Post by DBrocks on 2009-03-05
> **mlentink said:**
> Please do not. 
Wine will run some Windows programs, but certainly not all of them.
 
Maybe we could help you better if you just told us what it was you wanted to achieve, i.e. what it was you wanted to run this windows program for
 Sorry for jumping the gun. And I agree with mlentink, it's best if you tell us what the program is, and what it does. That way, we can see if its compatible w/ wine, and if not, we could find a linux alternitive. There's a linux alternative for most windows programs.

---

### Post by MilSpec109 on 2009-03-05
its a game called Postal 2. again, not too great with computers so i googled it and it said it was linux compatible. i got this VMware thing and my brother says theoretically it SHOULD work. sorry for the confusion, i must've missed what mlentink said.

---

### Post by Mud.Knee.Havoc on 2009-03-05
> **MilSpec109 said:**
> its a game called Postal 2. again, not too great with computers so i googled it and it said it was linux compatible. i got this VMware thing and my brother says theoretically it SHOULD work. sorry for the confusion, i must've missed what mlentink said.

I think that there's a linux version and a separate windows version.  Even the windows version runs under linux, though, using wine (according to winehq, it's rated "platinum", so it should run quite well).

---

