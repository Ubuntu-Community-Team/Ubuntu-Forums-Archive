---
title: "Howto auto-load nvnet for eth0????"
date: 2005-11-04
forum: Networking &amp; Wireless
---

### Post by fourhead on 2005-11-04
I had issues with the forcedeth driver on a fileserver running Ubuntu, so I pulled the propietary NVidia drivers and installed them without any problems (okay, I had to downgrade gcc first ;-) ). The module loads fine and speeds up networking a lot. But - how do I tell Ubuntu to use this driver automatically, just in the case that the server ever has to be rebooted? I put 'nvnet' into '/etc/modules', and it gets loaded during bootup, but forcedeth also gets loaded and the latter one is the one being used by eth0, unfortunately.

I was told to create a file '/etc/modules.d/nforce' and put 'alias eth0 nvnet' into it, which didn't help. Then I was told to put 'forcedeth' to '/etc/hotplug/blacklist' which makes sense, but which also didn't help. Still, both nvnet and forcedeth are loaded, and forcedeth is being used. I was also told to put 'nvnet' into '/etc/module.d/aliases' - which also didn't help.

Finally - and now it gets real strange - I did 'mv /lib/modules/<actualkernel>/kernel/drivers/net/forcedeth.ko /home/admin/' - but it STILL loaded after the next reboot!?!? Isn't that magic?

Does anybody know how I can tell Ubuntu to use nvnet and get rid of forcedeth?


Tom

---

### Post by mo_x on 2005-11-04
The steps you took should be sufficient:
- add forcedeth to /etc/hotlpug/blacklist
- create a file (nforce) in /etc/modprobe.d with contents "alias eth0 nvnet"

Try to find out why forcedeth still gets loaded, maybe a typo somewhere.

---

### Post by fourhead on 2005-11-05
Hi, thanks for your answer. Okay I've triple-checked for any typos, and there are no typos, but after a reboot both nvnet and forcedeth are loaded, and forcedeth is being used. Where else could there be an entry for forcedeth? In /etc/network/interfaces there's an entry like "auto eth0" or "eth0 auto", may that have to do with my problem?


Tom

---

### Post by mo_x on 2005-11-05
Computers don't do magic only humans do :D
I guess the "auto eth0" means that eth0 is started at boot and not by hotplug.
Did you remove the forcedeth.ko for the correct kernel version? Check whith "uname -r".
Try the following to find why forcedeth gets loaded:
```
cd /etc
sudo grep -r forcedeth *
```

---

### Post by fourhead on 2005-11-05
Okay grepping /etc showed that the only occurence of 'forcedeth' is in /etc/hotplug/blacklist - how surprising ;-). I have only ONE kernel version installed, so I can't do much wrong here. I've moved forcedeth.ko out of the /lib dir into my home dir, rebooted, and forcedeth is STILL loaded as shown by lsmod, and it's still used by eth0, showed by the slow transfer rates. So obviously, my computer IS doing magic ;-)

I've searched the whole harddisk, all directories for forcedeth*, and this file is nowhere except in my home directory, where I just moved it. Btw. I'm using Ubuntu 5.10, kernel 2.6.12-9-amd64-generic.

Any ideas? 


Tom

---

### Post by mo_x on 2005-11-05
I have no answer to magic :???: 
Maybe you can disable the network starting at boot time and see if the module is still loaded.

---

### Post by fourhead on 2005-11-05
Yes I might try this, but right now I helped myself with a little script which brings eth0 down, unloads both modules, loads nvnet and brings eth0 up again. Dirty, but it works. There's even more magic: This script even works when I call it remotely from a SSH client (putty), and the connection doesn't get lost, although I bring eth down and up again with a new driver. Wow. Is there a file in Ubuntu to put scripts that should be started after bootup (after the init scripts)? On Gentoo there was something like /etc/local.start or so.


Tom

---

### Post by ThiAm on 2005-11-29
Hi,

Happy to see that I am not the only one with this problem ;) 
I have been through the same steps as you on my Ubuntu 6.10 client with an Nvidia ethernet card... Grep forcedeth on the whole filesystem, commenting it everywhere it would be loaded, putting it on blacklist... without success and wondering why it keeps loading... :confused:  Finally I implemented the same dirty solution as you did:

sudo modprobe -r forcedeth
sudo modprobe -r nvnet
sudo modprobe nvnet

... and it works... but needs to re-do it after reboot...

