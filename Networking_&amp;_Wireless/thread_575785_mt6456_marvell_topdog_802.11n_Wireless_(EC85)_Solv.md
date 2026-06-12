---
title: "mt6456 marvell topdog 802.11n Wireless (EC85) Solved"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by blaquesmith0 on 2007-10-14
The missing step is forcing ndiswrapper to use an xp driver as follows:

"sudo ndiswrapper -i NetMW14x.inf" (/etc/ndiswrapper will create a folder named "netmw14x" inside it). 

"sudo ndiswrapper -a 11ab:2a08 netmw14x" (lspci -nn will show device ids)

which forces the Marvell Device ID to be associated with the TopDog XP driver.

"sudo ndiswrapper -l" will now say the device is present  and it can be configured normally.

I have used the drivers for the NETGEAR WN311T pci adapter as well as the Airlink101 AWLlH6045 pci adpter. Both are the most recent available as of 10/14/07. The only odd note is that both have ndiswrapper linked to usbcore. But if in doubt I use the NETGEAR drivers as they are better maintained.   
Side Note;  I installed wine to open the driver "exe" files and just opened a terminal in the wine psuedo programs folders to run ndiswrapper commands in the NETGEAR and/or Airlink101 driver folders . 

hardware: Gateway MT6456 (Marvell TopDog 802.11n EC85 wireless) wnr311t_setup_4_1.exe drivers, NetGear WNR834M Rangemax Next Draft N router firmware 1.4.23NA
Ubuntu: 7.10-rc-desktop-i386
  
Now get back to codeing...

--blaquesmith

---

### Post by xflatlinex on 2007-11-16
Wow, I have tried every trick on this subject and I still cannot get the wireless card to work for me.  I have the MT6456 Gateway and have gone though I believe every tutorial.  Does anyone have any further advice? I have 7.04 by the way, and I just need a really good step by step guide because obviously I am doing something wrong.  I can get the driver installed but when i "sudo ndiswrapper -l" i get the following error....."netmw14x  :  invalid driver!"
Thank you in advance.

---

### Post by xflatlinex on 2007-11-17
Just tried to reinstall, no luck...:-(

---

### Post by blaquesmith0 on 2007-11-25
Open gnome terminal input

1)  lspci -nn 

output should show:

05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Unknown device [11ab:2a08] (rev 03)

2) sudo ndiswrapper -i NetMW14x.inf

output should show:

netmw14x : invalid driver

3) sudo ndiswrapper -a 11ab:2a08 netmw14x

the system will give a warning... Ignore it! 

4)  sudo ndiswrapper -l 

output should show:

netmw14x : driver installed
        device ( 11AB:2A08 )  present

Thats all the steps except for extracting the firmware.

--blaquesmith

---

### Post by spyderpride on 2007-11-25
see below this post

---

### Post by spyderpride on 2007-11-27
OMG I got it working.

After you do everything blaquesmith says up there, use the following commands (they worked for me):

sudo ndiswrapper -m

sudo depmod -a

sudo modprobe ndiswrapper


# this can be useful if you continue having problems
tail /var/log/messages

---

### Post by blaquesmith0 on 2007-11-27
I didn't need to do that on feisty, gutsy, and on my current platform gutsy studio (all 32-bit). The bcm43xx module isn't loaded so it doesn't need to be blacklisted in/etc/modprobe.d/blacklist. I've only ever blacklisted 8139cp in /etc/modprobe.d/blacklist and that was on a msi ati rs480m2-il motherboard which has a realtek nic which uses the 8139too module. In this case the os i.e. device manager/hal still shows Marvell Technology Group Ltd. Unknown ( 0x2a08 ). In gnome terminal dmesg | grep bcm43xx or lsmod or syslog won't show the system attempting to load it. Anyway I'm glad to see someone else get the "TopDog" barking in Linux. I think I'll see if I can do this with a an amd64 kernel, you know, do the full 64-bit OS thing.

--ps. spyderpride, the hard part is finding a decent draft n 2.0 router.
 
--blaquesmith..

---

### Post by spyderpride on 2007-12-04
> **blaquesmith0 said:**
> I didn't need to do that on feisty, gutsy, and on my current platform gutsy studio (all 32-bit). The bcm43xx module isn't loaded so it doesn't need to be blacklisted in/etc/modprobe.d/blacklist. I've only ever blacklisted 8139cp in /etc/modprobe.d/blacklist and that was on a msi ati rs480m2-il motherboard which has a realtek nic which uses the 8139too module. In this case the os i.e. device manager/hal still shows Marvell Technology Group Ltd. Unknown ( 0x2a08 ). In gnome terminal dmesg | grep bcm43xx or lsmod or syslog won't show the system attempting to load it. Anyway I'm glad to see someone else get the "TopDog" barking in Linux. I think I'll see if I can do this with a an amd64 kernel, you know, do the full 64-bit OS thing.

