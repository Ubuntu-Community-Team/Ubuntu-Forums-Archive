---
title: "Acer Aspire 3003 wifi problems"
date: 2005-08-28
forum: Networking &amp; Wireless
---

### Post by skirkpatrick on 2005-08-28
I just bought an Acer 3003LXCI and am having a hell of a time with the wireless.  I've used ndiswrapper on my HP laptop before so I at least know the process.  I've also looked at almost every wifi thread here without any luck.

I found the Acer's Broadcom drivers on the Windows XP install.  I've installed ndiswrappers, installed the drivers, modprobed, rebooted and now I have problems.

dmesg:
> 
ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
ACPI: PCI interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 17
ndiswrapper: using irq 17
wlan0: ndiswrapper ethernet device 00:14:a4:14:3e:23 using driver bcmwl5
wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP
ndiswrapper: driver bcmwl5 (Broadcom,12/22/2004, 3.100.46.0) added


iwconfig:
> 
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ifconfig:
> 
wlan0     Link encap:Ethernet  HWaddr 00:14:A4:14:3E:23
          inet6 addr: fe80::214:a4ff:fe14:3e23/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Memory:e2000000-e2001fff


"iwlist wlan0 scanning" tells me that there are no scan results and the front wireless light won't come on.  I've setup ESSID and WEP key the same as I did in Windows on this laptop.

Can somebody please give me some direction on where to look?

---

### Post by skirkpatrick on 2005-09-01
It appears that the radio isn't turned on.  Anybody have any opinions?

---

### Post by ssck on 2005-09-01
[QUOTE=skirkpatrick]It appears that the radio isn't turned on.  Anybody have any opinions?[/QUOTE]

i am using acer travelmate 2300.there is a switch in front for me to turn it on.does your laptop have such a switch ?

---

### Post by skirkpatrick on 2005-09-01
Yes and it works fine in Windows but doesn't do anything in Linux.  Also, I have heard some people talk about the fact that the wifi needs to be turned on in Windows to have it work in Linux.  That didn't fix my problem either :(

---

### Post by ssck on 2005-09-02
just a check ... do you have eth0 up as well ? if so, can you sudo ifdown eth0.it seems that if eth0 is up, iwlist wlan0 scan will not work.

---

### Post by skirkpatrick on 2005-09-02
I'll have to try that later today when my son gets home from college (it's his laptop).  I think I've tried it with eth0 deactivated but maybe not.  Now my HP laptop (I just tried this) will allow me to scan with eth0 active and connected.

---

### Post by cbudden on 2005-09-02
[QUOTE=skirkpatrick]I'll have to try that later today when my son gets home from college (it's his laptop).  I think I've tried it with eth0 deactivated but maybe not.  Now my HP laptop (I just tried this) will allow me to scan with eth0 active and connected.[/QUOTE]
 Is your switch on of the ones that are orange in XP when turned on?  If it is, i found that it does actually turn the radio on and off.

---

### Post by skirkpatrick on 2005-09-03
Yes, it is an orange switch.  It works fine in Windows but doesn't appear to do anything in Ubuntu.  In fact, I just came from Windows and the light was still on.  I modprobed ndiswrapper and the light went out.

I used the driver that was in the Windows install.  I think I'm going to uninstall ndiswrapper and try out driverloader.  I've heard some people have had better luck with it.  At least I've got 30 days before I have to buy it.

---

### Post by ssck on 2005-09-05
[QUOTE=skirkpatrick]Yes, it is an orange switch.  It works fine in Windows but doesn't appear to do anything in Ubuntu.  In fact, I just came from Windows and the light was still on.  I modprobed ndiswrapper and the light went out.

I used the driver that was in the Windows install.  I think I'm going to uninstall ndiswrapper and try out driverloader.  I've heard some people have had better luck with it.  At least I've got 30 days before I have to buy it.[/QUOTE]

hi,

did you manage to get it up ?

---

### Post by skirkpatrick on 2005-09-06
Nope, I'm starting to think I need Viagra for my wireless  :roll: 

Here's what I posted in the "HOW TO: Configure wireless cards with Broadcom chipsets" thread:

[QUOTE=skirkpatrick]If I wasn't going bald before, I certainly am now.  Configuring wifi on my HP Pavilion laptop was a piece of cake.

Okay, I've read every message in this topic and several others as well.  I've followed almost every instruction given and some from links to other webpages.  I've got an Acer 3002LCi with built-in Broadcom wifi.  I have currently:

1) Built ndiswrapper v1.3rc1 and successfully installed it from a .deb (I've also tried v1.2).

2) I have installed the drivers that came with the Windows install and have even installed the ones specified on the ndiswrapper Wiki (currently installed).

3) I've installed acerhk and modprobed it as dictated on the ndiswrapper Wiki.

4) I've modprobed ndiswrapper and added it to /etc/modules.

5) All the .conf files have RadioState|0.

Dmesg looks fine, ifconfig looks fine, iwconfig looks fine.  The problem is that "sudo iwlist wlan0 scan" always reports "no scan results".  It's working fine in Windows, it's almost as if it's not turning on the radio but I can't find anything about turning it on in Linux.

Getting ACPI working correctly wasn't this hard.[/QUOTE]

My son has been doing his school work in Windows and booting to Ubuntu just to get used to it but can't do any real work until I can get the wifi working.

---

### Post by ssck on 2005-09-06
this is a long shot ... not sure if you want to try the older ndiswrapper 1.1 version.

---

### Post by skirkpatrick on 2005-09-06
I had originally tried the version in the repositories, 1.0 I believe and it didn't work either.  I wonder if it has anything to do with the fact that I'm running a K7 kernel on that machine (I built 1.3 with the K7 kernel headers).  My HP laptop is running the 686 kernel and the 1.0 ndiswrapper in the repositories.

---

### Post by ssck on 2005-09-07
[QUOTE=skirkpatrick]I had originally tried the version in the repositories, 1.0 I believe and it didn't work either.  I wonder if it has anything to do with the fact that I'm running a K7 kernel on that machine (I built 1.3 with the K7 kernel headers).  My HP laptop is running the 686 kernel and the 1.0 ndiswrapper in the repositories.[/QUOTE]

