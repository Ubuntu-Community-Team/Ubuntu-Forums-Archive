---
title: "Swap difficulties"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by CrazyWayToFly on 2011-02-04
Hi guys :) Linux noob here - I know my way around computers but I've only just started learning Linux.

I'm on a 6 year old Dell laptop with a 40gb HDD and 512mb of RAM. Because it's a Dell, it already had three hard disk partitions (Dell Utility, Dell Restore and the OS partition for Windows XP). I got bored, so I created a fourth partition (13gb) with the GParted live CD and installed Ubuntu 10.10 Desktop onto it.

The Ubuntu install worked great - I booted off the live CD and told it which partition to use and it installed without a hitch. But I then found that I couldn't boot into Ubuntu. I figured it was a bootloader problem, so I used the Rescatux live CD to overwrite the Windows XP bootloader with Grub. I now have a perfectly happy dual boot system.

The problem? Because there were four partitions on my HDD when I went to install Ubuntu, I couldn't create or specify a swap partition. On a computer with only 512mb of RAM I'm feeling the lack of swap, and have been trying to create a swap file, but I keep having problems.

I started trying to use this tutorial: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
But every time I type the first line ("sudo dd...") into the Terminal, it asks for my password, then as soon as I've entered it, tells me that no such file/directory exists. I've tried this about four times and get exactly the same result.

So then I tried to follow the instructions in jdong's post in this thread: [http://ubuntuforums.org/showthread.php?t=89782](http://ubuntuforums.org/showthread.php?t=89782)
I typed the first line and nothing happened, so I was impatient and went on to type the second and third. I was halfway through the third when it executed the first command. Once it had finished I tried the second again and it wouldn't let me (I forget exactly what it said.) I closed the terminal, reopened it and typed the first line again, to be informed that 'text file busy'.

So I closed the terminal, reopened it and typed in the second line ("sudo mkswap...") This seemed to work (setting up swapspace version 1, no label, UUID=...)
The third line ("sudo swapon...") gives the error message "swapon failed: Device or resource busy."

So how do I convince the computer to mount this file as swap? And if I stuffed it up too badly by rushing at the start, how do I find and delete this file so I can start again? (My Ubuntu partition is less than 15gb in size, so I can't afford to have 1gb of it stagnating in the file system somewhere.)

Thanks for any help :)

---

### Post by rUff3r on 2011-02-04
You want to create a swap file. I think at first you should look for what you have done so far. So change in your root partition with

```
cd /
```

then look whats there with

```
ls
```

You said u tried version 2 of the forums so there should be a file called swap_file ? 
Is there a /mnt directory? It should. But I guess it's not otherwise the first line of the Swap FAQ should have worked.

So if there is the swap_file just 

```
sudo rm /swap_file
```

to delete it. Then do exactly the steps from the forum thread. It should work. And be patient after the dd command. This can take some time. Especially on your old laptop. It could take about a minute.

---

### Post by oldos2er on 2011-02-04
> **CrazyWayToFly said:**
> I started trying to use this tutorial: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
But every time I type the first line ("sudo dd...") into the Terminal, it asks for my password, then as soon as I've entered it, tells me that no such file/directory exists. I've tried this about four times and get exactly the same result.


If you're referring to **sudo dd if=/dev/zero of=/mnt/512Mb.swap bs=1M count=512**, first run **sudo touch /mnt/512Mb.swap**

---

### Post by quadproc on 2011-02-04
> **CrazyWayToFly said:**
> Hi guys :) Linux noob here - I know my way around computers but I've only just started learning Linux.

I'm on a 6 year old Dell laptop with a 40gb HDD and 512mb of RAM. Because it's a Dell, it already had three hard disk partitions (Dell Utility, Dell Restore and the OS partition for Windows XP). I got bored, so I created a fourth partition (13gb) with the GParted live CD and installed Ubuntu 10.10 Desktop onto it.

I assume that you created a primary partition as your #4.  That could be unnecessarily confining.  I would have created a logical partition for the OS, another logical partition for my /home, and another logical partition for swap.

The swap partition should be at least as large as the amount of RAM that you have or will have.  This is because the hibernate function uses that swap space to copy out the contents of RAM before shutting down.

Since your disk isn't very big, it would probably be a good idea to defragment it before doing any partition work.  I find that I am using about 14 GB for my main OS partition (not counting /home or swap).

quadproc

---

### Post by CrazyWayToFly on 2011-02-04
The command to delete the swap file didn't do anything. I've got a screenshot of what the terminal did if that's any use - cd/ followed by ls displayed a lot of coloured text, swap_file definitely seems to be there, but sudo rm /swap_file just sat there.

quadproc - yes, it's a primary partition. So what should I have done - created the fourth as an extended partition and set up logical partitions for swap and /home on it? Also, what is the purpose of a /home partition? I don't think I've heard of this being done before. 

I ran Piriform Defraggler on the Windows system before I added the fourth partition. Defraggler not only defragments an NTFS disk, it moves all the data to the front of the drive. The two Dell partitions were at the front of the drive - I added the Ubuntu partition at the end of the XP partition.

EDIT: Oops, I ran cd / and ls again and the swap_file is gone. I'll try the set of instructions again :)

---

### Post by CrazyWayToFly on 2011-02-04
And it worked - I now have 1gb of swap :D Hopefully this will improve performance a fair bit.
Thanks heaps :)

---

### Post by NightwishFan on 2011-02-04
Glad you got it working! Certainly on 512mb a swap file is needed, but it should be snappy enough. :) If this is solved for you please mark as solved using thread tools at the top. :)

---

### Post by oldos2er on 2011-02-05
> **CrazyWayToFly said:**
>  Also, what is the purpose of a /home partition? I don't think I've heard of this being done before. 


[http://www.trainsignaltraining.com/ubuntu-linux-home-partition](http://www.trainsignaltraining.com/ubuntu-linux-home-partition)

[http://ubuntuforums.org/showthread.php?t=1496609](http://ubuntuforums.org/showthread.php?t=1496609)

---

### Post by quadproc on 2011-02-05
> **CrazyWayToFly said:**
> 
[quote]
quadproc - yes, it's a primary partition. So what should I have done - created the fourth as an extended partition and set up logical partitions for swap and /home on it? Also, what is the purpose of a /home partition? I don't think I've heard of this being done before. Ann posted a couple of pointers to good explanations about putting /home in its own partition so I won't say much here - just that yes, I would have created logical partitions for the different kinds of things that will be stored on the disk.  You will find that logical partitions start at number 5 so it is very common to see a disk show up as partitions 1, 5, 6, and 7 and there can still be space left over for other partitions.

These days, I consider a minimal disk setup to be one where I have a partition for the OS, another for swap, another for /home, and the remainder of space available for another OS partition.  This last comes in very handy when a new release comes out - I just put a new partition into the unallocated space, install the new release into the new partition, boot from the new release, fix up the /etc/fstab file so that it can find my previous /home partition, move the newly installed /home directory to something like old_home, reboot, and remove old_home.  I now have the choice of booting from either the old or the new release.  After a while, when I am convinced that I don't need the old release any more, then I can remove it and run grub-setup.  Then I have space for the next release.  And the entire process is fairly easy, painless, and quick.

quadproc

---

