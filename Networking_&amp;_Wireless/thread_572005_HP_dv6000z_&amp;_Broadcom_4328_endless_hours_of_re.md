---
title: "HP dv6000z &amp; Broadcom 4328 endless hours of research! Install &amp; configure in minutes!"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by adamos on 2007-10-09
I wanted to post this so I can help other people with the installation of the wireless card.
my specs: HP DV6000z, amd x2 TL56, 2gb ram, nvidia 6150, [COLOR="Red"]BROADCOM 4321AG draft n(4328 chipset)
[/COLOR]
First off to install Ubuntu 7.04(as of 6/9/08 I did a fresh install of Ubuntu 8.04 and it still works) you need to press F6 in the first screen when you boot and type [COLOR="Red"]noapic[/COLOR] and then press enter to start installing. (Skip this step for Ubuntu 8.04) 
I have a dual boot configuration so I had to configure my partitions. I put manual instead of automatic and I deleted the previous Linux partitions. I created a new 20gb ext3 and set **[COLOR="Red"]/[/COLOR]** for mountpoint. after this i created another partition of 350mb for [COLOR="Red"]swap[/COLOR]. The installation finished flawlessly. NOTE: if you don't put noapic, the computer will freeze after a while and you will get the message from GRUB fatal error. I learned the hard way :)

** If you tried to compile / install ndiswrapper and you failed go [here]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/") to uninstall it. This tutorial is intended for a fresh install. **   

WIRELESS CONFIGURATION
*Don't use the crappy drivers from HP. THEY DONT WORK. I used dell's drivers.(weird)*

CODE:

> sudo apt-get update
sudo apt-get install build-essentials
sudo apt-get install linux-headers-`uname -r`
wget [http://ftp.us.dell.com/network/R151517.exe](http://ftp.us.dell.com/network/R151517.exe)

now go to System/Administration/Synaptic Package Manager   *(I am doing this step because most of the people cannot compile the damn ndiswrapper. it happened to me)*

search for ndiswrapper - from the results shown select ndiswrapper-common & ndiswrapper-utils-1.9 and install them.

[COLOR="Red"]sudo -s
echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
exit[/COLOR]

after this you need to reboot!

go to the directory that you downloaded the R151517.exe
unzip -a R151517.exe
cd DRIVER
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l

*you should get a message that the driver is present and hardware found*

sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo -s
echo ndiswrapper >> /etc/modules
exit

sudo iwlist scanning    ** BINGO ** wlan0 works!

Now go to System/Administration/Network Tools - select the Wireless interface and configure your settings. Select the essid and put your password. In the connection setting where it says configuration put automatic configuration (DHCP) ** For Ubuntu 8.04 look at the bottom how to do the final step **

do a reboot now and you are all set!
open firefox to check if it works. It it doesnt - I did in terminal sudo modprobe ndiswrapper and I reconfigured the setting and it worked.


Some users noted that they have to restart after the final step to get the wi-fi working.


for any further assistance email or pm me

*** I NOTICED THAT SOMETIMES THE DEVICE STOPS WHEN YOU RESTART ***

here is the solution:   sudo ifconfig wlan0 up

*** 4/16 I upgraded to 7.10 with sudo apt-get dist-upgrade and wireless still works..***
*** 4/28 I upgraded to 8.04 and wireless still works! ***
sometimes when you switch between wireless networks you have to do a sudo /etc/init.d/networking restart

*** 6/11 For Ubuntu 8.04 fresh installations - After you finish the whole procedure go to System - Administration - Network and configure your wireless settings. I tested it on WPA2 Personal and works like a charm. 

*** I will make the how-to in a bash script to automate the process(maybe in two weeks). I am very busy with my job setting up new servers. If anyone wants to contribute pm me! ***

Thanks,
Adam

---

### Post by manro on 2007-10-23
Thanks adamos!

Just to let you (and the rest of the folks) know that this works on my HP dv9946us that have a Broadcom 4328 (rev03) chip and is running Guisty i386  distribution.

The only issue I found was that if I stop broadcasting my ssid Guisty do not connect to my network (I previously configure my connection with my ssid of course)

Thank a lot buddy! ...trying to make this card work was driving me crazy! :)

