---
title: "How to create a fast computer"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by cablefun on 2007-07-13
I want to find a way of connecting 2 or more computers together to create a single fast computer that can run normal apps under ubuntu. so for instance i can join 3 1ghz computers together to give me a computer that is as fast as say one 2ghz computer? :confused:

---

### Post by yabbadabbadont on 2007-07-13
I think you have a mistaken impression of what a linux cluster is.  Have a read through this: [http://en.wikipedia.org/wiki/Beowulf_cluster](http://en.wikipedia.org/wiki/Beowulf_cluster)

---

### Post by tutomlin on 2007-08-10
you might see some benefit from a load sharing cluster system like Kerrighed.  Basically these systems will distribute processes amongst CPU's so that you can run more programs at the same time.  Sadly all your programs will still be limited by the speed of the CPU's they run on.

Cheers

Tucker

---

### Post by tgalati4 on 2007-08-11
One way you can better performance with 3 machines is the following:

Set up the slowest machine as a server.  Put in a large drive and use it to store your music, videos, photos and have it networked to the other machines.

Set up the next machine as a desktop machine.  Put in a large drive and partition it with 3 partitions of 20 GB each and a 1-2 GB swap drive.  Pick three of your favorite linux distros (distrowatch.org) and install on each partition, then you can rotate distros as they get upgraded.

Set up the fastest machine as an Ubuntu Studio machine with a real-time kernel.  This is helpful for music, photo or video editing.  This is a single-purpose machine that is not loaded with all of the stuff on a normal desktop.  It will run faster for your primary creative task, but the realtime kernel is not responsive enough for desktop use.

By focusing tasks on each machine, you can optimize each machine for its task and by networking, you can share files between them easily.

Although clustering seems like a good idea on paper, you will get better mileage by optiizing each machine for its dedicated purpose.  You will also learn a lot about how flexible Linux is.

---

