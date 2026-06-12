---
title: "Help with latest LiveCD"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by furialis on 2009-06-04
I recently bought two SSD drives that will not work with the standard 9.04 Jaunty distribution. In my search it was suggested that I try to compile the latest kernel, and see if that works. Well, it did. 

Now my problem is that I need to have a LiveCD with the latest (?) kernel 2.6.29-4. I tried using remastersys but it doesn't work well with custom kernels.

Any beginner friendly options for me? Is there a way to just install the needed sata drivers? A remastersys backup is usually around a gig but after I compiled the new kernel, the remastersys backup was almost 3 gigs. Is there a way to fix that, or is that how much stuff the new kernel installs? I removed all references to the previous kernel through synaptic but the coaster I burned was still 3 gigs.

---

### Post by sandyd on 2009-06-04
> **furialis said:**
> I recently bought two SSD drives that will not work with the standard 9.04 Jaunty distribution. In my search it was suggested that I try to compile the latest kernel, and see if that works. Well, it did. 

Now my problem is that I need to have a LiveCD with the latest (?) kernel 2.6.29-4. I tried using remastersys but it doesn't work well with custom kernels.

Any beginner friendly options for me? Is there a way to just install the needed sata drivers? A remastersys backup is usually around a gig but after I compiled the new kernel, the remastersys backup was almost 3 gigs. Is there a way to fix that, or is that how much stuff the new kernel installs? I removed all references to the previous kernel through synaptic but the coaster I burned was still 3 gigs.
you can try compiling the SATA drivers maunally

---

### Post by sandyd on 2009-06-04
or you could try this..
im not really sure, but you can't die from trying can you?

```

sudo apt-get install dkms

```

then
```

cd ~
mkdir kernel
cd kernel
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2009-06-03/linux-headers-2.6.30-999-generic_2.6.30-999.1244047563_i386.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2009-06-03/linux-headers-2.6.30-999_2.6.30-999.1244047563_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2009-06-03/linux-image-2.6.30-999-generic_2.6.30-999.1244047563_i386.deb 
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2009-06-03/linux-source-2.6.30_2.6.30-999.1244047563_all.deb
sudo dpkg -i *.deb

```

this will install the daily build of the ubuntu kernels (assuming you got a i386 archetecture that is)

there are also you could try at 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by furialis on 2009-06-04
The problem isn't compiling the latest kernel, the problem is getting a LiveCD out of it. The necessary drivers are not included with the Stock 9.04 distribution. I can't boot without the sata drivers.

Do you know how I can figure out which sata drivers are needed? I really hate to ask to be spoon fed, but since I have no idea what I'm doing - or what to search for, could you provide some basic instruction for integrating drivers into a kernel?

Thanks for your time. If I can figure out how to make a working LiveCD I'll create a torrent of it. Someone else might find this useful.

---

