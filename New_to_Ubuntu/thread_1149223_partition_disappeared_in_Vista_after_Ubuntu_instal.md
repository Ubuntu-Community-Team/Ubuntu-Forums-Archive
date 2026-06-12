---
title: "partition disappeared in Vista after Ubuntu install"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by robertron76 on 2009-05-05
I just installed Ubuntu on my laptop.

Details :

laptop with 2 simple, basic, primary partition
1 --vista -- 120GB -- C label
2 --reserved for ubuntu -- 40GB -- F label

Installed ubuntu using liveCD, selected manual partition, selected the one with 40GB.I remember I gave "ext2" as file system.Is this ok?

everything works, I get booting options to start, able to start ubuntu or vista Independently.

But, in Vista - Windows Explorer, I'm no longer be able to see the F label with 40GB.It shows only C:\ Drive

Under disk management of Vista, I see the 40GB partition with 100% free space. I get an option of "Delete Volume" when I rt-click on this volume.

Is this normal or expected?

If I need to uninstall Ubuntu and recover this F:\ partition for data, how would I do that?

Is this possible?

---

### Post by lavinog on 2009-05-05
Its normal
windows doesn't know how to handle ext type file systems
there is a program to let you access it...ext2ifs: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by tommynz1975 on 2009-05-05
yes its normal...  windows can not nativly read linux disk systems or was that file :)

you will need to install a file to allow windows to read the linux drive,  some one else will post that,  I am guessing before I finish this message, you will have the required information.


[SIZE=6]Welcome to Ubuntu[/SIZE]

---