Annoying for me is that my computer hangs about 30" at each reboot looking for the network... Without success because using forcedeth at that time...

FYI. I upgraded to Nvnet 1.0-0310 available on Nvidia site since last week...

---

### Post by mo_x on 2005-11-29
I still is a strange problem:confused: 
You could create an init script that runs before the network is started.

---

### Post by ThiAm on 2005-11-29
Hum... Not sure how I should do that... I have just been starting using with Linux for the last three weeks... Could you tell me how to do this ?

---

### Post by jonny on 2005-12-01
I have exactly the same problem.  Does anyone know how to run this script on startup or how to stop forcedeth from loading?

---

### Post by mo_x on 2005-12-01
You have to create a script in the /etc/init.d directory for example
```
sudo gedit /etc/init.d/nvnet
```
Put the following text in it and save the file
```
#!/bin/sh

modprobe -r forcedeth
modprobe -r nvnet
modprobe nvnet

```
Now make it executable
```
sudo chmod ugo+x /etc/init.d/nvnet
```
Finally make a symbolic link so the script gets run at startup
```
sudo ln -s /etc/init.d/nvnet /etc/rcS.d/S38nvnet
```
The numer 38 decides when the script is run, I think 38 is just before networking is started but you may have to check the /etc/rcS.d directory an maybe change that.
I assume that forcedeth is loaded before that. I still wonder why it gets loaded.

---

### Post by jonny on 2005-12-01
mo_x, that wasn't quite right but it was close enough for me to get there.  Thanks - the forum is littered with dead end threads on this topic and you're the only person who gave a sensible suggestion.

For anyone else who's struggling, use this script instead of the one mo_x suggests```

#!/bin/sh

