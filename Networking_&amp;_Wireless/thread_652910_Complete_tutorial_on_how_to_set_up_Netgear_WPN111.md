---
title: "Complete tutorial on how to set up Netgear WPN111"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by Erwin Criddle on 2007-12-29
This is a complete how to on installing and setting up the Netgear WPN111 wireless device in Ubuntu Gutsy Gibbon.

1. Download the two attachments (WIndows drivers and ndiswrapper)

2. Install build-essential (Needed for compiling ndiswrapper)```
sudo apt-get install build-essential
```

3. Extract ndiswrapper```
tar -zxvf ndiswrapper-1.51.tar.tar
```

4. Go to the ndiswrapper directory```
cd ndiswrapper-1.51
```

5. Run```
make distclean
make
sudo make install
```

6. Check that ndiswrapper is installed properly ```
ndiswrapper -v
```
If it outputs something like this:
```
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.45
vermagic:       2.6.22-14-generic SMP mod_unload 586
```

It has installed correctly. 
If it show something different (Please upgrade ndiswrapper to the latest version by going to the ndiswrapper website [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)), run ```
sudo make uninstall
``` Three times and repeat steps 5-8 again and check ndiswrapper -v again. 

If it does display the correct output, then you can move to the next step 

7. Go back to your home directory```
cd ..
``` and then extract the windows drivers```
tar -zxvf win-drivers.tar.gz
```

8. Change directory to the windows drivers```
cd win-drivers
```

9. Run```
sudo ndiswrapper -i netwpn11.inf
```

10. Check if the windows driver is installed```
ndiswrapper -l
```
If it shows: then you can move onto the next step.
```
netwpn11 : driver installed
        device (1385:5F01) present
```
If not, remove driver```
sudo ndiswrapper -r netwpn11
``` And reinstall the driver```
sudo ndiswrapper -i netwpn11.inf
```

11. Run```
sudo depmod -a
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```
If it all goes to plan, Ubuntu should still be running OK and the Netgear device should be winking at you:KS

12. Finally make sure that the device initializes at boot, run```
nano /etc/modules
``` And add ndiswrapper at the end of the page.



Hopefully, if you have done everything correctly, you should have a working WPN111 Wireless device!

---

### Post by breaking on 2008-01-01
Excellent guide mate, I just bought one of these suckers and everything on the instructions worked perfectly, got this device running within minutes flat thanks to you.

---

### Post by ^Albe^ on 2008-01-12
simple and working: perfect
thx

---

### Post by jdix123 on 2008-01-14
I've followed your steps until and didn't get any error messages.  

But my little blue light isn't blinking, and I don't have a "Wireless" option when I open the System -> Network utility.

```

$ ndiswrapper -l

Installed ndis drivers:
dr71wu               driver present
netwpn11                   driver present, hardware present

```

So it recognizes the hardware, apparently.  But then when I try 

```

$ sudo ifconfig wlan0 down
wlan0: ERROR while getting interface flags: No such device

```

Its not recognizing the device.  I can see it under System -> Preferences -> Hardware Information under 8201DB/DBM (ICH4/ICH4-m) -> EHCI Host Controller -> WPN111 so I'm stuck, because as far as I can tell, the system can see it.

Ubuntu 7.1 i386

---

### Post by Erwin Criddle on 2008-01-17
Have you updated your kernel since installing and configuring ndiswrapper?

---

### Post by rayefrenzy on 2008-01-17
All right. 

I just did what you told me to, and it worked. Flawlessly. I was so overjoyed. Then I restarted, and it all went to ****. I opened up /etc/modules/ in gedit and it still has ndiswrapper chillin' there, ready to start when I boot.

Netgear is still winking at me! What on earth is going on? I checked ndiswrapper -l and it still says:

netwpn11 : driver installed
        device (1385:5F01) present

When I open up system>admin>network I  don't get any wireless options. 

Help me out please!

---

### Post by rayefrenzy on 2008-01-17
So, after restarting, like, 3 times, It showed up again... that REALLY doesn't make any sense... but whatever.

---

### Post by Erwin Criddle on 2008-01-18
If you find that the device dosn't work after restarting, it is to do with not deintialising the device.
Instead of restarting, shutdown the machine and it should start ok.

---

### Post by rayefrenzy on 2008-01-18
What I realised made this dumb thing work is unplugging it, plugging it back in, and then restarting. Its sort of annoying, but it works. and that's good enough.

