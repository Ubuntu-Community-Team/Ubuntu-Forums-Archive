---
title: "problem with with reduced networkinginternet speed"
date: 2021-01-10
forum: Networking &amp; Wireless
---

### Post by robdavies on 2021-01-10
I have three laptops at home, connected via ethernet wired through the house.


[LIST]
[*]Advent running Xubuntu 20.04 
[*]Acer running Xubuntu 18.04 
[*]Dell 830 running Xubuntu 20.04 
[/LIST]

I have broadband supplied by Virgin Media at 200Mb down and 20Mb up


I   was getting 200Mb download (on laptop 3 - Dell which was running   Xubuntu 18.04 at the time) until around March 2020 (beginning of COVID   19 lockdown), which it then dropped to 60Mb download. Repairing  it at   the time wasn't a priority, especially as I could still get a usable   speed.

Recently, I brought all of   the laptops together (to where the modem is) to do a proper speed test.  I  use a USB 3 gigabit ethernet adapter (TP Link UE300) for one of my   laptops, so I used that on all laptops for this test, together with the   same cat 5e cable.


Only one device was connected to the modem at one time during the test. These speed tests were performed on [speedtest.net]("https://speedtest.net/"), the results were :

[COLOR=#1A1A1B]
[LIST]
[*]Advent : 60Mb down 20Mb up 
[*]Acer : 200Mb down 20Mb up 
[*]Dell : 60Mb down 20Mb up 
[/LIST]

So   with the same cable and ethernet adapter I was getting different   results of different laptops. Even one I used to get 200Mb download on   with the same adapter.


I am  getting the correct speed from my broadband provider, as I get 200Mb  with one of the laptops. I have no ideas how to diagnose/repair this.  Can someone help?

Thanks for any help

Update :
I have booted my advent laptop with Xubuntu 16.04.4 live image and was able to get 135Mb download and 20Mb  upload. So its not a hardware issue, though don't know how to repair my Xubuntu 20.04 installation
[/COLOR]

---

### Post by TheFu on 2021-01-10
Good work on isolating the issue.  Initially, was considering that the USB2/3 ports in each laptop just weren't connected to the same hardware and some internal limit of the USB internal bus was the problem.  Could run an 18.04 Live Ubuntu environment (booted from USB) and completely rule that out?  Test that on all three systems for the full apples-to-apples comparison.  Same CAT5e and same USB3-ethernet adapter still, please.

Then do the same tests with a 20.04 Live Ubuntu environment (booted from USB) too.

Once that is done AND reported, some other ideas will become clear.

BTW, most websites limit how much bandwidth any single client can use.  I limit my users to 1 Mbps, so everyone gets the same.

Within your LAN, transferring files between these systems, what is the performance like?  I usually see around 40-75 Mbps, depending on the systems involved. My network is all GigE here.  Really, that's where network performance should be measured.  Leave the internet out of it. Use iperf3 between systems.  Run the server on 1 and the client on the other 2, connecting into the server.  That will show you how bad wifi networking is compared to wired AND that some wired ethernet chips are just bad.  Some only give 200 Mbps. Others only 650 Mbps.  There are good ones that do 920+ Mbps with minimal OS or CPU impact. Those are the ones we want.

---

### Post by robdavies on 2021-01-10
Thanks for your reply and for your help.

I will run the tests you have mentioned and will post the results when they are completed.

Thank you.

---

### Post by robdavies on 2021-01-17
This is what I have so far.

I tried to get Xubuntu 18.04 , 18,04,1 up to 18.04.5 , they weren't available. So, instead I downloaded these versions for Ubuntu. I also downloaded Xubuntu 16.04.6, 18.04.5, 20.04.1 and 20.10

I remember noticing the problem first occurring around March 2020 (I think) , this would fall between the releases of Xubuntu 18.04.4 (release February 2020) and Xubuntu 18.04.5 (release August 2020). It seems to me that an update occurred during 18.04.4 that caused this. Currently, the speed tests I've performed are showing the same conclusion.

I have run all of the Ubuntu versions on all of the laptops. I had a problem with the Dell D830 with the Nvidia nouveau driver, I don't use this driver normally as it freezes my computer, it froze during bootup on the Dell  laptop, so I wasn't able to perform the speedtest on all editions on he Dell laptop.

I used the command line speed test for all of the tests, I got more consistent results [https://www.speedtest.net/apps/cli](https://www.speedtest.net/apps/cli)

I have been able to get 200Mb download on all tests using Xubuntu/Ubuntu upto and including 18.04.4, after that it slows down to 60Mb max.

The * on the Xubuntu Dell tests, means that I initially got 6Mb downloads, I then had to upplug the USB ethernet and plug it in again. I then got the results as in the PDF. Come to think of it, in normal use, there were times during bootup I couldn't get any ethernet connection (no connection to router) had to unplug it then plug it in again, or reboot. I don't know if this is related.

I will update this post when I have completed the rest of the speed tests.

Thank you,
Rob

---

### Post by robdavies on 2021-01-17
I tested the USB separately using the following

1) cat xubuntu.iso | ps > /media/rob/usbdrive/xubuntu.iso

I got 9.2MiB/s write speed

2) cat /media/rob/usbdrive/xubuntu.iso | ps > /dev/null

