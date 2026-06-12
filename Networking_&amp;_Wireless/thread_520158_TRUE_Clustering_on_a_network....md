---
title: "TRUE Clustering on a network..."
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by tekoholix on 2007-08-07
I have SEVERAL boxes (all x86 PC's) on my SOHO network, varying greatly in HW config, and including desktop and notebook machines, ALL running Ubuntu (because we all just love it!!).  All but one runs Feisty, the other (test-box) runs Gutsy beta.

For several reasons (the largest, probably, being simple experimentation / self-education), I've become hugely interested in creating a cluster, and done a great bit of reading up on this sort of setup.  Unfortunately, however, none of my reading has shown me what I, in my own warped mind, understand the TRUE concept of cluster to be...

My own concept:  Several machines, linked by various network technologies (bluetooth, wifi, wired, VPN, etc...), with ALL non-hardware-dependent info AUTOMATICALLY sync'd (unless excluded from sync by owner / admin of machine), so that, INSTEAD of having to login to a remote, shared home dir, all machines ALWAYS have an identical /home directory, and all changes made on one are propagated to all others, instantly (if connected to network, and if not, sync'd as soon as detected on net).  As well, anytime software is installed on one of the machines, that install / config would also be automatically duplicated on all other machines, in the same manner.

Now that we have all software and config's the same, network-wide (and automatically remaining as such), there would be a master-server (that NEVER leaves the network), to which ALL work being done on the network would be communicated.  This master would then query all other systems on the net, as to their idle state, or even better, their work-to-capability ratio, and spread whatever tasks have been initiated on ANY system in the net to ANY system on the net, that can handle a portion of the work-load.  ALL work would be kept on the master server, and simply copied in bits and pieces (issued as tasks) to the other systems to be completed, and then, the master would await responses of success from each worker-ant.  If a success report is given for a particular issued task, that portion of work / data is then copied to the master completed, and then to the system which initiated the overall job, to be pieced together with the rest of that job, when all parts are completed.  If no success-report is sent to the master, that task would be issued again, to the next system in the cluster available for handling it...  This way, we could even start a task from a notebook computer, and remove that notebook from net, while our job is being completed (and while we're travelling or working), and come back (or connect remotely) to receive our completed task.  Basically a hotplugging system, in the cluster (any system in the net works on any task on the net / any system that is removed from the net cannot offer a success-report and completed portion of the job, so that portion is then re-issued, and that system goes about it's business until it's back on the net...

I LOVE Linux, and will NEVER go back to Windoze...  And, although I DON'T know how to make this idea a reality (I'm learning everyday, but there are a whole lot of days before I'll be this educated...), I'm hoping I can intrigue someone who CAN, enough that he might, if it's not already out there, and I just haven't found it yet.  I've been searching for several weeks, and this post is the closest I've found, although it's nowhere near what I'm looking for...:

[http://ubuntuforums.org/showthread.php?t=247218](http://ubuntuforums.org/showthread.php?t=247218)

Any help I can receive would be wonderful.  PLEASE, no flaming...  If this is already available, just point me in the right direction.  If (as I believe to be true) it is not, either TRULY educate me as to why it cannot be, be intrigued enough to help me make it so, or second my desire for it, so as to help me show a real need...

---

### Post by tutomlin on 2007-08-10
Hi,

I've also done some looking and I think I have at least partial answers to your questions.  I don't think there's one big single solution to your question but there is a combination that I think will work.

*My own concept: Several machines, linked by various network technologies (bluetooth, wifi, wired, VPN, etc...), with ALL non-hardware-dependent info AUTOMATICALLY sync'd (unless excluded from sync by owner / admin of machine), so that, INSTEAD of having to login to a remote, shared home dir, all machines ALWAYS have an identical /home directory, and all changes made on one are propagated to all others, instantly (if connected to network, and if not, sync'd as soon as detected on net). As well, anytime software is installed on one of the machines, that install / config would also be automatically duplicated on all other machines, in the same manner.*

I think you need to look up NFSroot here.  Basically NFSroot is a way to have machines boot off a server.  Once booted this way the system will run diskless, and you should be able to set all the home directories to the same folder, or set of folders, in the server.  If you do a lot of file access this will be a little slower than just opening a file from your local hard drive, but it's probably the fastest way I know of to keep all your systems on the same page.

other than that there's probably a way to have one computer mirror another, but I think this is typically only done for servers, where the environment and hardware are pretty standardized.  I'm not sure if there are solutions that will take care of things in the kind of heterogeneous environment that you describe.  You can probably write your own script to do this updating periodically, but that's way beyond my capacity.

*Now that we have all software and config's the same, network-wide (and automatically remaining as such), there would be a master-server (that NEVER leaves the network), to which ALL work being done on the network would be communicated. This master would then query all other systems on the net, as to their idle state, or even better, their work-to-capability ratio, and spread whatever tasks have been initiated on ANY system in the net to ANY system on the net, that can handle a portion of the work-load. *

For this you should look at openMosix or Kerrighed.  These are kernel level extensions to the linux kernel that will let computers in the cluster "migrate" active processes to the optimal processor.  At the moment openMosix is not compatible with the current Ubuntu, since it's based on the 2.4 kernel series and swapping back to that kernel apparently breaks the X environment.  Kerrighed seems to be more up to date, and supports the 2.6 kernel.  Also, to my knowledge neither supports SMP machines, so I don't know what will happen if you have a big dual or quad core as your head node.(this is why I haven't done this yet)  The Kerrighed guys were supposed to get this ironed out in july but I haven't seen any updates to that effect on their forums.  
These solutions are not quite what you want as all the processes maintain a link to their "home" computer, allowing them to return information to the user that started the process.  One of the reasons that I suggested NFSroot above is that these systems have to have the exact same kernel and software on all the computers in the kernel, and having all your systems pull from the same server guarantees that this is the case.

[I]ALL work would be kept on the master server, and simply copied in bits and pieces (issued as tasks) to the other systems to be completed, and then, the master would await responses of success from each worker-ant. If a success report is given for a particular issued task, that portion of work / data is then copied to the master completed, and then to the system which initiated the overall job, to be pieced together with the rest of that job, when all parts are completed. If no success-report is sent to the master, that task would be issued again, to the next system in the cluster available for handling it... This way, we could even start a task from a notebook computer, and remove that notebook from net, while our job is being completed (and while we're travelling or working), and come back (or connect remotely) to receive our completed task. Basically a hotplugging system, in the cluster (any system in the net works on any task on the net / any system that is removed from the net cannot offer a success-report and completed portion of the job, so that portion is then re-issued, and that system goes about it's business until it's back on the net...
[/I]

This part is really tricky, if you remove the computer that started a process in Kerrighed or OpenMosix I'm pretty sure the process dies.  The best I can suggest is to set up a Kerrighed network with a NFSroot base, then if you need to have a task run independently, SSH into the head node and start the task there, you can then pull the laptop, and the task should complete and store data or whatever on the server for you to access later.  I don't know how Kerrighed or openMosix Handle node dropout, ie if your laptop happens to be running someone else's process when you pull it out, I'm not sure what will happen.  I think that if you shutdown before disconnecting the processes will automatically migrate off to another cpu but I'm not sure, and I know that if you just shut off the network connection you'll lose the work, and the process will probably die.  Your best bet might be to keep the laptops out of the cluster and send all big jobs off to the cluster of your desktops.

I'm sure there are other people with solutions, but there doesn't seem to be many folks working on clustering ubuntu boxes, and most of those are looking for High Powered Computing clusters, which is a whole 'nother can of worms.

I hope that helps a little

Cheers

Tucker

---

