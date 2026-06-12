---
title: "Open Office slow, grays out ..."
date: 2009-05-15
forum: New to Ubuntu
---

### Post by cwmoser on 2009-05-15
Using:  Ubuntu 9.04 64-bit edition, 6GB RAM.

Sometimes Open Office runs great, other times is seems slow and the screen grays out.

I turned off the Compiz special effects and Open Office continued to run slow.

I not entirely sure, but I think its vmware Player.  When Open Office Writer got very slow and sluggist, I thought I would experiment and exit the vmware player I had running.  Then Open Office ran normally. 

Could be a coincidence.  It might not have anything to do with vmware Player.  It might be something to do with memory.

Anyone else experience this?  

Does Open Office run ok for you?

Carl

---

### Post by connorh123 on 2009-05-15
For me, it's Mozilla too.
It grays out, then comes back seconds later.

---

### Post by sundar_ima on 2009-05-15
in my case too. especially when there are more images. more over when i copy paste some web page directly (with some images), it takes hell lot of time to import. in both the cases M$ office 2003 did great job...

---

### Post by cwmoser on 2009-05-17
This fixed it for me - upgrade Open Office from 3.0 to 3.1:

How to Install OpenOffice.org 3.1 on Ubuntu 9.04

[http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml]("http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml")

Carl

[COLOR="DarkRed"]**FOLLOW UP -- Further testing ... this did not fix the Open Office slowness issue.**[/COLOR]

---

### Post by sundar_ima on 2009-05-22
it works well in ubuntu 9.04. i am also trying to do this in kubuntu 9.04 but not able to add key. can anybody tell how to add key in terinal (konsol)???

---

### Post by sundar_ima on 2009-05-22
i have done it by using this command...

**sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xd2bb86e0ebd0f0a43d4db3a760d11217247d1cff**

---

### Post by bubblehead74 on 2009-09-17
I can confirm that OO3 is very slow on my U9.04 as well. It was killing my productivity to the point I had to use MS Office in XP again. I think I will wait and see how the 3.1 will do in Karmic.

---

### Post by shae on 2009-09-17
Do you keep VMWare constantly running?

---

### Post by mcduck on 2009-09-17
> **bubblehead74 said:**
> I can confirm that OO3 is very slow on my U9.04 as well. It was killing my productivity to the point I had to use MS Office in XP again. I think I will wait and see how the 3.1 will do in Karmic.

Try disabling Java from OpenOffice's settings, it speeds up OpenOffice quite a lot (and if you ever try to do something that actually requires Java OpenOffice will automatically ask if you want to enable it again ).

---

### Post by bubblehead74 on 2009-09-17
> **shae said:**
> Do you keep VMWare constantly running?

Actually, I don't even know what VMWare is, so I hope I don't keep it running. I have a fresh install of U9.04.

---

### Post by bubblehead74 on 2009-09-17
> **mcduck said:**
> Try disabling Java from OpenOffice's settings, it speeds up OpenOffice quite a lot (and if you ever try to do something that actually requires Java OpenOffice will automatically ask if you want to enable it again ).

Thanks, I will try. Will other Java software be affected by this?

---

### Post by bigboy_pdb on 2009-09-17
> **bubblehead74 said:**
> Actually, I don't even know what VMWare is, so I hope I don't keep it running. I have a fresh install of U9.04.

I'm pretty certain that the comment about VMWare was intended for cwmoser.

cwmoser, you may want to try VirtualBox instead of VMWare in order to check whether or not the problem is directly related to VMWare. If it slows down in both it is probably a problem with the amount of RAM you have or something else, such as other software or hardware problems.

---

### Post by mcduck on 2009-09-17
> **bubblehead74 said:**
> Thanks, I will try. Will other Java software be affected by this?

No, as you only need to disable it in OpenOffice's preferences, not system-wide.

---

### Post by mi_were on 2009-09-17
my 9.04 will Gray out any application that I am  opening every so often, firefox,nautilus, open office name it.  When browsing my USB external drive the screen will gray out so long that I an get a cup of coffee before i can continue then get hit with the same problem so afterwards.](*,) This all started when I upgraded.

It is slowing getting me frustrated that I am seriously considering downgradng my OS one level until things stabilise!

---

### Post by jimsheep on 2009-09-17
OP claims 6GB RAM...i don't see this as being an issue, unless OOo can only see 3.7GB.  even so, i wouldn't expect VMware to cause issues.  i have a VM running on my work box all the time, and it's got 2GB RAM et cetera, et cetera.

just a thought.

---

### Post by Rolfffeof6 on 2009-10-27
I had this issue also.  Updating to OO3.1 did not help, nor did using Synaptic to completely remove and reinstall OO... several times.

My slow OO performance and grey-outs were resolved when I renamed home/.openoffice.org to force OO to use default parameters.

Of course, all my settings, custom menus and icons were gone, but they were easy to re-define.

OO is fast again!  No grey-outs, etc.  Hope this may work for you!

---

### Post by sundar_ima on 2009-10-29
> **Rolfffeof6 said:**
> I had this issue also.  Updating to OO3.1 did not help, nor did using Synaptic to completely remove and reinstall OO... several times.

My slow OO performance and grey-outs were resolved when I renamed home/.openoffice.org to force OO to use default parameters.

Of course, all my settings, custom menus and icons were gone, but they were easy to re-define.

OO is fast again!  No grey-outs, etc.  Hope this may work for you!

It would be better if you tell us step by step :)

---

### Post by Rolfffeof6 on 2009-10-30
> **sundar_ima said:**
> It would be better if you tell us step by step :)

> I set Nautilus to show hidden files: open file manager, go to home folder, select "View" from the menu and check "Show Hidden Files"

> I renamed the folder home/*myusername*/._**openoffice.org**_ to **_openoffice.orgxxx_** so that Openoffice couldn't find it's configuration files.

> When I next opened writer, for example, it recreated the configuration folder and set all parameters to default.

> OO is fast!

> I then reset some of the  parameters to my preferred font and size, etc. to the values they were before the renaming, selected different icons for the menus, etc.

---

### Post by elaterite on 2010-02-20
If the suggestions above did not work try this: Speed up OpenOffice
[http://mostlylinux.wordpress.com/software/speedupopenoffice/](http://mostlylinux.wordpress.com/software/speedupopenoffice/)

Cheers,
Bob

---

### Post by jbphuket on 2010-12-22
> **cwmoser said:**
> Using:  Ubuntu 9.04 64-bit edition, 6GB RAM.

Sometimes Open Office runs great, other times is seems slow and the screen grays out.

I turned off the Compiz special effects and Open Office continued to run slow.

I not entirely sure, but I think its vmware Player.  When Open Office Writer got very slow and sluggist, I thought I would experiment and exit the vmware player I had running.  Then Open Office ran normally. 

Could be a coincidence.  It might not have anything to do with vmware Player.  It might be something to do with memory.

Anyone else experience this?  

Does Open Office run ok for you?

Carl
This  solution works for me. I changed  this in my /etc/hosts file
Code:
127.0.0.1    hostname localhost hostname.(none)
Replace*hostname*with your hostname. (If you don't know what your hostname is you can enter 'hostname' in a terminal)

Open Applications->Accessories->Terminal

and at the terminal enter
sudo gedit /etc/hosts
N.B. I added this fix for ubuntu 10.10:
change the address 127.0.0.1 in the line containing (none) to: 127.1.0.0
this prevents it from changing with every boot

---