I got 17.8 MiB/s

This was run on the Advent laptop when running Xubuntu 20.04.1 that is already installed on it. With the ethernet it get 60Mb download. I wanted to test another device in case it was the USB bus effecting all devices rather than it affecting just this ethernet device.

---

### Post by robdavies on 2021-01-18
I tried iperf3 today, got 260Mb/s over my network between the Advent laptop and the Acer laptop. They are, however, connected via usb2 as neither of them have usb3.

I read that usb2 will realisticly get between 30MB and 40MB per second transfer rate due to overheads, 260Mb/s (32.5 MB/s) is between this rate.

I did get a breakthrough in that I tried another older kernel (5.0.0) from ubuntu.kernel.com and I ran the speed test from my dell laptop (running 20.04.1). It was getting 60Mb/s, this time it got 220Mb/s which is the full and correct speed.

So it seems like its a kernel problem.

Any ideas on who I can contact about this? Or what the next step I should take?

I hope I won't have to install lots of older kernels to narrow down which kernel started the problem for me, there are loads and loads of them.

Thank you,
Rob

---

### Post by robdavies on 2021-01-18
I tried to narrow down kernels that work :

5.3.0 - 200Mb
5.3.18 - 200Mb
5.4 rc1 - 60Mb
5.4.0 - 60Mb

Going to see if I download long term support kernels from kernels.org and see what results I get from that.

---

### Post by TheFu on 2021-01-18
What are the LAN -to- LAN tests using iperf3 showing? For good GigE connections, over 920 Mbps is expected.  Forget internet. There's too much out of our control there. Test only LAN-to-LAN performance.

Posting numbers without saying the test setup isn't too useful. I won't guess.

And please don't change between Mbps and MBps units.  Use 1 and stick with it!

---

### Post by Doug S on 2021-01-19
> **robdavies said:**
> I tried to narrow down kernels that work :

5.3.0 - 200Mb
5.3.18 - 200Mb
5.4 rc1 - 60Mb
5.4.0 - 60Mb

Going to see if I download long term support kernels from kernels.org and see what results I get from that.

You have already narrowed things down as much as possible, establishing the start (5.3.0) and end points (5.4-rc1) for a kernel bisection.
Anything in 5.3.18 would only be as backported from mainline, so don't deviate from the master tree.
Always before ever doing a kernel bisection, try the latest [Ubuntu mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D") kernel (no need to get stuff from kernel.org as ready .deb files already here), which as of writing this is [5.11-rc4]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.11-rc4/"). Kernel bisection is a lot of tedious work, involving typically less than 20 kernel compiles. In my experience, 4 times out of 5, once the problem commit is known and used as search term it turns out to be a known problem with a fix in progress (i.e check the mainline kernel weekly).

EDIT: Also have a detailed look at the Ubuntu kernel configuration differences between kernels 5.3.0 and 5.4-rc1. Sometimes, but not often, the issue is actually a configuration change. See the /boot/config* files.

---

### Post by Doug S on 2021-01-19
> **TheFu said:**
> Forget internet. There's too much out of our control there. Test only LAN-to-LAN performance.Agreed. However, if it is the only clear indicator type test the OP has, and as long as all tests are repeated several times, then I would continue the investigation. Yes, a more robust, controlled environment, test is ultimately needed for either a launchpad or upstream bugzilla bug report. The detailed method for such a test might be revealed if this thread is tugged at long enough. 
if indeed there is some kernel issue, it would be good to isolate it.

---

### Post by TheFu on 2021-01-20
I missed post#6 above. sorry. That has the most important information.
I did some testing using 5.4.x kernels between a few different systems here. They have a multitude of different NICs.

Both running 5.4.0.x
```
$ uname -r
5.4.0-62-generic
```
 It is using an old Marvell NIC driver=skge. The other NIC inthat  machine isn't good - realtek 8111h, I think. It was dropping packets.  