i am afraid i am not sure if this is the cause .... maybe someone in the forum can help  :)

---

### Post by skirkpatrick on 2005-10-02
Finally!  It's working!

I've wiped the Acer laptop and reinstalled Breezy but it might work with Hoary.  NDiswrapper from the repositories appears to be fine as well as using the Windows driver from the Windows install.  The problem, of course, was that the radio wasn't getting turned on.  I had tried to follow directions from several people with 5020 laptops but finally realized that they were all wanting to use acer_acpi, which is for 64-bit laptops.  I built and installed acerhk and was still having problems.  I found out that the DSDT I had downloaded and installed for the battery was from a prior version of the BIOS.  When I removed DSDT, the wifi worked fine but of course, no battery detection.  I followed the directions for reading my current DSDT, decompiled it, made a few changes based on the other DSDT's, recompiled and installed.  Now, wifi and battery detection are working and with NetworkManager, everything is now automatic.

If anybody needs any help with the Acer Aspire 3000 series laptops, I'll stay subscribed to this thread for another month.

---

### Post by ubuntu_123 on 2005-10-04
Hi, skirkpatrick

Could you kindly explain to me how do you set up the wireless in your Acer laptop? cause I have an Acer aspire 3003wlci, and I have all the problems like you have before: "eth0" does show up along with the modern card in "system->administration->networking", but no wireless.

and I look around in here, most of it I feel lost, I am very new to here and ubuntu(only two days).

Any help will really been appreciated.
yasir.

---

### Post by skirkpatrick on 2005-10-04
Okay, first you need to know what version of BIOS you have.  The easiest way is to break into the BIOS at boot by pressing the F2 key when the Acer screen is showing.  The BIOS version will be 3A something.  I've updated my BIOS to 3A26 by downloading the update from the Acer website and updating it through my Windows boot.

---

### Post by ubuntu_123 on 2005-10-04
Hi, there.

Yes, I check my BIOS which is 3A27. what should I do next? and if I change the BIOS that shouldn't affect my another partition for windows, right? sorry, I didn't know these stuffs.

Many thanks.
yasir.

---

### Post by skirkpatrick on 2005-10-04
We're not actually going to change your BIOS, we're just going to read something out of it, modify it, and then just let Linux know to use the modification.

 Perform this command in a terminal window: **cat /proc/acpi/dsdt > dsdt.aml**

What this does is pull the DSDT binary that's in your BIOS and puts it in a file.  The next step is to decompile it so that you can make changes.  This step seems to be causing a lot of problems because people can't seem to build the Intel DSDT compiler.  To make it easier, hopefully you can use the copy I built [here]("http://webpages.charter.net/clan_kirkpatrick/iasl").  The command you need to use is **./iasl -d dsdt.aml** and should create a file called dsdt.dsl.  If you can't get this to work, email me your dsd.aml and I'll make the changes for you.
What you need to change in the dsdt.dsl file is two things.  First, replace all both occurrances of the text "Z007" with "Ones".  Second, find the lines that are similar to this:
>     Scope (_PR)
{
Processor (CPU0, 0x00, 0x00008010, 0x06) {}
}
 and add the line "External (\_PR.CPU0._PPC)" just under it.