Thank you for the wonderful tutorial. It was the first one that worked :D

---

### Post by ^Albe^ on 2008-01-24
since i have reinstalled gutsy, i have the same problem
in the past with the gutsy "Upgraded" from feisty all fine
but after a full format/gutsy reinstall i loose the wireless part after a while (1-5 minutes) too

some trick, or so here
if connected with the wireless does not fall
for made solid the wireless is connect to an ap, after this is it possible to return to a wired and have always available  (for htat session obv) the wireless one!

the fastest mode for restart the wireless is:
sudo rmmod ndiswrapper
unplug/replug the wpn111
sudo modprobe ndiswrapper

i'm asking just in those days in the ndiswrapper chat/forum 
i hope to report any trick for solve

a note:
upgrading to the newest driver (and not using the one in this thread)  does NOT help

---

### Post by TheMadGeneral on 2008-01-24
I am a green as a clover leaf to this Linux and I just couldn't get it to work.  I really do need DUMMY step by step talk through.  I couldn't get past 3, above.  There must be a more user friendly way to install a driver.  As you know in  windows it seems so easy.  I don't want to give up just yet.

---

### Post by jdix123 on 2008-01-29
> **Erwin Criddle said:**
> Have you updated your kernel since installing and configuring ndiswrapper?


No.  Should I?

---

### Post by jdix123 on 2008-01-29
> **TheMadGeneral said:**
> There must be a more user friendly way to install a driver.  ...  I don't want to give up just yet.

The problem isn't with installing drivers in Linux.  The problem is that Netgear hasn't seen fit to release a linux driver for this device, so what we are trying to do here is install a windows driver in a linux environment.

If you can't get the command line installation to work, try installing the packages through the Synaptic package manager found in your System - Administration menu.  Let me know if you need more guidance than that and I'll help if I can :)

---

### Post by TheMadGeneral on 2008-01-29
I would really appreciate the step by step procedure as I have tried for an hour and a half to get it to work trying to install the packages through the Synaptic package manager found in your System - Administration menu with no luck.  Thanks for the reply.

---

### Post by jdix123 on 2008-01-29
Lets try again from the command line.  What's hanging you up?

---

### Post by TheMadGeneral on 2008-01-29
I have managed to copy all of the Netgear CD to my desktop.
I think I am pretty sure that I have managed to install the ndiswrapper-1.51 through the Synaptic package manager software.

What do I do now?

---

### Post by jdix123 on 2008-01-29
you want to make sure its installed correctly.  You do this by typing 

```

ndiswrapper -v

```

in a console.  See step #6.  The second code box is what the terminal output should look like.  Follow the steps and let me know if you get stuck again.

Anytime you see a code box like this:

```

type what you see into the terminal, or check your own terminal output against it

```

---

### Post by jdix123 on 2008-01-31
I'm still waiting for a reply about my issue, btw.  I know I was helping the guy above me but I'm still not set up.

---

### Post by TheMadGeneral on 2008-01-31
> **jdix123 said:**
> you want to make sure its installed correctly.  You do this by typing 

```

ndiswrapper -v

```

in a console.  See step #6.  The second code box is what the terminal output should look like.  Follow the steps and let me know if you get stuck again.

Anytime you see a code box like this:

```

type what you see into the terminal, or check your own terminal output against it

```

Sorry it took so long to get back to you but I was away on business.
Let me outline what I did;
[LIST=1]
[*]I opened Applications | Accessories | Terminal
[*]At the xxxx@ubuntu:~$ I typed ndiswrapper -v and Pressed return
[*]I got the following message 'The program 'ndiswrapper' is currently not installed.  You can install it by typing sudo apt-get install ndiswrapper-common
Bash: ndiswrapper: command not found.
[/LIST]

So I typed in sudo apt-get install ndiswrapper-common
I get asked for my password which I type in.
and press return.
I get the following;
Reading package lists... Done
Building dependency tree
Reading state information... Done
ndsiwrapper-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
And then I am returned to the command prompt (windows term maybe) xxx@ubuntu:~$

I DID NOTICE that this tutorial was for GUSTY GIBON I am using STUDIO will that make any difference?

---

### Post by the_bengine on 2008-02-01
Cheers Erwin, 

Another satisfied customer here. 
No need to reinstall any of it, worked straight off.