```

[ ID] Interval           Transfer     Bitrate
[  5]   0.00-10.00  sec   513 MBytes   **430 Mbits/sec**                  receiver
```

Going between 2 other systems with the same kernel on both, using virtio drivers (VMs on the same physical machine): ```

[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  30.4 GBytes  **26.1 Gbits/sec**                  receiver
```

That tells me it isn't the kernel, but a driver or HW issue.  I did some other testing with the 5.4.x kernels. All worked as expected. A 5.4.x kernel (i211 NIC) to 4.15.0-132-generic (usb3-gige-nic)```

[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  1.07 GBytes   **918 Mbits/sec**                  receiver
```
All fine, as expected. That's going through 2 GigE switches too.

My main system has an Intel NIC, but it still runs 4.15.x with 16.04. The other 2 physical systems just got 5.4.x kernels last week, but they have really old NICs on the front network. They get over 500 Mbits/sec.

Sorry for the complexity.  think it is a driver or hw issue, not the kernel. NIC drivers can be dependent on the kernel.
Can you isolate 1 NIC as the problem?

---

### Post by robdavies on 2021-03-07
Sorry its taken time to reply, I've been doing testing and searching if others have been having the same problem with the same adapter (TPlink UE300). I did think that I'd get an email if there was an update on the forum, my mistake. I missed a couple of updates from other people that had posted. I appreciate that you have taken time to run tests for this.

I'll start with what problem others have found :

There is a kernel driver bug reported which has limited the download speed which is the same problem as I've been having. It uses driver r8152. Its located in <linux_source_directory>/drivers/net/usb/r8152.c
[https://bugzilla.kernel.org/show_bug.cgi?id=205923](https://bugzilla.kernel.org/show_bug.cgi?id=205923)

I download a kernel from kernel.org (5.10.11 at the time), applied the changed suggested on the above page, built and installed it, I got full broadband download speed 200Mb download 20Mb upload. At the time of this test, I still tested using speedtest rather than iperf. Shall I repeat this test using iperf? I did this as a test/trial, as I had installed 5.10.11 from [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.10.11/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.10.11/) and got slow network speed as usual. This driver issue hasn't been fixed in the mainline or stable kernel yet.

Second is the speed tests :

I am using iperf3, the server is the acer laptop with a 1Gb ethernet adapter running xubuntu 20.04 lts. I had run a broadband speedtest and its getting 600Mb download on 600Mb/40Mb broadband, so I know the adapter will manage at least 600Mb. I also did a broadband test on this acer laptop using the UE300 adapter via usb3 and got 600Mb download, knowing that this adapter will perform at least 600Mb. Since my last post, my broadband has been upgraded to 600/40Mb (only mentioned it as my previous tests mentioned it as 200Mb)

I has to read and learn more about iperf. Any previous tests I had run were without -R option, so were upload speeds only. Sorry about that, I had missed that one.

The following tests were run on a Dell d830 running Xubuntu 20.10 with a TPlink UE300 usb ethernet adapter. Since my last posting, I had upgraded it from 20.04 to 20.10

default kernel on 20.10:
kernel 5.8.0-44-generic : download 60 Mb upload 260 Mb

The following kernels downloaded from ubuntu ppa, installed and speed tests run with iperf3 :
kernel 5.3.18    : download 310 Mb upload 260 Mb
kernel 5.4.0    : download 60 Mb upload 260 Mb
kernel 5.10.8    : download 60 Mb upload 260 Mb
kernel 5.10.10    : download 60 Mb upload 260 Mb
kernel 5.10.11    : download 60 Mb upload 260 Mb
kernel 5.10.20    : download 60 Mb upload 260 Mb
kernel 5.11.0    : download 60 Mb upload 260 Mb
kernel 5.11.3    : download 60 Mb upload 260 Mb

compiled kernel from kernel.org broadband speed using speedtest.net. Shall I run this test again using iperf? I will need to recompile this kernel again as I have removed it during a clearup of the kernels I have installed.
kernel 5.10.11 : download 220Mb upload 20Mb

Is there anything else I need to run/test? Is this enough to go on?

Thanks,
Rob

---

### Post by praseodym on 2021-03-07
Haven't read through, but: What hardware is in use? Please show
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
```

---

### Post by Doug S on 2021-03-07
If I understand correctly, then there is nothing left to do. There is already an upstream bug report. The problematic commit is already known. The solution is already known. So, the question becomes why hasn't an upstream patch been submitted correcting the problem?

---

### Post by robdavies on 2021-03-07
Thanks for all your help, I will wait for upstream to fix this.

---

