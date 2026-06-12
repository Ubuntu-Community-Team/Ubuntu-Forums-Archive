---
title: "HELP! 10.04 Lucid Lynx is SOO SLOW HELP!"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by x3jose on 2010-05-01
After doing an installation everything is just soo slow. When downloading, opening anything, high lighting with the pointer (only small areas thats how slugish), and typing goes for like 2-3 words then freezes then resumes.
Ram= 512mb
Processor= Intel Celeron M 
& for video : lspci | grep VGA= 01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]

---

### Post by The Thunder Chimp on 2010-05-01
Did you reboot your computer at least once after the install?

---

### Post by x3jose on 2010-05-01
> **The Thunder Chimp said:**
> Did you reboot your computer at least once after the install?
Like 4 times

---

### Post by chriswyatt on 2010-05-01
That sucks.

Go to System, Administration and System Monitor to see if anything's swallowing up your CPU (also click View, All Processes).  Sorry if you've already tried that.

---

### Post by x3jose on 2010-05-01
> **chriswyatt said:**
> That sucks.

Go to System, Administration and System Monitor to see if anything's swallowing up your CPU (also click View, All Processes).  Sorry if you've already tried that.
Most processes seem to be sleeping and cpu is from 4-6% and still slow

---

### Post by sunrex on 2010-05-01
> **x3jose said:**
> Most processes seem to be sleeping and cpu is from 4-6% and still slow

How much video ram is allocated to your IGP.

---

### Post by 4Orbs on 2010-05-01
Is it still slow after you turn off the desktop effects? Are you using the default desktop theme?

---

### Post by x3jose on 2010-05-01
> **sunrex said:**
> How much video ram is allocated to your IGP.
?? Im a total Newb in one of the restarts everything was fine..then I turned it off and sloW

---

### Post by x3jose on 2010-05-01
> **4Orbs said:**
> Is it still slow after you turn off the desktop effects? Are you using the default desktop theme?
It all was right after the installation & yes everything is default except I installed Amarok

---

### Post by swiftwood on 2010-05-01
mines being SLOW as well

might as well be on Windoze

is there a way of going back?

---

### Post by sunrex on 2010-05-01
> **swiftwood said:**
> mines being SLOW as well

might as well be on Windoze

is there a way of going back?

Put in the windows CD/DVD and install. Done.

If you don't have one, no. There is absolutely no way of going back.

---

### Post by chriswyatt on 2010-05-01
Legally :P

---

### Post by AlanR8 on 2010-05-01
Quickest version of Ubuntu I've ever used!

EVERYTHING just works on this Sony Vaio as in the signature line, Compaq Mini, HP Pavilion Media laptop and two year old home built desktop. 

I'm sure you'd agree that's a wide hardware spread.

So, what's your problem?

---

### Post by sunrex on 2010-05-01
> **AlanR8 said:**
> Quickest version of Ubuntu I've ever used!

EVERYTHING just works on this Sony Vaio as in the signature line, Compaq Mini, HP Pavilion Media laptop and two year old home built desktop. 

I'm sure you'd agree that's a wide hardware spread.

So, what's your problem?

Read the thread.

---

### Post by chriswyatt on 2010-05-01
Had you installed any proprietary drivers just before it started playing up?

---

### Post by Rasa1111 on 2010-05-01
OP~

 is "visual effects" turned off? in System>Preferences>appearance> Visual effects Tab...

is it checked to "none"?

if not, try that. 

very simple, but often does the trick.

sorry i could be of no more help.

---

### Post by AlanR8 on 2010-05-01
Just re read the thread (as suggested) and am still wondering what the problem is. 

We need to help this guy!

---

### Post by 4Orbs on 2010-05-01
Is it still slow after you stop listening to music with Amarok? Is it possible that Amarok is still scanning all your music files? Amarok is a KDE application that you've installed on a Gnome desktop... while this shouldn't cause any problems, it might be causing problems.

I suggest closing Amarok, then make sure it's not still running in the system tray, then see if your Ubuntu is still sloW.

---

### Post by Mutt77 on 2010-05-01
Ok did you install from a disc or from the update manager. I have found the update manager doesnt install everything correctly and I have to use the disc to install properly. Watch which updates you do if you have questions about them wait to see if anyone on here is having problems.

---

### Post by swiftwood on 2010-05-01
I switched java back to 

/usr/bin/gij-4.4 

that seemed to help

---

### Post by x3jose on 2010-05-01
I turned off the visual effects but still acts weird compared to the one time it did work. Amarok isn't scanning it acted weird even before I installed Amarok which took 2 hours to download.I used a live DVD to do the install. And how do you switch Java?

---