---

### Post by jdix123 on 2008-02-04
> **TheMadGeneral said:**
> 
I DID NOTICE that this tutorial was for GUSTY GIBON I am using STUDIO will that make any difference?


No, Gutsy Gibbon is the name for Ubuntu release 7.x  If you are using Studio, Kubuntu, Xubuntu, whatever, if its 7.x its still Gutsy Gibbon.  The core is still the same, but the extras are different.

---

### Post by jwalcker on 2008-02-07
Im stuck at the nano /etc/module command, how do i exit? i tried the ^X but it just shows up in text field

---

### Post by Erwin Criddle on 2008-02-09
If you cannot get use to the nano interface, try gedit. e.g. "sudo gedit /etc/modules"

---

### Post by rnzlzz on 2008-02-19
Thanks for posting the tutorial - The most useful I found.

I was able to get my Dell Latitude D800 working using ubuntu 7.10 
I had some transient problems - sometimes at boot it did not seem to work but I could not reproduce it consistently.
I blacklisted  the built in  Broadcom wireless and the transient problems are gone
 
To blacklist the built in broadcom use the following command
          nano /etc/modprobe.d/blacklist

At the end, add the following line
blacklist bcm43xx


Here my happy netwpn11 running - I am using to write this posting
sudo ndiswrapper  -l
       netwpn11 : driver installed
                device (1385:5F01) present


I still have problems connecting to a WPA protected access point.
I am looking into wpa_supplicant

Thanks again for the posting !

Renzo Lazzarato

---

### Post by gianchi on 2008-02-22
Hello Erwin.

I have a fresh install of Gutsy and a WPN111, so, I tried to install the driver following your tutorial, some hours ago.

Before starting, having plugged the router, I downloaded all the available upgrades and restarted the box, so that the kernel and everything was up to date.

Then I downloaded the last available ndiswrapper, the 1.52 and the windows driver you attached to this thread.

After that, I follow all the steps, carefully, one by one. Everything seemed to go fine, until step 11, after which the adapter wasn't blinking at me... :(

I edited the modules file, anyway, hoping that shutdown and booting again would have helped.... done that, still nojoy.

Unplugging and plugging again the device didn't help. I don't know what to do... ndiswrapper -v and -l outputs are ok... maybe I shouldn't have used version 1.52?

Any idea? (Please, keep in mind that I'm a newbie in Linux world ;) )

---

### Post by gianchi on 2008-02-22
No ideas at all?

Im having a terrible doubt.... I have 64bit version installed... do 32bit drivers work with it? And, if not... where can I find working Netgear drivers for Gutsy 64?

---

### Post by Erwin Criddle on 2008-02-23
You cannot use the Netgear WPN111 on a 64bit oeprating system. You have to be running a 32bit operating system.
Sorry:sad:
The only solution I can give you is to see if Netgear have 64bit drivers.
Since I also don't have a 64bit computer I don't know anything about it.

---

### Post by gianchi on 2008-02-23
Yep, after a bit more searching I noticed that :) And Netgear has no 64bit driver, unfortunately!

Oh, well, I uninstalled the 64 and installed the 32... I'm happy now. Thank you! ;)

---

### Post by gianchi on 2008-02-24
Ok, I did it. Installing the 32 was easy and smooth, everything went fine and I followed this tutorial to install the WPN111... everything ok, drivers installed and device regularly working....

I'd like to say everything is alright, but it isn't.... I don't know why, Network manager hangs up while looking for my network and it freezes the whole computer... only option I have left, is hitting the power button.

Anyone experiencing this? Any idea on how to solve this issue?

---

### Post by spaztaz666 on 2008-02-24
Ok, everything went smoothly,  the wpn111 started winking at me and i was good to go,

then i tried to connect to my wireless router, entered the passphrase but it wouldnt connect

[IMG]http://i243.photobucket.com/albums/ff15/spaztaz666/snapshot2.png[/IMG]

Then

[IMG]http://i243.photobucket.com/albums/ff15/spaztaz666/snapshot3.png[/IMG]

Then

[IMG]http://i243.photobucket.com/albums/ff15/spaztaz666/snapshot1.png[/IMG]

Then

[IMG]http://i243.photobucket.com/albums/ff15/spaztaz666/snapshot4.png[/IMG]

It just went round in a circle. I cant work out why.

