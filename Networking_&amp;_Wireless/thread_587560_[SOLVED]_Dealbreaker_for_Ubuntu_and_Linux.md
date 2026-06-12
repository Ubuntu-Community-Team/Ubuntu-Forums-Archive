---
title: "[SOLVED] Dealbreaker for Ubuntu and Linux"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by jludeman on 2007-10-22
I posted a few days ago about getting wireless working. After a lot of research I got it running. 

Then I noticed that dial up no longer worked.

I have a laptop and a desktop with wireless cards and a buffalo wireless g router.

The router has a default address.

As far as I know pppd is the only dialer for linux. Everything else is a front end for it.
I discovered that pppd is hard coded not to bypass the default route. 

Now that the wireless network is working the default route is the router adress.

If I type in the command route del default then the dialer works and I can get on the internet. Of course that kills the lan precluding any possible internet sharing.

I could build a firewall/server with a modem. Too expensive.

I could wait for broadband which is also too expensive.

Or I can stay in windows and use my existing hardware and software. Interestingly
windows allows me to share the modem and the network at the same time.

Too bad. I really wanted to move to Linux. Windows 2000 pro is the last Microsoft product I'm ever gonna own. In less than three years it will no longer be supported.

Guess I'll tough it out for a couple years and hope for a solution.

---

### Post by jludeman on 2007-10-23
I spent too many hours on the network thing.
I spent even more hours searching the web for an answer.
Made me tired and cranky.
Looks like route del default will let me dial into the net.
And I can still access the lan. I was too tired and cranky to remember ping etc.

I still don't know where the default thing is coming from. It shows up in resolv.conf
and the route tables at boot up. It's not needed by the lan and I'd like to get rid of it.

As to modem sharing I ran across Firehol and TinyProxy on the net.
I think I may be able to set the system up after alll.
I'll probably be real tired and cranky by the time I get the laptop setup.
Even in windows it was tough to find drivers etc. because Toshiba only supports Vista.
I hated vista and immediately upgraded to Windows 2000 pro. What I could not get drivers for I hung on a USB port or ignored.:roll:

---

### Post by ekravche on 2007-10-23
Try 7.04 it has better wireless support than 7.10 at this point. I regret upgrading to 7.10... I should have just left 7.04 and upgraded to 7.10 when it was more stable.

---

### Post by JoJerome on 2007-10-24
I too have been working for many hours over 2 weeks or so to get the wifi up and running on a friend's laptop. If it's not working by tomorrow, it will certainly be the deal breaker for him.

Not for me however. I guess it's personal preference, but I'd rather get my hands dirty and learn some code as a more than fair trade for no longer being a slave to Micro$oft.

I work at an electronics store where there is a steady stream of people coming in with horror stories about viruses, crashing programs, lost date, expensive upgrades and expensive repairs. Every such story makes me a tiny bit more willing to dig deeper and make this wifi card play nice with Linux! And it's taken some time, but I've gotten lots of help here and I think I might finally have the wifi working now.

Again, just a personal preference and my $0.02.

- Jo

---

### Post by jludeman on 2007-10-31
I got the laptop working. Actually it turned out to be plug and play. Installed from 7.04 dvd. Everything worked right away.
Wireless network, sound everything.

I've still got network problems probably do to lack of knowledge.
I'll be posting a question elsewhere on the forum and hopefully get some answers.

---

### Post by JoJerome on 2007-10-31
For what it's worth, got mine running too. Since I'm doing a new install, I re-installed 7.10 and tried starting the wireless adventure over from scratch. Turned out 7.10 saw the card all along. Just needed a little configuring to tell 7.10 which connection to use.

And I got lots of invaluable help here on the forums.:KS

- Jo

---

### Post by jludeman on 2007-11-07
This is what I did to setup my home lan in Ubuntu the way I wanted it.

System:

Why should you care? You probably should not care about my junk but it might pay to find out about your hardware. Then you can search for help on the net if something does not work. If your's matches mine I already figured it out. Look below.