Those are the only changes I had to make.  Now you need to compile your file into a new DSDT image.  Use the command **./iasl -tc dsdt.dsl** and it should produce a file called DSDT.aml.  As specified in the [ACPIBatter Wiki]("https://wiki.ubuntu.com/ACPIBattery"), if you are running Hoary, use the command **sudo cp DSDT.aml /etc/mkinitrd** to copy the file to its final destination (**sudo cp DSDT.aml /etc/mkinitramfs** if you're using Breezy) and then do **sudo dpkg-reconfigure linux-image-$(uname -r)** to reconfigure your kernel.  When you upgrade your kernel, it will still use your DSDT file.

If you have any problems, either the [ACPIBattery Wiki]("https://wiki.ubuntu.com/ACPIBattery") or the [ACPI Page]("http://acpi.sourceforge.net/") should answer some of your questions or, of course, post them here.

---

### Post by ubuntu_123 on 2005-10-05
Hi, skirkpatrick.

Thank you so much for your detail explanation.

My question maybe very basic and stupid, so I assume "&quot;" is a quote sign, right? Then I can't find "Z007" anywhere in dsdt.dsl. And your iasl works perfectly, thanks.

So, please look at the attached file to find out my dsdt.dsl

(The file is too big, it is beyond of the limitation of this forum, please decompress it with:  tar xzvf dsdt.tar.gz)

and also in your "sudo dpkg-reconfigure linux-image-$(uname -r)",  what is the last part of "linux-image-$(uname -r)"? how should I use it?

And I use Breezy 5.10.

Thanks.
yasir.

---

### Post by skirkpatrick on 2005-10-05
Hmm, not sure why the quotes didn't make it through.

I looked at your file and the lines with **Z007** are at line 3010 and 3011.

Type in **sudo dpkg-reconfigure linux-image-$(uname -r)** exactly as is.  the **$(uname -r)** gets automatically replaced with the version of the kernel you are using.

And don't forget to add the **External (\_PR.CPU0._PPC)** as specified earlier before you recompile your DSDT.

---

### Post by JazzCrazed on 2005-10-05
Thanks here, as well, skirkpatrick! Your help is greatly appreciated!

I'm having an issue, though, with the ./iasl command. When I try to run it, I get a "permission denied" error. I'm sudo, and everything. Any idea what's up?

I'm using an Acer Aspire 3002LCi, and I'm as big and as fat a n00b as it gets.

Thanks again for your help with this...
-JazzCrazed

*****EDIT:** I just CHMODded iasl and fixed it myself... Sorry!

---

### Post by ubuntu_123 on 2005-10-05
Hi skirkpatrick.

So, I change as you said like this:
 
at line 3010 and 3011.

            Name (PBST, Package (0x04)
            {
                0x00, 
                Ones,                  <---------------------- before is Z007 
                Ones,                 <----------------------  before is Z007
                0x2710
            })

And those are the only place for "Z007" occurs.
 
And 
    Scope (_PR)
    {   External (\_PR.CPU0._PPC)      <------------------------------  (1)
        Processor (CPU0, 0x00, 0x00008010, 0x06) {}        
        External (\_PR.CPU0._PPC)      <------------------------------  (2)
    }
    External (\_PR.CPU0._PPC)      <------------------------------  (3)

Since I am not quite sure when you said " just under it.", so I try the above 3 places.

And then for every placement I did :

/iasl -tc dsdt.dsl
sudo cp DSDT.aml /etc/mkinitramfs
sudo dpkg-reconfigure linux-image-$(uname -r)

reboot, and every time try to turn on the orange button, light still not on and "system->administration->networking" same as before.

And every time I got a warning:

**********************************
> 

yasir@rick:~$ ./iasl -tc dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler / AML Disassembler version 20050624 [Aug 27 2005]
Copyright (C) 2000 - 2005 Intel Corporation
Supports ACPI Specification Revision 3.0

dsdt.dsl  3387:     Method (_WAK, 1, NotSerialized)
Warning  2026 -                ^ Reserved method must return a value (_WAK)

ASL Input:  dsdt.dsl - 3467 lines, 121204 bytes, 1564 keywords
AML Output: DSDT.aml - 13969 bytes 377 named objects 1187 executable opcodes

Compilation complete. 0 Errors, 1 Warnings, 0 Remarks, 540 Optimizations
yasir@rick:~$ sudo cp DSDT.aml /etc/mkinitramfs
Password:
yasir@rick:~$ cd /etc/mkinitramfs/
yasir@rick:/etc/mkinitramfs$ ls
DSDT.aml  hooks  initramfs.conf  modules  scripts
yasir@rick:/etc/mkinitramfs$ sudo dpkg-reconfigure linux-image-$(uname -r)
Not touching initrd symlinks since we are being reinstalled (2.6.12-9.21)
Not updating image symbolic links since we are being updated (2.6.12-9.21)
Searching for GRUB installation directory ... found: /boot/grub .
yasir@rick:/etc/mkinitramfs$ Testing for an existing GRUB menu.list file... found: /boot/grub/men u.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.12-9-386
Found kernel: /boot/vmlinuz-2.6.12-8-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

yasir@rick:/etc/mkinitramfs$ gedit &
[1] 9360


> 
************************************************

Thanks, I really appreciates your help.
yasir.

---

### Post by ubuntu_123 on 2005-10-07
Anybody? any help? any hope?

Please?
yasir.

---

### Post by skirkpatrick on 2005-10-07
Yes, there is hope :D, I was just away from my computer too much the last 2 days.

First, my mistake in forgetting to tell you to do a **chmod +x iasl** to make the compiler executable.

Okay, the first problem is that you have too many External statements.  This is how my file looks in that area:
> 
     Scope (_PR)
     {
         Processor (CPU0, 0x00, 0x00008010, 0x06) {}
     }
     External (\_PR.CPU0._PPC)
 
I believe that I also got the warning about _WAK and I ignored it.  Now this change is only for your battery status.  You still need to go through the whole ndiswrapper process to get wifi working, which is a bit easier under Breezy than it is in Hoary.

In Breezy, the ndiswrapper kernel module appears to be installed by default.  Go into Synaptic and install **ndisgtk** which should automatically install **ndiswrapper-utils**.  If it doesn't just install it as well.

Now we need to tell the kernel to load the ndiswrapper module on every boot.  To do this, use **sudo gedit /etc/modules** and add **ndiswrapper** to the bottom of the list.  Reboot to make sure it is loaded.

You now need to know where your Windows wifi drivers are located.  On my now dual-boot machine, they were located in c:\Windows\802BG.  Copy everything that starts with "BCMWL5" to a location your Ubuntu can see (I mounted my NTFS drive under Ubuntu to get them).  Go to System->Administration and you will now see an item called "Windows Wireless Drivers".  This is the ndisgtk package you installed.  Run it and click on "Install New Driver".  Click on the little folder button to select your driver, which should be "bcmwl5a.inf" (I know that one works).  When it's finished, you should see "bcmwl5" listed in the left-hand box with "Hardware present: Yes" under it.

At this point, I highly recommend installing Network-Manager in Breezy.  It will automatically setup eth0 if an Ethernet cable is detected or setup wlan0 if it detects a wireless network with preference being to use eth0.  Once you've installed it through Synaptic, go to System->Preferences->Sessions and select the "Startup Programs" tab.  I added a new startup program called "nm-applet" with an order of 10.  This allows the little Network-Manager tray applet to startup.  I do still have a problem with ndiswrapper not correctly indicating signal strength, which is a known problem.

---

### Post by ubuntu_123 on 2005-10-07
Hi, skirkpatrick

Thank you for give me back the "hope":razz: .

So now, I did everything you said, I got the "wireless connection" by "System->administration->network", and then setup the wep key and use "DHCP", and also show "wlan0 is active". But internet doesn't work.

One thing occurs to me is that the light button to turn on the wireless card is not function, is it suppose to be turned on or off or it just work in silent? but it does work when in windows xp.

In another word, how do I know ubuntu already detect this hardware?

When I click on "System ->administration->windows wireless drivers", which show "bcmwl5a Hardware present:Yes", is that meant ubuntu already get it?

Thanks.
yasir.

---

### Post by skirkpatrick on 2005-10-07
A couple of things.

First, the orange LED that is normally on constantly in Windows when your wifi is active works differently in Ubuntu.  In Ubuntu, the LED flashes when you have network traffic.

Second, wlan0 won't work if eth0 is active.  If you use System->Administration->Networking, you need to deactivate eth0 and make sure that "Default Gateway Device" is set to wlan0.  To use eth0 again, you need to deactivate wlan0.  This is why it's easier to use nm-applet with Network-Manager as it will automatically switch back and forth for you, depending on which is available with preference for eth0.

The only problem I've found is that bootup will hang until you press Ctrl-C waiting for eth0 to find a connection if it doesn't have one.  I've gotta take the time to figure that out.

---

### Post by ubuntu_123 on 2005-10-07
Hi, there.

Thanks for your answer.

But now I deactivate etho and the default gateway is set to wlan0, it still doesn't work, and I even reboot the system, still no luck.

The orange LED has no reaction, no flash, nothing, and I try to push it to turn it on or off, still nothing.

When I reboot it does hang around for a long time when checking the network connection, then I just crl+c. and after I reboot, the "etho" automatically been activated along with wireless connection, even I deactived the eh0, still not working.

And I does did exactly like you said for "nm-applet", but nothing show up, and where is the network manager in the top-down menu?

Thanks, sorry it is getting longer and longer now.
yasir.

---

### Post by skirkpatrick on 2005-10-07
Don't trouble yourself with all the questions, everybody needs help from time to time ;)

Network-Manager does not show up in the applications list, it is a daemon that runs in the background.  nm-applet does not show up in the applications list either.  You should be able to do a **ps -A** and see Network-Manager and Network-ManagerD in the list of processes that are running (you did install Network-Manager through Synaptic, didn't you?).

If you have activated wlan0 in System->Administration->Networking, you can open a terminal window and do some verification.  Type **ifconfig** and you should see wlan0 listed.  If so, type **sudo iwlist wlan0 scan** and it should give you the details of any wifi networks it finds.  If not, we are getting closer to your problem.

---

### Post by ubuntu_123 on 2005-10-07
Hi, skirkpatrick.

Thank you for your answer.

My laptop is not in internet now and I use another network to access internet, but I will post the complete list later tonight when I get home. Basically, when I run "ifconfig", I get list for "lo" and another for "wlan0",  roughly it is like this:

(I type)
lo           Link encap:Local    Loopback
             inet addr:127.0.0.1  Mask:255.0.0.0
             ........

wlan0     Link encap:Ethernet   HWaddr  00:14:A4:2F:81:C8
             inet addr: fe80::214:a4ff:fe2f:81v8/64  Scope: Link
             ........

When I  run "sudo iwlist wlan0 scan", I got something like this, also roughly:

wlan0     Scan completed: 
             Cell 01  - Address : 00:E0:63:50:97:B8
                           ESSID: " "
                           Protocol: IEEE 802.11b
                           Mode:Managed
                           ....
                           Frequence : 2.412 GHz(Channel 1)
                           Quality:0/100 Singal level:-81 dBm Noise level:-256 dBm
                           Encryption key:on
                           Bit rate : 1Mb/s
                           Bit rate : 2Mb/s
                           Bit rate : 5.5Mb/s
                           Bit rate : 11Mb/s
                           .......
          Cell 02  -  format same as cell 01 but different.

          Cell 03  -  same as cell 02.

I am sorry, now I try to install Network-Manager through "Synaptic Package Manager", but couldn't find the appropriate package with the name of  "network-manager" something.

Thanks.
yasir

---

### Post by skirkpatrick on 2005-10-07
Hah!  Now we are getting somewhere!

Network-Manager is in the Universe repository, named **network-manager**.  Do a **sudo gedit /etc/apt/sources.list** and find:
> 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy

and add **universe multiverse** to the end.  You can also do this for all the other lines.

It appears your wlan0 is indeed seeing a wifi network that is "managed" instead of "open" and doesn't transmit its ESSID.  What do you normally have to know under Windows to connect to that network?

---

### Post by ubuntu_123 on 2005-10-08
Hi again, thanks again.

I am in canada, this is my source.list:

Like you said ,I put universe multiverse to the end of every line.

***********************************************
> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)]/ breezy main restricted


deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse



*************************************************
I saves it, and reboots it, nothing yet.

under windows we need to know:

Network name(SSID): we fill in this

Network Authentication : open
Data encription : WEP
Network key: we fill in this.

Key index : 1.

That's all.

Thanks.
yasir.

---

### Post by skirkpatrick on 2005-10-08
Okay, after you make any changes to /etc/apt/sources.list, you need to press the Reload icon in Synaptic so that it knows about the new repositories.  Then you'll be able to search for and install Network-Manager.

Now what's interesting is that you say that under Windows, your Network Authentication is Open while **sudo iwlist wlan0 scan** reports that it's Managed.

---

### Post by ubuntu_123 on 2005-10-08
Hi, skirkpatrick

Thanks, always.

When I go to Synaptic Package Manager I got two errors message:

> W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Preview i386 (2005090 breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Preview%20i386%20(2005090_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Preview i386 (2005090 breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Preview%20i386%20(2005090_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

Maybe it is still ok, seems it is about cdrom. So I reload it.

I double checks the wireless setting when I uses under windows XP service patch 2.  Network Authentication is Open.

Please follow this link to take a look the setting,

[http://www.utoronto.ca/ic/utordist/wireless/winxp_sp2.pdf](http://www.utoronto.ca/ic/utordist/wireless/winxp_sp2.pdf)

 that is the simple instruction for all people using that wireless network has to follow including the setting of Network Authentication, it is too big to be uploaded in here..

And I also attach another file with name "result " for running "sudo iwlist wlan0 scan", just for save some thread space. the first result with " wlan0     No scan results" is after I push the orange button one time, even the light is not on, the second result is after I push the button again, but the light still not on. it seems the button is working but not light on,and in windows xp has no problem.

Thanks.
yasir.

---

### Post by skirkpatrick on 2005-10-08
Those warnings are okay, it just means that Synaptic didn't see your Breezy install CD.  I comment out the first line of the /etc/apt/sources.list (put a # at the beginning of the line) so it doesn't check the CD.  But you should be okay.

It does indeed look like your button is working but as I said earlier, under Linux the light will flash when you are transmitting or receiving data.  Otherwise, it will be off which is different than Windows.

Your laptop can see 3 different wifi networks, only one of them is transmitting its ESSID (ecosuite14) and two of the networks are 802.11b while ecosuite14 is 802.11g.  None of them appear to use the same information that's in your PDF install guide.

What network is listed in your Windows setup?

---

### Post by ubuntu_123 on 2005-10-09
Hi, skirkpatrick

Thank you.

I am not quite sure the network list, but I checks the network connection in windows xp under control panel:

There are two of them list under LAN or High-speed Internet.

Wireless Network Connection
Broadcom 802.11g Network Adapter

Local Area Connection
SiS 900-Based PCI Fast Ethernet Adapter


When I setup windows, I don't remember whether there is a list about the network or not, but under ubuntu there are three show up, two like the above, plus the moderm.


Have a good weekend, I appreciates that.
yasir.

---

### Post by jonos on 2005-10-09
Hi guys,

Thanks for the HowTo it was simple to follow : good for me :D... Everything went right ( the dsdt changes, the compiling and the reconfiguring )but the power status still doesn't work. dmesg gives 

> ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node dbaa1ee0 start_node dbaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node dbaa1de0), AE_NOT_FOUND

So it seems that the DSDT.aml file isn't read. 

I'm working on an Acer 3003lci with hoary and a 3A24 bios version. Is there anything I should be doing different from what you said above with my actual configuration?

By the way the DSDT files proposed by the ACPI wiki has only a change in the Z007 not the other line you added. What is the purpose of that line (I'm just curious about the ppc that's in it actually)?

Thx

---

### Post by skirkpatrick on 2005-10-09
[QUOTE=ubuntu_123]
Wireless Network Connection
Broadcom 802.11g Network Adapter

Local Area Connection
SiS 900-Based PCI Fast Ethernet Adapter
[/QUOTE]

You want "Wireless Network Connection".  Double-click on it then click on the "Properties" button.  In the new dialog box, select the "Wireless Networks" tab.  In the "Preferred networks" box, select your currently active network and click on the "Properties" button.  It will show you the SSID, Network Authentication type, and Data encryption type.

---

### Post by skirkpatrick on 2005-10-09
jonos,

You are correct it sounds like DSDT.aml isn't getting loaded.  For Hoary, you need to copy the file to /etc/mkinitrd instead of /etc/mkinitramfs.

That other line had to be added to eliminate a compile error.

---

### Post by jonos on 2005-10-09
[QUOTE=skirkpatrick]jonos,

You are correct it sounds like DSDT.aml isn't getting loaded.  For Hoary, you need to copy the file to /etc/mkinitrd instead of /etc/mkinitramfs.

That other line had to be added to eliminate a compile error.[/QUOTE]


Hi Skirkpatrick,

Thanks for the fast answer but I did that already... Do you have another idea??

---

### Post by skirkpatrick on 2005-10-09
Hmm, did you also do **sudo dpkg-reconfigure linux-image-$(uname -r)**?

---

### Post by jonos on 2005-10-10
[QUOTE=skirkpatrick]Hmm, did you also do **sudo dpkg-reconfigure linux-image-$(uname -r)**?[/QUOTE]

yep 

I did that as well (just like your HowTo said...) 

what I get is: 
> 
Not touching initrd symlinks since we are being reinstalled (2.6.10-34.6)
Not updating image symbolic links since we are being updated (2.6.10-34.6)
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.10-5-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


but I just looked again and the DSDT.aml file I modified is there in the **mkinitrd** dir. To be absolutely sure, I decompiled that file and the changes are there...

Still doesn't work... :confused:

**Edit**:
Ok guys, I got it...
There is probably something in the mkinitrd.conf that wasn't right. I wasn't able to fix it so I just followed the instructions for the other way of fixing the DSDT.aml on the ACPIbattery wiki and that just made it go well.

thx for your help skirkpatrick : your howto was the most understandable I've found on battery problems

---

### Post by skirkpatrick on 2005-10-10
I'm afraid I can't help you too much more under Hoary as I've installed mine under Breezy.

---

### Post by JazzCrazed on 2005-10-10
I'm back again! I took a brief side-track, unsuccessfully, with a couple of PCMCIA cards.

Unfortunately, I get stalled with this far earlier than most:

```
~# cat /proc/acpi/dsdt > dsdt.aml
~# ./iasl -d dsdt.aml
./iasl: line 1: syntax error near unexpected token `newline'
./iasl: line 1: `<html>'

```

Any clue what's up? I've attached my dsdt.aml (renamed to .txt so that I could attach it) herein.

Thanks for your help!

---

### Post by jonos on 2005-10-10
If you're hoary you will probably have to put the DSDST.aml directly in the initrd.img. I was kinda scared to do it : I don't like touching to all that stuff :???: . but at the end I didn't need the backup I made. If you want to do the same you can just follow [https://wiki.ubuntu.com/ACPIBattery:](https://wiki.ubuntu.com/ACPIBattery:) you can start at the backup subtitle if you've followed all skirkpatrick's instructions

---

### Post by jonos on 2005-10-10
Hi Jazzcrazed

it probably has something to do with the iasl compiler... Did you CHMODed it?

But nevermind, I decompiled your dsdt.aml, changed it and recompiled it: So there it is (I also had to put it in a text version so you'll have to change the .txt to .aml to have it right)

---

### Post by skirkpatrick on 2005-10-10
I orginally started this laptop on Hoary and also put DSDT.aml directly in the initrd.img.  It worked but things broke as soon as I upgraded the kernel as you have to do it again for every kernel upgrade.  Too bad it doesn't seem to work by just putting DSDT.aml into a directory like in Breezy.

---

### Post by JazzCrazed on 2005-10-10
jonos and skirkpatrick, you guys both rock!

First off, thanks for compiling for me and saving me all those steps, jonos! I actually had CHMODed the compiler; before doing that, I got a "Permission denied" error which clued me into CHMODding it. That second error I received when running ./iasl after I CHMODed it is inexplicable to me.

But using your DSDT.aml, and following skirkpatrick's detailed steps thereafter, worked like a charm!

I'm posting via wifi right now just to verify that it works.

Thanks again!

**EDIT:** One thing that I noticed when configuring the networking to use my work AP's WEP key was that there was no option for WPA. At home I use WPA... I guess that's a tale for another howto!

---

### Post by skirkpatrick on 2005-10-10
Now WPA isn't something I've had to mess with.  Do a forum search for wpa_supplicant, I'm sure you'll find what you need there :D

---

### Post by beercz on 2005-10-11
[QUOTE=skirkpatrick]
What you need to change in the dsdt.dsl file is two things.  First, replace all both occurrances of the text "Z007" with "Ones".  Second, find the lines that are similar to this:
Quote:

Scope (_PR)
{
Processor (CPU0, 0x00, 0x00008010, 0x06) {}
}

and add the line "External (\_PR.CPU0._PPC)" just under it.

[/QUOTE]
hi skirkpatrick

I have decompiled my dsdt.aml, no problem.

However when I edit it, I cannot find either Z001.

My Scope (_PR) section looks like this:

    Scope (_PR)
    {
        Processor (CPU0, 0x00, 0x00001010, 0x06)
        {
            Name (_PCT, Package (0x02)
            {
                ResourceTemplate ()
                {
                    Register (SystemIO, 0x08, 0x00, 0x00000000000000B2)
                }, 

                ResourceTemplate ()
                {
                    Register (SystemIO, 0x08, 0x00, 0x00000000000000B3)
                }
            })
            Name (_PSS, Package (0x05)
            {
                Package (0x06)
                {
                    0x05DC, 
                    0x5DC0, 
                    0x0A, 
                    0x0A, 
                    0x89, 
                    0x00
                }, 

                Package (0x06)
                {
                    0x04B0, 
                    0x4E20, 
                    0x0A, 
                    0x0A, 
                    0x8A, 
                    0x01
                }, 

                Package (0x06)
                {
                    0x03E8, 
                    0x4650, 
                    0x0A, 
                    0x0A, 
                    0x8B, 
                    0x02
                }, 

                Package (0x06)
                {
                    0x0320, 
                    0x3E80, 
                    0x0A, 
                    0x0A, 
                    0x8C, 
                    0x03
                }, 

                Package (0x06)
                {
                    0x0258, 
                    0x2EE0, 
                    0x0A, 
                    0x0A, 
                    0x8D, 
                    0x04
                }
            })
            Method (_PPC, 0, NotSerialized)
            {
                Return (0x00)
            }
        }
    }

So I am not sure where to put my  External (\_PR.CPU0._PPC), but I think it should go after the last closing curly bracket (}).

Any suggestions?

Thanks in advance.

Ian

---

### Post by nocturn on 2005-10-11
[QUOTE=skirkpatrick]It appears that the radio isn't turned on.  Anybody have any opinions?[/QUOTE]

How did you see this?  

I have a broadcom card too (HP Pav. ZV5474EA) and I have the same problem after switching to Breezy.

I do have a switch, but it is turned on.

---

### Post by skirkpatrick on 2005-10-11
beercz:

If you can't find a Z001 (that's Z zero zero one), then you probably don't have that problem, although check dmesg and see if it's complaining about anything.  I would assume that the "External" line would go after the closing curly bracket of Scope.


nocturn:

iwlist semed to show that everything was working but would always return no scan results when I know that the AP was working.  I tried building and installing acerhk but even though I got some of the buttons working, the wifi wouldn't see the AP until I fixed the problem with my DSDT.

---

### Post by JazzCrazed on 2005-10-13
Hey everybody...

I'm back, but sadly not on my Acer, because it's having problems during boot.

It seems to freeze during "Loading ACPI Modules..." - very similar to what is happening to Ian per this thread: [http://ubuntuforums.org/showthread.php?t=68630](http://ubuntuforums.org/showthread.php?t=68630)

...and as described in this bug report: [http://bugzilla.ubuntu.com/show_bug.cgi?id=16863](http://bugzilla.ubuntu.com/show_bug.cgi?id=16863)

I'm using the same Kernel as he is, 2.6.12-9-386.

So I log into 2.6.12-9-386 Recovery Mode, and start from step 1 of skirkpatrick's  howto and the [ACPI wiki]("https://wiki.ubuntu.com/ACPIBattery?highlight=%28acpi%29"). I'm able to download the iasl source from Intel, compile (via ethernet connection), and run through all the steps with dsdt - all the way through to reconfiguring the kernel with the new DSDT.aml in /etc/mkinitramfs.

But it still freezes on loading ACPI modules.

The only way I can get into the desktop now is by adding this to Grub:
"acpi=off"

And of course wireless doesn't work as a result, and the power monitor is all kinds of wrong (reports "System is running on battery power 0 minutes (0%) remaining" when I'm plugged into the adapter). After getting into desktop, I am able to connect with regular old ethernet; I try reinstalling ndiswrapper through synaptic, and it's seemingly able to deal with my driver (System->Administration->Wireless Network Drivers: "bcmwl5a Hardware present: Yes").

At least I can still get by with regular old ethernet. But I miss wifi already... :(

---

### Post by skirkpatrick on 2005-10-13
Something that also occurred to me was that building and installing acerhk also helped with the wifi.  I'm almost thinking you have to have it as well.  Not sure what the ACPI problem is as I haven't seen it.  Now my Acer is also using the K7 kernel.

---

### Post by JazzCrazed on 2005-10-13
Before I break something, is this the same acerhk to which you're referring?:

[http://www.informatik.hu-berlin.de/~tauber/acerhk/](http://www.informatik.hu-berlin.de/~tauber/acerhk/)

It doesn't look like my model is included in that list... Though it has a link to this:

[http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html](http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html)

...which purportedly works with "later model" Acer laptops. I tried to follow its install directions, but I get a whole bunch of errors on compiling. It's a massively long list of errors, but I think it all comes down to me missing some specific library.

---

### Post by skirkpatrick on 2005-10-13
acer_acpi wouldn't work on mine, I think I read somewhere that it's for the 64-bit processors.  That's the acerhk I used, I'll go pry my son's laptop out of his hands and give you the startup parameters I used.

---

### Post by JazzCrazed on 2005-10-13
OK, downloaded the sources for acerhk and tried to compile by hitting in "make."

I got some errors that lead me to believe I was missing Linux header files. So I hit up "Linux headers" in Synaptic, and got this in return:

[B]linux-headers-2.6.12-9
linux-headers-2.6.12-9-386 [/B]

I installed both.

Then I returned to the directory in terminal and ran "make" again:

```
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/jazzcrazed/Desktop/DOWNLOADS/BIOS, DRIVERS, AND FIRMWARE/acerhk-0.5.27 modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** No rule to make target `DRIVERS,'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [acerhk.ko] Error 2

```

Yeah...Then I noticed there was an INSTALL script in there (anybody realize how clueless I am yet?), so I did:

```
# chmod +x INSTALL
#./INSTALL
```

...which resulted in this:

```
./INSTALL: line 1: Installation: command not found
./INSTALL: line 2: acerhk.c: command not found
./INSTALL: line 4: syntax error near unexpected token `('
./INSTALL: line 4: `1. You need the kernel sources (or kernel headers for your kernel)'
```

So apparently I need the kernel headers/sources. But I'm out of time for now...be back later with a status update!

And yes... I'm ultran00b. :D 

Thanks for your help!

---

### Post by skirkpatrick on 2005-10-13
I don't think you need the kernel headers.  However, you do need the gcc-3.4 compiler which is default for Hoary and in the Breezy repositories.  You can install it beside gcc-4.0 that's Breezy's default and it won't cause a problem.

---

### Post by CrippledCanary on 2005-10-14
About the ACPI problem. I have had the same problem when trying to run openSuSE 10.0.
I wrote a page [http://crippledcanary.se]("http://crippledcanary.se/?page_id=9") about it. The page links to a bug in bugzilla for SuSE as well as a bug for the Linux kernel that explains the nature of the problem a bit. I am going to install breezy this weekend and will post back my results of that.

---

### Post by JazzCrazed on 2005-10-14
skirkpatrick:

I installed gcc-3.4 and gcc-3.4-base via synaptic.

Then I ran the install script again:

```

#./INSTALL
./INSTALL: line 1: Installation: command not found
./INSTALL: line 2: acerhk.c: command not found
./INSTALL: line 4: syntax error near unexpected token `('
./INSTALL: line 4: `1. You need the kernel sources (or kernel headers for your kernel)'

```

I also tried running "make":

```
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/jazzcrazed/Desktop/DOWNLOADS/BIOS, DRIVERS, AND FIRMWARE/acerhk-0.5.27 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** No rule to make target `DRIVERS,'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [acerhk.ko] Error 2

```

:confused: 

CrippledCanary:

I checked out your page, and for the most part it is the same as skirkpatrick's howto in this thread, except for the step to copy DSDT.aml to /etc/acpi. I've only copied it to /etc/mkinitramfs.

I've copied it now and will report on the consequences shortly.

Thanks all!

---

### Post by skirkpatrick on 2005-10-14
JazzCrazed,

The INSTALL file is only a text document detailing how to build the program.  It looks like you now have the compiler working but it's having problems finding your kernel headers.  Make sure you have used Synpatic to install either linux-headers-386, linux-headers-686, or linux-headers-k7 depending on what kernel you are running.  They will update the headers any time you update the kernel.

---

### Post by JazzCrazed on 2005-10-14
skirkpatrick,

Wow, that was rather stupid of me not to realize it was just a readme file!

I actually had linux-headers-2.6.12-9 and linux-headers-2.6.12-9-386 installed, prior to getting those errors. Could these be the wrong versions?

Will it hurt if I install the other versions headers?

**EDIT:** Just discovered that it *does* matter what version I have installed... If I have versions other than my kernel, it ignores them in favor of 2.6.12-9; and if I remove 2.6.12-9, leaving other versions, it complains about their absence.

So here's the error I'm still getting when trying to run **make acerhk.ko** (per the readme file):

```
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** No rule to make target `DRIVERS,'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [acerhk.ko] Error 2
```

**EDIT 2:** Speaking of older kernels, I took a hint from beercz and I'm booted now into 2.6.12-8-386 - the other version that was present in Grub. Wifi works fine in this kernel. Is there any real reason for me to go with the newer version?

Also, anybody know what's changed between 8 and 9 that has caused this issue?

---

### Post by skirkpatrick on 2005-10-15
You're not stpi, just inexperienced :)  In source trees, it seems like the standard is that all files that are all upper-case are text files.

linux-headers-386 should just give you whatever is the latest headers just like linux-kernel-386 gives you the latest kernel.  I'm not even sure what kernel is running on my son's Acer.  It's hard to pry it away from him and right now, my wife is taking a nap on my chest on the couch while I'm using my HP laptop :D

---

### Post by CrippledCanary on 2005-10-16
Is this thread still about wifi problems on Acer Aspire 3003?

I have got wifi up and running on my Acer Aspire 3003 LMi using Breezy and ndiswrapper. If you still are running Hoary you should consider a change.

---

### Post by skirkpatrick on 2005-10-16
Yeah, it's still about wifi on Acer and Jazz is running Breezy.  My Acer is 2.6.12-9-k7 kernel with ndiswrapper 1.1-4.

---

### Post by JazzCrazed on 2005-10-16
It's running on my Aspire 3002LCi, but using the older 2.6.12-8-386 kernel. If I boot into 2.6.12-9-386, which my grub has as default, it - and ACPI - doesn't work.

---

### Post by CrippledCanary on 2005-10-17
As I said before I have a Asprire 3003LMi and after fixing the buggy DSDT I was able to use wifi using ndiswrapper and the downloaded ndis driver from Acers web page. I user kernel 2.6.12-9-386 for the moment and no customizations.
I don't know if it works on Aspire 3002 computers.

I plan to try a more AMD specific kernel if available but have not done so yet.

---

### Post by Chris Tucker on 2005-10-27
Ok, first off Great work so far, i have the aspire 3003wlci and ive managed to get my ACPI working after very little frustration, however, my wifi is not going so well... i went and got ndiswrapper, but it was the newest ver, not 1.1, im thinking that was my mistake but i have no idea.
what troubles me to be the cause of my problems is the first blurb that appears when i do iwlist wlan0 scan:

```
chris@AcerNotebook:~$ sudo iwlist wlan0 scan
Password:
Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:40:9E:72
                    ESSID:"ChrisHome"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-45 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

when i try to connect to this network by useing the network panel from System -> administration, and set my stuff there, it pops up a dialog with a bar that sweeps for what seems to be longer than it shoud, then that disappears, but nothing works. ive tried combinations of times of disableing the wired connection, but no luck. ive tried setting it all by command line, no luck.

i know my front button is not the problem as when i push it, and then do the scan, theres no result, so i always do the scan first to make sure the radio is on before setting stuff. so i think its the point that blurb that comes up at the begin of any wifi action that is my trouble.
right now, i am on 5.04, gnome. using the wifi driver for my broadcom card that i snatched from XP. , but tonight im going to backtrack my steps for getting my ACPI working, so i can do it again, and tomorrow i will hopefully be moving to 5.10.

any suggestions?
also, anyone get the function buttons to work successfully? if so im also having some trouble with that.

---

### Post by skirkpatrick on 2005-10-27
Well, you can scan for your network so it appears that you built DSDT correctly (building it incorrectly can cause your battery to work but not your wifi) and have acerhk installed (without acerhk, your radio won't get turned on).

It says the network is in managed mode, do you have the correct WEP key?  There still appears to be problems with WPA networks and the general consensus is to downgrade your network to WEP.  Also, your eth0 needs to be disabled to get wlan0 to connect.  That's one of the reasons I really prefer NetworkManager and nm-applet in Breezy, they'll handle wired/wireless changeover automatically for you.

As far as the function buttons, building and installing acerhk allowed some of the buttons to just work in Breezy (email, and that group) but I haven't played with any of the others.

---

### Post by Chris Tucker on 2005-10-27
i dont have acerhk installed, i havent gotten that to work. and ive played countless times with eth0 off, on, and anywhere in between!, my wep key is correct, and i have even tried it with encryption turned off... and removed the wep key from the laptop, absolutely no progress.
perhaps something ***did*** go wrong with the ACPI setup... 
any tips on acerhk? where to get it, if there is more than one option on the site, which one? etc.

---

### Post by skirkpatrick on 2005-10-27
Check out post [http://ubuntuforums.org/showpost.php?p=431179&postcount=4](http://ubuntuforums.org/showpost.php?p=431179&postcount=4) about acerhk.

---

### Post by Chris Tucker on 2005-10-27
guess i'll wait untill tomorrow, acerhk installed, no errors, but does nothing. Tomorrow i should have breezy.

---

### Post by CrippledCanary on 2005-10-27
I defenitly think you should go with the 5.10 version of Ubuntu.
After fixing the DSDT on my 3003LMi (witch is closely related to your machine) I used the ubuntu supplied ndiswrapper and downloaded windows drivers from Acers support site to get my WLAN to work. 
I don't have acerhk but the funktion buttons, battery and Suspend/Hibernate all work perfectly anyway.

The "System->Administration->Networking" configuration didn't take me all the way though, I had to do some manual changes to /etc/network/interfaces.

--- snip from /etc/network/interface---
# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface wlan0 inet dhcp
wireless-essid xxxxxxxx
wireless-key xxxxxxxxxxxxxxxxxxxxxxxxxxxxx
#These two lines were manually added.
wireless-keymode open
wireless-mode managed



auto wlan0

iface eth0 inet dhcp

---

### Post by JazzCrazed on 2005-10-28
Been really bad at paying attention to these forums... Sorry!

I also heartily agree with moving to 5.10 - if only to fresh install. I installed 5.10 anew on my laptop after getting a new HDD for my Aspire, and it seemed to cooperate far more easily with my hardware. Although shortly thereafter, I also purchased an Intel 2915ABG mini pci card to replace the Broadcom (cheating, I know! Sorry!).

Re: seeing your network but not being able to connect - make sure also to check on MAC filtering. I'm sure you did check for this - but worth double-checking... Easy to make a typo in your MAC address. That was something I neglected at first with my AP that had me frustrated for a bit (it scanned it and seemed to nearly connect, before just plain quitting the scan or reverting to another nearby AP, of which there are many in my apartment building).

Can you connect to other AP's, or do all of them give you problems?

PS: acerhk does seem to come with Breezy, so that's another incentive to upgrade. After fresh installing, the special buttons for both internet and e-mail work with no setup on my part - opens up Firefox and Evolution, respectively.

---

### Post by Chris Tucker on 2005-10-31
ok, ive managed to get up and running :D and, like everyone else, i shall post my story...

(this is on Breezy 5.10 a fresh install)

i started out ticked off, drove mad because it was becomeing teadious, then saw a slight bit of hope in this thread, but ended up only getting my ACPI working from here.
for the battery recognition, i just used the nice ACPI instructions found here ;) 
then, i followed through and apt-got ndiswrapper-utils and the gtk frontend., but, despite being able to load my drivers succesfully from C:\windows\802BG\BCMWL* , wifi would not connect, under any circumstance. it would display in sudo iwlist wlan0 scan , but not connect.

so i scrounged around and compiled from a bunch of different threads, a solution for my acer 3003wlci :
ok, so the wired and wireless dont play nicely together, so i disabled the wired untill i need it, by sudo pico /etc/network/interfaces:
```
# The primary network interface
#iface eth0 inet static
#       address 192.168.1.2
#       netmask 255.255.0.0
#       network 192.168.0.0
#       broadcast 192.168.255.255
#       gateway 192.168.1.1
#       # dns-* options are implemented by the resolvconf package, if installed
#       dns-nameservers 192.168.1.1

```
all commented out :) 
so, i changed around my wireless data
```
auto wlan0
allow-hoplug wlan0
iface wlan0 inet dhcp
wireless-mode managed
wireless-channel X
wireless-essid XXXXXX
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX open
map wlan0

```
yea, 26 character HEX key ;) no ones guessing that one.
one thing i added myself, was the map wlan0 , im not positive but i think that tells the system to use that as the default device to connect to the net, or anything for that matter.

i also shallowed my dhcp timeout from 60sec to 10sec, which speeds up boot time when not connected to any network.

this all might seem simple, but it can be a royal pain when you dont know it.

---

### Post by skirkpatrick on 2005-11-01
Check out [http://www.ubuntuforums.org/showthread.php?t=25683&page=26](http://www.ubuntuforums.org/showthread.php?t=25683&page=26), it also details how to disable having the network initialize during startup and let Network Manager handle it.

---

### Post by Chris Tucker on 2005-11-02
i left my network on during start, just the wifi not the wired, and lowered the dhcp timeout to save time. i did this because i want the system to update to ntp on boot, whenever possible.

---