the passphrase is  right, then only thing i can think is that i have two hard drivers, i use both one with xp and one with kubuntu 7.10 Gutsy that something is wrong somewhere. 

Please help

~Spaz

---

### Post by Erwin Criddle on 2008-02-26
spaztaz666:
This is very strange. It shouldn't fail to connect to the network.
The only thing I can think of is the following things:
1) Interference e.g. Microwave, Cordless phones etc.
2) Hidden ESSID

Report back

---

### Post by gianchi on 2008-02-26
Hello again!

I'm writing these lines from Gutsy, with the WPN111 working. It's something really weird, though, because, to make it work I have to unplug the key at start up and plug it while the OS is loading (the splash screen with the orange bar)... if I keep it plugged, Network Manager will freeze the system.... 

I'm happy it works, but I'm th kind of guy who's happier if he knows *why* things are working.... any idea about what is happening, behind that splash screen? I know I can disable it, but the writings are too fast for reading, is there a way to log what happens during boot, so I can review it later?

Thanks again for the tutorial, Erwin, and your kindness.

---

### Post by spaztaz666 on 2008-02-27
well, now it wont find the device all together, 
i plug it in and it flashes ok, but it doesnt pick up its a wireless device, if i manually configure its there Wlan0, andits enabled but i cant right click the icon and chose the wireless settings just wired (which dioesnt exist) any help??

~Spaz

---

### Post by Erwin Criddle on 2008-02-28
Try using WICD.
Install this package:[http://rapidshare.com/files/95699391/wicd_1.4.2-1-all.deb.html]("http://rapidshare.com/files/95699391/wicd_1.4.2-1-all.deb.html")
Be sure to remove network-manager first. :)

---

### Post by david_davis98 on 2008-02-29
> **spaztaz666 said:**
> well, now it wont find the device all together, 
i plug it in and it flashes ok, but it doesnt pick up its a wireless device, if i manually configure its there Wlan0, andits enabled but i cant right click the icon and chose the wireless settings just wired (which dioesnt exist) any help??

~Spaz

I get this problem.  Very flakey and often doesn't start on boot.  

I tried the quick fix on page 1 of this thread:
sudo rmmod ndiswrapper
unplug/plu wpn111
sudo modprobe ndiswrapper

Still didn't work but I found out by chance that if you do the above, then right click the icon and disable Networking, then right click again and enable it, it works.  Worth a try!

---

### Post by Trunten on 2008-03-01
Hello everyone! I registered just to say thank you for this tutorial. I am a completely new user to Ubuntu, and I was hoping there was still hope for my old desktop with my beloved Netgear wireless. Ha ha. :KS

Anyway, I will be giving this guide a try very soon... I still have a fresh new installation of Ubuntu on the old desktop. I haven't proceeded to do anything more to it other than just browse around and seeing what it comes with and can do. :popcorn:

I do have a question, of course. I actually have the alpha (5 at this time) of Ubuntu 8 installed (Hardy Heroin, I think is the name?), and it's dual booting with Kubuntu 8 (also alpha 5). Should I just wait for the final build of 8 before bothering with this tutorial in case it'd need updated? :confused:

Thank you again for this guide. I'll probably be lurking around here more often now! :)

---

### Post by Erwin Criddle on 2008-03-05
Trunten, I suggest that you wait for Ubuntu 8.04 to come out at full release before trying my tutorial. Otherwise you may find many problems and bugs.

---

### Post by toddysean on 2008-04-09
Thankyou so much! I tried this once before, but using your guide, I got it working! Thankyou!!!!

---

### Post by NSF12345 on 2008-04-12
ok,..im ok until the last stage

iv opened /etc/modules, but not too sure on how to amend the file with ndiswrapper. Iv simply typed it in at the end, Then i press ctrl+O (for ^O) to "WriteOut" but all i get is " [ Error writing /etc/modules: Permission denied ]

iv tried saving it as a different file, but the same happens: "Permission denied"

Anyone got any ideas?

---

### Post by NSF12345 on 2008-04-12
> **NSF12345 said:**
> ok,..im ok until the last stage

iv opened /etc/modules, but not too sure on how to amend the file with ndiswrapper. Iv simply typed it in at the end, Then i press ctrl+O (for ^O) to "WriteOut" but all i get is " [ Error writing /etc/modules: Permission denied ]

iv tried saving it as a different file, but the same happens: "Permission denied"

