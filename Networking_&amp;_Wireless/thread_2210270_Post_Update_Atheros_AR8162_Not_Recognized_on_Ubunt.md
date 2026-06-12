---
title: "Post Update: Atheros AR8162 Not Recognized on Ubuntu 12.04 &amp; New eePC 1015E-DS02"
date: 2014-03-10
forum: Networking &amp; Wireless
---

### Post by spock3 on 2014-03-10
Hi.

Been a long time Asus customer, just moved over from WinXP to brand new eePC 1015E DS02 running Ubuntu 12.04 & am absolutely loving it.

After successfully accepting all of the recommended software upgrades from the Ubuntu Software Center, my ethernet card is no longer working.

The wireless & Bluetooth work just fine.

In checking the hardware from a terminal session, I get the following:

H/W path       Device  Class          Description
=================================================
/0/100/1c.1/0  wlan1   network        AR9462 Wireless Network Adapter
/0/100/1c.3/0          network        AR8162 Fast Ethernet
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR9462 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan1
       version: 01
       serial: 6c:71:d9:7d:2c:d8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-60-generic firmware=N/A ip=192.168.1.5 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f7d00000-f7d7ffff memory:f7d80000-f7d8ffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8162 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f7c00000-f7c3ffff ioport:e000(size=128)

Since the ethernet controller was working just fine along with Bluetooth & Wireless, is it possible to do a selective rollback on the update or should I pursue
locating the correct driver and reconfiguring it to the ethernet controller?

Please advise.

Thanks

---

### Post by varunendra on 2014-03-10
Welcome to the forums spock3!

Instead of trying to roll back, I suggest you perform the update once again. It seems the previous update didn't complete successfully, since the required driver for this card should be in the kernel.

Please try -
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Watch out for errors, post back if you see any.

If that completes successfully, and the Ethernet still appears as "UNCLAIMED", please post back the outputs of -
```
uname -mr
modinfo alx
dmesg | grep alx
```

**PS:**
Terminal commands & outputs should always be posted within '**Code**' tags to preserve their formatting and make the post compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by spock3 on 2014-03-10
Thanks, Varunendra.

I performed the update again using the code block you supplied.

No errors were reported.

The Ethernet controller still showing as "unclaimed".

I did, however, get a partial result from the 2nd code block you supplied.

But, my system responded with a "not found" to the alx command input.

Not sure if this helps, but I included a [link to an old bug report/fix]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1024884") for this card.

Here's the code block from the session described:

```

~$ sudo apt-get update

Hit http://archive.canonical.com precise Release.gpg
Hit http://archive.ubuntu.com precise Release.gpg                                          
Get:1 http://archive.ubuntu.com precise-updates Release.gpg [198 B]                        
Get:2 http://security.ubuntu.com precise-security Release.gpg [198 B]                                
Hit http://asus.archive.canonical.com precise-annan Release.gpg                                      
Get:3 http://extras.ubuntu.com precise Release.gpg [72 B]                                  
Hit http://archive.canonical.com precise Release                                           
Hit http://archive.ubuntu.com precise Release                                              
Get:4 http://security.ubuntu.com precise-security Release [49.6 kB]                        
Hit http://asus.archive.canonical.com precise-annan Release                                          
Hit http://extras.ubuntu.com precise Release                                                         
Get:5 http://archive.ubuntu.com precise-updates Release [49.6 kB]                                    
Hit http://archive.canonical.com precise/partner Sources                                             
Hit http://asus.archive.canonical.com precise-annan/public Sources                                   
Hit http://extras.ubuntu.com precise/main Sources                                                    
Hit http://asus.archive.canonical.com precise-annan/public amd64 Packages                            
Hit http://asus.archive.canonical.com precise-annan/public i386 Packages                             
Ign http://asus.archive.canonical.com precise-annan/public TranslationIndex                          
Hit http://archive.canonical.com precise/partner amd64 Packages                                      
Hit http://archive.canonical.com precise/partner i386 Packages                                       
Ign http://archive.canonical.com precise/partner TranslationIndex                                    
Hit http://extras.ubuntu.com precise/main amd64 Packages                                             
Hit http://extras.ubuntu.com precise/main i386 Packages                                              
Ign http://extras.ubuntu.com precise/main TranslationIndex                                           
Get:6 http://security.ubuntu.com precise-security/main Sources [98.4 kB]                             
Hit http://archive.ubuntu.com precise/main Sources                                                   
Hit http://archive.ubuntu.com precise/restricted Sources                                             
Hit http://archive.ubuntu.com precise/universe Sources                                               
Hit http://archive.ubuntu.com precise/main amd64 Packages                                            
Hit http://archive.ubuntu.com precise/restricted amd64 Packages                                      
Hit http://archive.ubuntu.com precise/universe amd64 Packages                                        
Hit http://archive.ubuntu.com precise/main i386 Packages                                             
Hit http://archive.ubuntu.com precise/restricted i386 Packages                                       
Hit http://archive.ubuntu.com precise/universe i386 Packages                                         
Hit http://archive.ubuntu.com precise/main TranslationIndex                                          
Hit http://archive.ubuntu.com precise/restricted TranslationIndex                                    
Hit http://archive.ubuntu.com precise/universe TranslationIndex                                      
Get:7 http://archive.ubuntu.com precise-updates/main Sources [451 kB]                                
Get:8 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]                       
Get:9 http://security.ubuntu.com precise-security/universe Sources [30.9 kB]                         
Get:10 http://security.ubuntu.com precise-security/main amd64 Packages [369 kB]                      
Ign http://asus.archive.canonical.com precise-annan/public Translation-en_US                         
Ign http://extras.ubuntu.com precise/main Translation-en_US                                          
Ign http://archive.canonical.com precise/partner Translation-en_US                                   
Ign http://asus.archive.canonical.com precise-annan/public Translation-en                            
Ign http://extras.ubuntu.com precise/main Translation-en                                             
Ign http://archive.canonical.com precise/partner Translation-en                                      
Get:11 http://archive.ubuntu.com precise-updates/restricted Sources [8,028 B]           
Get:12 http://archive.ubuntu.com precise-updates/universe Sources [105 kB]                  
Get:13 http://archive.ubuntu.com precise-updates/main amd64 Packages [758 kB]        
Get:14 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]    
Get:15 http://security.ubuntu.com precise-security/universe amd64 Packages [91.2 kB]
Get:16 http://archive.ubuntu.com precise-updates/restricted amd64 Packages [12.2 kB]        
Get:17 http://archive.ubuntu.com precise-updates/universe amd64 Packages [237 kB]   
Get:18 http://security.ubuntu.com precise-security/main i386 Packages [396 kB]               
Get:19 http://archive.ubuntu.com precise-updates/main i386 Packages [781 kB]                 
Get:20 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]      
Get:21 http://security.ubuntu.com precise-security/universe i386 Packages [95.9 kB]     
Get:22 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]         
Get:23 http://security.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get:24 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:25 http://security.ubuntu.com precise-security/main Translation-en [172 kB]                 
Get:26 http://archive.ubuntu.com precise-updates/restricted i386 Packages [12.2 kB]               
Get:27 http://archive.ubuntu.com precise-updates/universe i386 Packages [242 kB]                    
Get:28 http://archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]             
Get:29 http://archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:30 http://archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Hit http://archive.ubuntu.com precise/main Translation-en                                    
Hit http://archive.ubuntu.com precise/restricted Translation-en                              
Hit http://archive.ubuntu.com precise/universe Translation-en                                
Hit http://security.ubuntu.com precise-security/restricted Translation-en                    
Hit http://security.ubuntu.com precise-security/universe Translation-en 
Hit http://archive.ubuntu.com precise-updates/main Translation-en       
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://archive.ubuntu.com precise-updates/universe Translation-en
Fetched 3,981 kB in 5s (694 kB/s)                 
Reading package lists... Done

~$ sudo apt-get dist-upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  udisks
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 250 kB of archives.
After this operation, 8,192 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://archive.ubuntu.com/ubuntu/ precise-updates/main udisks amd64 1.0.4-5ubuntu2.2 [250 kB]
Fetched 250 kB in 0s (319 kB/s) 
(Reading database ... 175019 files and directories currently installed.)
Preparing to replace udisks 1.0.4-5ubuntu2.1 (using .../udisks_1.0.4-5ubuntu2.2_amd64.deb) ...
Unpacking replacement udisks ...
Processing triggers for man-db ...
Setting up udisks (1.0.4-5ubuntu2.2) ...

~$ uname -mr

3.2.0-60-generic x86_64

~$ modinfo alx

ERROR: modinfo: could not find module alx

~$ dmesg | grep alx

~$ lshw -c network

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR9462 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan1
       version: 01
       serial: 6c:71:d9:7d:2c:d8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-60-generic firmware=N/A ip=192.168.1.5 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f7d00000-f7d7ffff memory:f7d80000-f7d8ffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8162 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f7c00000-f7c3ffff ioport:e000(size=128)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

~$ lshw -c network -short
WARNING: you should run this program as super-user.
H/W path       Device  Class          Description
=================================================
/0/100/1c.1/0  wlan1   network        AR9462 Wireless Network Adapter
/0/100/1c.3/0          network        AR8162 Fast Ethernet
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR9462 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan1
       version: 01
       serial: 6c:71:d9:7d:2c:d8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-60-generic firmware=N/A ip=192.168.1.5 latency=0 multicast=yes wireless=IEEE 802.11abgn


```

