---
title: "Newbie, green, neophite wanting to add Windows XP to an Ubuntu mini"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by Roberto S Cabrera on 2010-02-19
I startted to meddle w/ Ubuntu a year ago. I purchased a Dell Mini 9 w/ Ubuntu 8.04LTS installed. I also own a Latitude D800 w/ XT Pro with a variety of Window based applications that are industry specific. I want to be able to use the Window applications in my mini. Hence i would like to enable dual boot, partition my Mini w/ Ubuntu and add Windows XP Pro and the applications I need to use. Is what I want to do possible?... If it is, please, point me to the information/instructions and i will read, learn and do it.

---

### Post by zbirdman777 on 2010-02-19
Of course its possible. You have a few options here:

1. Install XP like you said
2. Install XP in a virtual machine
3. Try using your applications under WINE

What applications do you need? You may not even need to install XP.

In any case, this has instructions for dual booting.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

The instructions look complicated but the whole procedures not that bad.

I'd also suggest a 3rd partition to share files between the two OSs.

If you want to go the WINE or Virtual route things will be different. Both are easier in my opinion.

If you install WINE through the software center you can install many Windows applications just like it was on XP

---

### Post by Roberto S Cabrera on 2010-02-19
Thanks zbirdman777.
I would like to have ACT!, Calyx and NetReceipts in my mini. 
How do I partition in 8.04LTS? and create the dual boot scenerio.
where do I learn about and get WINE?

---

### Post by zbirdman777 on 2010-02-19
Try WINE first, if it works it will save you a lot of time.

To get WINE at your top right go to Applications, navigate to Add/Remove programs, search for WINE, simply install it there. Now, .exe programs that install in Windows are executable in Ubuntu. 

You can also open a terminal and type:
"sudo apt-get install wine"

If you want to install a windows program, right click on the installer and install with wine. (I don't remember the exact wording.)

Not all programs work, and even some that work aren't perfect so test this stuff out.

If you want to partition, I don't think you can do it while your using Ubuntu.

Use your Ubuntu installation disk and boot to it. Select "Try Ubuntu Without Changes to your computer" when you are into the live cd navigate to System > Administration > Partition Editor or GParted (same thing).

VERY IMPORTANT!
Make sure to back up your files before doing this or you WILL lose everything.

You can delete all of your partitions and create 2 new ones using this tool.

From there, install XP to one partition, then install ubuntu to the other after you are done with XP.

---

### Post by stlsaint on 2010-02-19
I dont own a netbook myself but after a little research it seems that your particular netbook runs on a 8GB SSD card for storage with 1GB RAM. If this is true for your netbook than i would not recommend running a full blown install of xp on there as a dual boot unless you plan to get a much larger storage device.

REASONS: 
1. Performance-Reviews of the mini shows that read/write performance is not all that great and throwing windows on there wont help any.
2. Storage-Mabye a base install of XP will hold but when you start adding on service packs and updates plus the applications you speak of that install is going to grow very quickly.

Though this is not ideal either, if you really MUST have windows on this machine i would have to suggest a virtual machine using the program virtualbox and if possible start looking at options for upgrading hardware on your system.

NOTE: If im wrong about the specs of your particular system please disregard.

---

### Post by snowpine on 2010-02-19
Windows is not going to run well in VirtualBox on an Atom processor, sorry. If the programs run well in Wine (you can check on the Wine website) that's probably your best solution. If not, I would recommend a dual boot. If disk space is an issue (my Dell Mini 9 only has 8gb, way too small, but maybe you have more?) you can pick up an inexpensive Mini 10v (with 160gb hard drive and Windows preinstalled) from the Dell Outlet for not much more than the price of Windows itself. :)

---

