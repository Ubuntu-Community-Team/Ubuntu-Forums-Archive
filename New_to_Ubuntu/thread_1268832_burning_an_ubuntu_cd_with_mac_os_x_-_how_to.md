---
title: "burning an ubuntu cd with mac os x - how to?"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by mjp29 on 2009-09-17
I want to install Ubuntu on a Pentium 4 system.  I want to download it with a Mac running os X and burn a bootable disk to install on the Pentium 4 system.

Can this be done?

Also, how does one tell if they have 32 bit or 64 bit Pentium 4 in Windows XP

---

### Post by NightwishFan on 2009-09-17
I would use 32-bit Ubuntu, it is still fast, and will definitely work.

Here is a link how to burn in Mac OS X:

[http://www.psychocats.net/ubuntu/maciso](http://www.psychocats.net/ubuntu/maciso)

---

### Post by cariboo on 2009-09-17
nevermind, I misread.

---

### Post by mprince on 2009-09-17
I find it easy to use this command using the mac terminal:

```
hdiutil burn ~/Desktop/Ubuntu-9.04.iso -speed 1 -noverifyburn -noeject
```

You just edit the path and name of the iso. Remove the -noverifyburn option if you want it to verify.

---

### Post by mjp29 on 2009-09-17
ok

just to be clear, I can download ubuntu for the PC intel onto the mac and burn the cd using that command line (in terminal) and it will work to boot the pc intel and install it to the pc

note:  I am not installing the ubuntu on the mac (just using the mac as a tool to get and burn the disk for the pc)

---

### Post by mprince on 2009-09-19
Yep. That's how I do it. My PC doesn't have a DVD burner, so I just download the .iso on my roommates mac and then burn it using the mac's DVD burner... Then use the disk to install on the PC.

---

### Post by mjp29 on 2009-09-19
Did it and it worked great.

Thanks!

---

