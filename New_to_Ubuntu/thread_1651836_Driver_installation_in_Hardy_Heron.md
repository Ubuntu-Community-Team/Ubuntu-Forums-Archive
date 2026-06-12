---
title: "Driver installation in Hardy Heron"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by grey1beard on 2010-12-23
I'm running 8.04/emc2 on an old Compaq Ipaq desktop and have successfully had it working in a wired LAN, but now need to run it wirelessly.
I have a TL-WN321G wireless dongle, and have downloaded a driver for it, which now resides, unpacked in a folder in my home directory.

What are the commands I need to type into a terminal window to install the driver ?

I've searched for any general instructions for installing drivers, but cannot find any. Perhaps someone could either give me specific instructions for this case, or what I think would be even more useful, a general case example, with an explanation of what each step does.

The alternative would be a link to a site that does so, but that I haven't been able to find.

MITA,
John

---

### Post by gordintoronto on 2010-12-23
You're using Windows thinking -- and that might be relevant as a last resort.

Try plugging in the wireless dongle with the power off, and start your system. It should "just work." If not, you should Google ndiswrapper.

Did you download a Windows driver?

If it "just works," you can find videos on youtube about connecting to a wireless router.

---

### Post by beew on 2010-12-24
I think 8.04 is dead, you can no longer get updates or install anything from the repositories. So why even bother? Should upgrade to 10.04 or 10.10 if I were you.

---

### Post by Rabhak on 2010-12-24
Beew's right. You should upgrade to a higher version... it's year 2011 dude!

---

### Post by grey1beard on 2010-12-24
Gordintoroto - No, I don't think Windows anymore.
Having plugged another identical dongle into my desktop system, running 10.10, and as you said, having just run out of the box, I was hoping for the same.
I had checked by reading the appropriate pages in the ubuntu/hardware supported documentation, where it gives "out of the box" for 8.04 with the RT73 driver.

All I'm asking for is a general procedure for installing a downloaded driver, if that's not too much to ask for.

I'm afraid, beew and Rabhak, you might think about why 8.04 and EMC2 are coupled together in my first post.
If you had any experience of EMC2, you might understand the issues that go with running a cnc machine.
Upgrading is _not_ the answer to every problem.

---

### Post by drpjkurian on 2010-12-24
Hi
To understand the basic methods to install the drivers, please follow my [blog]("http://ubuntucrack.blogspot.com/2010/07/how-to-install-targz-file-in-ubuntu.html"). and let me know if you need any help to build the driver from scratch, provided you have the appropriate driver for the wireless...

---

### Post by Sidewinder1 on 2010-12-24
> **beew said:**
> I think 8.04 is dead, you can no longer get updates or install anything from the repositories. So why even bother? Should upgrade to 10.04 or 10.10 if I were you.
8.04's end of life is not until April 2011; updates and all should work fine until then. 

Side

---

### Post by grey1beard on 2010-12-24
Good day Dr. Kurian, and thank you.
I've downloaded the original driver recomended by the manufacturers, (200912314051713.zip), and that unpacks into my home folder with the title /Driver for TL-WN321G in Linux/.
It contained two files, "module" and "WPA_Supplicant", and both contain readme files.
For an elderly newbie, the contents of these were extremely daunting, and I assumed from what little experience I have, that some command along the lines of "make" and "install" would carry out the compilation for me.
This was the reason for my original request for a general how-to for driver installation.
If a generalized approach didn't work, then I would come back for more help.
Regards
John

---

### Post by gordintoronto on 2010-12-24
The generalized approach includes using "make" and "make install." However, the specifics depend on the individual program or driver. You will need to install "build-essential" (using Synaptic, for example) before "make" will work.

You will need to know how to move around using ls and cd, just like back in the MS-DOS days. This is the price for using an old version of the OS.

---

### Post by grey1beard on 2010-12-25
No problems there Gordintoronto, I've been using 10.10 since it came out, and 8.04 for a year, so terminal in not unknown to me.
My problem is that unless I'm using it continually, I forget a series of steps, and I don't have any notes or can find a link that will lay out the process of driver installation.
John

