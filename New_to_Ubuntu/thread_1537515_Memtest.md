---
title: "Memtest"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by Whatrymes on 2010-07-23
It has been suggested to me to test my ram and motherboard memory. One suggested Memtest. I noticed at boot up my grub menu lists something called memtest. Is this the same thing? How can I check the results. I'm running Vista and Ubuntu 10.04.

Oh, any idea how much time I should allow for it to run? I have 4 GiGs of memory.

Thank you,
Ed

---

### Post by matrixblue on 2010-07-23
The memtest is the same. Memtest takes a while from my experience. You're looking at least an hour but of course it depends on how fast your system is.

---

### Post by Bluesan on 2010-07-23
[http://packages.ubuntu.com/lucid/memtest86+](http://packages.ubuntu.com/lucid/memtest86+)

[http://www.memtest.org/](http://www.memtest.org/)

---

### Post by wigg on 2010-07-23
I use memtest at work to diagnose user computers all the time.  I would suggest running memtest over night.  The program will loop forever and a good overnight barrage on your memory should be suffecient to find any blocks of memory that aren't holding data.

---

### Post by WrEtCh on 2010-12-02
Hello people,

I see you had a short conversation about the Memtest program. I have a small problem.
I am quite new to linux and just getting to know it and I am starting to love it, hehe. Anyways I am running an Ubuntu 10.10 netbook remix and two days ago, after a typical restart Memtes86+ kicked in. Well I saw that it was checking my RAM so I didn't bother canceling it. However this test was run for a veeeeeeeeeeery long time and as far as I understood it is just looping all over again until you stop.

Well the question would be - how do you stop it? When I reboot (press ESC) it just reboots and start with Memtest all over again and it is starting to get annoying cause I cannot reach my Ubuntu :)

Thanks for help.

---

### Post by soloman498 on 2010-12-02
[QUOTE=WrEtCh;10189359]Hello people,

I see you had a short conversation about the Memtest program. I have a small problem.
I am quite new to linux and just getting to know it and I am starting to love it, hehe. Anyways I am running an Ubuntu 10.10 netbook remix and two days ago, after a typical restart Memtes86+ kicked in. Well I saw that it was checking my RAM so I didn't bother canceling it. However this test was run for a veeeeeeeeeeery long time and as far as I understood it is just looping all over again until you stop.

Well the question would be - how do you stop it? When I reboot (press ESC) it just reboots and start with Memtest all over again and it is starting to get annoying cause I cannot reach my Ubuntu :)

Thanks for help
  I have just had that.I pressed esc and when the choice of O'S came up I selected Ubuntu with the arrow keys and when Ubuntu started I went to System-Administration-Startup Manager- Default operating system and changed it from memtest to Ubuntu and closed Startup Manager.Next time it starts it will start with whatever one you decide on.

---

### Post by WrEtCh on 2010-12-02
Hey soloman498,

Thanks for the fast answer. I understand your solution, but I also have the problem that during the booting period I don't have the ability to choose any OS. It loads automatically after each boot. Is there any key combination to stop automatic boot and choose stuff on your own?

As you can understand I am in an endless loop :)) Was thinking to load Linux from an USB and then try to work from there somehow. 

Cheers.

---

### Post by WrEtCh on 2010-12-02
Hello again,

I fixed my problem already :) A little effort, but I did it. Basically I loaded Ubuntu from a USB stick and accessed the grub.cfg file while commenting the memtest part on boot. Now I will just figure out how to have the boot menu while rebooting to avoid this problem in the future :)

---

