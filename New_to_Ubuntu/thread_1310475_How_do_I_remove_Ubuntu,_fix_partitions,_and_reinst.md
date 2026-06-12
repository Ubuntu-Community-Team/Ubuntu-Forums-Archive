---
title: "How do I remove Ubuntu, fix partitions, and reinstall?"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by K2IAX on 2009-11-01
I recently purchased a new computer with Vista and a 320 GB HD. I added a 500 GB HD and tried to install Ubuntu-Studio and then Ubuntu 9.04 to that drive. Studio worked but since then has developed problems. 9.04 wound up on a very small partition and didn't do much at all. Vista is doing as well as one might expect on it's own drive. 

My question is how can I remove both Ubuntu-Studio and 9.04 from the 500 GB HD without causing any problems with Vista.  The 500 GB drive is partitioned with a 5 gb, a 175 gb, and a 262 gb partitions.  This is a total of 442 gb from a 500 gb drive.  I allowed Ubuntu to do it's own partitioning and that is what it did. What I would like is to clean off the two Ubunto versions and install Studio 9.10 with about 60 percent of the space and the balance to 9.10. If needed, a swap partition could be taken out of the 9.10 space. 

Also, what problems might I have with keeping Vista as part of the "dual boot" function?  I seem to fight Ubuntu so please give plenty of detail in how to do what I have to.

---

### Post by profeta81 on 2009-11-02
Hi...

Do you actually need both ubuntu versions installed on your pc? the essential difference between ubuntu studio and the standard ubuntu is the kernel latency. Beside the kernel all other applications are the same. Even if you really want both kernels installed, you still don't strictly need two different partitions and two entirely separate systems. if you want the low latency (real time) kernel you can open the synaptic package manager and install the linux-rt package. Once installed it should appear in the list of available systems in the GRUBB menu. As for the applications, you can search for packages with an "ubuntustudio" prefix in the package name.

anyway, if you still want to go ahead (regardless of the waste of space), you should first find out in which partition windows is installed and then you can use a standard Ubuntu cd to reinstall the system. When you get to the partitioner (you need to select manual partition), first delete all partition apart from the windows' one (it should be the only ntfs partition so it should be easy to spot), and then you can create all the partition you want and select where you would like the system to be installed, it should be easy enough. Both installations can use the same swapp space, so you don't need to create two separate swapp areas. 

hope this helps....

---

### Post by K2IAX on 2009-11-02
Thanks for the information. I did not understand the difference between the two versions. The plan is (was) for one version for general use and Studio for video editing. Have not had a lot of luck getting video editing going on Ubuntu. I prefer "timeline" style editing like in Adobe Premier. What I have found doesn't quite do what I am looking for.  Also having trouble getting the capture part of it going. Thought that Studio would be better along with only having to reload it if I mess things up to badly.  With separate installs I would not have to redo all of it. 

However, what you say makes sense.  Will give it a try. Thanks for the help.

---

### Post by kansasnoob on 2009-11-02
This seems like a long read but I consider it the multi-booters bible:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

It would be well worth your while to spend a couple of days pouring over the graphical install examples.

---

