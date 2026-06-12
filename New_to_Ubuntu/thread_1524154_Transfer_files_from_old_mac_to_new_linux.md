---
title: "Transfer files from old mac to new linux"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by minidoc on 2010-07-04
Hello everybody,

So I'm very interested in getting an Ubuntu laptop and was wondering what is the best way to get a TON (like 300GB+) of mp3's from an iMac on to the laptop. Is this possible?

Thanks!

---

### Post by WRDN on 2010-07-04
Wow, thats a lot of music!

The simplest way would be to copy the files to an external HDD, and then copy them over to Ubuntu.

Alternatively, get a crossover ethernet cable, connect the two machines, then you can copy files directly from one machine to another - arguably the fastest solution.

If neither of those options are available to you, then you could set up server software (e.g. Apache) on the Mac, and download the files to the Ubuntu machine, over the local network (LAN).

---

### Post by minidoc on 2010-07-04
Wow, thanks for the fast reply! Does it matter if the HDD is formatted for Mac or Linux? And the crossover ethernet cable is just the regular old ethernet cable connected to the two ethernet ports, yes?

---

### Post by WRDN on 2010-07-04
You need to format the HDD to a file system both OS' will understand. If [this]("http://developer.apple.com/mac/library/documentation/Performance/Conceptual/FileSystem/Articles/MacOSXAndFiles.html") link is accurate, OSX does not support the common Linux filesystems such as ext3. However, Linux does support OSX' file systems (HFS, HFS+).
So, you should format the HDD in OSX to HFS or HFS+, your choice.

I believe you can use a standard ethernet cable, a crossover cable is different though, and is generally recommended for direct connections between machines.

---

### Post by minidoc on 2010-07-04
Thanks, WRDN. That's a really big help!

---