Enabled networking is checked.

Thoughts?

-g

---

### Post by varunendra on 2014-03-10
Had you manually compiled the Ethernet driver for your earlier kernel?

The required driver "alx" has been included in the kernel since version 3.8. The only situation I can think of when it "was working" earlier and post update it doesn't, is when you are still using a kernel version below 3.8 and manually compiled it for the previous kernel (which you must do again if using a kernel version < 3.8).

[s]Please show -
```
uname -mr
dpkg -l | grep linux-image*
locate alx.ko
```[/s]
EDIT: Nevermind, immediately realized that you had already posted relevant info. The above is not needed anymore.

My connection speed is practically unusable at the moment (awesome Vodafone GPRS, less than 1 KB/s average :| ). It took me 10 minutes to just refresh this page to be able to edit this post. I think I'll post tomorrow, hoping it will at least deliver a 1 KB/s consistently (which it is delivering a few hours a day, for last 12 days). If I could, I'd sentence Vodafone to death!

---

### Post by varunendra on 2014-03-10
Who knows if this vodafone service will ever get better, or will even stay alive tomorrow..

So.. while it is crawling and I am unable to sleep, here's a question for you, that may lead to a suggestion later -

Please post the outputs of -
```
apt-cache show linux-image-3.* | grep Package | sort -V
apt-cache show linux-generic-lts* | grep Package
```

This will show which latest kernel versions are available for you. I'm pretty sure you should have upto kernel 3.11 available, just want to confirm.

You seem to have three options -

[INDENT]**1)** Manually download and compile the alx driver, like you probably did earlier. This will ONLY install the driver, and won't touch the rest of the installation. The downside is that you'll have to do the same thing after Each kernel upgrade.

**2)** You may upgrade your kernel or the whole '[Hardware Enablement Stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")'. This will upgrade your whole system to the latest supported LTS packages. Possible risk is that some bugs may arise breaking some functionalities and this can not be reverted.

**3)** You may do a fresh installation of 12.04.4. This is probably the best and most troublefree option, if downloading a whole ISO and doing a fresh install (overwriting the current one) is not a problem for you.[/INDENT]