---

### Post by grey1beard on 2010-12-26
Well, I've spent most of the day trying to find help by reading many other people's cries for help, and only found it all very confusing.:confused:

**Resume**
Googling my own wifi usb shows a link to a driver, which the community documentation says will work "out-of-the-box in 8.04.
(It certainly did in 10.10 on another system)

I have the unpacked zip folder on the desktop, and this contains two folders - Module and WPA Supplicant.
Opening the read me file in module (which contains no inf file) lists build instructions, and I can't even perform the first line - what does the string x.x.x.x indicate ?

=======================================================================

Build Instructions:  

====================

1> $tar -xvzf RT73_Linux_STA_Drv_x.x.x.x.tar.gz

    go to "./RT73_Linux_STA_Drv_x.x.x.x/Module" directory.

    

Many thanks if you can get me past this first hurdle.
John

Afterthought
The driver label on the download site is 200912314051713.zip, and the folder name when extracted onto the desktop is "Driver for TL-WN321G in Linux"

---

### Post by grey1beard on 2010-12-27
[B]
1> $tar -xvzf RT73_Linux_STA_Drv_x.x.x.x.tar.gz
    go to "./RT73_Linux_STA_Drv_x.x.x.x/Module" directory.
[/B]
    
Well I managed to jump that hurdle by renaming the extracted folder to "Driver", and typed **cd Driver/Module**.


[B]2> $cp Makefile.4  ./Makefile       # [kernel 2.4]
    or
   $cp Makefile.6  ./Makefile       # [kernel 2.6][/B]
No problem here as I'm using Kernel 2.6
   

[B]3> [kernel 2.4]
    $chmod 755 Configure
    $make config         # config build linux os version[/B]

