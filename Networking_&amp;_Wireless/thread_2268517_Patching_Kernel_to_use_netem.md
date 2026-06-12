---
title: "Patching Kernel to use netem"
date: 2015-03-09
forum: Networking &amp; Wireless
---

### Post by nuno_almeida2 on 2015-03-09
Hello!

I am fairly new to Ubuntu and I am trying to use Linux's tool netem to emulate a p2p network for a thesis in electrotechnical engineering.
The problem is I never had much contact with Linux environment and im struggling to proceed with what I need, since the guides i find for netem are outdated by 8-9 years or so.

In this guide, [http://tcn.hypert.net/tcmanual.pdf](http://tcn.hypert.net/tcmanual.pdf) I'm told that "the source code of the netem kernel module and the source code of tc has to be patched". The point is to "install" routines that create 'tracefiles' to track packet-related issues like delay, drops or corruption. This is a problem because the guide is dated from 2006 and they were working with 2.6.x kernel versions and the kernel patch at [http://tcn.hypert.net](http://tcn.hypert.net) is version 2.6.16.19... The Iproute patch is 2.6.16-060323. 

So my major doubts are: Since i have kernel 3.10.13 is there anyway these patches will work for me? Do I have to build a 2.6.x kernel? Can i build a 2.6.x kernel on Ubuntu 14.04 (LTS)? 

I've been reading Ubuntu Unleashed to know more about the Linux kernel but can't seem to find my answers...

---

### Post by dino99 on 2015-03-09
open a terminal to install it:

sudo apt-get install netemul
[http://manpages.ubuntu.com/manpages/utopic/man1/netemul.1.html](http://manpages.ubuntu.com/manpages/utopic/man1/netemul.1.html)

and you are ready to use it out of the box ):P

---

### Post by nuno_almeida2 on 2015-03-09
Wow, thanks for the fast feedback. I will look into this!

---

### Post by nuno_almeida2 on 2015-03-09
So i've been looking into this. The problem is mean to emulate a network and not to simulate it. This is crucial since emulation will allow me to make a much realistic simulation as emulation allows for a real network to be used in conjunction with the emulated network! :) So from what I've read, netem is the most reliable free platform for this! :) 

Any other thoughts?

---

### Post by slickymaster on 2015-03-09
What about [CORE Network Emulator]("http://www.brianlinkletter.com/installing-the-core-network-emulator-in-ubuntu-linux/")? Would it serve your purposes?

---

### Post by nuno_almeida2 on 2015-03-09
I think it may. I'll try it, between today's night and tomorrow Thanks! :)

---

### Post by nuno_almeida2 on 2015-03-09
*I'm back again*

Seems it would not. This is, again, a simulator.

---

### Post by slickymaster on 2015-03-09
[http://wanem.sourceforge.net/](http://wanem.sourceforge.net/)

---

### Post by nuno_almeida2 on 2015-03-09
Hello!

I have posted this on another major forum but i dont know which is the most appropriate place! Sorry :(

I am fairly new to Ubuntu and I am trying to use Linux's tool netem to  emulate a p2p network for a thesis in electrotechnical engineering.
The problem is I never had much contact with Linux environment and im  struggling to proceed with what I need, since the guides i find for  netem are outdated by 8-9 years or so.

In this guide, [http://tcn.hypert.net/tcmanual.pdf](http://tcn.hypert.net/tcmanual.pdf)  I'm told that "the source code of the netem kernel module and the  source code of tc has to be patched". The point is to "install" routines  that create 'tracefiles' to track packet-related issues like delay,  drops or corruption. This is a problem because the guide is dated from  2006 and they were working with 2.6.x kernel versions and the kernel  patch at [http://tcn.hypert.net](http://tcn.hypert.net) is version 2.6.16.19... The Iproute patch is 2.6.16-060323. 

So my major doubts are: Since I have a 3.10.13 kernel is there anyway  these patches will work for me? Do I have to build a 2.6.x kernel? Can i  build a 2.6.x kernel on Ubuntu 14.04 (LTS)? 

I've been reading Ubuntu Unleashed to know more about the Linux kernel but can't seem to find my answers...

---

### Post by slickymaster on 2015-03-09
Threads merged.

Please do not create duplicate threads, it dilutes the community&#8217;s efforts to provide support and causes confusion.

---

### Post by nuno_almeida2 on 2015-03-09
As pointed by Razvan Beuran in *Introduction to Network Emulation ( *[https://www.dropbox.com/s/t4hur67502j64h3/Introduction%20to%20Network%20Emulation%20-%20%20Razvan%20Beuran.pdf?dl=0](https://www.dropbox.com/s/t4hur67502j64h3/Introduction%20to%20Network%20Emulation%20-%20%20Razvan%20Beuran.pdf?dl=0) )

the best option to do what I am trying to do is netem. Though I am open to suggestions, I'd be thrilled to resolve my netem issues and stick with it. WANEM though is a good option is really hard to work with since it needs to be run by system boot through a CD, which really makes things harder when using virtual machines to generate a pseudo-real virtual-machine-powered network in conjunction with a real network and the emulated network.

Simply put, what I want is to be able to patch my linux and Iproute kernels in order to proceed with netem.

Thanks for all your feedbacks and I'm sorry I duplicated the post, the intentions were the best.

---

### Post by slickymaster on 2015-03-09
> **nuno_almeida2 said:**
> <--snip-->

Thanks for all your feedbacks and I'm sorry I duplicated the post, the intentions were the best.
No problem with that nuno_almeida2. Best of luck to your assignment.

---

### Post by nuno_almeida2 on 2015-03-09
Any thoughts on patching the kernel? Can i install a kernel thats a previous version than mine?

---

