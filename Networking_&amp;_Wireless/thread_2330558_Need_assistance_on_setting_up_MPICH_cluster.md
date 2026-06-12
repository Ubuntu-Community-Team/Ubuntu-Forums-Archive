---
title: "Need assistance on setting up MPICH cluster"
date: 2016-07-12
forum: Networking &amp; Wireless
---

### Post by philm001 on 2016-07-12
Hello everyone,

I am running into a few issues with the SSH and MPICH executing. From some previous questions that I asked, I was able to progress to a point where I executed the mpi_hello.c program. 


For reference, I am working on following this tutorial on setting up MPICH: [https://help.ubuntu.com/community/MpichCluster](https://help.ubuntu.com/community/MpichCluster)


I created a directory in root called clusterFiles and I created a user on all of the nodes called clusterUser (clusteruser). I exported clusterFiles and I mounted clusterFiles in all of the nodes. Also, I changed ownership of clusterFiles to clusterUser on the master node. I also changed the home directory of clusterUser to be /clusterFiles.


I created an ssh key for clusterUser on the master node and I added the key to the authorized lists. I installed a keychain on the all nodes and on the master node I edited the .bashrc as specificed in the guide (I copied what was in the guide into .bashrc)


I also installed MPICH2 and GCC on all nodes.


I edited the machine file for my scpecific cluster.


However, when I go to execute the MPI hello_world.c program, this is where the errors occur.


I copied and pasted the code on the guide into a .c file and called it mpi_hello.c (This was done on the master node).


In the guide, the last part he just calls `mpicc [arguments]` and `mpiexec [arguments]`. However, when I go to call mpicc, I need to `sudo mpicc [arguments]`. Is this a problem I should be concerned with or would this be the proper way that it should it be done?


When I run mpiexec (without sudo), I recieve that following errors:


    clusteruser@rgcluster2blade1:~$ mpiexec -n 7 -f machinefile ./mpi_hello
    
    [mpiexec@rgcluster2blade1] HYDU_parse_hostfile (./utils/args/args.c:323): unable to open host file: machinefile
    
    [mpiexec@rgcluster2blade1] mfile_fn (./ui/mpich/utils.c:341): error parsing hostfile
    
    [mpiexec@rgcluster2blade1] match_arg (./utils/args/args.c:153): match handler returned error
    
    [mpiexec@rgcluster2blade1] HYDU_parse_array (./utils/args/args.c:175): argument matching returned error
    
    [mpiexec@rgcluster2blade1] parse_args (./ui/mpich/utils.c:1609): error parsing input array
    
    [mpiexec@rgcluster2blade1] HYD_uii_mpx_get_parameters (./ui/mpich/utils.c:1660): unable to parse user arguments
    
    [mpiexec@rgcluster2blade1] main (./ui/mpich/mpiexec.c:153): error parsing parameters


Are these files something that forgot to install? At first, I am thinking that I need sudo in front of mpiexec. So when I perform: `sudo mpiexec [arguments]` it "runs" but connects to the SSH cluster as root when I need it to connect as clusteruser.


My main concern is that he is not executing his commands as root. I am wondering if there is a step that is implied or at least there is a command that I was suppose to execute but didn't?


Also, I noticed that when I tried changing ownership of clusterFiles to clusterUser on the other nodes, I would get an operating not permitted error (I was root when I did this command). My thinking is that since I changed the ownership on the master node, it propagated to the other nodes since they have same username. So I was effectively changing the ownership to itself. Is this a correct thinking or is there more to it then that?

---

### Post by philm001 on 2016-07-12
Does anyone have any suggestions on how I can get more hits? Should I place this in a different section of the forum?

---

### Post by steeldriver on 2016-07-12
Be patient - you only started the thread an hour ago

Don't read too much into the 'Views' counter - it seems to be out of whack at the moment

---

### Post by QIII on 2016-07-12
Hello!

2 hours is not a long time on a world wide forum.  It could be the person who has the best answer is on the other side of the world and is sleeping right now.  Please wait about 12 hours without a response before you bump your question.

Even when they are working (which they are not now), the "views counters" are not worth paying too much attention to.  Some of those view are from people reading for their own answers, looking in to see if they can help and finding they can't, the Staff reading new posts, etc.  One thing that drives "views" up is webcrawlers and indexers.  Something that drives the "views" down is the database/site problems we experienced today.

Just be patient.  Someone will come along.

---

### Post by philm001 on 2016-07-12
OK, thank you guys for the reassurance!

I was looking at the views counter and there were alot of views for some you had already posted within an hour. I was getting worried.

---

### Post by madderhatter on 2016-07-25
I've been trying to set up a cluster myself and been having all sorts of problems.  I've been generally following the 13 step ones, but having all kinds of trouble with security issues.  Those steps seems to be left out.  Everything just isn't going smooth.  Most of the guides for beowulf clusters and mpi seem to be from like 2010 or before even.  Not having a fun time.  Maybe we can team up to make a better comprehensive guide?

---

### Post by madderhatter on 2016-07-25
Junk like this keeps happening that I have to refer to constantly, it's not fun, and now I still can't set up the ssh authorized key thing that the tuts tell me to do, it's one rabbit hole after another, taking me weeks. [http://stackoverflow.com/questions/15190391/ssh-directory-not-being-created](http://stackoverflow.com/questions/15190391/ssh-directory-not-being-created)

---