Please post back the outputs I asked, and let me know which option would you prefer *(I'll have to search the manual compilation instructions if you prefer option 1, so it'll be nice if you already have the link)*

---

### Post by spock3 on 2014-03-10
Thanks, Varun.

I included only the code snippet response from the 'locate alx.ko' command:

```


~$ locate alx.ko
/lib/modules/3.2.0-32-generic/updates/dkms/alx.ko
/var/lib/dkms/oem-combo-alx-ath9k-dkms/1/3.2.0-32-generic/x86_64/module/alx.ko


```

Let me know as soon as you get Vodafone resolved.

Thanks

---

### Post by spock3 on 2014-03-10
Hello again, Varun.

Also, please find the results of the output to the apt-cache code

```


~$ apt-cache show linux-image-3.* | grep Package | sort -V
Package: linux-image-3.2.0-23-generic
Package: linux-image-3.2.0-23-lowlatency
Package: linux-image-3.2.0-23-virtual
Package: linux-image-3.2.0-24-generic
Package: linux-image-3.2.0-24-generic
Package: linux-image-3.2.0-24-virtual
Package: linux-image-3.2.0-24-virtual
Package: linux-image-3.2.0-25-generic
Package: linux-image-3.2.0-25-virtual
Package: linux-image-3.2.0-26-generic
Package: linux-image-3.2.0-26-virtual
Package: linux-image-3.2.0-27-generic
Package: linux-image-3.2.0-27-virtual
Package: linux-image-3.2.0-29-generic
Package: linux-image-3.2.0-29-virtual
Package: linux-image-3.2.0-30-generic
Package: linux-image-3.2.0-30-virtual
Package: linux-image-3.2.0-31-generic
Package: linux-image-3.2.0-31-virtual
Package: linux-image-3.2.0-32-generic
Package: linux-image-3.2.0-32-virtual
Package: linux-image-3.2.0-33-generic
Package: linux-image-3.2.0-33-lowlatency
Package: linux-image-3.2.0-33-virtual
Package: linux-image-3.2.0-34-generic
Package: linux-image-3.2.0-34-virtual
Package: linux-image-3.2.0-35-generic
Package: linux-image-3.2.0-35-lowlatency
Package: linux-image-3.2.0-35-virtual
Package: linux-image-3.2.0-36-generic
Package: linux-image-3.2.0-36-lowlatency
Package: linux-image-3.2.0-36-virtual
Package: linux-image-3.2.0-37-generic
Package: linux-image-3.2.0-37-lowlatency
Package: linux-image-3.2.0-37-virtual
Package: linux-image-3.2.0-38-generic
Package: linux-image-3.2.0-38-lowlatency
Package: linux-image-3.2.0-38-virtual
Package: linux-image-3.2.0-39-generic
Package: linux-image-3.2.0-39-lowlatency
Package: linux-image-3.2.0-39-virtual
Package: linux-image-3.2.0-40-generic
Package: linux-image-3.2.0-40-lowlatency
Package: linux-image-3.2.0-40-virtual
Package: linux-image-3.2.0-41-generic
Package: linux-image-3.2.0-41-lowlatency
Package: linux-image-3.2.0-41-virtual
Package: linux-image-3.2.0-43-generic
Package: linux-image-3.2.0-43-virtual
Package: linux-image-3.2.0-44-generic
Package: linux-image-3.2.0-44-lowlatency
Package: linux-image-3.2.0-44-virtual
Package: linux-image-3.2.0-45-generic
Package: linux-image-3.2.0-45-virtual
Package: linux-image-3.2.0-48-generic
Package: linux-image-3.2.0-48-lowlatency
Package: linux-image-3.2.0-48-virtual
Package: linux-image-3.2.0-49-generic
Package: linux-image-3.2.0-49-lowlatency
Package: linux-image-3.2.0-49-virtual
Package: linux-image-3.2.0-51-generic
Package: linux-image-3.2.0-51-lowlatency
Package: linux-image-3.2.0-51-virtual
Package: linux-image-3.2.0-52-generic
Package: linux-image-3.2.0-52-lowlatency
Package: linux-image-3.2.0-52-virtual
Package: linux-image-3.2.0-53-generic
Package: linux-image-3.2.0-53-lowlatency
Package: linux-image-3.2.0-53-virtual
Package: linux-image-3.2.0-54-generic
Package: linux-image-3.2.0-54-lowlatency
Package: linux-image-3.2.0-54-virtual
Package: linux-image-3.2.0-55-generic
Package: linux-image-3.2.0-55-lowlatency
Package: linux-image-3.2.0-55-virtual
Package: linux-image-3.2.0-56-generic
Package: linux-image-3.2.0-56-lowlatency
Package: linux-image-3.2.0-56-virtual
Package: linux-image-3.2.0-57-generic
Package: linux-image-3.2.0-57-lowlatency
Package: linux-image-3.2.0-57-virtual
Package: linux-image-3.2.0-58-generic
Package: linux-image-3.2.0-58-lowlatency
Package: linux-image-3.2.0-58-virtual
Package: linux-image-3.2.0-59-generic
Package: linux-image-3.2.0-59-lowlatency
Package: linux-image-3.2.0-59-virtual
Package: linux-image-3.2.0-60-generic
Package: linux-image-3.2.0-60-lowlatency
Package: linux-image-3.2.0-60-virtual
Package: linux-image-3.5.0-18-generic
Package: linux-image-3.5.0-19-generic
Package: linux-image-3.5.0-21-generic
Package: linux-image-3.5.0-22-generic
Package: linux-image-3.5.0-23-generic
Package: linux-image-3.5.0-24-generic
Package: linux-image-3.5.0-25-generic
Package: linux-image-3.5.0-26-generic
Package: linux-image-3.5.0-27-generic
Package: linux-image-3.5.0-28-generic
Package: linux-image-3.5.0-30-generic
Package: linux-image-3.5.0-31-generic
Package: linux-image-3.5.0-32-generic
Package: linux-image-3.5.0-34-generic
Package: linux-image-3.5.0-36-generic
Package: linux-image-3.5.0-37-generic
Package: linux-image-3.5.0-39-generic
Package: linux-image-3.5.0-40-generic
Package: linux-image-3.5.0-41-generic
Package: linux-image-3.5.0-42-generic
Package: linux-image-3.5.0-43-generic
Package: linux-image-3.5.0-44-generic
Package: linux-image-3.5.0-45-generic
Package: linux-image-3.5.0-46-generic
Package: linux-image-3.5.0-47-generic
Package: linux-image-3.8.0-19-generic
Package: linux-image-3.8.0-21-generic
Package: linux-image-3.8.0-22-generic
Package: linux-image-3.8.0-23-generic
Package: linux-image-3.8.0-25-generic
Package: linux-image-3.8.0-26-generic
Package: linux-image-3.8.0-27-generic
Package: linux-image-3.8.0-29-generic
Package: linux-image-3.8.0-30-generic
Package: linux-image-3.8.0-31-generic
Package: linux-image-3.8.0-32-generic
Package: linux-image-3.8.0-33-generic
Package: linux-image-3.8.0-34-generic
Package: linux-image-3.8.0-35-generic
Package: linux-image-3.8.0-36-generic
Package: linux-image-3.8.0-37-generic
Package: linux-image-3.11.0-13-generic
Package: linux-image-3.11.0-14-generic
Package: linux-image-3.11.0-15-generic
Package: linux-image-3.11.0-17-generic
Package: linux-image-3.11.0-18-generic

~$ apt-cache show linux-generic-lts* | grep Package
Package: linux-generic-lts-quantal
Package: linux-generic-lts-quantal-eol-upgrade
Package: linux-generic-lts-raring
Package: linux-generic-lts-raring-eol-upgrade
Package: linux-generic-lts-saucy
Package: linux-generic-lts-saucy-eol-upgrade


```

