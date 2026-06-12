---
title: "distribute cumputing?"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by allenbradley on 2009-10-14
We have a lot of machines ( ~30 ) that run decent processors with good ram ( 1 GB ). However, these machines are connected via an NIS to a central computer, so most of the hard disk space ( ~ 100 Gb ) is wasted on each computer. That translates to almost 3 TB of useless space. Is there a way I can distribute the filesystem across machines, so that the space is not wasted?

Also, we run a few codes (using octave/scilab ) on these machines. Is there a way, again, to distribute computing across these machines?

Thanks

---

### Post by hal10000 on 2009-10-14
I would prefer to put all the disks in a single RAID and all the workstation booting diskless with NFS root to make use of your bunch of disks.

You could make a cluster with all your workstations to work as a number cruncher, but i don't have much experience here, so i can't help you further.

---

### Post by j7%&lt;RmUg on 2009-10-14
You could have a network share to give users access to important resources.

 also +1 to hal10000's idea with a RAID array.

---

### Post by XCan on 2009-10-14
I think RAID is a nice idea, and will likely yield you the best performance.

Another possibility could be for you to run an FTP daemon or something that supports distribution to multiple servers/drives, such as DrFTPD. 

Regarding distributed computing, I've written manual scripts that do that in Matlab, so I don't see how that would not work for Octave/Scilab. "Simply" run a script on the servers that checks a dir (be it a local or remote) for work units. Whenever your master server puts a new workunit there, the first non-idle worker will start to crunch and place the results back. The tricky part here is of course for you to figure out how to divide your workunits.

---

### Post by whitethorn on 2009-10-14
At my work they use Torque/PBS for distributed computing.  I believe there's another program from sun systems I believe it's written in java so you can use linux and windows to send jobs to it.

---

### Post by cholericfun on 2009-10-14
there is some way of doing parallel computing with octave.
but never looked at that myself.
heres an "example" with a whole linux liveCD
[http://idea.uab.es/mcreel/ParallelKnoppix/](http://idea.uab.es/mcreel/ParallelKnoppix/)

that is setup to do parallel octave work,
actually this looks like an interesting search hit:
[http://atc.ugr.es/javier-bin/mpitb](http://atc.ugr.es/javier-bin/mpitb)

BTW, writing parallel code is a very strange thing if your not used to it.
plus its easy to write code that will be *slower* in parallel because of communication time.
(and i guess you dont have some high-end connection between your Nodes)
on the other hand if your computations are memory-intensive you might even get super-linear speed up.

anyway, just wanted to add that parallel computing is not just like
```
for i=1:N; DO PARALLEL
```

---

### Post by XCan on 2009-10-14
Not to forget how to remerge the data in a sensible way if needed with low complexity. :)

---