Older desktop custom built by me. After that it was kludged together out of parts from deceased computers.

	Soltek motherboard - AMD 1.3 Ghz processor The bios does not support dvd's. This thing was really fast when I built 		it. The old computer had a 333 Mhz Intel Slot 2 cpu. That one worked great for 11 years.

	US Robotics modem - Real hardware modem that's been faithfully working since the late 90's. Has a built in speaker that makes a lot of noise when connecting. It's comforting to hear the Big Ben sound when a solid connection is made. Too bad you can't get a modern version. - plug and play

	VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio - plug and play
	Radeon Mobility 9600 graphics card - plug and play
	Broadcom BCM4306 802.11b/g Wireless LAN PCI card - see below

New laptop - Toshiba ? - Ubuntu just worked from the install disk. I had a real hard time locating and installing drivers when I replaced Vista with Windows 2000 on this computer. I hated Vista. That's one reason I'm doing linux.

Buffalo WHR-G54S wireless router
HP inkjet printer

Goals:
	Dual boot windows and linux on both machines.
	Share files from laptop to desktop.
	Share Internet connection over modem.
	Share printer.
	Working firewall - lan

--------------------------------------------
Install - why isn't this easy? 

My computer would not boot to the live cd. I had previously booted it successfully. Since then the cd drive broke and I replaced it with a dvd/cd writer. Solution: Make ISO of the original. Burn ISO to new cd. Problem solved.
fd0 error Here's a link.
[https://bugs.launchpad.net/ubuntu/+bug/97496](https://bugs.launchpad.net/ubuntu/+bug/97496)

I set up the partition manually during the install process. After I was happy the installer was not. It kept claiming I did not have a root partition. Link follows.
[http://clau.sparetimegroup.net/index.php/tech/ubuntu-610-installation-no-root-filesystem-error/](http://clau.sparetimegroup.net/index.php/tech/ubuntu-610-installation-no-root-filesystem-error/)
Solution: I just let the installer format the whole drive any way it wanted.

--------------------------------------------
Tools - for easier setup - I added these first.
	Emelfm - Swiss army knife for linux - you can do almost anything if you sudo emelfm. Also a pretty dandy file 		manager. Bookmarks for frequent folders. Built in terminal.

	Gnome desktop customize - Don't spend a lot of time here. You might screw up and have to start over. I did.
	
	Add to bottom panel: 
	Applications - Accessories - terminal - oh yeah you'll use this a lot.
	Search for files
	Your home folder

	Add to top panel: 
	Window Selector
	Network monitor set to ppp0 - so I can see what my internet connection is doing

--------------------------------------------
Dual boot - real easy - if you understand partitions and drives

There a lot of guides on the web for this. It's really very easy. Set up your partitions/drives. Install windows first.
Then install Ubuntu. The installer will do the grub menu for you and you're all set. Just make sure you understand the drives and partitions. You can do sudo gedit /boot/grub/menu.lst if you need to change the grub menu.

Optional: Download damn small linux and burn a cd. You can fix a lot problems in both windows and linux with this.
Boots fast reads windows and linux drives.

--------------------------------------------
Network setup - not so easy

The broadcom card in the desktop was not recognized by the installer. This is easy to fix.
See the how to here
[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)
Get the driver here
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)

Peculiar to my system is the Buffalo WHR-G54S wireless router. This is intended to be hooked to DSL or Cable. Mine is not.
I just use it as a wireless hub. I connect with an old fashioned modem.
The operating system quite rightly chooses the router as the default access point. Well that's quite wrong for me. I lose access to my ISP. See modem and file sharing for solutions.

--------------------------------------------
Modem sharing - not too easy

As stated above I have to change my routing table to connect to my ISP. Route -n shows that the wireless router is the default access point. Sudo route del default fixes that.
Do I want to sudo route del default every boot up? Heck no!
I can make a custom application launcher on the panel but I'll still have to log in with my password.
Solution: 
1. make a script in gedit as follows:
	#!/bin/bash          
	sudo route del default
2. Save it in your home folder as routedelsu
3. sudo visudo -f /etc/sudoers and add these lines at the bottom  
# lets yourusername run script routedelsu as super user
yourusername yourcomputername = NOPASSWD: /home/yourhomefolder/routedelsu

!!!!!!!!!WARNING!!!!!!!
This gives you or anyone who logs on as you a lot of power to screw up the system. be careful.
!!!!!!!!! END WARNING!!!!!!!

visudo manual:
[http://www.gratisoft.us/sudo/man/visudo.html](http://www.gratisoft.us/sudo/man/visudo.html)
sudoers manual:
[http://www.gratisoft.us/sudo/man/sudoers.html#examples](http://www.gratisoft.us/sudo/man/sudoers.html#examples)
(By the way - I pasted all commands into the terminal as I wrote this to check them. I also went to every link. I wish all contributors to the forum would do likewise. It would save readers some grief.)

Ok I got the modem going all the time on the desktop now to share with the laptop. This is almost too easy.
Solution:

Download and install tinyproxy
Excellent simple how to here.
[http://ubuntuforums.org/showthread.php?p=683303](http://ubuntuforums.org/showthread.php?p=683303)
I did not turn on filters for now. I just added my lan address for the desktop with the modem. Easy modem sharing.

--------------------------------------------
File Sharing - the hard way 
Get a phd in astrophysics. Follow up with a degree in advanced ... Never mind 
Don't waste your time trying to decipher SMB or NFS. Jump to the next step.

(Side Note: In windows I click on a folder and share it. In linux connected to windows over the lan I see my windows shares with a default Ubuntu install. Why is linux to linux on a home network so hard to implement or explain? I don't have time to care anymore.
I found one article on the web that said sharing is as easy as it is in windows. I laughed until I cried. After I thought about for a while I realized that if the network was all set up it probably would be easy.
Also setting up networks in windows is not trivial for those without the knowledge base to do it. I've been doing it for 15 years on the job so I don't remember exactly how hard it was the first time.)

--------------------------------------------
File Sharing - the easy way -vfstpd 

The vsftpd manual is here.
[http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html)
A very good how to on vsftpd setup is here.
[http://www.informit.com/articles/article.aspx?p=378136&seqNum=10&rl=1](http://www.informit.com/articles/article.aspx?p=378136&seqNum=10&rl=1)
You'll need to understand users and groups.
If you don't understand users and groups there is an excellent article here.
[http://www.freesoftwaremagazine.com/articles/users_in_ubuntu](http://www.freesoftwaremagazine.com/articles/users_in_ubuntu)
If this is your computer then you are able to log into ftp and go anywhere and do just about anything. Other members of the admin group have the same privileges.

My vsftpd.conf with comments.
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
#locks everybody into their home directory
chroot_local_user=YES
# enable a list file of those not locked into their home directory
chroot_list_enable=YES
# the administrator is on the list and can go anywhere
chroot_list_file=/etc/vsftpd.chroot_list
ftpd_banner=Welcome to Jim's handy dandy ftp service!

--------------------------------------------
Printer Sharing - the easy way - Ubuntu default

Menu - System - Administration - printing
All I had to do is locate the printer from the database.
For sharing click share printers under the global settings menu.:cool:

---

### Post by jludeman on 2007-11-07
After some more web research I can update the install process above.

--------------------------------------------
File Sharing - the hard way 
I finally found a link that enabled me set up nfs the way I wanted it.
[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)
I followed his directions and got file sharing. I wanted the shares available at boot so I added the following line to /etc/fstab:
192.168.11.3:/home/jim/LAP /home/jim/LAP nfs rsize=8192,wsize=8192,timeo=14,intr

I still had to set permissions for the shared files and folders or they would not show up in nautilus.
Doing permissions from nautilus is a nightmare even with gksudo nautilus. So I used sudo emelfm and got it done.

--------------------------------------------
Network setup - not so easy
Using wl_apsta-3.130.20.0.o with bcm43xx-fwcutter worked but was flaky. It took several tries to hook up when first loaded.
It also would disconnect randomly.
I did lspci and discovered I had a BCM4306 wireless card.
I located another web article here.
[http://davidwatson.org/2007/05/broadcom-4306-on-feisty-fawn.html](http://davidwatson.org/2007/05/broadcom-4306-on-feisty-fawn.html)
Using the correct windows driver solved all the flaky problems.

--------------------------------------------
Modem sharing - not too easy
Tinyproxy was a good solution. However a little browsing led me to discover that I could not access sites with https:\\ in their address. Tinyproxy information is hard to come by. I don't know the solution to the problem so I'll live with it. 
The bad part is that [https://help.ubuntu.com/](https://help.ubuntu.com/) is not usable. So I can't access the official Ubuntu help site.

--------------------------------------------
Printer Sharing - the easy way - Ubuntu default
Turned out sharing was pretty easy - but!!
While I was struggling with the share setup and sending test pages I discovered that the default cartridge was color.
On my printer it would cheerfully print nothing and spit out a blank page. Not too obvious whether this was a sharing problem or something simple. Another round of banging my head against a wall. 

--------------------------------------------
Laptop Audio

I thought this worked from the clean install because my Turtle Beach usb audio played system sounds over the headphones.
When I finally put a music cd in nothing played. I found a link that got the internal card working.
[http://ubuntuforums.org/showthread.php?t=562835&highlight=82801](http://ubuntuforums.org/showthread.php?t=562835&highlight=82801)

lspci results:
 Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

sudo gedit /etc/modprobe.d/alsa-base
alias snd-card-0 snd-hda-intel
options snd-card-0 index=0
options snd-hda-intel index=0
options snd-hda-intel model=3stack
reboot - sounds and music come from the internal speakers.

I still have not gotten the Turtle Beach to play music from any source.

--------------------------------------------
Conclusions
The hardest part of the installation was finding information. Sadly there is a lot of bs out there. People answer questions that they are not qualified to answer. People answer questions that they are qualified to answer but in high tech babble leaving out essential information. People answer questions that were not asked. Some people feel that lifestyle advice is a substitute for a real answer. For example: How do I get my modem working under Ubuntu? Answer: Get broadband. Thanks a lot A**H***.

Sadly most of my good information did not come from the Ubuntu forums. Google turned out to be my biggest helper.

The GUI is not ready for casual users. Most of my work was done from the terminal or Emelfm. I must have done a lot of muttering because my wife started saying stuff like sudo grep lspci.

---

### Post by mainely_linux on 2007-11-07
> **jludeman said:**
> I discovered that pppd is hard coded not to bypass the default route.

This is actually not correct, you can tell pppd to take over the route.

Add the following line to your /etc/ppp/options file:

```

replacedefaultroute

```

First connect to your wireless network,
Then initiate your dialup with wvdial, kppp or whatever frontend you use.

You'll be able to use your wireless lan and surf on the dialup.

I live in the Maine woods with no broadband capability so I feel your pain!

---

### Post by jludeman on 2007-11-07
Thanks for the tip. I'll try it right now. 
I'm in the piney woods of coastal North Carolina. I almost visited Maine this summer but with the gas prices I only made it as far as the outer banks.

It worked great! Now I can get rid of my kludgy workaround. Thanks a lot.

---

### Post by Keen101 on 2007-11-21
Just thought I'd let you know that I have had horrible experiences with network manager. (the default wireless manager in the notificatin area/tray)

I don't even use it anymore. Instead I just use the network admin.

I just went to >System >Preferences >Sessions and unchecked network manager then logged out then back in, and then set it manually with network admin on >System >Administration >Network.



-keen101

---