---

### Post by spock3 on 2014-03-10
Varun,

On the 3 options to choose, being new to Linux Ubuntu, I'm leaning toward option #1 to start.
[I][B]
How often on avg does the kernel change?[/B][/I]

-g

---

### Post by Bashing-om on 2014-03-10
spock3; Hello,

As I pass by and lend a hand.
Your are booting;
> 
~$ uname -mr
3.2.0-60-generic x86_64

Instead of:
> 
Package: linux-image-3.11.0-18-generic
 as varunendra advises, with 3.8 kernel and above should have the internet driver pre loaded.

So the question now is why are you not booting that latest kernel ? I will consider how to verify that the Hardware Enablement Stack is active.

And I will
[INDENT][INDENT]pass your way again
[/INDENT][/INDENT]

---

### Post by spock3 on 2014-03-10
Is that a setting I can check for during the interim by rebooting & calling up the bios setting?

---

### Post by varunendra on 2014-03-10
> **spock3 said:**
> On the 3 options to choose, being new to Linux Ubuntu, I'm leaning toward option #1 to start.
[I][B]
How often on avg does the kernel change?[/B][/I]
It updates almost once a month I think.. Haven't updated for ages (still using 3.2.0-36.. ;)) so.... am I right Bashing-om? Or almost right?