### Post by x3jose on 2010-05-01
Let me rephrase it has only worked once correctly and i restarted like 10 times now.The time it worked visual effects were on normal. So how do keep it like that...Working correctly because even then it worked WAY faster than just turning off the effects.

---

### Post by Axilus on 2010-05-01
When I first got into Ubuntu I was checking out features and opened the Remote Desktop. That tends to eat up a lot and doesn't show up in the system monitor for some reason.

Did you ever run that?

---

### Post by Jerry N on 2010-05-01
I would re-install Ubuntu, at least that is what I would do on earlier versions.  It runs just fine for me but it is the slowest install I ever saw.  I installed Win 7 on a new computer today in about 1/4 the time it took to install 10.04 on the same machine.  And there were only 18 Win 7 critical updates waiting to be installed.  

I am going to try installing from the Desktop Live disk rather than the Alternative Install next time, as soon as I make a few hardware changes on my older computer.

Jerry

---

### Post by ARhere on 2010-05-01
> **x3jose said:**
> It all was right after the installation & yes everything is default except I installed Amarok

Hi X3jose,

If your PC hangs and nothing is using the CPU resources, then chances are you have a peripheral or extra piece of software that your OS is waiting for a response from.  Since you said this has been acting this way after a fresh install, I suspect a piece of hardware that is just holding the CPU's attention too long.

Try removing pieces of hardware (*USB devices first, then anything extra the PC does not need like the CD-ROM or sound card*) one at a time and reboot and retry.

-AR

---