rmmod forcedeth
modprobe -r nvnet
modprobe nvnet
```I found that forcedeth is so stubborn that it refuses to depart with a simple modprobe -r

Also, S38 isn't the right spot.  I needed to rename the script so that it runs after hotplug but before the network gets configured.  I used this line instead:
```
sudo ln -s /etc/init.d/nvnet /etc/rcS.d/S40hz_nvnet
```
All is now sweet - I can free up my PCI slot for some more interesting hardware than a network card.

---

### Post by mo_x on 2005-12-02
Good to see you got it working. I didn't test it myself, forcedeth is doing fine for me :-)
From your post I get the opinion that the forcedeth gets loaded by hotplug. Might be interesting to know why. Did you blacklist it correctly?

---

### Post by jonny on 2005-12-03
I concluded that hotplug is loading forcedeth, too.  It's strange - I am confident that I blacklisted it correctly, and I'm not alone in having this problem.

At least it works now.  I guess that I really should do the public spirited thing and write a how-to.

---

### Post by Gerrath on 2005-12-09
All,
Could the forcedeth module be being loaded in the kernel init-ramdisk (initrd.img-2.6.12-10-686)?  Uhm, I will try to remove the ramdisk tonight and see if it fixes the issue.
Regards,
Gerrath

---

### Post by neurosis on 2006-02-10
I'm having major forcedeth problems as well (in an SSH session, when a command outputs too much, the entire session freezes - ACK). I'm not in front of the computer, but was researching switching to nvnet, and came across the suggestion that in /etc/modules.conf (or somewhere appropriate, /etc/modules.d/nforce -- again, not in front of the right computer :) ) you put:

alias eth0 nvnet
alias forcedeth off


This was in the nForce Release Notes (/usr/share/doc/nforce).

---

### Post by hary_tp on 2006-02-12
hello i'm having the same problem but I have 2 NICs nv and 3c59x they both didn't load. I've used the script you made. managed the 3c59x its ok. don't need nvnet. Sorry for my english

---

### Post by raphha on 2006-02-15
Hi,

I also have problems with the forcedeth driver... did you managed to get it up and running?

'bout your problem: the module is loaded from the initrd *bootloader-magic* :)

I read about a way to prevent it being loaded: add a file to your /etc/moprobe.d/ directory called (e.g., name not important) forcedeth and add a line: "install forcedeth /bin/true". This will tell the kernel "when you want to load f. just exit with success and do nothing"

does that explain it?
I'd be happy to hear about your experiences with the nvnet module...
regards,
raph

---

### Post by neurosis on 2006-02-15
Turns out my problem was hardware related. Swapped the board out for a new one and forcedeth and nvnet both work. However.. both of them are getting loaded at boot time for some reason - but the card is binding to forcedeth.

---

### Post by rysiek on 2006-03-19
Yep, the module is being loaded by *bootloader-magic*, before any module-loading scripts start at all. Now, anyone could *please*:
1. explain, WTF is *bootloader-magic*? ;)
2. find a way to disable the loading of a certain module (like e.g. forcedeth)

Thx in advance

---

### Post by raphha on 2006-03-19
[QUOTE=rysiek]
1. explain, WTF is *bootloader-magic*? ;)
2. find a way to disable the loading of a certain module (like e.g. forcedeth)
[/QUOTE]

Hello...
well, being a little smarter than I was a while ago, I have to apologise for notcomming back here to share my "findings" :) but now here they are:

1. *bootloader-magic* was just a joke... the module is loaded from the initial ramdisk ("initrd"). Now what's that? When the computer is powered on, after some initial test done by the BIOS, it loads the bootloader (normally grub). Grub then loads the kernel and the initial ramdisk. the initial ramdisk contains files and directories which are loaded into memory (hence the name), because the first storage thing the kernel can access (before even knowing about hard disks and the like) is the main memory. Now from that initial ramdisk, drivers are loaded and scrips started. It's from there where the forcedeth driver comes from! You can check what is in your initial ramdisk as follows (as a normal user):
a) copy the initial ramdisk to a temporary directory:
   # mkdir /tmp/initramdisk
b) copy the initrd of your running kernel into that directory
   # cp /boot/initrd.img-`uname -r` /tmp/initramdisk
c) change to that directory
   # cd /tmp/initramdisk
d) extract the image
   # cat initrd.img-`uname -r` | gunzip | cpio -i
now you should see the contents as normal files and directories, amongst them the forcedeth module...

2.  to disable the module, do the following things:
a) become superuser
b) add a file "nvnet" to /etc/modprobe.d/, containing
   alias forcedeth = off
   alias eth0 nvnet
c) recreate your initrd:
   # mv /boot/initrd.img-`uname -r` "/boot/initrd.img-`uname -r`_old"
   # update-initramfs -c -k `uname -r`
d) reboot   
   

This should work, but I can't check it right now, because I don't have access to the machine I installed the nvnet driver on, just try and tell us about your results!

best regards,
raph

PS: While I did my best to provide only harmless and correct instructions, I can't guarantee for that, so use all information at your own risk...

---

### Post by rysiek on 2006-03-19
not knowing what *bootloader-magic* was was just a way of making you tell everybody about it the way it should be told - I knew what it was (I've mangled with initrd's some time ago when some module didn't want to get loaded), but I did not know how to explain it nicely. thanks for this one! :)

although what I didn't know was how to get forcedeth *not* loading - and here came you and solved the case - thanks again. :)

as always, there are "buts":

1. the /etc/modprobe.d/nvnet file (actually, the name of the file does not matter at all, AFAIK, it just has to be in /etc/modprobe.d/) should contain:
```
alias forcedeth off
alias eth0 nvnet
```
(without the "=")

2. I prefer to do the re-creation of initrd the (K)Ubuntu way:
```
sudo dpkg-reconfigure linux-image-`uname -r`
```
(backuping the original initrd is, off course, always recommended ;) )

and WHOA!! here I am on my nvnet-driven-network-interface writing thison the forum - thanks for the third time, Raphha!

(maybe you should write a wiki entry for this one - or, if I find some time, I can do it. but the credits will all be yours anyway ;) )

Cheers
rysiek

---

### Post by raphha on 2006-03-19
hi rysiek,

the comment on the magic-thing was just to be sure it's clear...
about the buts... you are right, filename doesn't matter, and the alias lines won't work with the "=" sign (always a bad idea to write about sth without testing it...)
and I wasn't sure if the dpkg-reconfigure would work, now I have learned sth too :)
I don't have much time at present, but I plan to write a HowTo on the full server setup (setting up nvnet happend to be part of it) with raid(boot) lvm, samba file server and fetchmail-exim-spamassassin-clamav-courierIMAP, but well, this may take a while, so feel free to write a wiki about the driver and don't worry about credits - if you write the wiki entry, it's your contribution (the things I wrote here are just the summary of what I found in different places ;) )
so long,
raph

---

### Post by rysiek on 2006-03-20
Well, we got ourselves a Wiki entry:
[https://wiki.ubuntu.com/NvNetInstallationHowTo](https://wiki.ubuntu.com/NvNetInstallationHowTo)
\\:D/ 

and as I said, I have included you in the credits, Raphha. now just don't say I didn't warn you. ;)


oh, BTW: please read it and correct it, I'm quite new to creating wiki pages. thanks. :)

Cheers
rysiek

---

### Post by mo_x on 2006-03-22
The howto looks good. Maybe you need to add that you need the build-essential package and gcc-3.4 for breezy.

---

### Post by raphha on 2006-03-22
Hi mo_x, thanks for the hint, I thought about it the other day, but was to lazy to make the changes :rolleyes:, now it's included.
But well, feel free to add your comment and hints directly in the wiki, that's why it's a wiki  ;) 

so long, raphha

@rysiek: couldn't withstand the temptation to add your name at the bottom :-D , after all, I wouldn't have started the HowTo, but I think it was a great idea.

---

### Post by rysiek on 2006-03-22
ahh, well, if you insist. ;)

Cheers, and thanks again for the help, guys.
rysiek

---

### Post by throbi on 2006-04-08
Hello guys!

I've found this topic and the WIKI really helpful. I have the same problem with forcedeth but I'm unable to install the nvnet. I followed the HOWTO described in the WIKI, the module nvnet.ko is generated but test fails with the message:

> [FONT="Courier New"]ERROR: Unable to load the kernel module 'nvnet.ko'.  This is most likely
       because the kernel module was built using the wrong kernel source files.
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.[/FONT]


The install log contains this message, too:

> [FONT="Courier New"] Kernel module load error: FATAL: Error inserting nvnet
   (/lib/modules/2.6.12-10-386/kernel/drivers/net/nvnet.ko): Invalid module
   format
[/FONT]

I have checked, the right kernel source (2.6.12-10-386) is used. However, I still have my old tree for 2.6.12-9-386 under /lib/modules, but it seems to be harmless.

I also ignored the following warning: 

> [FONT="Courier New"] You appear to be compiling the NVIDIA kernel module with a different compile
   r than the one that was used to compile the running kernel.  This may be fin
   e, but there are cases where this can lead to instability.  The compiler use
   d to compile the kernel was gcc 3.4; the current compiler is gcc 4.0.

   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: No)[/FONT]

What did I do wrong?

---

### Post by raphha on 2006-04-08
Hi throbi,
actually, very often ignoring error messages leads to problems and your case is no exception :p
The solution is to use the gcc 3.4 to compile the nvidia module. HowTo? As follows:

```
# cd /usr/bin
# sudo mv gcc gcc_backup
# sudo ln -s gcc gcc-3.4
```
Now compile the modules you want to compile, after that do
```
# cd /usr/bin
# sudo mv gcc_backup gcc
```
or skip the last 2 steps to always use gcc-3.4 when invoking the compiler with "gcc".

of course, you need to have gcc-3.4 installed for that to work, if you haven't done so yet, a "sudo apt-get install gcc-3.4" should help. (You can have multiple versions of gcc installed at the same time.)

Maybe this is actually not the "cleanest" method to tell the nvidia installer, what compiler to use, but it's working and I didn't have no success with setting environment variables like "export cc=/usr/bin/gcc-3.4". If anyone has a better idea than messing with symlinks, please let us know!

so long,
kind regards,
raph

---

### Post by throbi on 2006-04-08
Thanx, Raphha!

You are amazing! Your answer to my post arrived in 24 minutes! I think that beats the response time of paid-for support services, too!

You have guided me to the solution:

>  I didn't have no success with setting environment variables like "export cc=/usr/bin/gcc-3.4"

CC should be all capitals :-) **export CC=/usr/bin/gcc-3.4** worked for me, and now nvnet is up and running!

Thanx again!

---

### Post by zwastik on 2006-04-18
hi, i have read the wiki and is very usefull, but i have one little problem:

I installed a non debian kernel, the last stable from kernel.org, so when I use 
# dpkg-reconfigure linux-image-`uname -r`- 

i get : 

> Package `linux-image-2.6.16.5-' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: linux-image-2.6.16.5- is not installed