Best regards,
Manro

---

### Post by adamos on 2007-10-24
no problem my friend, this card was a pain in the *** to configure.. but my research worked :)

---

### Post by manro on 2007-10-24
> **adamos said:**
> no problem my friend, this card was a pain in the *** to configure.. but my research worked :)

Man, it really do!

Regards,
Manro

---

### Post by DeadToad on 2007-10-25
It was such a pain in the Azz that I uninstalled Ubuntu 7.10 and went back to Vista.

---

### Post by EXCiD3 on 2007-10-25
:'( Nooooooooo!!!! Not another Windows user! :'(

Haha, if you want a good running install just use Feisty. Gutsy is crap for the moment, not matter what they say, its not as reliable as Feisty is.

---

### Post by ebsmith1515 on 2007-10-25
I have a couple problems, but it seems like I am really close.  When I run the iwlist scan it looks fine, and I see names of wireless networks that I know should be there, but when I go to network tools and select the wireless interface (yes it is there), the configure button is grayed out.  And I can't get it to do anything wirelessly.

---

### Post by ebsmith1515 on 2007-10-25
Well I actually just rebooted for about the fourth time and it decided to work.  And I didn't even have to configure it.  So it works now. (I'm posting ths message unplugged :).  Thank you very much.  This worked great for my BCM4321 card.

---

### Post by adamos on 2007-10-27
as i stated in my write up i had to reboot twice.. but as soon as it starts thats it :)
also, gutsy = bad experience for me. i am staying with feisty for a while


Adam

---

### Post by o.besner on 2007-12-03
I can't believe someone finally found how to use a 4321 with Ubuntu.

Thanks alot !

---

### Post by kevdog on 2007-12-03
Persistence pays off, however the solution you found works for other broadcom cards also.  Checking dmesg might have helped the debugging process also.

Anyway, glad you got it working.  Hope you edited you grub file to add the noapic boot flag.

---

### Post by adamos on 2007-12-21
thanks for your kind comments.

it was a lot of work!

now i am stuck on solaris 8 because of my job.


i am trying to convince them to use ubuntu server on a new project we are working on right now.


Thanks again,

Adam

---

### Post by mryumyum on 2008-02-08
I followed your walkthrough and everything seems ok as far as getting the driver loaded up:

        matthew@Ubuntu:~$ ndiswrapper -l
        bcmwl5 : driver installed
                device (14E4:4328) present

but for some reason:

        matthew@Ubuntu:~$ sudo iwlist scanning
        lo        Interface doesn't support scanning.

        eth0      Interface doesn't support scanning.

The wireless card isn't even on the list (wlan0 I believe)!

This is the most recent version of NDISWrapper, so I don't think that's the issue. I've tried hours of different things and plenty of drivers and nothing seems to work. I finally got it to at least admit that my device was present (I didn't really do anything, it just started finding it one time), so I guess I'm progressing in the right direction. A final boost into wireless nirvana would be nice.

Thanks for your help! (You have no idea how much it's appreciated.)

---

### Post by mryumyum on 2008-02-08
OMG, YOU'RE AMAZING!!!!!

You didn't even reply yet and you managed to fix it!!

As you may have guessed, it works now.  I just rebooted AGAIN, and it works. I have an HP dv6458 with a Broadcom 4328 wireless chipset. For those who are wondering what to do, just follow adamos' instructions completely and then restart your computer a few times with the wireless switch set to the on position (right) so that you will know it is working.  It might just be coincidence, but the last time I restarted before it worked, I unplugged my ethernet cable out of my laptop, so maybe it continued to detect stuff until it found something.  Who knows, Gutsy is pretty shitty as far as that goes.

Anyway good luck to the others of you and definitely try adamos' solution even if you don't have the exact same setup.

:):):):):):):):)

