---
title: "Make the most of my pc's resources."
date: 2010-06-08
forum: New to Ubuntu
---

### Post by wesselvanpersie on 2010-06-08
Hello,

I have  a pc with 12GB ram, a i7 2.667 CPU and a solid state disk.
How can I make Ubuntu make the most of these resources?

I'm mostly programming in java and python.
Or using the data mining toolkits WEKA and RapidMiner (both are written in java).

Best regards,

Wessel

---

### Post by Chesamo on 2010-06-08
What do you mean, "make the most of"? Ubuntu will allocate the resources that your programs need; that's what operating systems do.

---

### Post by Paddy Landau on 2010-06-08
[Download]("http://www.ubuntu.com/desktop/get-ubuntu/download") and install the 64-bit Ubuntu. On a machine like yours, Ubuntu will fly. Fast.

---

### Post by LowSky on 2010-06-08
12GB of RAM? I can't find a use for more than 4GB.

---

### Post by jakupl on 2010-06-08
> **LowSky said:**
> 12GB of RAM? I can't find a use for more than 4GB.

One use: Virtual machines.

wesselvanpersie: Omg. /drools

---

### Post by LowSky on 2010-06-08
> **jakupl said:**
> One use: Virtual machines.


Yeah I guess, LOL

---

### Post by julio_cortez on 2010-06-08
> **jakupl said:**
> One use: Virtual machines.
I second that.

Anyway, I also have a core i7 and 6GB of RAM (opposed to your 12 that looked too much to me while buying parts) and Kubuntu literally flies.

In my opinion, for java programming that machine is just perfect..
I see the same with mine: it looks oversized but at least Photoshop, Matlab and Eclipse load in a split second (Eclipse especially used to make me die when I loaded it on my old machine:lolflag: )

I'm planning to add a SSD too, sooner or later..

---

### Post by wesselvanpersie on 2010-06-11
Is it useful to load the entire OS into RAM every time you boot your system?

---

### Post by -kg- on 2010-06-11
[LIST]

[/LIST]> **wesselvanpersie said:**
> Is it useful to load the entire OS into RAM every time you boot your system?

It can be.  You would have the advantage of the immediacy of RAM without having to access the hard drive for various operations.  You would have to assure that every file necessary for the operation of the software you intended to use was also uploaded to RAM, and that the output of that software is to RAM and not the hard drive in order to be practical.

On the downside, you would have to assure that these files were updated to the hard drive, both periodically and upon shutdown or completion.  Not doing this could cause data loss in case of unintentional shutdown or power loss (unless you have good UPS backup power).  Of course, boot time would be dramatically increased.

I used to do something similar back in the late '80s.  I ran DOS (naturally!) and had upgraded my desktop at that time with extra memory.  I had a Word Processor which would take ***forever*** to do each and every operation, running as it did from (5 1/4") floppy.

I programmed autoexec.bat and config.sys to create a RAM Disk in upper memory and loaded the entire Word Processor into it at boot time.  Of course, this took forever at boot time, but once done, the Word Processor literally ***flew!!***

You have one heckuva setup of hardware.  Another use of such massive resources would be in the CAD/CAM area.  CAD software would be able to run virtually unfettered, depending on the size of the project.

---