### Post by itisachilles on 2010-05-01
just like jerry n said i would try to reinstall (after backing up every thing) and also try o make sure that the ubuntu partition has enough space to function properly (like if you have another distro or a windows version) you could wait for a net-book "stripped down" version for 10.04 if your running on an older machine and also try disconnecting and or turning off your Internet or wi-fi (i.e. switching your wireless LAN to off or pulling out the Ethernet cable to see if it has something to do with any problems with your network**_ [COLOR=Red]especially[/COLOR]_** if its the Internet-based applications are what are slow for you hope you have some luck with lynx because I'm on it right now and its running just like 9.04 did for me.

---

### Post by 4Orbs on 2010-05-01
Have you run the system Update Manager after installing Ubuntu? That potentially could fix something. You also might take a look at the System Monitor and see how much empty space remains on the / partition.

---

### Post by nerdopolis on 2010-05-01
It could be problems with the new mode setting driver for the video card... With my card, I had to revert to the old style driver by appending the nomodeset option to the boot command with GRUB. Perhaps you can try that?

[QUOTE=http://www.ubuntu.com/getubuntu/releasenotes/910]  (for GRUB 2: edit /etc/default/grub and add nomodeset to GRUB_CMDLINE_LINUX,  then run sudo update-grub; for GRUB 1: edit /boot/grub/menu.lst and add nomodeset  to the line beginning with # kopt=, then run sudo update-grub)[/QUOTE]

---

### Post by x3jose on 2010-05-01
> **Jerry N said:**
> I would re-install Ubuntu, at least that is what I would do on earlier versions.  It runs just fine for me but it is the slowest install I ever saw.  I installed Win 7 on a new computer today in about 1/4 the time it took to install 10.04 on the same machine.  And there were only 18 Win 7 critical updates waiting to be installed.  

I am going to try installing from the Desktop Live disk rather than the Alternative Install next time, as soon as I make a few hardware changes on my older computer.

Jerry I have reinstalled already 4 times each time by downloading the iso just in case and using a different dvd each time

---

### Post by x3jose on 2010-05-01
> **ARhere said:**
> Hi X3jose,

If your PC hangs and nothing is using the CPU resources, then chances are you have a peripheral or extra piece of software that your OS is waiting for a response from.  Since you said this has been acting this way after a fresh install, I suspect a piece of hardware that is just holding the CPU's attention too long.

Try removing pieces of hardware (*USB devices first, then anything extra the PC does not need like the CD-ROM or sound card*) one at a time and reboot and retry.

-AR
?? Im pretty much a total newb..IDK anything bout ^

---

### Post by x3jose on 2010-05-01
> **itisachilles said:**
> just like jerry n said i would try to reinstall (after backing up every thing) and also try o make sure that the ubuntu partition has enough space to function properly (like if you have another distro or a windows version) you could wait for a net-book "stripped down" version for 10.04 if your running on an older machine and also try disconnecting and or turning off your Internet or wi-fi (i.e. switching your wireless LAN to off or pulling out the Ethernet cable to see if it has something to do with any problems with your network**_ [COLOR=Red]especially[/COLOR]_** if its the Internet-based applications are what are slow for you hope you have some luck with lynx because I'm on it right now and its running just like 9.04 did for me.
Everything is slow not just internet based stuff
> **4Orbs said:**
> Have you run the system Update Manager after installing Ubuntu? That potentially could fix something. You also might take a look at the System Monitor and see how much empty space remains on the / partition. I shall right now could you explain about empty space on partition? thanx

> **nerdopolis said:**
> It could be problems with the new mode setting driver for the video card... With my card, I had to revert to the old style driver by appending the nomodeset option to the boot command with GRUB. Perhaps you can try that?
How would I sorry im a total Newb thanx

---

### Post by 4Orbs on 2010-05-01
Open the System Monitor from the System Administration menu. There are four tabs at the top of the monitor. Click on the "File Systems" tab and you'll be able to see how much space is used on the / partition. Only takes a few moments to check.

---

### Post by kio_http on 2010-05-01
Could you please post your computer hardware specification?

---

### Post by kio_http on 2010-05-01
I believe I know what's causing the slow speed. Could you please state your hard drive capacity, RPM, partition size for Ubuntu and SWAP.

---

### Post by x3jose on 2010-05-01
> **4Orbs said:**
> Open the System Monitor from the System Administration menu. There are four tabs at the top of the monitor. Click on the "File Systems" tab and you'll be able to see how much space is used on the / partition. Only takes a few moments to check.
2.2gb used nothing noticeable
> **kio_http said:**
> I believe I know what's causing the slow speed. Could you please state your hard drive capacity, RPM, partition size for Ubuntu and SWAP. Im sorry im a NEWB..??How would I find all this out. I've used 8.04 & 9.04 and ran fine..I did a full Partition

---

### Post by swiftwood on 2010-05-01
My swap disk isn't on my Linux partition for some reason

> $ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0



looks pretty large though
> ls -l /host/ubuntu/disks/swap.disk
-rwxrwxrwx 2 root root 1000000000 2008-11-29 01:46 /host/ubuntu/disks/swap.disk


---

### Post by ankit singh on 2010-05-01
even my pc has slowed down after install nvidia driver. It boils my blood to see that the panels become visible only after 20 seconds of login in.

---

### Post by Power-Inside on 2010-05-02
> **ankit singh said:**
> even my pc has slowed down after install nvidia driver. It boils my blood to see that the panels become visible only after 20 seconds of login in.
Maybe you did'nt install the driver properly or the right driver version. Try to install an alternate nvidia driver or simply turn off the desktop effects and see if this helps.

---

### Post by ankit singh on 2010-05-02
> **Power-Inside said:**
> Maybe you did'nt install the driver properly or the right driver version. Try to install an alternate nvidia driver or simply turn off the desktop effects and see if this helps.

I installed nvidia driver from System-hardwaredrivers
and when this didn worked,
I went for manual installtion which also didn worked.

---

### Post by Soul-Sing on 2010-05-02
try this:

```
gksudo gedit /etc/sysctl.conf
```
Enter.

Add this beneath the text (copy/paste):
#
# Swappiness
vm.swappiness=10


Take a look here to see if its ok (swappiness=10) in the swappiness file:

```
cat /proc/sys/vm/swappiness
```

---

### Post by kio_http on 2010-05-02
> **leoquant said:**
> try this:

```
gksudo gedit /etc/sysctl.conf
```
Enter.

Add this beneath the text (copy/paste):
#
# Swappiness
vm.swappiness=10


Take a look here to see if its ok (swappiness=10) in the swappiness file:

```
cat /proc/sys/vm/swappiness
```

+1
My idea exactly, however I asked earlier what is the size of the swap partition as I would prefer giving an appropriate swapiness value.

To find the size of your swap partition install gparted in ubuntu software center. The start the gparted program by pressing ALT + F2 when on desktop and typing GKSU gparted. Also I've found Kubuntu 10.04 to be a bit faster than Ubuntu which has NVIDIA problems etc in lucid.

Try [http://kubuntu.org]("http://kubuntu.org")kubuntu
Decide whether you like it. Here is a screen-shot of the default "look".
Every theme element has a downloader wizard for more themes, icons, titlebar looks (including transparent), widgets.

[IMG]http://2.bp.blogspot.com/_qapdbswj4rA/SRuaa0NdMdI/AAAAAAAAAHY/zOrumEzs9YY/s400/plasmathemes.jpeg[/IMG]

---

### Post by x3jose on 2010-05-02
What ever I'm tired of 10.04 im just going to go back to 9.10 downloading the iso as we speak

---

### Post by Usabent on 2010-05-02
Its a bug i know i shearched up and its a bug. You have to wait until 10.10 i think

---

### Post by alphacrucis2 on 2010-05-02
> **Usabent said:**
> Its a bug i know i shearched up and its a bug. You have to wait until 10.10 i think

Bugs can still be fixed after release. Do you have a launchpad link for this particular problem?

---

### Post by x3jose on 2010-05-02
How would i report this anyways?

---

### Post by Dougie187 on 2010-05-02
If I might ask, as I am unsure after reading all of this thread. You mentioned that after installing it ran fine once, and then never again.

Is this common throughout each of the 4 installs you did? (ie. each time you install, do you get one boot that is trouble free, followed by slow boots?)

Also, is there anything in particular that you do between the good boots and slow boots? I know you installed amarok, did you by any chance, not install this on the 4 installs you did after the first one?

---

### Post by swiftwood on 2010-05-02
cranked mine up to 100

this things is actually livable now

thanks!

---

### Post by x3jose on 2010-05-02
> **Dougie187 said:**
> If I might ask, as I am unsure after reading all of this thread. You mentioned that after installing it ran fine once, and then never again.

Is this common throughout each of the 4 installs you did? (ie. each time you install, do you get one boot that is trouble free, followed by slow boots?)

Also, is there anything in particular that you do between the good boots and slow boots? I know you installed amarok, did you by any chance, not install this on the 4 installs you did after the first one?
No It only worked that one time on that one install. The boots are fine if you mean startup its the actual main thingy. I only installed (amarok) it on one installation and it was still when it was acting slow (about 2-3 hours to download) not that one time it worked fine. So far i'm using 9.10 I got tired of 10.04

---

### Post by charles_shipp on 2010-05-02
> **x3jose said:**
> After doing an installation everything is just soo slow. When downloading, opening anything, high lighting with the pointer (only small areas thats how slugish), and typing goes for like 2-3 words then freezes then resumes.
Ram= 512mb
Processor= Intel Celeron M 
& for video : lspci | grep VGA= 01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
typre in faster Ubuntu then change the swapiness

---

### Post by flyfishingphil on 2010-05-02
Went to do updates earlier and it said everything was up to date. Using Koala and the Update Manager said the upgrade to Lucid was available. Clicked on upgrade and let it go thru its full process. Koala was clean and fast. Lucid is just about as slow a Win3.1 on baud modem when it comes to the inter net.

System Toshiba Laptop L305 32 bit ACPI x86 based
Intel Pentium Dualt CPU T3400 @ 2.16GHz
RAM 3 GB Swap avail 3.2 GB
File Systems dev/sda5/  ext4 Total=74.4 GB Free=66.1GB Available=62.3GB Used=8.3GB
System Monitor Processes shows Firefoc Sleeping & Java Sleeping

Problems noted: Very slow on opening anything on the net. (Kind of like the first time you go there but even when you go back to a page it reads "Looking up (whatever)" in lower left corner of page)
Went to Pogo.com to see what it did there. Click on game, make room choice, watch for a minute or 2 while it seeks site, claims to be looking up game, page shows game icon, upper bar shows URL and it says starting applet in lower bar. Then shows done but nothing there but same game icon. No game access.
Went to FreeSlots.com and could open games but real "choppy/jerky" video action on slot machines.

Followed search suggestions in thread. Here's what I get:

Went to Admin.Hardware Drivers> showen "No proprietary drivers in use"

Went to Update Manager > all up to date

Did Kio search gksudo gedit /etc/sysctl.conf and got the following in seperate window:

#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net.ipv4.icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net.ipv4.icmp_ignore_bogus_error_responses = 1
# 
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1

Typed in this: cat /proc/sys/vm/swappiness number that returned was "60"

Ran system test > everything operates properly.

Is this an inherent "bug" on 10.04? Do I need to drop Lucid and go back to Koala for the better operation system and wait a while longer before I go to Lucid, or just put up with the problems and pray for a "speedy" update for the problem?

---

### Post by swiftwood on 2010-05-10
sorry this did not work out video playback as way too slow

When I went to reinstall I couldn't find a large enough continuous disk space to do it.

I wound up reformatting my disk

since I do not have the Window XP disks, my dual boot is gone.

now I cannot run SolidWorks which I use for work

I'm really disappointed by this.

---

### Post by crjackson on 2010-05-10
Okay, I have 2 similar systems and it was slow for me too.  The problem is the x200 video card and only having 512mb of memory.

You ARE hitting your swap file like a mad man.  10.04 seems to require a little more memory and it's enough to break the camel's back.

Either upgrade your hardware (mine was a desktop version of the x200) so I got a 128mb x300 card from ebay and it took off like a rocket.

On one of my other machines I doubled the memory to 1MB and it eliminated all slowness.

Shared memory is killing you. Since it looks like you are running a laptop given that your graphics card is an x200M, I would suggest:

1) Upgrade your memory (preferred solution for mobile computing).

2) Use a less demanding version (i.e. 9.10 or 9.04) of Ubuntu.

---

### Post by swiftwood on 2010-05-11
Mine's an old laptop

I've already installed a much memory and as large a harddrive as it can handle.

---