---

### Post by DEW26M on 2008-02-12
I realize this forum is for the dv6000z, but i have the dv2622ca, which uses the same wireless card. I followed these instructions to the letter, and still i have no wireless capabilities!! I have tried every other method in the forums, with no avail PLEASE HELP ME ?!?!?!

---

### Post by swiftfoottim on 2008-02-21
Wow, I am so grateful to you!  I'm running an HP zv6000 with the 4306 rev 03 chipset and couldn't find anything.  The Dell drivers listed here worked first try.  Just make sure to reboot.  After three nights of trying to configure just my wireless, I can finally move on to other configuration options for this whole new OS! 

A thousand and one thanks to you!

---

### Post by Victormd on 2008-02-22
Like everyone else, Thanks so much for this thread... Now the tough part, my network adaptor is detected BUT no connection. I've restarted I don't know how many times and still no go. I'm running an HP dv6458se and broadcom wireless and I know it should work, but for some reason that I can't explain, it doesn't! Everytime I go into network tools, loopback interface (lo) is selected and no "configure" possibilities. Then I have wireless interface (wlan0) [does not configure] and wireless interface (wlan0:avahi) that, when I click configure, shows "the interface does not exist"... HELP!!!

Got it up and running... had to compile ndiswrapper from source and that did the trick!

---

### Post by harold4 on 2008-02-24
Anyone able to connect to Draft N using this method?  I can get on G just fine, and the card will see N, but not authenticate.

---

### Post by Denbert on 2008-02-25
Hi there,

every thing worked out as described - except the wireless lan....

