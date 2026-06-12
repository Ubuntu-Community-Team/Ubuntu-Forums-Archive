---
title: "How do I install drivers for the Nvidia gt220 please?"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by brawd on 2010-05-30
Hi All,

I've been on this for two days. I've searched the forums and web but I find the notes too deep.

The system is AMD Athlonx2 64bit in an Asrock AliveNF6P mobo.
The Nvidia onboard graphics installed OK and also driver 96 works for 3D effects.

Then I installed the graphics card and it shows up in Terminal, after using lspci, as 'nVidia Corporation GT216 [GeForce GT 220] (rev a2)'.

It didn't work with the nvidia 96 driver I had installed for the mobo graphics, nor did it work with the other two hardware drivers listed.

When I enable pci express graphics in the bios and plug the monitor into the gt220 I get low graphics. I downloaded a driver from nVidia site and that now is in my /home/downloads folder. It's named NVIDIA-Linux-x86_x64-195.36.24-pkg2.run

How would I get that to run please?

regards,

brawd.

---

### Post by TeoBigusGeekus on 2010-05-30
[https://help.ubuntu.com/community/InstallingRunPackage]("https://help.ubuntu.com/community/InstallingRunPackage")
and
[http://ubuntuforums.org/showthread.php?t=239797]("http://ubuntuforums.org/showthread.php?t=239797")

---

### Post by brawd on 2010-05-30
Thanks Teo,
It worked up to a point. It apparently unpacked the file and then told me it had to be run as root. This is what it comes back with:

ERROR: nvidia-installer must be run as root

 The only way I know how to be root is using Terminal. Well I made myself root in Terminal and typed in the name of the file it always comes back with 'command not found.

The name of the file is 'NVIDIA-Linux-x86_64-195.36.24-pkg2.run' without the apostrophes. I think the file name might be screwing up that approach.

Any ideas how to make myself root at the folder please?

regards,

brawd

---

### Post by TeoBigusGeekus on 2010-05-30
try
```
sudo ./NVIDIA-Linux-x86_64-195.36.24-pkg2.run
```

---

### Post by brawd on 2010-05-30
That didn't quite work but it gave me a big clue. That and the link in your previous allowed me to run the file by first being root, then using chown +x and then ./filename.

But then the installation stopped and said I'm using an x server, ( which I know nothing about - nothing new there then) and I must exit it!!

Aarrgghh.

I bet if anyone can tell me how to exit my -until now unheard of - xserver I bet I find myself in sudo hell.

However needs must. Anyone with any ideas on how to exit an xserver?

regards,

brawd.

---

### Post by TeoBigusGeekus on 2010-05-30
Boot up and choose recovery mode from grub... You should enter the shell.
[xserver]("http://en.wikipedia.org/wiki/X_Window_System")

---

### Post by brawd on 2010-05-30
Thank you Teo. It works. My picture on my screen is soo sharp now. 
Thank you again.

And as a former design engineer myself I hope that Autocad is configured in Linux.

my best wishes,

brawd.

---

