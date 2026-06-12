---
title: "Newbie - Firefox problem in VMware player"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by harry003 on 2010-03-31
Lucid installed cleanly and everything seems to work except Firefox. Please help me.

I am a fairly experienced Microsoft user who is looking to migrate to Ubuntu, but I need to test the waters first. I chose Gnome because I like Firefox and wanted to stick with it.

I have done complete clean installs twice in a VMware Player (I have tried wubi at least 3 times but it returns an error message part-way through and dies every time) and everything seems to work fine except that Firefox hangs in "Loading" and eventually times out. It will not even ping 192.168.1.1 but the hardware is cool because here I am via XP. I am connected via Ethernet via router and DSL modem. I found a setting where I seem to have a choice between Loopback and Ethernet, but when I try to choose Ethernet it automatically resets to Loopback, whatever that is.

I have found and tried several "remedies" in Ubuntu forums but none have worked. I happily used MS-DOS for a decade before Windows came along, so I am not uncomfortable with a command line, but I need some straightforward coaching here. 

Thanks in advance, Harry

---

### Post by bhmildy on 2010-03-31
loopback is the virtual internet connection that confirms that your network card is installed correctly. pinging 127.0.0.1 will confirm that it's installed correctly.  I don't think that 192.168.1.1 actually means anything other than it's the typical subnet mask of a home network.

have you installed guest additions in virtualbox?
post your system specs, including your network card.
post your virtualbox version
post your xp service pack.

i bet guest additions is your problem.

---

### Post by harry003 on 2010-03-31
Thank you !

I have a very strong desktop that I built myself with a Realtek LAN built  into an Asus motherboard. I update XP every Tuesday (ha ha) and try to run as mean and clean as I can which is why I want to move over to Linux. 

I followed instructions that I found about VMware player (I gave up on wubi after several tries because it always returned errors and failed to finish installing even though I downloaded more than 1 version from various sources) but what is a virtual box?

If that is the VMware Player I downloaded the latest version that I could find via Google, clean and new each time.

If I need to wipe it all (yet again) and install clean (yet again) I will, can you please point me to the latest and greatest sources?

Thank you very much.

ps - VMware Player appears to be v 3.0.1 as far as I can tell.
pps - what is a guest addition?

---

### Post by JKyleOKC on 2010-03-31
A number of virtualization programs exist; VMware Player is just one of many. VirtualBox from Sun (now owned by Oracle) is another. Others include VMware Server, XEN, and QEMU, just to name a few.

I run both VMware Server and VirtualBox here, on different machines, and personally prefer VirtualBox but their performance seems to be pretty much the same. There's a version of VirtualBox in the repositories, but it's slightly crippled in that it does not support any USB interfaces. You can download a full version from Sun's web site at [http://download.virtualbox.org](http://download.virtualbox.org), though, that's free of cost for personal use. The VMware Server program has to be downloaded from VMware's web site and is also free for personal use.

You may want to visit the Virtualization forum here to get lots more information and HOW-TO data about the subject. It does require adequate RAM and works best with dual-core or hyper-threading processors (although I have two machines running VirtualBox with only 512 MB of RAM in one and 256 MB in the other, and older single-core CPUs in both; they both work, but are dog-slow in comparison with the speed on my two multi-core systems with 2 GB of RAM each)...

EDIT: Both VMware Server and VirtualBox provide "guest addition" packages that make their operation much more comfortable. These are packages that you install in the guest operating system after you have it up and running; they provide much better video resolution, seamless mouse and keyboard integration, and a few other benefits. They aren't available for all guest systems, but are for the ones most often used...

---

### Post by harry003 on 2010-04-01
JKyle - 

thank you for your help. 

I gave up on VMware and took your advice to try Virtualbox. it took several hours and 2 tries, but it is up and running pretty well. internet works too, here I am.

there are a number of things that frustrate me, I really wanted to keep all this completely away from my C: drive, and not burn any CDs, but it seemed to force me into a very limited number of installation choices. 

certainly, when I understand the ins and outs better, I will be able to do more, but after dozens of hours and a half-dozen install attempts, I gave up and let it do whatever it wanted by default. I hate having my virtual Ubuntu machine all buried in the very heart of my C: drive in Documents and Settings, but I have wasted so much time I was tired of fighting it.

thanks for your help

---

### Post by JKyleOKC on 2010-04-01
Open up the VirtualBox main dialog (in Windows) and look under "File" for the "Preferences..." item. Select it and you'll find two text boxes on the first property tab, to set the default folders for the virtual disks and the virtual machines. You can put them on another drive if you want to keep them away from C: but they do have to be Windows folders since VBox itself is running in Windows.

If you do change those folders to some other drive, you can then move their entire content over to those new locations and the VMs should continue to work as if they never had been moved. I've even copied such VMs and their disks from one actual machine to another. This is one of the great advantages of virtualization!

---

### Post by harry003 on 2010-04-02
Well that is just too cool. Windows would never allow to even find, much less move, all their precious installation!

Sounds like you could manage to keep the whole thing on a flash drive, if it was big enough.

This transition from Microsoft may be slow and painful, but I am starting to feel that it will really be worth it.

Thank you enormously for your help!

---

