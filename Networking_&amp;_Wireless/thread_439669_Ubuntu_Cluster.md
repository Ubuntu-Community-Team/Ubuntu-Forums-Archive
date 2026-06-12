---
title: "Ubuntu Cluster?"
date: 2007-05-10
forum: Networking &amp; Wireless
---

### Post by Blake Morgan on 2007-05-10
Has anyone had any experience building a cluster computing environment with Ubuntu machines?  I tried installing some cluster tools using Synaptic, and it didn't like it. Said that those features weren't supported by my kernel. 

Cool, I know how to roll my own kernel (using Debian...Ubuntu's gotta be similar...), but what switches do I need to flip? 

Further, the clustering tools distributed with Ubuntu seem to be based on Red Hat Linux. But RH based stuff is notoriously fickle about Debian-based environments. Has anyone experimented with openMosix using Ubuntu? It has provided a _very_ stable cluster environment for me in the past, but using a _much_ older kernel. I want clustering using Ubuntu, damn it! And I want it now!

It is like I have a vague idea of what needs to happen, in my head, but I'm having a hard time putting the right tools together. 

I have an active cluster running, using openMosix with Debian (kernel v2.4.27), but I want to take advantage of the stability and modern drivers of Ubuntu Feisty Fawn... yo.

Best regards,
Blake

---

### Post by tutomlin on 2007-06-11
I've seen some posts about OpenMosix in Ubuntu saying that the older kernels you have to use break the x-server. (Never tried it personally so this is just heresay)

I've been looking around and came up with Kerrighed:  [http://www.kerrighed.org/wiki/index.php/Main_Page](http://www.kerrighed.org/wiki/index.php/Main_Page)
which is pretty similar to OpenMosix but it's up to the 2.6 kernels now.  (SMP support slated for July)

I have yet to see a good cluster tutorial for Ubuntu, so I just might futz around and put one together after the SMP update to Kerrighed.

None of this really helps you out with a cluster "NOW!", sorry.


Tucker

---

### Post by AmericanAqualung on 2007-07-05
Hey,
I totally understand where you're coming from with this - we just did it at Haverford College.  My recommendations would be to use a set up that has passwordless ssh on the root accounts between a head node and several compute nodes.  Then use dsh (distributed shell), ntp (network time protocol), nfs (network file system), some sort of scheduling software (we used torque/MAUI) and OpenMPI.  Although it seems like a lot, a skilled person can probably do it fairly quickly or with available guides (very scattered) and forums you'll get it (this is how we did).  Within a week or so, I should have my own notes from our cluster posted on my webpage at <http://students.haverford.edu/aohara>.  If you opt to go a similar way, and have problems feel free to e-mail me and I'll try to help.  E-mail is [email]aohara@haverford.edu[/email]

-Andy O'Hara

---

### Post by motin on 2007-07-16
I have been dreaming about the idea of setting up a plug n play cluster environment using Ubuntu machines since I first started searching about "linux" on Google (migrated around 3 months later, with the clustering possibility one of the factors speaking for the linux platform). 

In another environment, I've set up Torque and love it for it's batch processing capabilities, but it is not nearly as flexible as OpenMOSIX I've heard. 

Installing the Red Hat suite on Dapper led to some issues where I didn't understand how to configure things properly and ended up deinstalling the packages. I do remember though that the suite included installing the bigiron flavour kernel which had to be used...

My dream comes true when I can install some packages that would set up my desktop as a flexible cluster node. By having the same packages installed on two 100mbit connected Ubuntu computers with the same packages, there should be a possiblity to enter their IP-Addresses from Desktop #1, perform some sort of authentication matching/pairing of the nodes, and voila - they should cooperate in sharing computing of processes. I need no shared file system except for eventually some small shared partitions needed for the cluster to function efficiently. 

The ultimate vision of course is having Avahi-enabled network discovery of new nodes with automatic configuration/authentication alongside with the ability to effeciently use the cluster over a wireless connection. I could then increase the processing power of my laptop just by being at home where another 3 cluster nodes would stand. Outside home I'd do with the laptop's processing power...

Bah I keep blabbing. Point is I'll help trying things out and give feedback on any proposed solutions for making Ubuntu clustering a reality. 

Cheers!

---

### Post by tutomlin on 2007-07-24
In response to motin,

(Note that I know next to nothing about the actual programming involved I'm just extrapolating from my experience as a user and frequenter of web boards)

I know that the knoppix guys had something called openknoppix, based on openmosix that did most of the stuff you're talking about.  basically you'd install the system on a head node and the boot the nodes from a live CD.  As far as I understood the head node would autodetect the worker nodes and prompt you to integrate them into the cluster.  It seems like there shouldn't be too much problem doing something similar with an ubuntu clustering package: download it and designate head/worker status, then let the software find the other ubuntu pc's with cluster package on the network.  You'd obviously want to have some sort of password login system to integrate each node for security.  but these things seem pretty doable given the software that's available, someone would just need to put it all in one pretty package.

My biggest problem with this type of thing is the user tools for administrating the cluster.  I'm not a server admin, nor am I a linux guru.  I'm happy to spend a couple of weeks digging around forums and howto pages to get it set up but once I'm done I want two things: 

first there has to be an easily comprehensible way for me to see what the cluster is doing.  This means either a GUI or a really creative shell interface.  Apparently openmosix had some of this for the 2.4 kernel series but I have no idea what their roadmap to 2.6 is.

Second, I need to be convinced that I can see some benefit.  I'll happily set up a cluster 'just cause I can' but if I know that my applications won't see any benefit I'll shut it down to save $ on power.  Basically most of us will probably only see a benefit from a one or two extra computers to migrate off apps when we're doing several things, but big monolithic processes will remain stuck on the head node.  And as most of us migrate to multi-core computers the ability to migrate processes to other computers may be less and less attractive.  This would be instantly resolved for me if I found a decent open source FEA package that I could run on a linux cluster, but everybody has different wants in this area.

Anyway that's my wordy $0.02 I'd love to help solve some of this, but my coding background is pretty weak and I don't know where to start.

Cheers

---

### Post by motin on 2007-11-07
Thanks for the pieces of eight. We ought to publish this concept as a blueprint and see how the rest of the community reacts to it don't you think?

---

### Post by ajt on 2007-11-10
> **motin said:**
> Thanks for the pieces of eight. We ought to publish this concept as a blueprint and see how the rest of the community reacts to it don't you think?

I'm running an 84-node openMosix cluster under Ubuntu 6.06.1 LTS. You can download the deb's of my Ubuntu port of linux-2.4.26-om1 from:

[http://bioinformatics.rri.sari.ac.uk/openmosix]("http://bioinformatics.rri.sari.ac.uk/openmosix")

I posted messages about this a while ago on the Ubuntu forums, and openMosix mailing lists. Please let me know how you get on if you download and use my deb's. You need to iinstall modutils to boot a 2.4 kernel under Ubuntu.

Tony.

---

### Post by motin on 2008-02-06
> **ajt said:**
> I'm running an 84-node openMosix cluster under Ubuntu 6.06.1 LTS. You can download the deb's of my Ubuntu port of linux-2.4.26-om1 from:

[http://bioinformatics.rri.sari.ac.uk/openmosix]("http://bioinformatics.rri.sari.ac.uk/openmosix")

I posted messages about this a while ago on the Ubuntu forums, and openMosix mailing lists. Please let me know how you get on if you download and use my deb's. You need to iinstall modutils to boot a 2.4 kernel under Ubuntu.

Tony.

Awesome! Thanks that's probably a great thing to start off with if you want a larger Ubuntu-based cluster!

However, since it may require heavy work to get the 2.4 kernel to work on most modern laptops and for the loss of features compared to 2.6 - it probably won't suffice when we are talking about the home clustering solution.

---

### Post by motin on 2008-02-06
Went for a search on the forums again. Found some more related threads:
An older thread about clustering on Ubuntu: [http://ubuntuforums.org/showthread.php?t=210205](http://ubuntuforums.org/showthread.php?t=210205)
A nwere thread about wanting to cluster Ubuntu server: [http://ubuntuforums.org/showthread.php?t=483039](http://ubuntuforums.org/showthread.php?t=483039)
OpenMosix 2.6 installation problems + request: [http://ubuntuforums.org/showthread.php?t=97008](http://ubuntuforums.org/showthread.php?t=97008)

And, about that blueprint - someone had begun: [https://blueprints.launchpad.net/ubuntu/+spec/openmosix](https://blueprints.launchpad.net/ubuntu/+spec/openmosix)

So I started to write a specification in the Wiki - and it ended up in a new blueprint as well (since I had no permissions to change the above specification to point to this spec):
Blueprint: [https://blueprints.launchpad.net/ubuntu/+spec/easy-ubuntu-clustering](https://blueprints.launchpad.net/ubuntu/+spec/easy-ubuntu-clustering)
Spec in Wiki: [https://wiki.ubuntu.com/EasyUbuntuClustering](https://wiki.ubuntu.com/EasyUbuntuClustering)

As you can see - it is mainly only a placeholder - but maybe we can help to draft it together?

Cheers,

Fredrik

---

### Post by Megatog615 on 2008-02-06
In my case I would use a cluster environment to boost the processing power of all the Ubuntu machines in my home. The clear answer for this is OpenMosix, however it is old and unmaintained, and I intend on using Ubuntu 8.04. What I need is a cluster system that merely shares CPU power. I don't need shared directories and whatnot, as this is a bad idea since I have no one computer that is on all the time, so I can't have a main node. So OpenMosix seems like the right idea since its use is to distribute processes among multiple computers. The cluster system needs to also be able to move processes between computers so that if one goes down for the night, the process doesn't die.

---

### Post by motin on 2008-02-08
I've updated [https://wiki.ubuntu.com/EasyUbuntuClustering](https://wiki.ubuntu.com/EasyUbuntuClustering) with links to the three big SSI cluster projects: OpenMosix, OpenSSI and Kerrighed of which the last seems the most viable option. Anybody care to try it out? I will in some time at least. 

Cheers

---

### Post by rucadulu on 2008-02-09
Hi, I love the Idea of doing a cluster on a home network. I like the idea of using the kerrighed solution for this as it is still supported. I have 12 desktops and 1 laptop that could be used for a test environment.
Intel machines: 1 Pentium 2 400mhz 128mb ram 
                       2 Celeron 466mhz 192mb ram   
                       2 Pentium 3 500mhz 386mb ram 
                       1 Pentium 3 700mhz 512mb ram 
                       1 Celeron 766mhz 256mb ram  
                       1 Pentium 4 2.4ghz 512mb ram 
                       1 Celeron 2.7ghz 512mb ram
                       1 Pentuim 4 3.0ghz 1024mb ram 
                       1 Pentium 4 3.2ghz  1512mb ram
AMD machines: 1 Athlon 64 3800+ 2.4ghz 2048mb ram
                       1 Athlon Turion 64 1.8ghz 1024mb ram
I have no Idea how to setup a cluster, however I would love to try and learn; if anyone is interested in setting up a cluster and would like to give me a hand. We can setup a vpn for this purpose and give it a shot. You can email me at [email]rucadulu@gmail.com[/email] if you are interested.

---

### Post by rucadulu on 2008-02-09
I have download and burned several copies of the Parallel Knoppix live cd. I going to setup an cluster using these and see exactly how it is done and then I will try setting up the same type of cluster in Ubuntu. As I have to travel out of town this week It will be most likely be a week or two before I get this completed. I will keep all that are interested informed of my progress as often as I can.

---

### Post by motin on 2008-02-10
> **rucadulu said:**
> I have download and burned several copies of the Parallel Knoppix live cd. I going to setup an cluster using these and see exactly how it is done and then I will try setting up the same type of cluster in Ubuntu. As I have to travel out of town this week It will be most likely be a week or two before I get this completed. I will keep all that are interested informed of my progress as often as I can.

Sound like a great way to go about it. Good luck with that and be sure to post any problems you might encounter and we'll try to solve them. I will myself try to cluster my laptop and a stationary computer using Kerrighed on Ubuntu - also within the closest weeks - just need the free afternoon and evening...

---

### Post by tutomlin on 2008-02-18
In response to megatog:

As far as I know, in all the mosix type cluster solutions processes maintain a link to the system that started them even when operating on a different cpu.  This means that none of them can maintain the process when the initiating system shuts down out of the box.

If you were really good, you could look into checkpoints on the cluster, and then have a script running on each node that checks to see if your critical processes are running, and if not loads them from the last checkpoint, effectively bringing the process back in a couple of min if the original node goes down.  

The actual scripting for that is beyond me at the moment, but it seems like that scheme should work as a cludge solution.  I don't recall offhand what the checkpoint system is like in mosix, but I think it is "under development" in kerrighed.

I'm also not sure about dynamic node addition to the cluster. In kerrighed you can only drop nodes not add them, and I don't think the drop process is graceful.

As for the blueprint/spec I think that having a well organized goal is a really good idea.
People on this thread have identified a couple of points that would be good goals but I don't know what already works and what doesn't.  I've been planning to try out kerrighed for a while, but I've been swamped.  My plan was to get things going as well as I could and then try out something like this: [http://linuxmint.com/wiki/index.php/Remastersys](http://linuxmint.com/wiki/index.php/Remastersys) to make a liveCD that others could use based on my efforts.  Having never used either kerrighed or remastersys this may be too ambitious for me but it sounds like the right way to go.

---

### Post by ajt on 2008-02-25
> **tutomlin said:**
> In response to megatog:
[...]
As for the blueprint/spec I think that having a well organized goal is a really good idea.
People on this thread have identified a couple of points that would be good goals but I don't know what already works and what doesn't.  I've been planning to try out kerrighed for a while, but I've been swamped.  My plan was to get things going as well as I could and then try out something like this: [http://linuxmint.com/wiki/index.php/Remastersys](http://linuxmint.com/wiki/index.php/Remastersys) to make a liveCD that others could use based on my efforts.  Having never used either kerrighed or remastersys this may be too ambitious for me but it sounds like the right way to go.

I posted on this forum about my experiences with openMosix under Ubuntu 6.06.1 LTS some time ago, but in view of the end-of-life stateement from Moshe Bar the leader of the openMosix project I'm now evaluating Kerrighed as an alternative to openMosix on our Beowulf cluster [http://bioinformatics.rri.sari.ac.uk](http://bioinformatics.rri.sari.ac.uk). We've got it running on a couple of nodes, and it looks very interesting, albeit rather fragile: Crash one node and the rest of the Kerrighed cluster becomes catatonic. However, it's early days!

I'm interested to hear from anyone else interested in running Kerrighed under Ubuntu.

    Tony.

---

### Post by uzi1978 on 2008-03-20
Hi all.

I found some good info here, thanks. I am currently working on a PS3 cluster (3 machines a.t.m). I have Ubuntu running on them but I can't find which clustering software to use on PowerPc architecture.

Any help/links would be greatly appreciated.
Thanks.

---

### Post by Kulgan on 2008-03-21
Yup. Count me in. 
I'm not a linux or programming whizz, but I have a few machines for testing and don't have to be spoon-fed instructions (most of the time). 
Just waiting for my powerline adaptor to arrive before I'm completely networked.

---

### Post by ayenack on 2008-03-21
This is a interesting app. It's in the repo's as fai-server or fai-client.

Here's the home page.

[http://www.informatik.uni-koeln.de/fai/](http://www.informatik.uni-koeln.de/fai/)

---

### Post by paradexes on 2008-03-21
I noticed the Redhat cluster is available on repos. Would that not be useful? (clustering n00b here trying to contrib)

I am also looking to build a cluster. I want to set up a cups/samba print server cluster. I am hoping a cluster with some mirroring capabilities is possible. I suppose I could start a new thread, but I am guessing any solutions for clustering are found would be great. That is really all I need at this point. 

Seeing as there is tons of documentation for RHEL clustering (and the packages are ported to ubuntu), why not use that instead?

my .2 cents

---

### Post by kvk on 2008-03-29
This is really interesting stuff-it's fun to see other people playing with the same things. I'm trying to get some funding to construct a small cluster with four nodes (if I had the money I'd just build it myself- it's under $1000 or so) to run ecosystem models. I need to go back and follow all the links people have posted- there's some great material there. My major issue will be writing the code into the models that allows synchronous but separate processing; hopefully I can assign a distinct processor to each species, and then another processor to handle the integration processes (predation). If I get it up and running I'll post the results and blueprint.

---

### Post by Kulgan on 2008-03-30
O.o
Seems like quite a project!
Hope to hear of your success :D

---

### Post by djh82uk on 2008-04-10
Is there any update on this?

I have a cabinet with 40 Sun Ultrasparc nodes, and am hoping to have a good go at clustering, I am however somewhat new to all this.

DJH

---

### Post by bullethead67 on 2008-04-14
IM looking into clustering 5 PCs (2.8 GHz Gigabit Ethernet) and would love to use Ubuntu. I read on the kerrighed site that Ubuntu has a problem not sure what exactly.

Can anybody ten me why all the Clustering interest has seemed to die?? everywhere I look I see abandoned or dropped projects.

 I would like to use a Cluster as my main PC with one Head Computer and 4 nodes. I think I would be able to make a Heavily graphical 3D environment. I also really would like to play games.

Can Chromium project be Coupled with Kerrighed or does Kernighed already do the same things?

 what about Mosix2 there is a download available limited to 6 nodes but I havent seen it mentioned here. is there a reason it is not desireable?

---

### Post by bullethead67 on 2008-04-14
I seem to be looking at either OpenSSI or Kerrighed. I cant decide as OpenSSI seems the most stable and Kerrighed is Higher performing. Here are a couple documents to read for anyone who hasent already found them.


[www.plurix.de/publications/2005/ICA3PP05.pdf](www.plurix.de/publications/2005/ICA3PP05.pdf)
www2.informatik.uni-jena.de/~ckauhaus/2005/harpy.pdf
[ftp://ftp.inria.fr/INRIA/publication/publi-pdf/RR/RR-5399.pdf](ftp://ftp.inria.fr/INRIA/publication/publi-pdf/RR/RR-5399.pdf)

---

### Post by motin on 2008-04-14
> **bullethead67 said:**
> Can anybody ten me why all the Clustering interest has seemed to die?? everywhere I look I see abandoned or dropped projects.

I would like to use a Cluster as my main PC with one Head Computer and 4 nodes. I think I would be able to make a Heavily graphical 3D environment. I also really would like to play games.

The general theory is that with multi-core processors being cheaper and with increasing amount of cores/threads, the advantages of clustering in smaller environments aren't big enough to motivate development of casual clustering. 

When building larger clusters, there are enough open clustering solutions. 

If we want to change this and convince "the world" that there is plenty of need for casual clustering, we need to - for starters:
1. Collect all our information about clustering in a single Wiki reference page 
2. Outline possible ways to perform casual clustering using Ubuntu
3. Write a specification for Ubuntu to be approved for a soon-to-come fresh new release of Ubuntu

My suggestion is to do all three at the same place: [https://wiki.ubuntu.com/EasyUbuntuClustering](https://wiki.ubuntu.com/EasyUbuntuClustering)
So if you feel like contributing, that's a great place to start!

---

### Post by bullethead67 on 2008-04-15
> **motin said:**
> 

If we want to change this and convince "the world" that there is plenty of need for casual clustering, we need to - for starters:
1. Collect all our information about clustering in a single Wiki reference page 
2. Outline possible ways to perform casual clustering using Ubuntu
3. Write a specification for Ubuntu to be approved for a soon-to-come fresh new release of Ubuntu

My suggestion is to do all three at the same place: [https://wiki.ubuntu.com/EasyUbuntuClustering](https://wiki.ubuntu.com/EasyUbuntuClustering)
So if you feel like contributing, that's a great place to start!

there is one achievement although extremely difficult would immediately have a dramatic effect on the mini cluster community. This would spark a tide of interest bringing talented and able persons to the table to Contribute.

1. Run Crysis on Linux on full settings

Before anyone decides to slam this post. I am aware that it Cant be done yet. Video games are definitely the door to Concentrate on. Many gamers would put an exorbanate amount of effort and energy into just a few more frames per second. Currently games like this Cannot be shifted to process on multiple Cores but every thing else Can.This would Relieve "pressure" on whatever Core was running the game in question.

with this in mind I believe my options are kerrighed and Chromium. Currently I dont know  enough about chromium to see if it would be able to integrate with Kerrighed.

I am going to try to start focusing on Kerrighed at this time.when I can get something useful/ to apply to the easy ubuntu Clustering wiki I will. at this time I believe I am at the Difficult ubuntu clustering stage and have little to Contribute.

---

### Post by greggers42 on 2008-05-12
I'd like to set up a small ubuntu cluster with a view to running VMware.

Tried loading kerighed on Gusty Gibbon 7.10 but started getting errors at the $sudo make patch command so those instructions dont work.

Has there been any progress on a clustered linus solution?

---

### Post by jvin248 on 2008-06-12
My plans are to set up a server to run Kerrighed with Xubuntu (save gui speeds) and VirtualBox to provide Virtual Machine environment.

Most of the time I would run applications on the server itself (email, browser, Open Office, etc) since these tasks won't need the horsepower.  Then when I need to run Finite Element Analysis (FEA) under a VM (forced to have specific OS integrated with application software - so better as VM) I can gang on additional clustered clients - for a small problem I add three, a big problem I go 10+.  I would also like to run a CAD system under VM, but suspect there won't be any performance gain there as it's graphics and not compute intensive (though gaining collective ram would benefit large models).  The other is video encoding using the cluster - either a VM with a dyne:bolic system (which has it's own cluster rendering setup that I'd not use) or straight Xubuntu with specific loaded apps (cinelerra, kino, etc).

I've tried the PelicanHPC option (it's great and easy!) - but it is really set up to run programs that are built to use parallel threads - some of the tasks I need to speed up are single threaded - my FEA package has single threaded meshing and parallel capable solver where I find the meshing is the bottle neck on a single processor machine. Kerreghed seems able, from my reading, to enable increasing the performance of these single and parallel programs.

The note previously with games "like Crysis": the extreme gamer population is small (5% of user base) but when teamed up with the needs of an also small specific scientific community they become a large segment.  I think that VM inside the SMP cluster becomes a powerful solution.  Then any user can "drop in" their software needs via VM and gain all the advantages of adding more cluster clients as their problem solution requires.

Another additional stretch: Take a Kerrighed backend cluster and add a LTSP.org front-end cluster - then you have a personal, educational, or business class solution to reuse old iron that is flexible to match the user needs.

---

### Post by drubulvr on 2008-06-19
PelicanHPC is now a Debian distro...running the new kernel...so we really need this ported to Ubuntu!  Why can't it just be ported :(

I'm trying to build a viz cluster with the newest nvidia drivers and I finally got one node to work.

Now my question is: should I put all 4 tiles on one machine?  Is there a way they other tiles can run on the other node?

I think it may be easier to just add a vid card and put it on the head node.

---

