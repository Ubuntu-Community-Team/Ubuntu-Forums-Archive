---
title: "ubuntu 12.10.3 + realtek 8111E wifi card connection issues solved!"
date: 2013-12-09
forum: Networking &amp; Wireless
---

### Post by servalboi on 2013-12-09
if you have a realtek 8111E ethernet card and are having really messed up ping issues and or connection issues, here is a howto for you.
granted it's long, but it goes through all the other "fixes" first combining them all into one that should in the end fix the issues

so here's what you will need the 8.037.00 drivers from the realtek website you can get them here
[B][http://tinyurl.com/57n6q4](http://tinyurl.com/57n6q4)

the other thing you will need is time and patience.

so to begin we are gonna drop to root, so open a terminal and type in sudo su <enter>

this will drop you to a root terminal, it's diffrent than the admin terminal that you get with sudo so here's a warning for you new guys out there....
BE VERY CAREFULL!! YOU CAN MESS UP YOUR COMPUTER ALOT IF YOU DO NOT DO EXACTLY AS I SAY!"

now
here's the things to do

1) download the realtek drivers for the 8111E card here> [B][http://tinyurl.com/57n6q4](http://tinyurl.com/57n6q4)
2) open the file and drag it into your home folder
3) in terminal we are going to do the following, disable wireless n


in terminal type:[/B][/B][B][B] rmmod iwlwifi <enter> your internet should croak at this point
if you get the error : ERROR: Module iwlwifi is in use by iwldvm
then first do a "rmmod iwldvm" and that should take care of the issue

so now, you should be without net, don't worry you have this window open so all is fine ^_^
now what you want to do is type this in term:

[/B][/B]echo "options iwlwifi 11n_disable=1" >> /etc/modprobe.d/iwlwifi-disable11n.conf

one of the bugs thats in ubuntu 12.04 is where some computers have issues using wireless N-
you might want to disable wireless -n in your router as well, this may fix your issue, in which case stop here. for you others, continue on.

