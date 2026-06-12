---
title: "ndiswrapper"
date: 2005-05-16
forum: Networking &amp; Wireless
---

### Post by astronerd on 2005-05-16
Hi all, 
   I just installed ubuntu for the first time and I am having some problems with ndiswrapper.  I had it working on FC3 with the same driver etc. and now when I try and use it in ubunut I get 
Fatal: Error inserting ndiswrapper(/lib/modules/2.6.10/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): operation not permitted

I dont know what the deal is, I am still pretty much  a noob at linux, esp ubuntu now.  Any help or ideas?  I have used the same instructions that I used for FC3 install, is there something different that I need to do for ubuntu?
Charles

---

### Post by kleeman on 2005-05-16
There is a detailed howto available for Ubuntu which I used today with success:

[http://www.ubuntuforums.org/showthread.php?t=31926](http://www.ubuntuforums.org/showthread.php?t=31926)

---

### Post by astronerd on 2005-05-16
Thanks, I will try it out.... Do you need an active internet connection to use the apt get commands and get the needed files etc used in the guide?

---

### Post by greenwom on 2005-05-16
I'm a newbee to

Did you use the the ndiswrapper package from the repositories.

use synaptic or 

sudo apt-get install ndiswrapper 

I got my WPC11 working with ndiswrapper but I also played with some other stuf I found in the forums.  I recently sent this private message to another fellow nuub.

[COLOR=Navy]Well I'll try to remember everything I did
it took a but once I had it..... sweat

I follwed a couple of different how-tos and eventually got the card to work. To be honest I don't know if what I did in one how to was it or if it was a combo of a couple procedures.
DO NDISWRAPPER first,.

Here's what I have to say about it but there's a lot in the forums to, thats how I did it.

Ok well first thing you have to do is get ndiswrapper installed

sudo apt-get install ndiswrapper-source
sudo apt-get install ndiswrapper-utils

Then get the windows drivers, I'll try to email the ZIP to you.

There are a few driver files in the package you will only need one, each driver is used for different hardware.
I use the 'lsrtnds' file. You will read in the forums that other use differnt, you may just want to play with it.

To install the driver
ndiswrapper -i drivername.inf

you can test the driver with
ndiswrapper -l

That command will tell you if the driver is present and if it found the hardware

If the .inf driver doesn't work remove it with
ndiswrapper -e drivername.inf

[http://www.ubuntulinux.org/wiki/Ori...term=kismetThis](http://www.ubuntulinux.org/wiki/Ori...term=kismetThis) is the WIKI I followed

This is one of the threads I wrote in
[http://ubuntuforums.org/showthread....t=linksys+wpc11](http://ubuntuforums.org/showthread....t=linksys+wpc11)[/COLOR]

---

### Post by somuchfortheafter on 2005-05-16
unless your only source listed in your /etc/apt/sources.list file is your cd rom drive you will indeed need an active internet connection.

---

### Post by astronerd on 2005-05-16
Sorry guys, few problems/questions....
    So when I did the sudo make command in the ndiswrapper folder I got this error....
 " Cant find kernel sources in /lib/mod/2.6.10/build   give the path to kernel sources with KSRC=<path> argument to make "
I have no idea what that means or what to do.  I looked in the package management and it said that the kernel headers were installed, are these the same or am I missing something?  
2) When I did "sudo apt-get ...."  anything, I get
     Reading package list......Done
     Building dependency tree...... Done
     E: Couldnt find package blahblah
What's the deal?  In my /etc/apt/source file I only had my Cd-rom listed, do I need to put in the ubuntu cd to get that to work?  Sorry if this seems really really dumb, I am just very new to all of this and I dont really know what means what yet....  
  3)  In the tutorial/faq that was linked earlier in this thread, the author says to delete the previous ndiswrapper and install the new one.  Is this necessary or can I just install the new one once I get all this other mess sorted out?  
Thanks in advance!
Charles

---

### Post by kleeman on 2005-05-17
First, if you are using Ubuntu/Debian in a serious fashion you should familiarize yourself with how apt-get works. Info here: [http://ubuntuguide.org/](http://ubuntuguide.org/)
Second, it sounds like you need the kernel-source package installed. Use synaptic to find it and install it (after you set up /etc/apt/sources.list properly - see above link).
One wrinkle is you need to decompress the source when it is installed: cd to /usr/src
and issue sudo tar jxvf linux-source-2.6.10.tar.bz2  (if your using hoary) followed by

sudo ln -s linux-source-2.6.10 linux

About cleaning up, I'm not sure but I guess the howto author is speaking from experience.....

---

### Post by astronerd on 2005-05-17
Is there any way I can get the kernel source package without an internet connection?  I cant get online at all from ubuntu, but I can from my windows side.... Is the kernel source package on the install cd, or is it only in a repo?

---

### Post by kleeman on 2005-05-17
I doubt that it is on the cd. Download it in windows and read it from the windows ntfs filesystem (find out where in /etc/fstab). It may be easier to get an ethernet cable and plug it into a router somewhere because ubuntu is MUCH easier with an internet connection.

---

### Post by astronerd on 2005-05-17
So I got the [http://archive.ubuntu.com/ubuntu/pool/universe/k/kernel-source-2.6.10/kernel-source-2.6.10_2.6.10-6_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/k/kernel-source-2.6.10/kernel-source-2.6.10_2.6.10-6_all.deb)  package and uncompressed it in /usr/src but I still get the same error when I try to "sudo make" in ndiswrapper.  It tells me that "cant find kernel sources in /lib/mod/2.6.10/build  give the path to kernel sources with KSRC=<path> " 

I dont know what else it could be, do I need to add a link somewhere?...

---

### Post by NoTiG on 2005-05-17
[QUOTE=astronerd]Hi all, 
   I just installed ubuntu for the first time and I am having some problems with ndiswrapper.  I had it working on FC3 with the same driver etc. and now when I try and use it in ubunut I get 
Fatal: Error inserting ndiswrapper(/lib/modules/2.6.10/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): operation not permitted

I dont know what the deal is, I am still pretty much  a noob at linux, esp ubuntu now.  Any help or ideas?  I have used the same instructions that I used for FC3 install, is there something different that I need to do for ubuntu?
Charles[/QUOTE]

I believe that means you have linux-headers-2.6.10-5 installed.. but you do not have the linux-headers-2.6.10-5-386 ... or linux-headers-2.6.10-5-amd64-generic . you have to get both headers... open synaptic and search for linux-headers. DL the ones for your particular architecture.. and it will automatically dl the other one as well. THey ARE on the install CD.

---

### Post by NoTiG on 2005-05-17
[QUOTE=astronerd]So I got the [http://archive.ubuntu.com/ubuntu/pool/universe/k/kernel-source-2.6.10/kernel-source-2.6.10_2.6.10-6_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/k/kernel-source-2.6.10/kernel-source-2.6.10_2.6.10-6_all.deb)  package and uncompressed it in /usr/src but I still get the same error when I try to "sudo make" in ndiswrapper.  It tells me that "cant find kernel sources in /lib/mod/2.6.10/build  give the path to kernel sources with KSRC=<path> " 

I dont know what else it could be, do I need to add a link somewhere?...[/QUOTE]


TO astro : you have to make a symbolic link called build in the /lib/modules/2.6.10-5*/ directory, to your linux-headers whcih are in /usr/src . to do this type:

sudo ln -s /usr/src/linux-headers-2.6.10-5 /lib/modules/2.6.10-5-386/build

NOTE: if your using 64 bit its not 386 obviously so substitute.

---

### Post by astronerd on 2005-05-17
[QUOTE=NoTiG]TO astro : you have to make a symbolic link called build in the /lib/modules/2.6.10-5*/ directory, to your linux-headers whcih are in /usr/src . to do this type:

sudo ln -s /usr/src/linux-headers-2.6.10-5 /lib/modules/2.6.10-5-386/build

NOTE: if your using 64 bit its not 386 obviously so substitute.[/QUOTE]
 Thanks so much guys!  Got it working now, am posting this from Ubuntu!  Thanks again for all the help.
Charles

---

### Post by kleeman on 2005-05-17
Well done!

---

### Post by greenwom on 2005-05-18
Feels good when you get it working for the first time :)

---