--ps. spyderpride, the hard part is finding a decent draft n 2.0 router.
 
--blaquesmith..

You're right, edited my post.

Be sure to post if you get it working in 64-bit. I certainly can't, but I would really like to start taking advantage of this 64-bit processor :). When I try to use the netmw14x driver, it says it can't find netmw146 or something like that.

---

### Post by drazabyss on 2007-12-30
> **blaquesmith0 said:**
> Open gnome terminal input

1)  lspci -nn 

output should show:

05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Unknown device [11ab:2a08] (rev 03)

2) sudo ndiswrapper -i NetMW14x.inf

output should show:

netmw14x : invalid driver

3) sudo ndiswrapper -a 11ab:2a08 netmw14x

the system will give a warning... Ignore it! 

4)  sudo ndiswrapper -l 

output should show:

netmw14x : driver installed
        device ( 11AB:2A08 )  present

Thats all the steps except for extracting the firmware.

--blaquesmith
Alright, I seem to have difficulty pulling the information from diswrapper with the -i command.  When I follow the above instructions (and I have verified the ID and version) I get an error that reads that NetMW14x.inf can not be installed because it cannot be found in line 119 of diswrapper1.9.  The command does create the directory in the <ect> folder, but it is empty.  Doing -i again says the driver is already installed, but the -a command will fail and -l will display NetMW14x.inf is invalid.

I'm a complete newb with linux and ubuntu in every way (6 hours or so in) though I have a pretty high level of aptitude for softwares.  Any help would be appreciated.

---

### Post by brake16 on 2008-01-04
Good Morning

I'm having the same exact problem as drazabyss.  The only difference between my system output and the output from blaquesmith0's example from the lspci-nn command:

[INDENT]08:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Unknown device [11ab:2a08] (rev 03)[/INDENT]

So instead of 05, mine starts 08.  

I tried adding the extra commands from spyderpride, but nothing happened (no output, error or otherwise). 

Any help would be greatly appreciated.

brake

---

### Post by spyderpride on 2008-01-13
You may need to put the netmw143.sys and netmw145.sys files in the same directory that you put the NetMW14x.inf file. I'm not sure if that does anything, but its the only difference I can see between what I did and the instructions.

Here's exactly what I did (assuming Wine and ndiswrapper are already installed):

1) Download wn311t_setup_4_1.exe (or whatever the newest version is) from Netgear.

2) Use Wine to run the .exe, complete the installation.

3) Open up a terminal and change the directory to wherever the drivers are in Wine's drive_c. All the files you need should be in there.

4) sudo ndiswrapper -i NetMW14x.inf

5) sudo ndiswrapper -a 11ab:2a08 netmw14x

6) sudo ndiswrapper -m

7) sudo depmod -a

8) sudo modprobe ndiswrapper

---

### Post by Trafalger61 on 2008-01-22
okay, I'm a def. a Linux noob, but I love it, so much better than any windows OS i've ever used.  Anyhow, I still cannot get my wireless card to work.  I followed blaquesmith's directions and nothing works, and then I tried using some of the other techniques on this post and still nothing.  I downloaded the netgear ledriver version 3.1.   I downloaded the file and installed it using WINE.  Here's my terminal code:


bryan@achilles-laptop:~$ sudo ndiswrapper -i NetMW14x.inf
Password:
driver netmw14x is already installed
bryan@achilles-laptop:~$ sudo ndiswrapper -a 11ab:2a08 netmw14x
driver 'netmw14x' is not installed (properly)!
bryan@achilles-laptop:~$ sudo ndiswrapper -l
netmw14x : invalid driver!
bryan@achilles-laptop:~$ 
bryan@achilles-laptop:~$ 

thanks in advance,
                                          trafalger

---

### Post by DarkLightConnection on 2008-01-29
@Trafalger:

Create a copy of NetMW145.sys and rename it to NetMW146.sys

The problem is that the .inf file has a section that calls a driver called NetMW146, but on the pack only 143 and 145 are included... Windows ignores this and goes directly to the driver that works, but ndiswrapper don't, it expects it to be there.

Or at least that's what did the trick for me, your mileage may vary.

PS. I also have a MT6456 notebook, glad to see I'm not the only one.. this is a fairly unknown model:(

---

### Post by darkscript on 2008-02-28
You guys have no idea JUST how Much this has helped me...I have been without a wireless driver for over a few months ever since buying this gateway. Actually I am using the model m1817, but it is the same thing... 

I am like screaming with joy and using wireless now... hahaha I love you guys...

but i'm actually going to post something useful for some people who might have use for it...

