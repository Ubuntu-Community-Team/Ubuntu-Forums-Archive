---
title: "Back up utilities"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by Gregz on 2009-08-12
I was going through some post about back-up utilities and found partimage was highly talked about. So I did:

 "sudo apt-get install partimage" 

It installed but where did it go cannot find it or access it. 

I want to back up the whole hard drive to DVD will this work??


                            Thanks 

                             Greg

---

### Post by zeroseven0183 on 2009-08-12
Here's the instruction to run PartImage: [http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage). It says there that there are two ways to use it:

> There are two ways to use Partition Image:
1. **The command line** You must type a command. For example: partimage -od -f1 -z1 save /dev/hda12 /mnt/backup/hda12.partimg.gz
2. **The GUI (Graphical User Interface)** This is an easy way: you just have to fill in the boxes in the GUI window


  You can obtain the list of all commands, by typing **partimage --help**, so they won't be explained here. 


Hope that helps.

---

### Post by Gregz on 2009-08-12
Thank you  this thread is resolved

---

