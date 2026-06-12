---
title: "GRUB command to change kernel"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by Tib-Tib on 2011-02-19
Hi,
I just got a laptop (DELL PP06S) from a friend set up on kubuntu.  He told me to download and run the updates packages if I had time. So  so did I and now the computer stops on an error at boot and I can't log  in at all to type any command.
The error message coming up is:

ata1.00: exeption Emask 0x0 SAct 0x0 action 0x6
ata1.00: BMDMA stat 0x24
ata1.00: failed command: WRITE DMA
ata1.00: cmd ca/00:38:e7:14c/00:00:00:00/e0 tag 0 dma 28672 out
ata1.00: res 51/84:00:1e:15:7c/00:00:00:00/e0 Emask 0x10 (ATA bus error)
ata1.00: status: { DRDY ERR }
ata1.00: error: { ICRC ABRT }

And it seems to try that action over and over but I never get to log in and type any command.
I got told to check the drive cables connections, which I did but it made no difference.
I  also got told that I could try to start with an older kernel, I tried  all the different kernels available in the GNU GRUB but no success.
The different options availables are:

Ubuntu, with Linux 2.6.32-26-generic
Ubuntu, with Linux 2.6.32-26-generic (recovery mode)
Ubuntu, with Linux 2.6.32-25-generic
Ubuntu, with Linux 2.6.32-25-generic (recovery mode)
Ubuntu, with Linux 2.6.32-24-lowlatency
Ubuntu, with Linux 2.6.32-26-lowlatency (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

From my understanding these are the new and older kernels, is that right?
I had to do the updates in 3 times so I guess the kernel from before then isn't in the list anymore.

Every one of them shows the same error message and no way to get a console.
So I can't type any command.
Though, I found out that I can type commands in the GRUB, is there any way to change the kernel from the GRUB?
If so what would be the commands?

Thanks

TiBo

---

### Post by chessnerd on 2011-02-20
First of all, welcome to the Ubuntu Forums. :)

Now, on to your issue:

> **Tib-Tib said:**
> From my understanding these are the new and older kernels, is that right?
You are correct, those would be your previous kernel versions.

Unfortunately, if this error prevents you from booting *all* of them, including the recovery mode ones, that's not a good thing at all. I hate to be the bearer of bad news, but there isn't much you can do. :( 

You can use a Live CD to boot, mount your partition, and get your files. However, beyond that, I don't too many options (other than a reinstall).

The error seems to be coming from the fact that the OS can't write to the hard drive. That makes me think that you should run a disk check to see if the drive is having issues. 

Using a Live CD (or DVD or USB) with Ubuntu on it, load up the Disk Utility (it is located under System > Administration in Gnome). Select the hard drive, choose SMART Data, and click Run-Self Test (you can choose the Short one). If it comes back with no errors, then that is your queue to back-up your data and reinstall Kubuntu. If it has errors, then that might mean that the hard drive is failing.

While I hate to see any version of Ubuntu have issues like this, I do hope that your hard disk isn't failing and that the problem is Kubuntu's fault. Otherwise, you're looking at getting a new hard drive.

Best of luck, and do let us know how it goes.

---

### Post by Tib-Tib on 2011-02-20
Ok thanks for that, I was hoping I wouldn't have to reinstall but after listening to advices from a lot of different people and trying all I could it seems like the last solution...

As this laptop just got given to me I luckily don't ave any data stored on it yet!

So you are advising me to run the live CD just to check that my hard drive isn't failing?

I don't have CD player so where could I download the Live USB?

---

### Post by chessnerd on 2011-02-20
> **Tib-Tib said:**
> So you are advising me to run the live CD just to check that my hard drive isn't failing?

I don't have CD player so where could I download the Live USB?

I would advise running the check to make sure that the hard drive you are using isn't failing. It isn't likely, but I have found it to be the case on a couple of systems I've looked at.

The Live CD and Live USB use the same ISO file. The only difference between a Live CD and Live USB (other than the fact that one is on a CD and the other is on a USB) is how they are created. The easiest way to make a Live USB is with [UNetBootin]("http://unetbootin.sourceforge.net/") (which can even download the ISO for you if you don't already have it). The UI is pretty easy to figure out, but [here is a guide]("http://www.makeuseof.com/tag/install-linux-with-ease-using-unetbootin/").

Might I ask: How did you get Kubuntu on your system in the first place? Or was it there when you got it?

---

### Post by Tib-Tib on 2011-02-20
I am actually using a mac to communicate right now and it seems like the UNetbootin is designed to run on either windows or linux

My friend who gave me the laptop set it up on kubuntu but I happen to now be in New Zealand and him in Australia so he can't really help me.
Though he gave me the instructions on how to reinstall kubuntu and this needs a windows computer as well.

So I will hunt for a windows computer tomorrow.

Thanks a lot

---

### Post by Tib-Tib on 2011-02-24
Right!

after hours and hours of unsuccessful trials from different suggestions from different members of different forums, I decided to reinstall the whole thing.
Really that's what I should have done from the start!

Though the same error message seems to still show up at the start very quickly but everything runs perferctly.

And my hard drive seems to work perfectly fine.

Thanks everyone for your help!

TiBo

---