Now what ? No mention of Kernel 2.6 !!!
Do I ignore 3> and jump to 4>, or ignore only the first line and type make config ?
(I understand the 755, but do I not need to do it if I'm using 2.6 ?)
Help please.


[B]4> $make all            # compile driver source code

4.1> $make install

5> $cp rt73.bin /etc/Wireless/RT73STA/	    # copy firmware
6>  $dos2unix rt73sta.dat
    $cp rt73sta.dat  /etc/Wireless/RT73STA/rt73sta.dat       
    # !!!check if it is a binary file before loading !!!  
7> $load                
    #[kernel 2.4]
    #    $/sbin/insmod rt73.o
    #    $/sbin/ifconfig rausb0 inet YOUR_IP up
    #[kernel 2.6]
    #    $/sbin/insmod rt73.ko
    #    $/sbin/ifconfig rausb0 inet YOUR_IP up
[/B]

I'll need more help further down, but one thing at a time is good.:D
John

---

### Post by grey1beard on 2010-12-27
OK, I've used both lines of 3>, and it now reads
[B]Ralink RT73 Station Configuration
Linux kernel source directory [/usr/src/linux-2.6.24-16-rtai]:[/B]

As the flashing cursor has not changed for 3 mins, I typed **make all**
and the following errors appeared -

[B]./Configure : line 82: [:make: binary operator expected
Linux kernel source directory : make all[/B]

followed by several lines "can't read....", finishing with

[B]expr : syntax error
./.Configure: line 104: [: -lt: unary operator expected
Module install directory : /lib/modules/2.6.24-16-rtai/kernel/drivers/net[/B]

and has now given me the first line of my command line where I typed "make config"

OK, slapped wrists accepted.
1. What have I done wrong ?
2. Do I need to delete anything/start again ?
3. What to do now ?

---

### Post by grey1beard on 2010-12-28
I've gone back to the Make config line as in post #13 and  am left with 

[B].............Ralink RT73 Station Configuration.............
Linux kernel source directory [/usr/src/linux-2.6.24-16-rtai]:[/B]

and with a flashing cursor at the end of the line.
I've left this for 20 mins without any sign of it doing anything.
How long does it take ?
I would expect it to show some activity, ie lines of code, then finish with a line that looks like [B]userL#/Desktop/driver/Module$
[/B]
Any advise ?
John

EDIT 1hour 20mins - no change

---

### Post by grey1beard on 2010-12-28
Decided to move on as there have been no responses, so I hit the enter key and got the following -
[B]Linux source tree '/usr/src/linux-2.6.24-16-rtai' is incomplete or missing !
Configuration failed
make *** [config] Error 1
user:~/Desktop/driver/Module$[/B]

Could anyone out there translate the above for me ?
John

---

### Post by grey1beard on 2010-12-28
Next step is to find the rtai package.
I've searched my file system(show hidden files as well) but not present.
I've googled for the rtai.org site but I can't find a package with the label
**linux-2.6.24-16-rtai**

I'd be grateful for a lead.

John

---

### Post by grey1beard on 2010-12-28
I've just found a file config-2.624-16-rtai in the boot folder, and the first commented lines are
> #Automatically generated make config: don't edit
#Linux kernel version: 2.6-24-16-rtai
#Sat Apr 12 20:56:09 2008

Is this a clue ?
If so, what use can I make of it ?

John

---

### Post by NFblaze on 2010-12-28
I dont have this USB, and I dont know exactly what's going on in your situation. Though, I've seen this question before and someone had created a deb file for this driver. So here is the link to that file
[http://ubuntuforums.org/showpost.php?p=10110342&postcount=16](http://ubuntuforums.org/showpost.php?p=10110342&postcount=16)

Try it out and I hope you have success.

---

### Post by grey1beard on 2010-12-28
Thanks NFblaze, I'll add it to my "things to try" list.
I'm trying to install a tk-link usb stick in an 8.04 system, on which it is supposed to work OOTB, but I'm having trouble installing the RT73 driver.
One thing I have spotted is that RALink used several chipsets, which may go some way to explaining the difficulties.
When I tried my other identical stick on my 10.10 desktop, it did work instantly, with no help from me at all !
Regards
John

---

### Post by NFblaze on 2010-12-29
Perhaps the drivers are already compiled in a later kernel. You might be able to upgrade to a later kernel and no longer need to compile them.

---

### Post by grey1beard on 2010-12-29
> **NFblaze said:**
> Perhaps the drivers are already compiled in a later kernel. You might be able to upgrade to a later kernel and no longer need to compile them.

Still being a newbie, I can't tell my kernel from my elbow, so would this be a case of "suck it and see" ? 
As I mentioned in an earlier post, this is a new install, so if it goes pear shaped I'm not losing much more than time.

John

---

### Post by grey1beard on 2010-12-29
I've just searched my 10.10 system for "RT73" and  found two folders that are dated to when I first mounted the TK-Link dongle in 10.10 that I'm trying to install in my 8.04 system.
They are 

[B]rt73usb.ko  /lib/modules/2.6.35-24-generic/kernel/drivers/net/wireless/rt2x00.........object code
rt73usb.h  /urc/src/linux-headers-2.6.35-24-generic/include/config ................C header[/B]

Are these files the sort of thing you had in mind ?
Would they be sufficient to create the driver if I copied them over to the appropriate places in my 8.04 system, or is there some other method I should follow ?

John
EDIT There is also a file rt73.bin  /lib/firmware that I guess is part of the package.

---

### Post by NFblaze on 2010-12-29
I can say explicitly if those files are enough to carry on. Though, my experience with trying to fix my broadcom drivers told me that the *.ko* filenames are normally the drivers/modules you'll need to load using *insmod* or modprobe so that the kernel recognizes the drivers. 

Though, upon googling your specific drivers apparently alot of resources say that you are suppose to blacklist **rt73usb.ko** and use **rt73.ko** along with that firmware you've found.


EDIT: Actually, I was just reading that the modules wont work across different kernel versions depending on how the kernel was compiled. So, the following block of text may not work for you.

Though, if your 10.10 installation is working fine without it being blacklisted (what does your **/etc/modules/blacklist.conf** file say). I would say go ahead and copy those files into the respective correct folders on your 8.04 install directory.

Then open a terminal and try to
*modprobe rt73usb*

---

### Post by grey1beard on 2010-12-29
> what does your /etc/modules/blacklist.conf file say

I don't have a modules folder in /etc !
John

EDIT
I've copied the files across to my other system via a usb stick to the desktop.
I then tried to use copy/paste to get them into their respective folders using the file browser, but it doesn't work - paste is greyed out.
Am I not doing it correctly ?
John

---

### Post by gordintoronto on 2010-12-29
> **grey1beard said:**
> I'm afraid, beew and Rabhak, you might think about why 8.04 and EMC2 are coupled together in my first post.
If you had any experience of EMC2, you might understand the issues that go with running a cnc machine.
Upgrading is _not_ the answer to every problem.

Puzzling. When I go to the EMC web site, one of the things that pops out at me is: "The EMC2 team has a custom Live-CD (EU mirror) based on Ubuntu 10.04 with emc 2.4.x included, that will let you try out EMC2 before installing, and it's also the easiest way to install Ubuntu and EMC2 together."

---

### Post by grey1beard on 2010-12-29
Many of the users of EMC2, myself included, have found that there are major latency issues with some hardware when upgrading to 10.04.
In my case, a latency of 9000 microseconds(?) changes to 150000 after switching, which makes using it(10.04) out of the question. It creates the possibility of loss of position and worse, when trying to run a cnc program.

I can, and have run the cnc mchine successfully in 8.04, and all I'm trying to do is to get a wireless connection to the internet out in the workshop. My pc doesn't have an expansion slot for a card, so I can only use usb.
If I put the router in the workshop with a wired conection to the cnc, my systems in the front of the house can't pick up the signal from the router.

Yes, I could probably find another way by spending more money, but the TK-WN321G is said in the ubuntu docs to work out of the box with the RT73 driver in 8.04.
I just can't get there.
John

---

### Post by gordintoronto on 2010-12-29
> **grey1beard said:**
> In my case, a latency of 9000 microseconds(?) changes to 150000 after switching, which makes using it(10.04) out of the question. It creates the possibility of loss of position and worse, when trying to run a cnc program.


I have read of something called a "real time kernel." Perhaps it would help with latency.

150,000 microseconds of latency is outrageous!  Back in the Commodore PET days, I tweaked "the kernel" to drop the maximum delay in servicing an interrupt to 100 microseconds, from 1/600 of a second. My current computer is around 1,000 times as fast as the CPU in the PET...

---

### Post by grey1beard on 2010-12-30
I may be mistaken - it might be nanoseconds :) but it's a change of that order.
I think a real time kernel is involved, but I'm geting into deep water there.
John

---

### Post by grey1beard on 2011-01-02
The New Year has started, but this problem is stuck.

I have tried following the Module/readme instructions in the manufacturers driver folder(see #11 - #16) but have not got further with that installation in my 8.04 system, but this might be the best option.

I've tried installing the windows driver via system/admin/windows wireless drivers/add new driver, but this rejects rt73.inf as an invalid driver.

I've tried copy/paste to install drivers from my 10.10 installation back to my 8.04, but that route is greyed out when I try.(#24)

If anyone out there has any advice to offer, or best of all has actually installed this usb into 8.04, I should be very glad to hear from them.

On 28.02.2009, mekk4996 posted an update to the Ubuntu doc/community documentation/hardware support page that the TL-WN321G "worked out of the box" in 8.04,8.10,9.04.
I wonder how he/she managed to do that, i.e. actually load the driver ?

John

---

### Post by grey1beard on 2011-01-03
OK, so some progress.

I used the method in New RT73 Wireless Driver Installer Script by zszafran  [http://ubuntuforums.org/showthread.php?t=848445](http://ubuntuforums.org/showthread.php?t=848445)

This has got the driver installed and trying to make a connection.

So far however, I can't get it to connect, but that may just be down to my not setting the properties correctly.
Anyway, I'm posting this as solved, as my last step is a separate issue, and I may need to stat a new thread ;)

John

---

