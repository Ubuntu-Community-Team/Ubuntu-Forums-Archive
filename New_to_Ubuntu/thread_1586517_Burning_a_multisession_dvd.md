---
title: "Burning a multisession dvd"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by miklu on 2010-10-02
Brasero is not able to write a multisession dvd.

I tried all options like "only append" etc. and ended up destroying the dvd.

What is the problem?

Incidentally, k3b is also not working.

Thank you in advance.

---

### Post by sikander3786 on 2010-10-02
Brasero works for me.

Did you also try Gnome-Baker?

---

### Post by miklu on 2010-10-02
Can it have something to do with the hardware?

---

### Post by Old_Man_Unix on 2010-10-02
Under options when you burn a disc, you will see **Leave the disc open to add other files later**

Select that and Brasero will leave the disc open when you are done rather than closing it.  So if you reload the disc and add more files, you can have a multi-session disc.  If at any time you want to close that disc, uncheck that box and the disc will be closed when you eject it.

At least, that is what is supposed to happen.

Unfortunately, this doesn't work with some drives - maybe a lot of drives.  It seems to be an upstream problem with one (or more) of the programs that Brasero calls upon to do its work.  That would at least explain why it is only happening in some cases and not in others.  About the only thing you can do is file a bug report - make sure that you include the make and model number of your optical drive. 

I hate to say this, but if burning different types of optical media in various formats  is a crucial part of your work, you may have to consider one of the non-free solutions.

---

### Post by miklu on 2010-10-02
Thank you, old man.

Brasero does show some free space in the disc, but ...

The writer is sony rw, so maybe the hardware has developed a problem (?).

Thank you.

---

### Post by ellgor on 2010-10-03
Hi,

This has been a problem for a while, a workaround, earlier versions of K3b did multi-sessions I found a post that has links to a working version of K3b, before starting remove any version of K3b you may have:

[http://packages.ubuntu.com/jaunty/libk3b3](http://packages.ubuntu.com/jaunty/libk3b3)
[http://packages.ubuntu.com/jaunty/k3b-data](http://packages.ubuntu.com/jaunty/k3b-data)
[http://packages.ubuntu.com/jaunty/k3b](http://packages.ubuntu.com/jaunty/k3b)

use gdebi to install and load in the lib and data packs first or an error will occur (also it will pull in some extra packages, this is normal) and to stop apt from upgrading K3b do this:

sudo gedit /etc/apt/preferences


Package: k3b
Pin: version 1.0.5*
Pin-Priority: 1001

Package: k3b-data
Pin: version 1.0.5*
Pin-Priority: 1001

save the file and all should be well.

Regards, Ellgor

---

### Post by miklu on 2010-10-04
Thank you ellgor.

But I am not sure I am quite upto it!

Regards.

---

### Post by aosodoev on 2010-11-07
Not sure if it has something to do with your problem, in my case brasero could not burn multisession disk with appended files with message "Disk is not empty" and only options to erase or replace disk. I turned on DAO in Edit > Modules > growisofs > settings. It solved this issue for me.

---

### Post by miklu on 2010-12-01
Thank you all for your kind suggestions and comment.

Brasero started writing after installation of a new dvd writer - asus.

---

### Post by jivabill on 2013-04-03
I am having the same problem with Brasero.  When I try to burn a multi session DVD, I am not presented with the option list where I can select "leave the disc open".  Example:  I want to start a new DVD and put one folder containing bout 15 files on it.  I want to be able to add more files later.

Start a new data project, drag the folder in, all fine.  Then when I click Burn I get the burn properties window and NONE of the options are shown.  So the only thing I can do is verify that the DVD+R I put in is being used and I can click Burn.

When I click Burn system wants to write the DVD, closed so I have wasted an entire DVD for about 300 mb of files.

I did notice on one occasion while trying to burn to a CDR-RW and having about 15 individual files dragged in for the project, (but no folder, just files),  THEN I got the list of options and could select "leave disc open".

Needless to say this is frustrating and therefore Brasero is of no use to me, i have to find another burning program to do my work.

Any thoughts/helpful ideas/etc much appreciated.
thank you for reading
bill

---

### Post by wildmanne39 on 2013-04-03
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