To proceed with option #1, please follow the exact steps as in this post : [http://ubuntuforums.org/showthread.php?t=2199111&p=12898240#post12898240](http://ubuntuforums.org/showthread.php?t=2199111&p=12898240#post12898240)

Please also take a note of **Post #4** there to be able to recompile it whenever a kernel upgrade occurs.

**PS:**
@Bashing-om,
> **Bashing-om said:**
> 
Your are booting;
```
~$ uname -mr
3.2.0-60-generic x86_64
```
Instead of:
```
Package: linux-image-3.11.0-18-generic
```
....
So the question now is why are you not booting that latest kernel ?
You may already be aware of all of what I'm going to post, so the explanation below is for those who may not be aware of these facts and may wonder the same as quoted above-

The "apt-cache show" command shows all the versions that are "Available" for installation, not necessarily installed.
The installed (or installed --> removed) packages can be listed with "dpkg -l" command.

The "linux-image-3.11.0-18-generic" package listed in spock3's post is currently not installed (obviously), although we can do so if we wish. It is usually recommended to Upgrade the whole stack (kernel+xorg packages), but is not done automatically *(otherwise the system will break if, for example, the user upgrades to 12.10 later, while the HE stack is already upgraded to 13.04 or 13.10)*.

It is left to user's decision whether to upgrade the HE stack or not. Once the user is aware of the fact that they should NOT (and don't need to) upgrade their **OS Release** AFTER upgrading the HE stack to an even higher version, it is highly recommended to upgrade it _**IF**_ they need better hardware support.

However, I personally don't push it too much because a user may be happy with their current system performance, and we can't guaranty that it will improve or even stay the same with a whole new kernel and xorg packages. The new HE stack may come with its own bugs (which may not exist on the existing setup), and the transition may have some bugs as well.

So.. if the rest of the system is working well, and it is just one driver which we can get otherwise, I prefer to install/upgrade just that driver instead of upgrading the whole HE stack. And I believe spock3's decision to go with option #1 is based on the same reason - they're happy with the current setup and don't want to experiment with it. :)

---

### Post by Bashing-om on 2014-03-10
spock3; Hi !

EDIT: never to mind this posting, my ignorance was showing !

Booting the kernel is past the BIOS stage. It may, however, be of interest to know what kernels that grub does show.
Do you see kernel version 3.11.0-18-generic as an option in the grub boot menu ?
Boot ubuntu, soon as bios screen clears, depress and hold the right shift key -> grub boot menu
should appear.
If you do see that later image as an option, or maybe even in a sub menu ? what results when you select it to boot ?

[INDENT][INDENT]remains a mystery to me
[/INDENT][/INDENT]

