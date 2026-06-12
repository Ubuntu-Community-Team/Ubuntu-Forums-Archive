---
title: "Ubuntu 8.10 install partitioner is dumb"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by Pas_sa on 2009-04-19
I don't recall running into this problem before when installing Ubuntu onto a HDD running Windows already.

I used to run Ubuntu on this laptop but had to remove it due to space limitations. I bought a new 160GB disk for the sole purpose of being able to dual boot again.. but I'm having some difficulties installing:

The partitioner offers me two options. Despite detecting it as an NTFS volume, the only automatic option is to use the entire disk. The manual option doesn't let me resize the NTFS partition.

Do I have to prepare my partitions manually? I've never had to do this with Ubuntu.. I just want it running with Windows harmoniously and GRUB as my bootloader..

---

### Post by mikewhatever on 2009-04-19
If it's really dumb, how come it worked for me?:rolleyes:

---

### Post by LesterPalooza on 2009-04-19
My Ubuntu Installer did not allow the option of resizing the NTFS partition either. Instead, my friend and I had to do it on Windows.

I partitioned part of my NTFS as free space and retried installing Ubuntu. There was an option Guided - Use free space something something..

Now I cannot guarantee that what we did is gonna work for you...

---

### Post by juancarlospaco on 2009-04-19
Use Gparted on the LiveCD.

[I]Windows Partitioner=Erase all,make NTFS,install
OS X Partitioner=dont do nothing, if no HFS+, No install[/I]

---

### Post by Ericyzfr1 on 2009-04-19
I agree Gparted LiveCD should do it. You should not have any problem and I think it is the best way to go.

---

### Post by -kg- on 2009-04-19
I do not remember where I read it, and cannot find the information, but there is a bug in the installer where the Guided Installation selection in the installer will show that it is trying to format the whole disk, though it won't actually do that.

My suggestion is to use manual partitioning and just manually create the partitions that you need.  You can do this with the GPartEd Live CD, then during the installation process, choose "Manual Partitioning" and mark the partitions you create as "/" (root) and "swap" (and if you decide to create a separate "/home" directory, there is an option to mark a partition as "/home" as well).

A good guide on partitioning operations can be found at:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by GCoffee on 2009-04-19
If i remember rightly this could be because you didnt shutdown windows right - but im not totally sure.

---