the main question is: how to rebuild the initrd when using a non debian kernel?

thanks

---

### Post by raphha on 2006-04-18
Hi zwastik

try "update-initramfs", which is a script that wraps "initramfs". If this doesn't work for you, try using "initramfs" directly (check man pages!).

good luck,
raph :)

---

### Post by searocræft on 2006-06-13
Cheers, this thread was a great help!

---

### Post by chumba on 2006-07-13
Thank you guys for very helpfull thread and a [wiki howto]("https://wiki.ubuntu.com/NvNetInstallationHowTo"). Right now I'm on my way to become a linux expert from complete linux noob as I was just one week ago :) .
However, I think I should let you know that even after following your how-to I was still getting forcedeth at the end of the procedure.

```

#lsmod | grep forcedeth
forcedeth              27908   0
```
And it stayed there whatever I did. I do not know what was so different from the way like it should be (maybe it's myself or my freshly installed Ubuntu 2.5.15-26-amd64-generic). 
It was there untill I created new blacklist entry:
```
#gedit /etc/modprobe.d/blacklist-net
```
and added **blacklist forcedeth** there. Only then after reboot forcedeth was gone.

---

### Post by rysiek on 2006-07-15
upgraded to Dapper the other day and walked through the wiki again, to get the nvnet up-and-running, and definetely, chumba's right. the module needs to be blacklisted, **but in that case we don't have to rebuild the initrd**. which is great news, IMHO.

I have included it in the wiki, too.

cheers
rysiek

---

### Post by DilworthX on 2006-07-16
I followed the instructions on the NvNetWiki HowTo, but forcedeth still gets loaded. Any suggestions? I'm using Dapper and I have and the chipset is Nvidia Nforce 430/410. BTW, I can't access internet at all on Ubuntu.

---

### Post by DilworthX on 2006-07-16
Okay, I got the internet to work after physically removing the power cable from my pc. Wow, that's wierd -I thought that was just heresay. 

Anyway, I still have forcedeth booting up alongside nvnet. Like I said, I followed the instructions and blacklisted forcedeth. It still shows up.

Any suggestions? Thanks.

---

### Post by drifting on 2006-07-31
> **DilworthX said:**
> I followed the instructions on the NvNetWiki HowTo, but forcedeth still gets loaded. Any suggestions? I'm using Dapper and I have and the chipset is Nvidia Nforce 430/410. BTW, I can't access internet at all on Ubuntu.

I have the same problem, wonder if you have found anything more on the subject?

Paul.

---

### Post by mc^2 on 2006-08-13
Hi, I've got another problem. After some manipulations, I managed to load nvnet instead of forcedeth (even though I use dapper I had to rebuild the initrd and everything worked fine) but it resulted in a complete disappearing of eth0 (I have only loopback in ifconfig). I have a pretty new Asus MB with nForce570. I can use forcedeth instead but I have to plug off the computer while rebooting WinXP -> Ubuntu (and it pisses me off). 

Is there any way to make nvnet work or to find a well-working forcedeth?

---

### Post by mikeh on 2006-08-16
I'm trying to get hibernate working on an nforce4 system, and following this.
I can manually 'modprobe nvnet', but it isn't coming back after a resume.

I'm using dapper, but it seemed I had to rebuild the ramdisk. Its hard to be sure, since the video (geforce 6100) doesn't work yet either, after resume.
I have to blindly get the ethernet going, then ssh in :( 

I can do "/etc/acpi/hibernate.sh ; modprobe nvnet" remotely and get it back.
Looks like the resume scripts don't work. Something is crashing:

> # ../hibernate.sh ; modprobe nvnet 
 * Shutting down ALSA...                                                 [ ok ]
zsh: segmentation fault  ../hibernate.sh
# disabled, not active [unchanged].  

Any suggestions where to go from here?
Possibly related to nvsound??

---

### Post by mva.led on 2006-09-29
I'm a similar problem: Both nvnet and forcedeth are getting loaded.

I did:
sudo modprobe -r forcedeth
FATAL: Module off not found.

And then:
lsmod | grep force
forcedeth XXXXXXX 0

I can't remember now the numbers...

My chipset is a nForce 410.

lspci says:

0000:00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)

Any ideas?

---

### Post by raphha on 2006-09-30
Hi!
Did you follow this guide step by step?
[https://help.ubuntu.com/community/NvNetInstallation](https://help.ubuntu.com/community/NvNetInstallation)

I think that modprobe failure comes from your entry "alias forcedeth off". This should have been created after the modprobe command. Try "rmmod forcedeth" instead.

Anyways, if you have executed all other steps, after a reboot you should have only the nvnet driver working.

raph

---

