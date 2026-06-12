---
title: "How much memory do I need for Ubuntu 10.10?"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by thisisjay on 2010-12-12
I have 2gb and I notice in System Profiler that I am using between 9000 and 1900 MB. It seems to fluctuate randomly and wildly regardless of what I have open. I have the 64 bit version.

1. Do I need 4gb?

2. Is there a way to see what process is actually using the memory in real time?

3. WTF??? I only use about 50% of the 2g in the 64 bit version of Windows 7.

---

### Post by snowpine on 2010-12-12
1gb is the recommended minimum RAM for Ubuntu.

The terminal command 'top' will tell you what's using your RAM.

Linux memory management is very different from Windows.  You may find this article informative: [http://www.linuxatemyram.com](http://www.linuxatemyram.com)

---

### Post by amjjawad on 2010-12-12
> **thisisjay said:**
> I have 2gb and I notice in System Profiler that I am using between 9000 and 1900 MB. It seems to fluctuate randomly and wildly regardless of what I have open. I have the 64 bit version.

1. Do I need 4gb?

2. Is there a way to see what process is actually using the memory in real time?

3. WTF??? I only use about 50% of the 2g in the 64 bit version of Windows 7.


[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes)

> 
**System Requirements**

 The  minimum memory requirement for Ubuntu 10.10 is 256 MB of memory. Note  that some of your system's memory may be unavailable due to being used  by the graphics card. If your computer has only the minimum amount of  memory, the installation process will take longer than normal; however,  it will complete successfully, and the system will perform adequately  once installed. 
Systems  with less memory may be able to select "Install Ubuntu" from the boot  menu to run just the installer, rather than the whole desktop, or may be  able to use the alternate install CD. 
 
I have installed Ubuntu 10.10 on P4 with 448MB RAM and it worked perfectly without any problem.



[https://help.ubuntu.com/community/UsingTheTerminal#System%20Information%20Commands](https://help.ubuntu.com/community/UsingTheTerminal#System%20Information%20Commands)

---

### Post by cgroza on 2010-12-12
I am running here with 1GB of RAM and I have another PC running Lucid on 512MB RAM and it works just fine.

---

### Post by oldos2er on 2010-12-12
[http://www.linuxatemyram.com/index.html](http://www.linuxatemyram.com/index.html)

---

### Post by cgroza on 2010-12-12
And for your "WTF": Linux doesn't wastes memory, it uses it by caching files into the RAM for better speed. This allows to take advantage at maximum of your hardware.
Many people like to see a big piece of empty memory: that is just waste!

---

### Post by amjjawad on 2010-12-12
> **cgroza said:**
> many people like to see a big piece of empty memory: That is just waste!

+1

---