Anyone got any ideas?

also, when i run "ndiswrapper -l" in step 10 it says:

netwpn11 : driver installed
          device (1385:5F01) present
netwpn11.nf : invalid driver!

not sure if that makes any difference or not

Thanks in advance for any help you could give.

---

### Post by NSF12345 on 2008-04-12
> **NSF12345 said:**
> also, when i run "ndiswrapper -l" in step 10 it says:

netwpn11 : driver installed
          device (1385:5F01) present
netwpn11.nf : invalid driver!

not sure if that makes any difference or not

Thanks in advance for any help you could give.

ok. i managed to edi the etc/modules file by puttin sudo at the beginning of the command so it reads:

sudo nano /etc/modules

still got the "invalid driver" prob though. i think this is why my dongle isnt working yet

---

### Post by darkrituals on 2008-04-24
Hi guys & girls:),

Im new to linux distro's etc decided to install kubuntu on my spare notebook which went with no problems kubuntu now fully installed great.

Until i then realised that i now cant access the net due to drivers 
etc now i have a netgear WPN111 adapter and thought id give the tutorial a try this is where my problem begins as soon as i try to pass code sudo apt-get build-essential i get the message:

E: couldnt find package build essential

could some1 please help me?

sorry for the noob question 

Thanks in advance

James

---

### Post by az_cchow on 2008-05-04
Erwin,

I was trying to download attachment: ndiswrapper-1.51.tar.tar posted by you and was getting the following messages:

Your help on this matter is greatly appreciated.

CChow

+++++++++++++++++++++++++++++

vBulletin Message
You are not logged in or you do not have permission to access this page. This could be due to one of several reasons:
You are not logged in. Fill in the form at the bottom of this page and try again.
You may not have sufficient privileges to access this page. Are you trying to edit someone else's post, access administrative features or some other privileged system?
If you are trying to post, the administrator may have disabled your account, or it may be awaiting activation.

++++++++++++++++++++++++++

---

### Post by Dural on 2008-05-07
I tried your guide and it helped me successfully install the WPN111. Currently, the blue light on it is blinking. However, in Ubuntu Hardy Heron (x86 32-bit), when I type in iwconfig in the Terimnal, it says this message:

> lo      no wireless extensions
eth0    no wireless extensions

I tried to connect the WPN111 to the network, but when I check the Network Settings, I only see options for a Wired Connection and a Point-to-Point connection. How can I make the WPN11 connect to a wireless network?

---

### Post by aim@mail.nu on 2008-06-19
see next post

---

### Post by aim@mail.nu on 2008-06-19
> **NSF12345 said:**
> ok. i managed to edi the etc/modules file by puttin sudo at the beginning of the command so it reads:

sudo nano /etc/modules

still got the "invalid driver" prob though. i think this is why my dongle isnt working yet

I think you key in the wrong driver's name there is no .nf it must be .inf
please try to do the correction and see if it work

---

### Post by aim@mail.nu on 2008-06-19
> **darkrituals said:**
> Hi guys & girls:),

Im new to linux distro's etc decided to install kubuntu on my spare notebook which went with no problems kubuntu now fully installed great.

Until i then realised that i now cant access the net due to drivers 
etc now i have a netgear WPN111 adapter and thought id give the tutorial a try this is where my problem begins as soon as i try to pass code sudo apt-get build-essential i get the message:

E: couldnt find package build essential

could some1 please help me?

sorry for the noob question 

Thanks in advance

James

I have similar problems, the tutorial should be more details,

If you have that massage, it means that in your system have no "build-essential". So you must download them from the Internet.

**_So you must be connected to a wired network and have access to the internet_**,
Run that command again and it will start downloading and finally install them to your system.
I have that similar error first time then I connect to RJ45 lan port then it start donwload from the internet.

also I did exact "sudo apt-get install build-essential" you did not have "install" in your statement.

---

### Post by aim@mail.nu on 2008-06-19
> **Dural said:**
> I tried your guide and it helped me successfully install the WPN111. Currently, the blue light on it is blinking. However, in Ubuntu Hardy Heron (x86 32-bit), when I type in iwconfig in the Terimnal, it says this message:



I tried to connect the WPN111 to the network, but when I check the Network Settings, I only see options for a Wired Connection and a Point-to-Point connection. How can I make the WPN11 connect to a wireless network?

