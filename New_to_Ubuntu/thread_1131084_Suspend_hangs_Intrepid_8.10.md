---
title: "Suspend hangs Intrepid 8.10"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-04-20
On my children's computer, I've installed Intrepid 8.10 (dual-boot with Windows).

*Suspend* works fine with Windows. But with Intrepid, *suspend* hangs the machine and I have to turn the power off by pressing the power button for several seconds.

As an experiment, I booted the machine into recovery mode and chose "Drop to root shell prompt". I typed the command "suspend", and again the computer just hung.

Do you know how I can fix the suspend function?

---

### Post by Paddy Landau on 2009-04-21
I've discovered (see [another thread]("http://ubuntuforums.org/showthread.php?t=1125457")) that ndiswrapper is at cause.

In other words, ndiswrapper causes Intrepid to hang when suspending.

---

### Post by unutbu on 2009-04-21
I don't know if this will work, but the following looks easy to try, and is reversible, so perhaps its worth a go:

[https://help.ubuntu.com/community/NetworkManager/](https://help.ubuntu.com/community/NetworkManager/)
Search for the word "suspend".
The instructions there say it works for Dapper to Feisty. 
If you find there is no file called 
```

/etc/dbus-1/event.d/25NetworkManager
```

on your system, perhaps try 
```

/etc/init.d/NetworkManager
``` 
instead.

(According to [https://lists.ubuntu.com/archives/ubuntu-users/2008-June/148584.html](https://lists.ubuntu.com/archives/ubuntu-users/2008-June/148584.html) it sounds like the place where Ubuntu stores this script may have changed.)

---

### Post by Paddy Landau on 2009-04-21
Thanks for the idea. Unfortunately, it doesn't work. So back to the drawing board.

---

### Post by unutbu on 2009-04-21
What is the command you use to disable ndiswrapper? Something like
```

sudo modprobe -r ndiswrapper
``` or
```
sudo ifdown wlan0
```?

If you wrap that command in a script and get it to run upon suspend, shouldn't you be good-to-go? (Of course, resuming might be another matter).

If you edit
/etc/acpi/suspend.d/07-network-manager.sh 

to include a line like
```

echo "$(date): Running NM script" > ~/suspend.debug
```

can you confirm that the script is being run?

---

### Post by Paddy Landau on 2009-04-21
> **unutbu said:**
> What is the command you use to disable ndiswrapper?
My driver is rtl8187. I added it to the modprobe blacklist, and that prevented it from starting (so I had no wireless access). Perhaps it doesn't prevent ndiswrapper from starting; if so, then my test was invalid.

> **unutbu said:**
> If you edit
/etc/acpi/suspend.d/07-network-manager.sh 

to include a line like
```

echo "$(date): Running NM script" > ~/suspend.debug
```can you confirm that the script is being run?
Thank you for that idea. It confirms that the script is ***not*** being run.

That means that the suspend command hangs before it gets to the acpi commands!

Hmm... :confused:

Is there a log somewhere that I can check for error messages?

---

### Post by Paddy Landau on 2009-04-21
> **Paddy Landau said:**
> My driver is rtl8187. I added it to the modprobe blacklist, and that prevented it from starting (so I had no wireless access). Perhaps it doesn't prevent ndiswrapper from starting; if so, then my test was invalid.Actually, the test did work; it allowed the computer to suspend and resume, so I guess it was valid after all.

---

### Post by Paddy Landau on 2009-04-21
Right, a new spanner in the works...

Testing on my Hardy, whose suspend does work, I find the following for /etc/acpi.

[LIST]
[*]Scripts that I put into start.d, ac.d and battery.d all work.
[*]Scripts that I put into suspend.d and resume.d don't run.
[/LIST]
Thus, I think we first need to figure out how to get those scripts to run in the first place!

---

### Post by unutbu on 2009-04-21
Perhaps I had pointed you to the wrong directory.

In my /var/log/pm-suspend.log I see
```
Initial commandline parameters: 
Mon Apr 13 19:36:42 EDT 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/00clear suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend: success.
/usr/lib/pm-utils/sleep.d/05led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/10NetworkManager suspend: success.
/usr/lib/pm-utils/sleep.d/48hid2hci suspend: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend: not applicable.
/usr/lib/pm-utils/sleep.d/50modules suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend: success.
/usr/lib/pm-utils/sleep.d/95led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend: success.
Mon Apr 13 19:36:44 EDT 2009: performing suspend
```
So it looks like scripts in /usr/lib/pm-utils/sleep.d/ rather than /etc/acpi/suspend.d are getting run.

If you are using rtl8187, doesn't that mean you are not using ndiswrapper?

Perhaps before touching anything in /usr/lib/pm-utils/sleep.d/,
un-blacklist rtl8187. Reboot so your network adapter is working. Then try 

```
sudo modprobe -r rtl8187  # See if you can shut it off manually
```
Then try suspend. Does that work?

---

### Post by Paddy Landau on 2009-04-21
> **unutbu said:**
> Then try suspend. Does that work?
**Yes!**

Thank you so much for your help.

The rtl8187 is a Windows XP driver for which I used ndiswrapper to install. But your method works perfectly. Thanks for pointing out the correct directory; I amended 10NetworkManager for suspend and resume.

---

### Post by prostar on 2009-04-21
WOW! I've been searching for months on how to fix this, and it was the bloody wireless driver the whole time?!? Why does NetworkManager report success in /var/log/pm-suspend.log? 

What did you change to make this automatic? Just add lines in /usr/lib/pm-utils/10NetworkManager?

---

### Post by Paddy Landau on 2009-04-22
> **prostar said:**
> What did you change to make this automatic? Just add lines in /usr/lib/pm-utils/10NetworkManager?
I found out that you don't suspend ndiswrapper; it seems that ndiswrapper is just the mechanism for installing the driver.

Instead, find out what driver you're using. In my case, I used ndiswrapper to install rtl8187. I see it running when I use the command:
```
ps -e|fgrep rlt8187
```The trick is to suspend (in my case) rtl8187, not ndiswrapper.

So, here's what I did to 10NetworkManager. I amended the last few lines as follows; notice how I separated suspend and hibernate, and resume and thaw.
```
case "$1" in
    hibernate)
        suspend_nm
        ;;
    suspend)
        suspend_nm
        # Paddy: Disable the ndiswrapper wireless for the RTL8187, because it hangs the suspend.
        modprobe -r rtl8187
        ;;
    thaw)
        resume_nm
        ;;
    resume)
        # Paddy: Enable the ndiswrapper wireless for the RTL8187 that we suspended.
        modprobe rtl8187
        resume_nm
        ;;
    *)
        exit $NA
        ;;
esac
```**Remember to back up this file before you change it!** Of course, in your case, you use your driver instead of rtl8187.

I hope this helps.

---

### Post by snorbens on 2009-04-22
Hi,
Thanks I also use rtl8187 and after using modprobel I could manually suspend.

The problem is I am a noob using Jaunty.

I could not seem to be able to get into NetworkManager.

Could someone please explain step by step how to alter the code so that It will do it automatically on suspend/resume please and I would be forever grateful.

Cheers

Mervyn

---

### Post by unutbu on 2009-04-22
First, make a copy of the file we are about to edit:
```
sudo cp /usr/lib/pm-utils/sleep.d/10NetworkManager /root/10NetworkManager
```

Now fire up the text editor:```

gksu gedit /usr/lib/pm-utils/sleep.d/10NetworkManager
```

Go to the bottom of the file, and change

```
case "$1" in
	hibernate|suspend)
		suspend_nm
		;;
	thaw|resume)
		resume_nm
		;;
	*) exit $NA
		;;
esac
```

to the code that Paddy Landau posted. (Thanks Paddy!)

Save and exit gedit. Then try suspend/resume.

---

### Post by snorbens on 2009-04-22
Hi, Thanks for your reply but not having any luck.

This what I get when I input the first line of code.

mervyn@mervyn-laptop:~$ sudo cp /usr/lib/pm-utils/sleep.d/10NetworkManager /root/10NetworkManager
cp: cannot stat `/usr/lib/pm-utils/sleep.d/10NetworkManager': No such file or directory
mervyn@mervyn-laptop:~$

I am using Jaunty by the way.

I am sorry I do not know how to put the code into a box

Cheers

Mervyn

---

### Post by unutbu on 2009-04-22
snorbens, please post the output of:
```

apt-cache policy pm-utils
ls -l /usr/lib/pm-utils/sleep.d/
ls -l /var/log/ | grep suspend
```

To post it in a code box, see
[http://ubuntuforums.org/showpost.php?p=5490091&postcount=43](http://ubuntuforums.org/showpost.php?p=5490091&postcount=43)

---

### Post by snorbens on 2009-04-22
Hi Unutbu,

I have done it, thanks I needed to put 55NetworkManager and not 10NetworkManager and everything works wonderfully now.

Many thanks to both you and Paddy.

All I need to do now is work out how to automatically resume without having it input my password.:)

Thanks very much indeed

Mervyn

---

### Post by unutbu on 2009-04-22
I'm glad it worked out. :)

I'm not sure I can help you with the password problem, but could you explain, in what context do you need to type in a password? After a resume, don't you end up exactly where you suspended?

---

### Post by clive littlewood on 2009-04-22
Hi

The resume password is to secure your computer after suspend,as anybody could just restart if you were not there. !!!!

I would leave it as is for 5 seconds extra work.

Clive

---

### Post by snorbens on 2009-04-22
> **unutbu said:**
> I'm glad it worked out. :)

I'm not sure I can help you with the password problem, but could you explain, in what context do you need to type in a password? After a resume, don't you end up exactly where you suspended?

When It resumes it asks for my password before it returns to where I suspended from.
I have automatic login when I start but wants my password on resume?

Thanks.

---

### Post by snorbens on 2009-04-22
> **clive littlewood said:**
> Hi

The resume password is to secure your computer after suspend,as anybody could just restart if you were not there. !!!!

I would leave it as is for 5 seconds extra work.

Clive

Yes  Clive, you are right of course. I just found it perplexing that on startup I have automatic login.

Not a problem....I would rather have suspend work than not and as you say it only takes a couple of seconds.

Cheers

---

### Post by Paddy Landau on 2009-04-22
> **snorbens said:**
> When It resumes it asks for my password before it returns to where I suspended from.
I have automatic login when I start but wants my password on resume?
Start a new thread on this with an appropriate title.

---

### Post by waxwing_user on 2009-04-22
I've done what Paddy recommended to fix my suspend operation.  Furiously, it still hangs up.  I'm running Hardy Heron but hope the files will still be the same.  This is what I have for a sleep file:

> case "$1" in
	hibernate)
		suspend_nm
		;;
	suspend)
		suspend_nm
		modprobe -r rtl8185
		;;
	thaw)
		resume_nm
		;;
	resume)
		modprobe rtl8185
		resume_nm
		;;
	*)
		exit $NA
		;;
esac


I've also tried driver net8185 which was the file .inf file I put in.  I'm trying the WINXP driver.  I wonder if I should try a different driver?
Or maybe there's another sleep file I should be working with?

How confusing.

Andrew

---

### Post by Paddy Landau on 2009-04-23
> **waxwing_user said:**
> I've done what Paddy recommended to fix my suspend operation.  Furiously, it still hangs up.
OK, here's how you can test before making permanent changes.

[LIST=1]
[*]Undo the changes that you made to your file.
[*]Reboot! <- Important
[/LIST]
Now, we need to find what driver is running. Try these commands and see which of them gives you any output.
```
sudo ps -e | fgrep 8185
sudo ps -e | fgrep rtl
sudo ps -e | fgrep net
```Look at the output and see whether you can find your driver. If you can, then that's the name you want. For example, suppose your output looks something like this:
```
 6689 ?        00:00:00 net8185
```Then you know that net8185 is your driver.

Now manually type the following:
```
modprobe -r net8185
```Obviously, use the name of your driver instead of net8185. Your wireless should stop working!

* By the way, when you resume or reboot, enter the following command to resume wireless.*
```
modprobe net8185
```*Again, use your driver name instead of net8185. It may take several seconds to get going.*

Suspend. What happens?

[LIST]
[*]If it works, you got it. Make the changes to your file. Reboot! Test.
[*]If it doesn't work, then it's probably something else that's causing your suspend to hang.
[/LIST]
Let us know what happens. If you get stuck, let us know exactly where you get stuck.

---

### Post by waxwing_user on 2009-04-23
Ah,  I think I see part of the problem.  Running "...fgrep net" gave me

netdaemon as the driver.  I think I read somewhere that netdaemon should be taken out but I can't think where I read that or how to do so.  How would that be done?

Thanks

---

### Post by unutbu on 2009-04-23
I'm not sure that netdaemon is really your wireless driver. (Google suggests its some other kind of app -- [http://www.penguin-soft.com/penguin/man/1/netdaemon.html](http://www.penguin-soft.com/penguin/man/1/netdaemon.html).)

Here's another way to find the name of your driver:
Type
```
sudo lshw -C network
```

In the output you should see something like:

```
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:f0:93:54:20
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=**ndiswrapper+neta5agu** driverversion=1.53+D-Link,05/08/2006,1.5.202.2 ip=192.168.1.81 link=yes multicast=yes wireless=IEEE 802.11g
```

In the above, neta5agu is the driver.

---

### Post by Paddy Landau on 2009-04-23
> **unutbu said:**
> Here's another way to find the name of your driver...
Well, in my case where everything is working great, I get the puzzling result that my driver is listed by neither *lshw* nor *ndiswrapper*. Only *ps* shows it.
```
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:a0:d1:8a:2f:7e
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:44:7a:69:9c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.5.103 multicast=yes wireless=IEEE 802.11bg
$ sudo ndiswrapper -l
$ ps -e | fgrep rtl8
 3260 ?        00:00:00 rtl8187
```Hmm... :confused:

---

### Post by waxwing_user on 2009-04-23
Here's what I get

************************************

$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:b6:3e:70
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=64.185.134.61 latency=32 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 20
       serial: 00:14:d1:5b:41:66
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8185 driverversion=1.52+Realtek,11/20/2007,5.1102.1 latency=64 link=no maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
$ sudo ps -e | fgrep net8185
$ sudo ps -e | fgrep net
 5144 ?        00:00:00 netdaemon
$ 

***************************************

I am noting two things:  My physical ID for both devices is 1 (the last message on this thread read 1 and 0 for real id's).  I still read netdaemon as the driver.  There must be a way to change that.

I will investigate further.

---

### Post by unutbu on 2009-04-23
You know Paddy Landau, I don't think you are using ndiswrapper. According to [http://linuxwireless.org/en/users/Drivers/rtl8187](http://linuxwireless.org/en/users/Drivers/rtl8187), the rtl8187 is a native linux driver. (Good on you!)

So you might have the ndiswrapper package installed, and maybe 
```
lsmod | grep ndiswrapper
``` might even show ndiswrapper is loaded. But 
since
```

sudo ndiswrapper -l
```

returns nothing, I think ndiswrapper is not being used to control your wireless device.

Perhaps that is why the "modprobe -r rtl8187" works for you. 
(The equivalent does not work for me.)

I'd hate to ruin your nice working setup, but if you are confident you know how to get wireless working on your machine (just in case), you might want to try removing the ndiswrapper package. I bet your wireless would still work.

---

### Post by unutbu on 2009-04-23
> 
configuration: broadcast=yes driver=ndiswrapper+net8185 
waxwing_user, lshw is saying that your RTL-8185 Wireless adapter is being driven by 
ndiswrapper+net8185.

ndiswrapper is a kernel module which acts as an interface between the Linux kernel and the Windows driver net8185. The ndiswrapper module reads (or, you might say, loads) the net8185 drive from /etc/ndiswrapper/net8185/, but net8185 does not show up in the output of "sudo ps -e". The output about netdaemon is a red-herring. 

The "ps" command outputs all the processes running on your machine, and the "| fgrep net" filters the list of processes and prints only those lines which contain the string "net". Having output from this command does not necessarily imply it is your wireless driver.

What Paddy suggested was a good idea, but since everyone's system is a bit different, no single command seems to work for all of us.

Would you try this experiment?  Run the command
```

sudo ifdown wlan0
```

This will shut down your wireless interface.
Now try to suspend/resume. Does it work?

To restart the wireless interface, type
```

sudo /etc/init.d/networking restart
```

Sometimes you have to wait and run this command a few times before your wireless connection will be re-established. Don't worry too much about that -- we can make that work better later. First, let's find out if 
```

sudo ifdown wlan0
```

helps you suspend.

---

### Post by Paddy Landau on 2009-04-23
> **unutbu said:**
> You know Paddy Landau, I don't think you are using ndiswrapper. According to [http://linuxwireless.org/en/users/Drivers/rtl8187](http://linuxwireless.org/en/users/Drivers/rtl8187), the rtl8187 is a native linux driver. (Good on you!)
Yet again, I feel confused! The wireless didn't work until I used ndiswrapper to install the Windows driver, which I downloaded from the official Realtek website. Further, when I contacted Realtek, I was told that they definitely didn't support the wireless under Linux.

I wonder, I wonder...

> **unutbu said:**
> ... if you are confident you know how to get wireless working on your machine...
After all this discussion, nope, I'm not confident at all! (I do have a full Partimage backup just in case, but I'm not going to experiment today. I'll wait until I have some spare time in case the thing goes bang.)

I'm sorry that my method doesn't work for the others. I hope you all get it working.

---

### Post by waxwing_user on 2009-04-27
after trying "sudo ifdown wlan0"  I get this:

ifdown: interface wlan0 not configured

Admittedly I don't have a "wireless provider" set up but I wouldn't think that should matter.  Perhaps I should go to a hotspot, connect, and try those commands again. :(

---

### Post by unutbu on 2009-04-27
waxwing_user, what is the output of the two commands:
```

ifconfig
iwconfig
```

The command 
```

sudo ifdown wlan0
```
will disable the wlan0 interface. If your network interface is called something other than wlan0, then you'll need to use that name instead of wlan0. 

The ifconfig and/or iwconfig output should show you what the network interface is called.

---

### Post by waxwing_user on 2009-04-29
ifconfig gives me this:

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:b6:3e:70  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1969 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1969 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:73229 (71.5 KB)  TX bytes:73229 (71.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:d1:5b:41:66  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:d1ff:fe5b:4166/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2856 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3018 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2219112 (2.1 MB)  TX bytes:520124 (507.9 KB)
          Interrupt:11 Memory:48000000-48000025 

iwconfig gives me this:

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Starbridge"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:E0:98:C0:C3:AB   
          Bit Rate=48 Mb/s   Tx-Power:46 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:100/100  Signal level:-30 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

********************************************
So, I guess we can be sure that wlan0 is the proper wireless address.  Since I'm now writing post from a wireless hotspot, I will try disabling the connection and see what happens.

---

### Post by waxwing_user on 2009-04-29
Well, "sudo ifdown wlan0" still didn't work.  It keeps saying that wlan0 is not configured.   I've tried looking in System-Administration-Network but there seems no way to configure.  Should I be putting in ESSID?  Right now I have it on Roaming Mode.

Thanks

---

### Post by unutbu on 2009-04-29
Perhaps try
```

sudo ifconfig wlan0 down
```

This is another way to shut down the wlan0 interface.
To bring the interface back up, type

```

sudo ifconfig wlan0 up
```

---

### Post by waxwing_user on 2009-04-29
"sudo ifconfig wlan0 down" worked partially.  After using it, ifconfig showed no wireless card.  The wireless connection was still maintained though and suspend still hung up.  I tried it again.  Connection disappeared although top panel still showed it as connected.  Browser stopped working.  Email stopped working.  Reactivated wireless with "sudo ifconfig wlan0 up."  Browser still continued to not work.  Email also not working.  Do I have to reboot?  Will try that next.

Thanks,  getting there.

---

### Post by unutbu on 2009-04-29
waxwing_user, I've recently learned that Ubuntu comes with two independent ways of suspending/hibernating. One method is provided by pm-utils and the other by acpi-support. The method provided by pm-utils is the default. It is hooked up to the gnome-panel menu in the upper-right-hand corner, and to the gdm login F10 menu.

acpi-support, in contrast, is not hooked up anywhere by default, except as scripts that already exist on your machine. (At least, I think that's the way things are.)

I think there might even be other ways to suspend or hibernate provided by the uswsusp and hibernate packages.

If you would like to try suspending by using the acpi-support script, try the command
```

sudo /etc/acpi/sleep.sh sleep
```
and to hibernate:```

sudo /etc/acpi/hibernate.sh force
```

Finding some other method to suspend/hibernate may be easier than trying to fiddle with pm-utils. (I've run out of ideas in that direction).

For info on uswsusp, see [http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855) and [http://ubuntuforums.org/showthread.php?p=6819660](http://ubuntuforums.org/showthread.php?p=6819660)

---

### Post by waxwing_user on 2009-05-06
Thanks for all the suggestions here.  The last suggestions by Unutbu took me farther on the suspend function.  Perhaps if I upgrade to Intrepid I might have better luck with these problems.  Yes?  Will continue to work on this issue.  Thanks again.

waxwing_user

---

### Post by Zer0Nin3r on 2009-05-07
Would have just marked a 'Thanks' but it looks like they got rid of that feature.  So lucky us we get a post!  :neutral:

Anyway, solved my problem that I have been having for years now.  Interesting to find that it was related to the RTL8187 driver.

---

### Post by prostar on 2009-05-16
Was that the same as my problem (where you have to rmmod/insmod in the suspend scripts)? That is mostly working for me now. I say mostly because every 1/5 times it will not resume, but I know that's an ongoing issue. The other annoyance is that when it resumes, the network manager is always disabled. I have to right click and re-enable to get connected.

---