first of all...at least for now the driver can found from netgear, not marvell , [http://firmware.netgear-forum.com/WN511T/wn511t_3_0_setup.zip](http://firmware.netgear-forum.com/WN511T/wn511t_3_0_setup.zip)
and it is to version wn511t_3_0_setup.zip

Eventually I am going to package the necessary files into a zip, and I hope and pray that these work with windows xp as I will soon be dual booting this for one of my classes that I will need it on.

Anyways, Just use wine or cabextract i beleive to get the files you need...

like OMGSH i never thought I would be blessed enough to have the driver working...i'm having like a spaz attack or something.

---

### Post by animatt on 2008-03-31
Hello,  I had this problem solved awhile ago,  I followed maybe even this thread months ago.

Anyway I was doing a clean wipe and install to newest Ubuntu Heron 8.04 beta.

I forgot about the annoying driver file.  If you are on linux it can be a pain since it is not a simple archive file.  

I did install WINE to extract it.  But I really hate installing software I will never use again.

Anyway I am here to post a zip file that will contain just the 14x.inf and 145.sys files this way anyone can extract this nicely from a linux or mac or windows computer.

SO here you go I hope this helps someone out.

---

### Post by bowzer on 2008-04-12
hi: 
Thanks to all who have contributed to this thread.   I have a brand new Gateway m6750 with the Topdog wireless card. It had Vista on it, but after the latest Microsoft upgrade prevented me from logging in after the reboot I decided enough was enough.  I have loaded Hardy 64 bit (this is a Core 2 duo system.)  Everything looks good except that I have been unable to get the wireless to work following the instructions here.  (I have a Linksys WRT54g that isn't the most reliable thing - disconnects, web into it and it often crashes...) Heading out the door for something better.

Anyway, I haven't been able to get the wireless to work.  Ndiswrapper seems to go ok, but

 sudo ndiswrapper -l
netmw14x : driver installed
	device (11AB:2A08) present

 lspci -nn := 02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Unknown device [11ab:2a08] (rev 03)

windows wireless drivers shows it is installed

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

i have also tried the 64 bit driver netmw245.inf without joy.

any ideas?

---

### Post by cougar52 on 2008-04-21
I also have the M6750. It is a great laptop and the fix worked perfectly as described in this thread on the 32-bit version of Ubuntu. However, I just switched to 64-bit Vista/Ubuntu and the fix is no longer working just as described above. Ndiswrapper reports driver installed but no wireless.

---

### Post by spyderpride on 2008-04-29
Anyone get the Topdog working in AMD64? The needed netmw146.sys seems to be non-existent.

Is there a workaround to let 32-bit drivers work in a 64-bit environment?

Since a lot of people looking at this thread seem to have the MT6456, I have a quick question.  What is your average CPU temperature and battery life? Mine is about 75 C and 1 1/2 hours, which is quite crappy. C-States not supported at all.

---

### Post by vodo321 on 2008-04-30
I also have a M-6750 and have reached the same point. I have tried looking all over. iwconfig shows there are no wireless extensions for lo and eth0. please help

---

### Post by kiwisoup on 2008-05-07
I finally got it to work after installing 32 bit instead of 64 bit...

only problem is that every time I restart the computer I have to redo the last two commands. Why do I seem to be the only one having this problem?

I had no issues or errors when doing the commands, so I don't know what the problem is. Can somebody either help me figure out what the issue is or at least automate those two commands to run automatically on startup?

---

### Post by drdanield@gmail.com on 2008-06-07
:lolflag: SUCCESS WITH GATEWAY LAPTOP M-6319 AVAILABLE THROUGH COSTCO

Excellent job everyone.  Thank you so so much.  I recently got a Gateway M-6319 or M6319 and the instructions worked great using the newer Netgear driver.  To save others some time, I provided the pruned drive and modified instructions at [http://nohair.com/code/computers:ubuntu:gateway_m-6319](http://nohair.com/code/computers:ubuntu:gateway_m-6319)

I'm still working on the following on the laptop Gateway M-6319:
Screen brightness doesn't work yet
Microphone doesn't work yet
Sound max volume is still too low

If you can help me please please don't hesitate.  It took me days to find this thread because there is no place mentioning the Gateway M-6319.  I suspect others with same laptop may never find help for their laptop wireless unless they're savvy enough to find their wireless by searching the output of 'lspci -nn' and then search for the pci id "11ab:2a08" and ubuntu keywords.  That's how I found the thread.

---

### Post by .:Christopher:. on 2008-06-16
Well i have gotten my wifi card to work but it seems that every time i shut off my computer or log out i have the same problem over again and the only way to fix this seems to be sudo modprobe ndiswrapper and then it works but is there a way around this so i dont have to do this every time i login? as it is my laptop that i do shutdown all the time. it also does it if i hibernate it.

-christopher

---

### Post by euclidprime on 2008-07-22
A clue ...

I'm trying to get this working on a friends Gateway MT6458 running a 64 bit kernel. I copied netmw145.sys to netmw146.sys as suggested. After "modprobe ndiswrapper" I find this in dmesg output:

ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B

Any suggestions? Can somebody take it from here?

---