Mystery explained " apt-cache show" ! for some reason stuck in my mind along the vein of what a "dpkg -l " would have shown. Excuse me please.
DOHH

---

### Post by spock3 on 2014-03-11
Thanks, concur on the option #1 selection logic: if it's not broken, no need to fix everything else.

Also, still ramping up on Linux & need to devote more time to the desired applications needing to be installed
& utilized:

MySql 5.1/5.5
Python 2.7
iPython

Does any of the HE stack NOT installed hold any remaining relevance to the proper performance
of those applications layered on top of the tech stack?

* Forgive me for a potential noob question, but this my 1st of several machines I intend to cycle away
from WinXP to Linux Ubuntu.

Thanks all.

---

### Post by spock3 on 2014-03-11
Thank you Varun/All.

Just successfully completed option #1 (driver rebuild) & now have regained wired connectivity.

Here's the code response:

```


Your backported driver modules should be installed now.
Reboot.

~/Desktop/backports-3.10-2$ sudo modprobe alx
~/Desktop/backports-3.10-2$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR9462 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan1
       version: 01
       serial: 6c:71:d9:7d:2c:d8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-60-generic firmware=N/A ip=192.168.1.5 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f7d00000-f7d7ffff memory:f7d80000-f7d8ffff
  *-network
       description: Ethernet interface
       product: AR8162 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 10
       serial: 74:d0:2b:4c:41:32
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full ip=192.168.1.2 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:f7c00000-f7c3ffff ioport:e000(size=128)
mojo@mojo-1015E:~/Desktop/backports-3.10-2$ 



```

This was a good learning exercise, thank you for all of your help?

Since the 199 make files were downloaded to the desktop, are they no longer needed
and can be now be safely deleted?

Please confirm.

Thanks,

Spock3
"Logic over Emotion"

---

### Post by varunendra on 2014-03-11
> **spock3 said:**
> Since the 199 make files were downloaded to the desktop, are they no longer needed
and can be now be safely deleted?
Deleting them is safe, but you don't want to do that. When a new kernel gets installed, and you need to execute the instructions in **post #4** of the same thread you have followed, you'll need these files again.

If the files are extracted within a folder on the desktop, keep this folder safe with the instructions to re-build the driver when needed.

If the files were extracted on the desktop itself, not within a folder, then it is better to keep the downloaded archive safe, and delete these files. Because there might be some hidden files created during the compilation, which may be needed for the instructions of post #4 to complete successfully. So unless you know how to view and copy the hidden files too, it is better to start fresh, from within a new, empty folder next time. :)
---------------------------------------

Regarding your question in your second last post above, I've no idea about any of those applications, but no application or package has ANY kind of dependency on the available higher HE stacks.

The HE stacks are completely optional and when (IF) you upgrade them, the packages that depend on its components get updated accordingly too (after running an update). If you don't upgrade the HE stack, your current setup will still be 'Complete' in itself, just no as updated as it '_Can be_'.

Please mark the thread as [SOLVED] using "Thread Tools" link above the top post. Feel free to ask if you have more questions, the 'Solved' prefix doesn't mean the topic or discussion is closed. :)
*(oh, but if the discussion is not related to the original topic, it should be continued in a new, relevant thread).*

---

### Post by spock3 on 2014-03-11
Ok, thanks. Much appreciated all the help on this guys. Between your help & what I'm learning about Ubuntu, I'm now an advocate convert.

* Kicking myself now, why I didn't migrate sooner from WinXP ;)

I'm now marking this thread as solved.

---

### Post by spock3 on 2014-03-11
Thanks, guys marking this one as solved since the driver rebuild fix provided by Varun worked perfectly.

---

### Post by Bashing-om on 2014-03-11
spock3; You do good work !

Welcome to our world.

[INDENT][INDENT]it is 'buntu
[INDENT][INDENT]all things are possible
[/INDENT][/INDENT][/INDENT][/INDENT]

---