Please see my network manager here: [http://www.hegnstoften.net/network.png](http://www.hegnstoften.net/network.png)

Seems to be working, but there is no working WLAN.

Any suggestions?

---

### Post by Victormd on 2008-02-25
Try compiling ndiswrapper from the source...

Look at this link:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

One of the best I've seen so far.

---

### Post by adamos on 2008-02-26
If you tried to install ndiswrapper before, follow the first three steps from [https://help.ubuntu.com/community/Wi...ndiswrapper%29](https://help.ubuntu.com/community/Wi...ndiswrapper%29)
and then try to do it like my writeup and i am positive it will work.

This procedure worked perfect for feisty. I haven't upgraded to Gutsy yet because of several issues that other users have with Gutsy. 

Thanks,

Adam

p.s: A cheap alternative solution is a usb dongle supported by ubuntu. linksys, edimax and some belkin versions work out of the box. I am currently using a alpha usb 500mw usb(>$100) and its amazing

---

### Post by Man Man on 2008-04-10
Hm, I feel like I'm close to getting it to work... I have an HP Pavilion dv2810us with an AMD Turion 64 X2 TL-60.  The wireless is listed as Broadcom Corporation BCM4310 USB Controller (rev 01).  I used the ndiswrapper from source to install the driver, but now it refuses to recognize the card:

> nikolai@ubuntu:~$ sudo ndiswrapper -l
bcmwl5 : driver installed
nikolai@ubuntu:~$ sudo ndiswrapper -l
bcmwl5 : driver installed
nikolai@ubuntu:~$ sudo ndiswrapper -m
module configuration already contains alias directive
WARNING: /etc/modprobe.d/blacklist line 27: ignoring bad line starting with '''
WARNING: /etc/modprobe.d/blacklist line 33: ignoring bad line starting with 'ls'
WARNING: /etc/modprobe.d/blacklist line 35: ignoring bad line starting with 'cd'
nikolai@ubuntu:~$ sudo modprobe ndiswrapper
WARNING: /etc/modprobe.d/blacklist line 27: ignoring bad line starting with '''
WARNING: /etc/modprobe.d/blacklist line 33: ignoring bad line starting with 'ls'
WARNING: /etc/modprobe.d/blacklist line 35: ignoring bad line starting with 'cd'


Help?!  I am COMPLETELY new to GNU/linux, so I have a hard time understanding close to 50% of the tutorials I've found.

---

### Post by Ayuthia on 2008-04-10
> **Man Man said:**
> Hm, I feel like I'm close to getting it to work... I have an HP Pavilion dv2810us with an AMD Turion 64 X2 TL-60.  The wireless is listed as Broadcom Corporation BCM4310 USB Controller (rev 01).  I used the ndiswrapper from source to install the driver, but now it refuses to recognize the card:



Help?!  I am COMPLETELY new to GNU/linux, so I have a hard time understanding close to 50% of the tutorials I've found.

The error messages that are showing up is telling you that /etc/modprobe.d/blacklist has some information that it does not like.  It looks like you might have pasted some commands into it.  Usually the blacklist file should have something like:
```
# Anything that starts with a '#' will be a comment
blacklist xxxx
```
Basically the file should only be blacklisting modules that you don't want to have start up.  If you need more help with this, please post lines 27-35 from /etc/modprobe.d/blacklist

---

### Post by Lazy-buntu on 2008-04-10
Currently I dual boot Windows Vista and Ubuntu 7.10 (Gutsy), but I'm running into a problem with my wireless.

I used ndiswrapper to install my wireless driver (broadcom chip =/ ) and the good news is I can see wireless networks when I do iwlist eth1 scan. (my wireless card is eth1--it doesn't appear as wlan0)

There's a problem though: I can see the networks, but I cannot connect to them. My network has a WEP key (hex) and a broadcasted ESSID. So, in my network tools I set my ESSID, put my WEP key in, and set my IP to DCHP.

I heard ipv6 can cause problems according to the built in help topics in ubuntu--it tells you to gedit /etc/modprobe.d/aliases and change ....... pf 10 ipv6    to      ........ pf 10 off--I did this and rebooted, no go. (I did change it back since then.)

Any ideas? (BTW: I can't get a wired connection, so I haven't been able to do any  updates)

---

### Post by Lazy-buntu on 2008-04-10
made my own thread: [http://ubuntuforums.org/showthread.php?p=4692890#post4692890](http://ubuntuforums.org/showthread.php?p=4692890#post4692890)

anything related to my problem please post there =)

---

### Post by Man Man on 2008-04-10
> **Ayuthia said:**
> The error messages that are showing up is telling you that /etc/modprobe.d/blacklist has some information that it does not like.  It looks like you might have pasted some commands into it.  Usually the blacklist file should have something like:
```
# Anything that starts with a '#' will be a comment
blacklist xxxx
```
Basically the file should only be blacklisting modules that you don't want to have start up.  If you need more help with this, please post lines 27-35 from /etc/modprobe.d/blacklist

Yep, because of another tutorial I followed, the blacklist file contained the driver I am trying to install.  So I fixed that, but I still have the problem that when I listed ndiswrapper drivers, there is no device linked to bclwm5.  I have tried to do this manually:
> 
nikolai@ubuntu:~$ lspci -n
00:00.0 0500: 10de:0547 (rev a2)
00:01.0 0601: 10de:0548 (rev a2)
00:01.1 0c05: 10de:0542 (rev a2)
00:01.2 0500: 10de:0541 (rev a2)
00:01.3 0b40: 10de:0543 (rev a2)
00:02.0 0c03: 10de:055e (rev a2)
00:02.1 0c03: 10de:055f (rev a2)
00:04.0 0c03: 10de:055e (rev a2)
00:04.1 0c03: 10de:055f (rev a2)
00:06.0 0101: 10de:0560 (rev a1)
00:07.0 0403: 10de:055c (rev a1)
00:08.0 0604: 10de:0561 (rev a2)
00:09.0 0101: 10de:0550 (rev a2)
00:0a.0 0200: 10de:054c (rev a2)
00:0c.0 0604: 10de:0563 (rev a2)
00:0d.0 0604: 10de:0563 (rev a2)
00:12.0 0300: 10de:0531 (rev a2)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:09.0 0c00: 1180:0832 (rev 05)
01:09.1 0805: 1180:0822 (rev 22)
01:09.2 0880: 1180:0843 (rev 12)
01:09.3 0880: 1180:0592 (rev 12)
01:09.4 0880: 1180:0852 (rev 12)
04:00.0 0280: 14e4:4315 (rev 01)
nikolai@ubuntu:~$ sudo ndiswrapper -a 14e4:4315 bcmwl5
WARNING: Driver 'bcmwl5' will be used for '14E4:4315'
This is safe _only_ if driver bcmwl5 is meant for chip in device 14E4:4315
nikolai@ubuntu:~$ sudo ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4315) present
nikolai@ubuntu:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.



Failure!  Confusion!

---

### Post by Gunzoid on 2008-04-10
Whoa!! 2800+ views! Must be related to my problem. 
I'm trying to install a Linksys WPC54G v.3 in Gutsy and doing way too much research without getting anywhere-except rebooting into WinXP constantly so I can get online and read more how-to's. 
I believe it uses the BCM43xx.
Here's the steps I used to install it:
Installed ndiswrapper-common and ndiswrapper-utils-1.9
Copied the NT drivers from the Linksys CD into /home/LinksysApapter
Renamed LSBCMNDS.inf and bcmwl5.sys to LSBCMNDS.INF and BCMWL5.SYS
in terminal> sudo ndiswrapper -i LSBCMNDS.INF
then> sudo depmod -a
sudo modprobe ndiswrapper
sudo modprobe -r acx
sudo gedit /etcmodprobe.d/blacklist and added "blacklist acx"
Plugged in wireless card and:
ndiswrapper -l
Output was:
lsbcmnds: driver installed
device (MAC) present (alternate driver: bcm43xx)
Hmmmmm....looks good so far....
sudo ndiswrapper -m
sudo gedit /etc/modules and added "ndiswrapper" at end of file.
Reboot- nothing.
No other interface shown- only loopback and eth0 (wired)
Card roaming-no networks found.
Nothing in Network Tools.

Soo..I'm lost. I've only been using Ubuntu for a couple of days and don't know my way around linux at all. It would be much easier if I could just get this wireless adapter running so I could get online in Ubuntu and not have to constantly reboot into Windows to learn this stuff. I've read everything I could find on getting this card recognized and thought I had picked a routine that would work-but no.

Any help would be very much appreciated.

---

### Post by Gunzoid on 2008-04-10
Well I'll be goddamned.
In total frustration and not knowing what the hell I was doing, I got my Linksys WPC54G v.3 running in Gutsy.
See my previous post for the install routine.
I ran these commands:
sudo modprobe -r bcm43xx (unloads the alternate driver bcm43xx in case it was running)
sudo gedit  /etc/modprobe.d/blacklist and added "blacklist bcm43xx" at the end of the file.
On reboot the card connected immediately and I'm running on it now.

I sure don't know if this is a legit way of getting that card running, but it worked. Maybe it will save someone else from tearing their hair out.

---

### Post by Ayuthia on 2008-04-11
> **Man Man said:**
> Yep, because of another tutorial I followed, the blacklist file contained the driver I am trying to install.  So I fixed that, but I still have the problem that when I listed ndiswrapper drivers, there is no device linked to bclwm5.  I have tried to do this manually:


Failure!  Confusion!
```
nikolai@ubuntu:~$ sudo ndiswrapper -a 14e4:4315 bcmwl5
WARNING: Driver 'bcmwl5' will be used for '14E4:4315'
This is safe _only_ if driver bcmwl5 is meant for chip in device 14E4:4315
```
I looked at the help info for using ndiswrapper -a and it mentions that this option is dangerous.  Not for sure what is meant by that, but you might be better off using 'sudo ndiswrapper -i bcmwl5.inf' instead.  You should try to remove that driver 'sudo ndiswrapper -e bcmwl5' and then install it again using the ndiswrapper -i method.  Not sure if that will help or not, but you will be going down the more common path.  If this doesn't help, can you provide your laptop make and model and also where you found your driver.

---

### Post by adamos on 2008-04-14
What wireless card are you using?

---

### Post by swiftfoottim on 2008-04-26
Ughh, I decided to do a complete reinstall to Hardy Heron this weekend and thought that I'd get the wireless going easily.  Followed this tutorial for  Gutsy and it worked well.  Now I'm left with this output when I try the install.

jared@jared-laptop:~/Desktop/Drivers/DRIVER$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down


Any thoughts?  I'm not sure if this means that the network device isn't working or if it just isn't getting anything.  Thanks for the help!

---

### Post by swiftfoottim on 2008-04-27
Don't I have to blacklist the old driver to get it working?  I can't get this going in Hardy Heron but I don't know enough about Ubuntu to decide if it should automatically work or if it's different.

---

### Post by swiftfoottim on 2008-04-29
Rolled back to 7.10 and it worked like a charm again.  Not sure if I'm missing something in 8.04 or what.  I did notice that the ndiswrapper -m command wasn't supported in Heron though.  I may have to consult the man pages for a solution to that one.

---

### Post by swiftfoottim on 2008-04-29
Okay, I did an update to Hardy Heron and the wireless didn't work.  However, I enabled the device in the restricted hardware manager while I had a wired connection to the internet.  There was an automated process and then I ran the sudo iwlist scanning and bingo, wireless worked.

Seems like there may now be a simple solution in Hardy Heron!  Woohoo!

Thanks for the tutorial again though, still led me in the right direction.

---

### Post by adamos on 2008-04-30
no problem, I did this when i was using 7.04, then i upgraded to 7.1 and now i am using 8.04 without a problem. sometimes when i switch networks ex. from my college wireless to my home wireless i have to do a **sudo /etc/init.d/networking restart** to get it up and running.

---

### Post by adamos on 2008-06-10
I did a clean install with 8.04 and I followed my tutorial and it was saying that the interface wasnt suupported. I went to System - Administration - Network and configured the Wireless Interfaces and it started working immediately.

Thanks,

Adam

p.s Maybe some day next week I will automate the process in a bash script because I was so lazy to follow my own write up (being a sysadmin you become frustrated typing the same commands for something you did before :) )

---

### Post by Denbert on 2008-06-10
> **adamos said:**
> 

p.s Maybe some day next week I will automate the process in a bash script because I was so lazy to follow my own write up (being a sysadmin you become frustrated typing the same commands for something you did before :) )

O'boy, I'd love to see a script for this.

:guitar:

---

### Post by deltaprime on 2008-06-16
nice :popcorn:

[SIZE=3][COLOR=Red]**HP dv2000 series works.**[/COLOR][/SIZE]

[I]**NOTE TO ADAM:**
had to restart after the tuto so i think you should include that as a final step.
and include how to cleanout the ndiswrapper for a fresh start before the tuto for others (had to do it twice :mad:  )[/I]

Finally lets call this thread (SOLVED) 

THANKS ADAM!:)

---

### Post by adamos on 2008-06-18
Thanks for the clarification. This tutorial was indented for a clean install but it seems like people try to install ndiswrapper before reading the tutorial and it doesn't work unless you clean up previous installation attempts.

---

### Post by bebops_lost on 2008-06-21
I have an HP tx1314 with a Broadcom 4321AG 802.11a/b/g/draft-n Wi-Fi Adapter and this guide worked beautifully.\\:D/
THANKS!

---

