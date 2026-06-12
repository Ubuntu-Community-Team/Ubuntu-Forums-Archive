---
title: "Clusters"
date: 2004-12-12
forum: Networking &amp; Wireless
---

### Post by Rink on 2004-12-12
Hi,

I have a 3 or four networked boxen which I'd like to be able to use in a cluster.

They all have different distros (ubuntu and knoppix, different versions) installed on them at the moment.

Does anyone have any experience of using something like mosix or beowulf?

Can anyone offer me a bit of advice on this?

Dave

---

### Post by spb on 2004-12-29
If you have a homogenious cluster of dedicated machines you'll see a speed-up of maybe 0.75*number of machines (assuming that the software is well parallized).  

For an inhomogenious cluster, in the best case, the slowest machine will be the bottleneck.  In the worst case the difference in the rates will cause the machines to crash -- I'm working with 24 node homogenious cluster and because of communication limitations we're having problems running on more than 16 at a time without crashing -- of course I'm just a hack but know enough to know where the problem is :7) 

-=-=-=-=-=-=

If you want to play with clustering (maybe a two node cluster to start) then you should consider reading the site 

[http://www.ic.uff.br/~vefr/research/clcomp/cocoa-1.html](http://www.ic.uff.br/~vefr/research/clcomp/cocoa-1.html)

Here they explain how to configure the hardware for a simple cluster.  The is the page I read when I build my first cluster.  

Then you'll need libraries to execute the parallel code.  The most popular libray is called MPI or MPICH.  There is, what I think, an easier although less powerful library called PVM which you can also use.  There are examples of using PVM at:

[http://heather.cs.ucdavis.edu/~matloff/PVM/NotesPVM.NM.html](http://heather.cs.ucdavis.edu/~matloff/PVM/NotesPVM.NM.html)

I've not programmed with MPI or PVM but PVM seems pretty straight forward (compared to MPI).  

sb

---

### Post by Tashka3261 on 2007-05-15
> **Rink said:**
> Hi,

I have a 3 or four networked boxen which I'd like to be able to use in a cluster.

They all have different distros (ubuntu and knoppix, different versions) installed on them at the moment.

Does anyone have any experience of using something like mosix or beowulf?

Can anyone offer me a bit of advice on this?

Dave


[mapquest photosynthesis Tsunami blood pressure Pay Day Loans](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/forced-porn.html)

---

### Post by madphoenix5600 on 2007-05-15
> **Rink said:**
> Hi,

I have a 3 or four networked boxen which I'd like to be able to use in a cluster.

They all have different distros (ubuntu and knoppix, different versions) installed on them at the moment.

Does anyone have any experience of using something like mosix or beowulf?

Can anyone offer me a bit of advice on this?

Dave


[mapquest photosynthesis Tsunami blood pressure Pay Day Loans](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/forced-porn.html)

---

### Post by GreyDazeR6605 on 2007-05-15
> **Rink said:**
> Hi,

I have a 3 or four networked boxen which I'd like to be able to use in a cluster.

They all have different distros (ubuntu and knoppix, different versions) installed on them at the moment.

Does anyone have any experience of using something like mosix or beowulf?

Can anyone offer me a bit of advice on this?

Dave


[physics Girls Paris Hilton Britney Spears Cash Advance](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/index.php)

---

### Post by karku6a5161 on 2007-05-15
> **Rink said:**
> Hi,

I have a 3 or four networked boxen which I'd like to be able to use in a cluster.

They all have different distros (ubuntu and knoppix, different versions) installed on them at the moment.

Does anyone have any experience of using something like mosix or beowulf?

Can anyone offer me a bit of advice on this?

Dave


[physics Girls Paris Hilton Britney Spears Cash Advance](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/index.php)

---

### Post by tutomlin on 2007-06-11
Well, I'm guessing that you aren't going to write your own apps to use this cluster (most people don't want to) so your best bet is probably either Kerrighed or Openmosix, OpenMosix is stuck on the 2.4 kernels which apparently have trouble with the x-server in Ubuntu.  

both of these require recompiling the kernel, but they'll automatically migrate your processes from an overloaded machine to a relatively free machine.  They WONT make a single app run faster than it would on a machine by it's self

In theory these should work with any combination of distro's if each box is on exactly the same kernel and have all the same libraries for the apps to run.


here's the kerrighed page
[http://www.kerrighed.org/wiki/index.php/Main_Page](http://www.kerrighed.org/wiki/index.php/Main_Page)

If you do want to write your own apps check out :
[http://www.clustermonkey.net/](http://www.clustermonkey.net/)
which has some pretty good basic tutorials on setting up and programming for a cluster


hope that helps

Tucker

---

### Post by omid on 2007-07-30
[this]("https://wiki.ubuntu.com/MpichCluster") also is a wiki page for clustring in ubuntu

---

