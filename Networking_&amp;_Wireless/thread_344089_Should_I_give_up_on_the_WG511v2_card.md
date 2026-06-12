---
title: "Should I give up on the WG511v2 card?????"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by Moffind on 2007-01-22
I've posted this before and had no response - feel like giving up at the moment - a bit fed up with it all......

anyway.......

Having some problems with the Netgear WG511v2 (china) card.

Installed so far using Dapper, Ndiswrapper-1.34 and Marvell driver Libertas 802.11b/g Wireless v2.3.0.19 from [http://www.station-drivers.com/page/marvell.htm](http://www.station-drivers.com/page/marvell.htm).

Using the all the Netgear drivers from the CD didn't work.

Using ndiswrapper -lI get the message:

mrv8ka51 : driver installed
device (11AB:1FAA) present (alternate driver: mrv8k)

So it can find the card and the driver, but there's no light on the card.

I blacklisted a number of items early on:

prism54
islsm_pci
islusb
isl3886

is this correct?


I've done a modprobe for ndiswrapper and rebooted.

I'm not sure what to do next?

Running through the iwconfig nothing happens.....help please, simple step by step instructions if you can I'm new to all this.

Thanks Moff

---

### Post by crysys on 2007-01-22
I'm in the same boat.  This card does not like linux.  Any help would be appreciated.

Ha! It figures that as soon as I'm about to give up I find a solution.  Try this howto, it worked for me using a wg511v2 on an old gateway 450sx4...
[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29")

I'll add that the howto uses ver 1.29 of ndiswrapper but I used the latest, 1.34, without trouble.  I'm also using Xubuntu 7.04 Herd2 so I can't say how well this works with edgy or dapper.

---

### Post by TotalNewb on 2007-02-06
this seems to be the biggest problem card... Of all the wireless internet cards, it's just my luck that I happened to purchase the hardest card to get to work on Ubuntu.... the problem is all the directions ppl give assume you've been with linux for years... I've been with linux for about a month now... I begin to doubt Ubuntu's slogan "linux for human beings"? what? like superhumans with massive intellegence maybe... I'm just an average human here... just now in my second semester of college...I went to Ubuntu because it gave me a sense of extra security that windows simply CANNOT provide... I want to figure this out... I just cant find anyone willing to provide me with the help i need.... anyway... i need to wrap up b4 I start to ramble... I think I speak for all noobs w/ the Netgear WG511 when I ask for someone to plz plz plz plz plz plz plz plz plz PLZ help. We're desprate here... can some Linux Genius create a linux driver for this thing.... Like maybe a bin file... maybe it's not that easy... but PLEASE we are seriously desprate here... please???

---

### Post by smCw6GNakQn300£ on 2007-02-06
> **crysys said:**
> I'm in the same boat.  This card does not like linux.  Any help would be appreciated.

Ha! It figures that as soon as I'm about to give up I find a solution.  Try this howto, it worked for me using a wg511v2 on an old gateway 450sx4...
[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29")

I'll add that the howto uses ver 1.29 of ndiswrapper but I used the latest, 1.34, without trouble.  I'm also using Xubuntu 7.04 Herd2 so I can't say how well this works with edgy or dapper.

Hi all,

I am a **COMPLETE** newbie at Linux, and I tried a couple of months ago to get Dapper working on an old laptop (Dell Inspiron 7000). Ubuntu installed no problem, but I couldn't get connected to the Internet.

I have since purchased a wireless router (Netgear DG834G) and a wireless PCMCIA card for the laptop (Netgear WG511 v2).

In the past hour or so, I have followed the above guide to the letter (apart from the latest version of ndiswrapper - 1.37) and my wireless connection to my router is working perfectly!!!!

The only compromise I had to make was to change my router setting to be WEP encrypted instead of WPA encrypted. However, my next task is to find a way to enable the WPA encryption - can anyone help?

Again, the above procedure is excellent - many thanks for the link crysys.

EDIT: Forgot to mention - I am typing this message via my wireless connection!

---

### Post by theRevMom on 2007-02-10
Well Bry, I'm happy for you.   But... I followed them to a T as well and I kept getting errors.  The final straw for me is that it says it cannot open Mrv8000c.inf: 

No such file or directory at /usr/sbin/ndiswrapper line 174.

When I rund the ndiswrapper -l I get:
* :invalid driver! 
mrv8000C : invalid driver!
wg511v2 : invalid driver!
yourwifi : invalid driver!

I have no idea where "yourwifi" came from
the wg511v2 comes from a previous attempt to install from the WinXP *inf file using directions on another post.
And the mrv8000c comes from this attempt.  

I'm reaching max out here.  I'm tempted to give up.  Anyone have any suggestions how to repair these idiot errors?  (Yes, I'm the idiot!)

:confused:

---

### Post by Floppyjoe on 2007-02-10
You will need to delete those invalid drivers by using the following:

```
ndiswrapper -l
```
to list the invalid drivers and then:
```
ndiswrapper -e drivername
```
Where drivername is the name of the listed invalid driver.

Then you will have to try to install them again making sure the your terminal is in the proper directory where the driver files are. Also make sure you spell it correctly because the names are case sensitive. 

I would try to go through your tutorial again.

Good luck!
Floppyjoe

---

### Post by theRevMom on 2007-02-10
Joe, 

I get an error when I run the second command.  

"Can't remove directory /etc/ndiswrapper/mrv8000c (permission denied) at /usr/sbin/ndiswrapper line 128"

suggestions?

Okay.... ;used the sudo. and three removed.  But there is a fourth..

ndiswrapper -l renders:
* : invalid driver!


When I try to remove * using the same line, it give me the usage options for NDISWRAPPER

??

---

### Post by gradedcheese on 2007-02-10
run those command with sudo:

sudo ndiswrapper -e drivername

---

### Post by theRevMom on 2007-02-10
Okay.  I'm going through the directions again.  Now I've got another stopper.

In Step 3 - Prepare the Linux build environment
Install the correct headers for your version of Ubuntu: (don't worry if it tells you that yours are up to date.)

user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r` 
user@ubuntu:~$ sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build

When I do this (I'm running Dapper), I get a list of possible headers.  at the end it says 
"You should explicity select one to install."

Okay, which one?

---

### Post by gradedcheese on 2007-02-10
run:

uname -r

you will get a response like "2.6.17-10-386", then pick from the list based on that (ex: "linux-headers-2.6.17-10-386")

---

### Post by theRevMom on 2007-02-10
thx.... stand by.... I really appreciate your help!

---

### Post by theRevMom on 2007-02-10
I'm back to the same error.:

aaron@aaron:~/tew-421pc/Drivers/Windows XP$ sudo ndiswrapper -i Mrv8000c.inf
installing mrv8000c ...
couldn't open Mrv8000c.inf: No such file or directory at /usr/sbin/ndiswrapper line 174.


So, how do I find the ndiswrapper line 174 error's solution?

---

### Post by gradedcheese on 2007-02-10
this means "hey, this file called Mrv8000c.inf doesn't exist" ...where did you put that file?  does it show up if you do 'ls'?

---

### Post by theRevMom on 2007-02-10
I'm nbot sure what you  mean by "do "is"?

Here's the results of DIR
aaron@aaron:~/tew-421pc/Drivers/Windows XP$ dir
Mrv8000c.cat  Mrv8000c.INF  Mrv8000c.sys

So it's in that directory.... is the problem with the CAPS?
Is Dapper case sensitive?

:confused:

---

### Post by gradedcheese on 2007-02-10
Linux is case sensitive :)  As are pretty much all systems, except for that Microsoft one.  

Also, I meant run:

```

ls

```

in the shell.  It's the same as 'dir', essentially.  Anyhow:

```

sudo ndiswrapper -i Mrv8000c.INF

```

---

### Post by theRevMom on 2007-02-10
Okay. So I went back and did the caps.  It said the driver was already installed.  But it also came up invalid.  

So, I did 

sudo ndiswrapper -e mrv8000c 

to remove it.

When I do 

sudo ndiswrapper -l 

I get

* : invalid driver!

How does one remove * ?

---

### Post by theRevMom on 2007-02-10
Okay, card present.  But when I ran iwconfig, it returned:
lo       no wireless extensions
eth0   no wireless extensions
sit0    no wireless extensions

Hmm.... is it not seeing  wlan0?

---

### Post by gradedcheese on 2007-02-10
try:

lsmod | grep ndis

does that respond with anything?  If not:

sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart

---

### Post by theRevMom on 2007-02-10
> **gradedcheese said:**
> try:

lsmod | grep ndis

does that respond with anything?  If not:

sudo modprobe ndiswrapper

FATAL: Error inserting ndiswrapper (/liv/modules/2.6.15-28-386/kernel/drivers/net/diswrapper/ndiswrapper.do): Invalid argment

sudo /etc/init.d/networking restart
*Reconfiguring network interfaces...
/etc/network/interfaces:28: dulicate interface
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:28: duplicate interface
ifup:couldn't read interfaces file "/etc/network/interfaces"

Does that translate into anything meaningful to you?  I'm :confused:

---

### Post by gradedcheese on 2007-02-10
Yes.  Your /etc/network/interfaces file is filled with junk (probably from your multiple attempts at adding/removing the driver), also the ndiswrapper module fails to insert, and thus you don't have WiFi (until that's fixed).  Please post the contents of /etc/network/interfaces here (you can open the file in a text editor or run "cat /etc/network/interfaces").

---

### Post by theRevMom on 2007-02-10
Here's the file.... 

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0

iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid aaronlap
wireless-key 53902cce3c
auto wlan0

iface eth3 inet static
address 192.168.1.111
netmask 255.255.255.0
gateway 192.168.1.1

auto eth3

iface eth0 inet dhcp

auto eth0

-------------------------------------------------------------------------------------------

that computer will not connect even with the RJ45 connection.... tho it did before I started this process. I'm sitting with it on the desk top next to the E-machine running Dapper just fine over the wired network.

---

### Post by gradedcheese on 2007-02-10
Ok, here's what I suggest we do:

1) identify what the actual interfaces you have are
2) clean up the /etc/network/interfaces file
3) very carefully follow the instructions again to install ndiswrapper and the Marvell Windows driver, then modprobe the ndiswrapper driver
4) make sure everything is ok by checking lsmod
5) get you online

Please post the contents of /etc/iftab (they should be in the form "interface MAC_address") for step 1.

---

### Post by theRevMom on 2007-02-10
Results of  cat /etc/iftab

eth0 mac 00:06:5b:e6:ab:08 arp 1
eth1 mac 00:50:04:29:84:92:arp 1
eth2 mac 00:01:02:e3:b9:b6 arp 1

-------------------
I have an integrated network port, a modem, and the wireless PCMCIA.

---

### Post by gradedcheese on 2007-02-10
Alright.  Looking at your MAC prefixes: eth2 looks like a 3COM, as does eth1.  While eth0 looks like Dell.  In case you're curious, the MAC prefixes are listed here: [http://standards.ieee.org/regauth/oui/oui.txt](http://standards.ieee.org/regauth/oui/oui.txt)  That said, 00-50 is usually Marvell, I bet that's the PCMCIA card in question.

Lets just remove everything except for eth0 for now.  You can remove something from /etc/network/interfaces by putting a '#' as the first character on the line.  Please open the file like this: "sudo gedit /etc/network/interfaces" and remove the lines about eth1, eth2, eth3.  Leave eth0 and lo alone though.  Now save the file and exit gedit, and restart networking:

sudo /etc/init.d/networking restart

Having done that, please carefully run through the ndiswrapper setup and Windows driver install (using the instructions you were using before).  Post here if you run in to any errors or other trouble, and keep in mind that you need to run certain things with 'sudo' and that all files are case sensitive.  When you're done, you should be able to load the driver like this:

sudo modprobe ndiswrapper

and then restart networking again.  'iwconfig' should then show you a new wireless interface.

---

### Post by theRevMom on 2007-02-10
I'm not sure it's an error, but when I get to this instruction:
Using ndiswrapper we can list the installed driver to make sure that we have it:

user@ubuntu:~$  ndiswrapper -l

the response is not the same as in the instructions.  There appear to be two drivers installed:

* :driver installed
        device (11AB:1FAA) present (alternate driver: mrv8k
mrv8000c : driver installed
        device (11AB:1FAA) present (alternate driver: mrv8k)


I'm not sure what the "*" is.

When I explore the file structure, there's a folder * at
/etc/ndiswrapper/*

---

### Post by gradedcheese on 2007-02-10
Interesting.  I don't know much about ndiswrapper specifically, but perhaps this * thing isn't a problem.  However naming a file or folder '*' in a Linux file system is a terrible idea, I wonder why they did that?  '*' generally implies wildcard, for example 'file*' means "anything starting with 'file'", including file1, file12, etc.  So, if you run:

```

ls -al /etc/ndiswrapper

```

what do you have?  Assuming that it's safe to continue, lets see if you can get through the instructions to where we can 'modprobe' the driver and make sure it's up and running.

---

### Post by theRevMom on 2007-02-10
> **gradedcheese said:**
> Interesting.  I don't know much about ndiswrapper specifically, but perhaps this * thing isn't a problem.  However naming a file or folder '*' in a Linux file system is a terrible idea, I wonder why they did that?  '*' generally implies wildcard, for example 'file*' means "anything starting with 'file'", including file1, file12, etc.  So, if you run:

```

ls -al /etc/ndiswrapper

```

what do you have?  Assuming that it's safe to continue, lets see if you can get through the instructions to where we can 'modprobe' the driver and make sure it's up and running.

ls -al /etc/ndiswrapper   returns:
total 12
drwxr -xr-x   3 root root 4096 2007-02-10 21:30 .
drwxr -xr-x 109 root root 4096 2007-02-10 21:29
drwxr -xr-x 2 root root 409602007-02-10 15:44[COLOR="RoyalBlue"]*[/COLOR]

and the * is in [COLOR="RoyalBlue"]Blue[/COLOR]

---

### Post by theRevMom on 2007-02-10
sudo modprobe ndiswrapper
returned:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-28-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

same as before....](*,)

---

### Post by gradedcheese on 2007-02-10
It's ok, we'll get it working.  Now, you're following:

[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

and if so, you did step 1 (remove existing ndiswrapper) and went to step 5 (since you don't need to install the headers and download ndiswrapper again), right?

---

### Post by Floppyjoe on 2007-02-10
You possibly should remove that * driver with:
```
sudo ndiwrapper -e *
```

---

### Post by theRevMom on 2007-02-10
I've gone back again to step one.  Again.  The ndiswrapper will not uninstall.  If it was installed with MAKE, I don't know what directory it is in.  

I'm really not a ditz!  I've always been able to figure out all things computer.  This is driving me nuts!

Ah, but on the bright side, I'm now typing from the unit through the integrated RJ45 port

---

### Post by gradedcheese on 2007-02-10
"If you have an existing copy that you installed using make then change to the driver's directory and remove it using make:"

so, you cd to the directory where you ran 'make', and you run 'make uninstall' -- does that work?

---

### Post by theRevMom on 2007-02-10
okay.  I found it and did the make uninstall.  I get the following error:

NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places. 
Run uninstall as many times as necessary until no "removing messages appear below.
Make: ***[uninstall] Error 1

---

### Post by Floppyjoe on 2007-02-11
> **theRevMom said:**
> okay.  I found it and did the make uninstall.  I get the following error:

NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places. 
Run uninstall as many times as necessary until no "removing messages appear below.
Make: ***[uninstall] Error 1
I get that too when uninstalling. I think you are good to go and ready to reinstall.

---

### Post by theRevMom on 2007-02-11
okay.  got to step 5 again.  results below.

aaron@aaron:~/ndiswrapper-1.37$ make
make -C driver
make[1]: Entering directory `/home/aaron/ndiswrapper-1.37/driver'
Can't find kernel build files in /lib/modules/2.6.15-28-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/aaron/ndiswrapper-1.37/driver'
make: *** [all] Error 2
aaron@aaron:~/ndiswrapper-1.37$


so, how do I give the path to the kernel build directory?  And where would that be?:/

---

### Post by Floppyjoe on 2007-02-11
Try the command:
```
sudo make
```

---

### Post by theRevMom on 2007-02-11
yeah. did that.  went back to step 3 and am doing the linux headers thing. again.

oKAY.... I am cooking.... I'm to step 6 and the LIGHT on the card is ON!!!

---

### Post by gradedcheese on 2007-02-11
the "linux headers thing" is installing the linux kernel headers.  you only do it once, if you have them installed, you can skip that step.  To check:

ls /usr/src/

do you have 'linux-headers-2.6.something' in there (matching "uname -r" output)?  If so, then you're all set.

---

### Post by gradedcheese on 2007-02-11
> **theRevMom said:**
> yeah. did that.  went back to step 3 and am doing the linux headers thing. again.

oKAY.... I am cooking.... I'm to step 6 and the LIGHT on the card is ON!!!

Good work!  Now run "iwconfig" and post the output.

---

### Post by theRevMom on 2007-02-11
aaron@aaron:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"flyinghermes"
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:0F:66:AF:BE:46
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm
          RTS thr:2346 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

aaron@aaron:~$ sudo gedit /etc/network/interfaces




Okay, I'm encripted at only 64bits... the instructions give for 128.... will going through the system administration networking window take care of that?

---

### Post by gradedcheese on 2007-02-11
that looks great!  are you able to get online now?  you can run 'ifconfig wlan0' to see your IP address (if any)

> 
Okay, I'm encripted at only 64bits... the instructions give for 128.... will going through the system administration networking window take care of that?

yeah, you can now use the usual Networking graphical tool to set things up.

---

### Post by theRevMom on 2007-02-11
rebooting with just the wireless (no rj 45)

can't find the router.....  checking wep

---

### Post by theRevMom on 2007-02-11
netstat -rn returns an empty routing table.

System > Administration> Networking to Network settings.  Wireless conncetion is not configured.  Configured it.
Activated it.
checking connectivity.

Netstat -rn still returns an empty routing table.

still can't connect to the net using Firefox

cannot connect to the router at it's address in firefox.

---

### Post by Floppyjoe on 2007-02-11
How are you connecting to the internet with wifi? Are you using a program like network-manager or are you configuring your connection manually in the configuration files?

---

### Post by theRevMom on 2007-02-11
> **Floppyjoe said:**
> How are you connecting to the internet with wifi? Are you using a program like network-manager or are you configuring your connection manually in the configuration files?

Q1.  I'm not sure what you mean?  How am I connecting to the net to post here?  I have a hardwired computer sitting beside the one I'm working on.  The laptop has a wireless card (we've been working on getting it running) and I have a LINKSYS BEFW11S4 directly above my head.

Q2.  network manager?  I used the System>Administration>Networking Network settings applet.


I'm pretty sure this has to do with the network settings.  The card can see the router (and my neighbor's).  I just can't log on to it. Networking issue now, not the card.

---

### Post by Floppyjoe on 2007-02-11
Can you post the output of the file /etc/network/interfaces?
```
sudo gedit /etc/network/interfaces
```
and:
```
iwconfig
```

---

### Post by theRevMom on 2007-02-11
auto lo
iface lo inet loopback

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

auto eth0
iface eth0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
#wireless-essid aaronlap
#wireless-key 53902cce3c
#auto wlan0

#iface eth3 inet static
#address 192.168.1.111
#netmask 255.255.255.0
#gateway 192.168.1.1

#auto eth3

iface wlan0 inet dhcp
wireless-essid flyinghermes
wireless-key s:961beb53c8

auto wlan0

--------------------------------------------------------


aaron@aaron:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any
          Mode:Managed  Frequency:2.432 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm
          RTS thr:2346 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.




-------------you have the patience of a saint.... thank you!:KS

---

### Post by Floppyjoe on 2007-02-11
If you are not using the network-manager applet(if you have not installed network-manager and network-manager-gnome then you are not using the network-manager applet) to connect to the internet then you should possibly change your /etc/network/interfaces file to the following and where it says wireless-channel put the channel that your router is set to:
```
sudo gedit /etc/network/interfaces
```
Edit the file to this:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid flyinghermes
wireless-channel 6
wireless-mode managed
wireless-key s:961beb53c8
```

---

### Post by theRevMom on 2007-02-11
Did as you posted. 

The card cannot get the router to assign it a dhcp.  the networking restart command returns a long list of attempts with no DHCP offers received.

The router is set to WEP.... would it be easier to go WPA?

---

### Post by Floppyjoe on 2007-02-11
Wep is definitely easier. It is also less secure. 
Do you have to modprobe ndiswrapper after a reboot?
If so issue the command:
```
ndiswrapper -m
```
and edit the file /etc/modules:
```
sudo gedit /etc/modules
```
And add the word ndiswrapper. Then save and exit gedit.
Also you need to go into System/Administration/Networking and disable your wired ethernet interface because only one network interface should be enabled at one time.Then reboot.

---

### Post by theRevMom on 2007-02-11
rebooting

......

firefox still can't connect.

okay.... I had the network key set at ascii not hex.... waiting to see if this makes a difference

nope...

suggestions?

---

### Post by Floppyjoe on 2007-02-11
What is the output of:
```
ifconfig
``` If this shows you have a IP address assigned to wlan0 then disregard the next command
```
sudo dhclient wlan0
```
If you have a IP address assigned in wlan0 after ifconfig can you ping google.com

Can you try connecting without encryption?
Usually when i set up my wireless I first see if I can connect without encryption and then add it later when I get it working. You will need to turn off encryption on your router and edit the file /etc/network/interfaces to remove the wireless-key line.

Edit:
I'm getting a bit tired over here and I think I will turn in. Sorry to leave you hanging but there is always tomorrow or should I say later today.

---

### Post by theRevMom on 2007-02-11
I really appreciat your help..... It's been a long 12 hours.

g'nite'

---

### Post by Floppyjoe on 2007-02-11
I am having difficulty seeing why you should not be able to connect already. 
Do you have Mac address filtering turned on on your router?
If so you will have to add you computers Mac address to the accepted list.

---

### Post by theRevMom on 2007-02-11
No Mac Filtering.  The only thing that is enabled in the MAC filtering tab is Block Anonymous Internet Requests.

All of the VPN passthroughs are enabled.

I'm going through the settings on each now and comparing.  It works just fine if I turn the encryption off.  So it seems to be an encryption issue. 

I don't know what the encryption on the card is set to ... does it matter?  The router is set to 64 bits 10 hex digits.

The encryption key in the laptop settings is the router's WEP key 2.  The router is set to default to key 2.  

I can't locate a place in the laptop settings to enter the passphrase.... should there be a place?

The other thing that is different here is that the wired connections all have assigned IPs.  

Other ideas?

---

### Post by Floppyjoe on 2007-02-11
> **theRevMom said:**
> No Mac Filtering.  The only thing that is enabled in the MAC filtering tab is Block Anonymous Internet Requests.

All of the VPN passthroughs are enabled.

I'm going through the settings on each now and comparing.  It works just fine if I turn the encryption off.  So it seems to be an encryption issue. 

I don't know what the encryption on the card is set to ... does it matter?  The router is set to 64 bits 10 hex digits.

The encryption key in the laptop settings is the router's WEP key 2.  The router is set to default to key 2.  

I can't locate a place in the laptop settings to enter the passphrase.... should there be a place?

The other thing that is different here is that the wired connections all have assigned IPs.  

Other ideas?
I think you can enter a password in System/Administration/Networking with the correct interface. 
Now do you mean that your IP addresses are all static IP's. I have not thus far used a static IP and am unfamiliar on how exactly to set those up. I'm sure it is pretty simple though. But one would think that if it worked getting a dhcp offer without encryption that it should also work with encryption.

---

### Post by theRevMom on 2007-02-11
The hardwired computers on the network all have static IP addresses.  

This afternoon I can't get the card to see the router. 

Whew.  sixteen hours of this is getting to me.

EDIT:

rebooted.  Turned off Encryption in the router.  Can access web.  Cannot see the other computer in the router.

---

### Post by Floppyjoe on 2007-02-11
I'm assuming your router is set up as a dhcp server. I don't know how else your card could have got a dhcp offer from it otherwise. 

Getting your computers to network together is a whole new can of worms for me.
I have been able to share a network printer with all of my computers using cups.

---

### Post by theRevMom on 2007-02-11
FloppyJoe and GradedCheese -- The two of you have been a HUGE help to me.  THANK YOU!!!  I really appreciate your time and input.  Whether or not this ever sees the REST of the network is immaterial compared to being able to use it away from a set place.  

The laptop belongs to my son who is a college student (see TotalNewB).  He needs wireless in the classroom.  THANK YOU both for being there to help me get this up and running.  Total kudos....

---

### Post by Floppyjoe on 2007-02-11
If you are planning to roam with the laptop i might consider installing network-manager and network-manager-gnome. But with this utility you need to comment out all the network interfaces in /etc/network/interfaces except for the lo interface using # at the beginning of the lines.. Then you need to disable all your network interfaces in System/Administration/Networking. Network-manager then takes control of these interfaces. If you install it, it will not appear in any of the drop down menu's but will be an applet on the top menu bar.

---

### Post by theRevMom on 2007-02-11
What would be the name of the application in the Add/Remove Applications menu? 

EDIT:  In Internet options I found two:  KnetworkManager and Network Manager.  Suggstion?

I've isolated the communication issue to the WEP encryption.  I'm researching options for it. now.

---

### Post by Floppyjoe on 2007-02-11
Under Internet-Network Manager-Network Manager applet

---

### Post by theRevMom on 2007-02-11
thx.  installing now.  :guitar:

---

### Post by Floppyjoe on 2007-02-11
You may need to log out and back in to get it to work or alternatively reboot.

---

### Post by theRevMom on 2007-02-11
OH &&&&^%$%.  I rebooted.  It's hung at 
*Loading hardware drivers.....
firmware_helper[3077]: wait_for_sysfs: main: error loading 'lib/firmware/mrv8k-b.fw' for device '/class/firmware/0000:03:00.0' with driver 'mrv8k'
udevd-event[3003]: wait for sysfs:waiting for 'sys/devices/platform/i8042/serio0/serio2/bus' failed.

then it went dead.

EDIT:  restarted using the power button.  hit the escape button to restart with from recovery.  got to the network and stopped flowing.... at


[17179629.28400] ADDRCONF (NETDEV_UP): eth0: link is not ready
[17179629.284000] IPv6 over IPv4 tunneling driver

and stopped....

---

### Post by Floppyjoe on 2007-02-11
> **theRevMom said:**
> OH &&&&^%$%.  I rebooted.  It's hung at 
*Loading hardware drivers.....
firmware_helper[3077]: wait_for_sysfs: main: error loading 'lib/firmware/mrv8k-b.fw' for device '/class/firmware/0000:03:00.0' with driver 'mrv8k'
udevd-event[3003]: wait for sysfs:waiting for 'sys/devices/platform/i8042/serio0/serio2/bus' failed.

then it went dead.
Can you reboot into gnome failsafe mode and remove network-manager then? You might need to press escape at boot-up.
I'm off to church now will be back at 9-9:30

---

### Post by Floppyjoe on 2007-02-11
Did you find out what went wrong?

---

### Post by theRevMom on 2007-02-11
no.  I forced a reboot in failsafe mode.  
I uninstalled the Network Manager, but it would not uninstall.  It is running.  Even after another reboot and uninstall.

I also can't get a terminal window open.

And I'm back to not seeing the card, the network, or anything. 

EDIT:  Oh and now the shut down won't work.  I'll either have to wait for it to go into hibernation or force a shut down with the power switch.... which is how the last problem started..... ugh.

 I'm hanging it up for the day.  Too many hours doing this and not getting the rest of life worked on.  
Thanks for your help.  I'll come back when I've got time again.

---

### Post by smCw6GNakQn300£ on 2007-02-12
Hi folks,

reading the rest of this thread, I guess I was just lucky!

However, I do have a problem with this.
After having it all running perfectly, a couple of things happened at the weekend:
- I tried installing "EasyUbuntu" to get some standard items installed. This kept erroring when trying to download/install items, so I eventually un-installed it
- Ubuntu installed some system updates

Now, the system doesn't even recognise my wireless card any more

I've still to try running the procedure again (which steps can I leave out?), but am I correct in thinking that the system updates for Ubuntu have overwritten some of the files that I updated when running the procedure?

If so, is there a way to prevent this from happening, or will I have to repeat the procedure every time Ubuntu updates itself??

(I am running Edgy and am a complete newbie to all things Linux)

Cheers

---

### Post by theRevMom on 2007-02-12
Bry
A Similar thing happened to me.  I started from scratch except that I didn't download NDISwrapper again because I still had the TAR.GZ     Since then, I've had to reload the whole system again..... I installed the Network Manager.  It wasn't pretty.

Good luck.

---

### Post by TotalNewb on 2007-02-14
I've got my WG 511 installed... but now, when I boot up, it freezes at "Loading manual drivers"... sooo, now what? any ideas?

---

### Post by smCw6GNakQn300£ on 2007-02-15
> **theRevMom said:**
> Bry
A Similar thing happened to me.  I started from scratch except that I didn't download NDISwrapper again because I still had the TAR.GZ     Since then, I've had to reload the whole system again..... I installed the Network Manager.  It wasn't pretty.

Good luck.

Well, after a complete re-install of the system (hammer to crack a nut!!), and following the guide again, my wireless is all working flawlessly again.

Now, if I can just create a script to perform the guide operations, in case it happens again...

---

