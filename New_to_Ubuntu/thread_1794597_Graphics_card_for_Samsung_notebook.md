---
title: "Graphics card for Samsung notebook"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by mlempenau on 2011-07-01
I have bought a new Samsung notebook NP-NF208-A02TH.  My graphics for desktop suck.  Youtube is ok.  Jpg pics are not.  ???  

I read another thread and entered what they suggested into a terminal and got:

mike@mikesnotebook:~$ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
mike@mikesnotebook:~$ glxinfo | grep direct
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils
mike@mikesnotebook:~$ sudo apt-get install mesa-utils
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mesa-utils
0 upgraded, 1 newly installed, 0 to remove and 13 not upgraded.
Need to get 27.6 kB of archives.
After this operation, 135 kB of additional disk space will be used.
Get:1 [http://th.archive.ubuntu.com/ubuntu/](http://th.archive.ubuntu.com/ubuntu/) natty/universe mesa-utils i386 8.0.1+git20110129+d8f7d6b-0ubuntu2 [27.6 kB]
Fetched 27.6 kB in 0s (76.8 kB/s)   
Selecting previously deselected package mesa-utils.
(Reading database ... 133696 files and directories currently installed.)
Unpacking mesa-utils (from .../mesa-utils_8.0.1+git20110129+d8f7d6b-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up mesa-utils (8.0.1+git20110129+d8f7d6b-0ubuntu2) ...
mike@mikesnotebook:~$ glxinfo | grep direct
direct rendering: Yes
mike@mikesnotebook:~$ dmesg |grep INTEL
[    0.000000] ACPI: FACP 7f5bfdc8 000F4 (v03 INTEL           06040000 PTL  00000002)
[    0.000000] ACPI: DSDT 7f5b9d3c 05F98 (v01  INTEL BEARG31A 06040000 MSFT 03000001)
mike@mikesnotebook:~$ dmesg |grep INTEL

Is version 2 the latest video driver for the N10 family?  Not sure what the rest means.  Thanks for helping.

---

### Post by OldBoy44 on 2011-07-01
Hi.

I am no expert, but it appears you have Natty which I believe you will find does not support the Intel integrated graphics controller. You could try choosing Classic (no extras) although from memory others have had problems with this too. If you have no joy perhaps you may go back to the last LTS 10.04 OS. Others may have a better solution.

Cheers, :)

---

### Post by beew on 2011-07-01
> **aussiebean said:**
> Hi.

I am no expert, but it appears you have Natty which I believe you will find does not support the Intel integrated graphics controller. 

Cheers, :)

You've got to be kidding me?? LTS10.04 supports it but 11.04 doesn't and they actually release it??? Do you have a source to that? Thank you.

---

### Post by OldBoy44 on 2011-07-01
So sorry - a big blue on my part - I was thinking of Unity.

I feel like a complete fool, :(

( 67 year old fool - I will keep right out of it in future)

Running the following in a terminal will show if Unity is supported or not -

```

/usr/lib/nux/unity_support_test -p

```

---

