---
title: "Is it possible?"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by steviefordi on 2008-11-12
**THIS EXPLANATION ISN'T VERY CLEAR, SEE MY POST BELOW FOR A MORE CLEARLY STATED PROBLEM**

In my workplace we have a Windows network (ugh!). At the moment, various departments map their U: drive to share \\mainserver\files.

We need to replace this server with one that is named differently, and also have an effective disaster recovery plan.

Us programmers have not always used U:\ when referencing files, and some programs have hardcoded \\mainserver\files\. Currently the 'server migration' project as it's known, has centered around going through all the code our busy IT department has written over the past decade or so, replacing any references to \\mainserver\files\ with U:\.

This is a huge task, and is frought with risk as most of the applications are for important clients that won't appreciate something going wrong just because we needed to change to a new server.

The hope is that everyone in the company that uses \\mainserver\files\ can just re-map their U:\ drives to the new \\server\share and all will be well. It is also hoped that this is all we'd need to do in a DR situation, remapping U: from the broken server to the backup one.

Now, hopefully you understand my problem, here is my question:

Could we integrate a linux server into our windows network, call it 'mainserver' and set up a share called 'files'. On the linux server, we mount the volume that replaces the old \\mainserver\files into the share on the linux server?

If this is possible, everybodies U:\ drive will remain mapped to \\mainserver\files (now a linux server), and all programs will continue to work correctly. In a Disaster Recovery situation we just unmount the broken server and mount the backup one.

---

### Post by chrestomanci on 2008-11-12
Having just finished updating the DR plan at my place I have some experience of this.

Is your existing server windows or some sort of Unix/Linux? Because if it is windows, then I suggest you stick with windows in your DR plan.

If I where writing the DR plan for your office, then I would not be specifying a switch of server OS when disaster strikes. You want to keep everything as simple as possible, in order to minimise risk and because all sorts of distracting bad things will be happening around you. If the replacement does not work then you want the minimum of variables to check and fix.

So if your existing server is windows, then you want to spec something like:

> 
One windows server, Minimum spec 2x X GHz Cpu, Y Gigabytes of Ram, with windows server verson Z, fully patched.

Must have the domain name "mainserver", and if possible the IP address of aaa.bbb.ccc.ddd. 

All shared files should be restored from the daily off-site backup (stored at location Y, keys are held by Mr Jones & Mr Smith).

The following shares should be setup...


If on the other hand your **existing** mainserver is Linux/Unix, then you should specify similar hardware and the same OS, as again you don't want to introduce extra problems into a DR situation.

If you have an existing windows file server and you want to migrate to a Linux one, then that is an entirely separate project. I would suggest that it is something you want to do gradually one application at a time. I also think that rather than changing your applications to use a drive letter, you ought to be changing them so that they get their paths from config files that you can more easily change. That way when one application grows very big, you can move it to it's own dedicated share, or server without changing everything again.

---

### Post by steviefordi on 2008-11-13
I completely agree with your point about configuration files chrestomanci, it is something we have been working on.

I think I may not have explained the problem and my proposed solution very well so I'll try and state it more clearly.


**Problem:**

**1.** Currently programs run that could be referencing **U:\** or **\\mainserver\files\** for their paths.

**3.** We need to replace mainserver (it's on its' last legs) with one called '**newserver**', which will cause many programs to fail.

**4.** newserver will be backed-up to another server - **newserverbackup** - which will be used in a disaster situation.



**Proposed solution:**

The proposed solution is to take advantage of how the linux filesystem works by adding a new linux server in place of the old mainserver. It will not be used for data storage but just as a relay to the data store.

**1.** On the linux server we create directory **/media/datastore/**. 

**2.** We call the linux server mainserver and share **/media/datastore/** as **\\mainserver\files**.

**3.** All U:\ drives will be mapped to \\mainserver\files so they don't change from how they are now.

**4.** We mount **\\newserver\files** into directory **/media/datastore**. If \\newserver goes down we just mount \\newserverbackup instead.

If this is possible, it covers the drive mapping\unc referencing problem that the programs have and disaster recovery of \\newserver becomes a simple task - just mount \\newserverbackup\files in place of \\newserver\files.

Drive mapping U: to \\mainserver\files remains as it is, but the data found there is dependant on what share has been mounted.

---

### Post by chrestomanci on 2008-11-14
That plan sounds like it will work. The only thing to be aware of is that you are creating an I/O bottleneck through your linux server, as all file requests will have to pass through it. So for every megabyte of files that users read or write mainserver will transfer 2 Mb, and newserver 1 Mb, with a total of 3 Mb through your switch.

You might want to investigate fitting a second network card to mainserver, in order to spread the load.

---

### Post by steviefordi on 2008-11-19
Very good point, I appreciate your help and advice chrestomanci.

---