I am now successfully install WPN111 but with pain though. I got this massage from "iwconfig"
aim@aim-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"OPTUSAF7753E"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:1E:2A:F7:75:3E   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:70/100  Signal level:-51 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I don't understand that, but it is working fine for me now. (Not after reboot though-- see my later post)

---

### Post by aim@mail.nu on 2008-06-22
[B][COLOR="Red"]+++++++++++++++++++++++++++

I start new thread with more comprehensive instructions. And leave out all the complaint and the jass.

[http://ubuntuforums.org/showthread.php?t=844856&highlight=wpn111](http://ubuntuforums.org/showthread.php?t=844856&highlight=wpn111)

I left below posts for the time being, if the admin think it should be remove please do so.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++[/COLOR][/B]




I am new to linux and especially UBUNTU first time. I have try other Linux 10, 7, 5, 3 years ago, and leave them in the cd cases. Untill UBUNTU came.
To me I want to use UBUNTO from now on, **_but after 20 hours of how to config WPN111 with UBUNTU_** I think I am not sure again. And start reviewing again.

Back to the story of WPN111.

I try all instructions in the thread ... 
and concluded that they(ALL instructions and suggestions) all works, 
but temporary and not everytime you implement those steps.
**_Don't reboot OR HYBERNATE your computer_** or it may not work again. Many reboots are successful, no flaw, but not too many you will got it a dead wireless connection.

I have to uninstall all steps in the tutorial and start from step one and then reboot, it TOOK ME 15 minutes to 20 minutes, the reboot, each time TO GET IT CONNECT TO INTERNET and still many times it will not work. I try for about 10 uninstall and reinstall and all other options and reboot about 30 odds times reboots, to get the answer, how to do it so every time I turn on my computer it will work.

I fail to get the answers from my efforts in experiments.

I forget to say I used a notebook - AUSUTEK OEM bare bone, Synnex is my wholesaler in Melbourne, Using Intel CPU. And us UBUNTU 8.04 latest kernel and internet full updated, before I start install wpn111.

For example,
On my compaq 2500 notebook, we have netgear wireless PCMCIA card, we found that we need to insert the card into PCMCIA slot only after Xp fully loaded. Otherwise it would not connect to the internet, and that is 100% concluded steps to do.

For Ubuntu 8.04 and WPN111, I found no definite pattern, except fully uninstall and reinstall and reboot (15-20 minutes for this tutorial), and sometimes even that is not 100% that it will work.

Conclusion **_I gave up with this tutorial (manual console cammand) and found it is not reliable for my notebook_**. Though wpn111, it is perfectly work with my XP home which is my secondary OS on this notebook.

I found though [B][U]using synaptic package manager to download Ndiswrapper-utils-1.9, ndiswrapper-common, ndisgtk(graphical interface).
And use this graphic interface to produce much more reliable internet connection for wpn111.[/U][/B]

Though I have to uninstall and reinstall, using /SYSTEM/ADMINISTRATION/WINDOWS WIRELESS DRIVERS/ WPN111 driver already more than 10 times until now. Please look at the steps below of what I have done and found it is much easier to do than this tutorial.


Before you start - I am not sure if you have to do step 2 of tutorial or not since I did it before I try the Synaptic, the Ubuntu Guru please confirm this.
==========================
step2. Install build-essential (Needed for compiling ndiswrapper)
Code:

sudo apt-get install build-essential
=====================================


1. you must download wpn111 and unzip into win-drivers folder first as describe in this tutorial step 7
=======================
and then extract the windows drivers
Code:

tar -zxvf win-drivers.tar.gz

=================================


2. click on Ubuntu Menu Bar => System / Administration / Synaptic Package manager => then in the new window of the Synaptic=>click search icon ==> you will get new pop up window, key in Ndiswrapper and click search icon.

You should see 3 above package

Make sure you select all 3 package, I did not choose ndisgtk(graphical interface) in the first time and have to rely on the manual console command lines to uninstall and reinstall driver, which is painful time.

Then you clik on Ubuntu menu bar ==>/SYSTEM/ADMINISTRATION/WINDOWS WIRELESS DRIVERS/ and choose install icon to install wpn111 from the directory that you keep the driver, though the name is "wpn11.inf"
not wpn111l.inf

I HOPE MY 30 HOURS EXPERIENCE will help someone else, as a return for all the good work the GURU of Linux has done Ubuntu and other Linux for us.

I still have not got the reliable internet connection after reboot until now. After 4 days of work on this. Can the GURU help us.?

Thanks in advance,
I gave up and will buy other usb wireless now Can the GURU suggest me please which one to buy that will work for sure.

Best Wishes to everyone

---

### Post by aim@mail.nu on 2008-06-26
[B][COLOR="Red"]+++++++++++++++++++++++++++

I start new thread with more comprehensive instructions. And leave out all the complaints and the jass.

[http://ubuntuforums.org/showthread.php?t=844856&highlight=wpn111](http://ubuntuforums.org/showthread.php?t=844856&highlight=wpn111)

I left below posts for the time being, if the admin think it should be remove please do so.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++[/COLOR][/B]


To any new use UBUNTU 8.04 like me also new to LINUX.

After many pains to get internet connection through wpn111, I found it pretty stable now, with web 128 bit connection to Netgear wireless Adsl2 router modem. How ever still struggling with WPA & WPA2 Setup with the same model.

I finally found that:

After I have done: install Ndiswrapper and WPN111 driver as in the previous post or according to the tutorial in the start of this post.

1. I must set the network setting(System/Administrarion/Network=>Network setting window), Wireless Connection/unlock-with password/Properties => wlan0 Properties ==++>>> click enable roaming mode.

2. use only the nm-applet, network icon(similar to window network icon, on the right hand top corner between user name icon and the speaker icon) to do the network connection.

Trouble shooting from my experience. After 70 odds hours of pains and more than 100 shutdown, reboots and hibernate.

1. If you left click the icon and did not find any wireless access point's wireless signal, go to check your wpn111 driver, if it is installed properly by checking System/Administration/Window Wireless Drivers=> The must be netwpn111 icon on the left saying" Hardware present= Yes or No. If there is not netwpn111 icon, you must install the wpn111 driver by clicking install new driver.

2. If there is netwpn111 icon as in no.1
It must say =Yes and the blue light on the wpn111 must be blinking. 

If you don't get these "Yes" and the "Blue blinking LED" on wpn111, ===> Shutdown your computer and turn on again, they should work both. 

(Don't Hibernate--more reliable with shutdown-- the tutorial and earlier posts said that, so I found that is true.)

And if you have problems connecting to the internet in the future check and do the above 2 steps, and I found it is normal that randomly it will not work and the UBUNTU will occasionally hung up during the start up. Sometimes You may have to reboot twice before It will work both.

3. When both "Yes" AND "BLUE BLINKING led" on wpn111
You would see wireless signals from access points, left click on it, enter what ever security setting required by the access points. (Ask your net work admin if you don't understand that)
Click on "CONNECT" button.

The network nm-applet icon must change to circle spinning arrows.
And got connected to the Internet.

If it is not connected and not spinning at all.
 
====> Shutdown and start again.===> this is normal, wpn111 is window base drivers not linux ==> if you want to still save money and use this usb wpn111, you got to put up with this, for the moment until the gurus find a better solutions.

4. Many times I have to start from scratch to delete even the wpn111 driver and reinstall it and start from no.1 to get it connect again.


Best of luck,,,, I hope it will help someone else not to waste much time like me again.

I found doing the ways I post here is better than the "Complete tutorial on how to set up Netgear WPN111" at the beginning of this thread. BUT THIS IS UBUNTU 8.04 and with my notebook.

Any the tutorial is my teacher and it must be praised and honored.
Nothing wrong with the tutorial, It works for me in the beginning as well but i found wpn111 will not connect to the internet every time I reboot. And to get it work again I found the above trouble shoots is quicker to put it back to work. 

Thanks for all those "teachers who wrote tutorials and posts comments and feed back earlier"

---

### Post by DouginMaine on 2008-06-29
Thank you so much for this carefully crafted set of instructions.  I am very new to UBUNTU and am barely crawling; so I need all the help I can find.  I used your instructions to get the WG111v3 USB Wireless adapter to run on my computer.  After a bit of fumbling, I completed this task successfully.  

Thanks again for providing such clear instructions.

---

### Post by Fletch273 on 2008-07-11
Thank you very much.  I tried another guide before this one and it didn't get me anywhere.  This was very quick and very simple for a new linux user.

---

### Post by phob on 2008-07-22
great guide!!!
Does it works with ubuntu hardy heron???

---