now that we have taken care of one of the main issues, we are going to go back to that file we downloaded
so in the terminal where you typed "sudo su", go to the file in your home folder that you downloaded hopefully you unpacked it so that it will actually be a folder, well in terminal go to that folder
(i always drag the folder from the archive to my home folder, and in this case rename it "realtek" that way you only have to copy paste the following command : cd /realtek

now lets get what we need.....

"apt-get install build-essential"
<password>

ok so either you already had this package or do not, if you did don't worry it's ok, if you did not, great you got it!


We have to blacklist the old driver (r8169) to prevent the system to be able to  load it. To do this, easily set a new entry in  &#8220;/etc/modprobe.d/blacklist.conf&#8221; which is called: blacklist r8169

we can do this the hardway by going to /etc/modprobe.d/blacklist.conf using gedit....but i hate the hard way so here;   echo &#8220;blacklist r8169&#8243; >> /etc/modprobe.d/blacklist.conf <enter>  put that in your terminal and boom done in once nice line of code, i love linux!

ok so now we should still be in the directory realtek, so in there we are gonna do this
in terminal (you should still have superuser or sudo su mode at this time)

make clean modules <enter>
after a few seconds (depending on your cpu) the driver is done being built on to the next command!

make install <enter>

this will make and install the driver that is needed by your system to function.
(some gibberish will go by at this point please only report errors.)

welcome to your new realtek lan driver! ^_^

we are not done yet though, we have to do a few more commands, in terminal type :

depmod -a <enter>

this will let the system know about the r8168 driver.

now we need to rebuild the kernel module dependancys, so we enter this command:

insmod ./src/r8168.ko

the new driver is now inserted into the kernel.

hold on! we are still not done yet.

we got to make it availible for boot so in termnial put in:

mkinitramfs -o /boot/initrd.img-`uname -r` `uname -r` <enter> (copy everything before the enter tag or it won't work!

now this command is neat beacuse it called on a function called uname to automatically enter the info about your kernel and such.

ok so we want the driver loaded at boot.

so in terminal type :

echo &#8220;r8168&#8243; >> /etc/modules <enter>

we have one more thing to do after this, and this is tricky....i botched it a few times getting it down pat, but ill help you out ^_^

now, this is the important part. so pay attention!

enter the commands as i have them written.

gedit /etc/default/grub <enter>

ok lots of stuff in here but im going to make it easy for you ok? ^_^

first ill give you an example of my grub file, DO NOT USE THIS EXAMPLE IT MIGHT BOTCH YOUR COMPUTER!

================================================================================
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_LINUX_DEFAULT="biosdevname=0"
===============================================================================
now the line we are interested in here is the last one, you won't see it in your grub file becasue it has to be put there to work.

so in that gedit do this
put your cursor at the end of the last GRUB_CMDLINE_LINUX="" line and press return, 
move the cursor WITH THE MOUSE NOT THE BACKSPACE BUTTON to the line above the one you are at now.

in that space you created type:

GRUB_CMDLINE_LINUX_DEFAULT="biosdevname=0"

if you have done it right, it should look like my example.
now save the file and close gedit.

DO NOT REBOOT YET!!!!!!!

we have one last command to enter into the superterminal window

that is:

update-grub

when this finishes, just type reboot and your system will power down
firefox users should leave there browser window open on this page,
when you start firefox after reboot it will bring you back to this page
if you restore session.

if you've done everything right, your pings should look like this:

=================================================================================
.5 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2540 ttl=45 time=41.0 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2541 ttl=45 time=41.2 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2542 ttl=45 time=41.0 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2543 ttl=45 time=40.2 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2544 ttl=45 time=41.0 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2545 ttl=45 time=40.9 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2546 ttl=45 time=41.0 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2547 ttl=45 time=40.6 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2548 ttl=45 time=40.9 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2549 ttl=45 time=40.8 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2550 ttl=45 time=40.7 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2551 ttl=45 time=41.4 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2552 ttl=45 time=40.5 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2553 ttl=45 time=40.6 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2554 ttl=45 time=41.0 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2556 ttl=45 time=40.6 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2557 ttl=45 time=41.1 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2558 ttl=45 time=41.0 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2559 ttl=45 time=41.2 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2560 ttl=45 time=41.0 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2561 ttl=45 time=41.0 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2562 ttl=45 time=40.6 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2563 ttl=45 time=41.0 ms
64 bytes from pc-in-f147.1e100.net (74.125.28.147): icmp_req=2564 ttl=45 time=40.6 ms
================================================================================================

so now you know the fix, i hope it worked for you just as it worked for me.

if you have any questions let me know. ill help! ^_^

---

### Post by chili555 on 2013-12-09
I have a few questions. First, your thread title is ' ubuntu 12.10.3 + realtek 8111E wifi card connection issues solved!' but the 8111E is an ethernet card, not wifi. Second, what does *iwlwif 11n_disable* have to do with Realtek ethernet? I'd estimate that 95% of laptops with Realtek 8111E ethernet have other than an Intel wireless card. Third, if you unload the wireless driver and the ethernet isn't working properly, how are you going to be able to "apt-get install build-essential" <password> ? Next, in order to compile anything, don't you also need to install linux-headers? Finally, I have never seen or heard of the GRUB_CMDLINE_LINUX_DEFAULT="biosdevname=0" step before. Can you please supply a reference?

---

### Post by servalboi on 2013-12-09
uh the instructions are clear, you download the driver and unpack it to your home directory relableing it "realtek" to make things simple or choose a name of your own, you get build essential BEFORE you do anything with that file. at least, thats what i thought i wrote, if not ill correct it.

as for the title, i have been up for WAY too long figureing this out....a day or two straight? hate to put a problem down once i find one lol

basicaly part of the issue with the realtek 8111E cards using the centrino chipset for wifi is there is something wrong in the ubuntu kernel with both of those drivers, the iwlwifi driver is broken in the current kernel, and even more than that, so is the 8111e driver it's a generic catch all driver that is not perfect for every card, and i suspect that is where the high ping comes in, the 8111E driver for realtek is botched as well in the current ubuntu install so replace the generic driver with the one from realteks website.

though, i have a sneaking suspicion that it's really "GRUB_CMDLINE_LINUX_DEFAULT="biosdevname=0"" that does the trick, i have yet to test this, but you may only need to enter that one line into grub and then update-grub and everything might just work peachy keen, as i said i have not tested that idea yet so i do not know if it works, if it does, then ill re write the howto.
at least i should try to rename it, though i cannot figure out how.

i was just trying to help a problem that i along with im sure hundreds of others are having a problem with since ubuntu 12.10 or 13.04. as the issue seems to exist in both versions of ubuntu.

---

### Post by chili555 on 2013-12-10
I still doubt there is any connection whatever between 8111E ethernet and the wireless driver iwlwifi. As well, you have still not provided any reference or documentation regarding the GRUB_CMDLINE_LINUX_DEFAULT="biosdevname=0" step. I therefor suggest that anyone who reads this proceed with extreme caution.> you get build essential BEFORE you do anything with that file. at least, thats what i thought i wrote, if not ill correct it.It is not that your instructions are unclear about getting build-essential before you compile the ethernet driver; it is unclear about how you are going to get build-essential and the needed linux-headers (that you failed to mention) if, as you said:> **so now, you should be without net, don't worry you have this window open so all is fine ^_^**

---

