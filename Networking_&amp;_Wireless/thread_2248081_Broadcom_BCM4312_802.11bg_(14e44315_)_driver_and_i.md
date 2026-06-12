---
title: "Broadcom BCM4312 802.11b/g (14e4:4315 ) driver and issues"
date: 2014-10-12
forum: Networking &amp; Wireless
---

### Post by Gia90 on 2014-10-12
Hi guys,
After reading and trying every solution suggested on the web, I'm here to ask your help to enable this wireless card hopefully without issues.

My OS is BackBox 3.13, which shoud be based on Ubuntu 12.04, and no available driver seems to be working as expected.
Hope you can help me,
Thank you.

---

### Post by wildmanne39 on 2014-10-12
Hi, please click on the wireless script in my signature and follow the directions for running it and posting the reults here.
Thanks

---

### Post by Gia90 on 2014-10-12
> **Wild Man said:**
> Hi, please click on the wireless script in my signature and follow the directions for running it and posting the reults here.
Thanks

Here it is.
[ATTACH]257143[/ATTACH]

---

### Post by Hadaka on 2014-10-12
Hi, indeed you do have some issues, let's see if
we can get it running. Please open a terminal ctrl/alt/t
then please COPY and paste one line at  a time. This must
be done from a wired connection,connected to the internet.
please do, and ignore errors or file not found, do each line.
```
sudo apt-get update
sudo sed -i 's/^REG.*=$/&IT/' /etc/default/crda #set country code to europe/rome
sudo rm /etc/udev/rules.d/70-persistent-net.rules # names your eth0 and wlan0
sudo sed -i '/^blasklist b43/ d' /etc/modprobe.d/blacklist.conf #removes b43 from blacklist
boot
```
then let's clean up the wireless..again you must use a wired connection
please copy and paste and ignore errors ,,,
```
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -rf ssb
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer
sudo apt-get install firmware-b43-lpphy-installer
sudo modprobe -rf b43
sudo modprobe -v b43
```
next..please set your network mgr. IPv4 and IPv6 to look like the attached.
[ATTACH=CONFIG]257145[/ATTACH][ATTACH=CONFIG]257146[/ATTACH]
BOOT..disconnect the wired connection and test.

---

### Post by Gia90 on 2014-10-12
> **Hadaka said:**
> 
```
[...]
boot
```
It seems I don't have "boot" installed...
I ignored it and went on with the other commands.

I blacklisted the b43 adding a line in /etc/modprobe.d/blaclist.conf which your commands didn't remove, so I did it manually.
Then rebooted and it seems to be working.

I already tried installing "firmware-b43-lpphy-installer" and it was working till it randomly started to drop internet connection even if it kept connected to the AP with excellent signal.
To make it working again I could only put wlan0 down and then up again, wait some minutes or, eventually, reboot...
I hope your suggested config for ipv4 and ipv6 will help (even if I already tried them without success..).
Btw I will keep you updated on how it behaves.

Another question: Does b43 load the right firmware? I copy/paste from dmesg:
```
b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
``` 

There are newer ones which (I think) should be more advisable for my os version...

Thank you for your help!!

**UPDATE:**
The connection drop issue descriped above is still here...
Suddenly web pages stopped loading and it couldn't ping any host.After a while it started working again, at first slowly and then at normal speed.

---

### Post by Hadaka on 2014-10-12
BOOT means "restart" "ctrl/alt/del" "system restart"
please do a restart and then run and post wild Mans script
file again please.
thanks
Avviare il computer
riavviare il computer

---

### Post by Gia90 on 2014-10-12
I already did restart.
The updated wild Mans script results are attached.
Thank you.

---

### Post by jeremy31 on 2014-10-12
> **Gia90 said:**
> I already did restart.
The updated wild Mans script results are attached.
Thank you.

Did you run the command to purge bcmwl-kernel-source?  The wl module still shows in the report
This is the command from Hadaka's post ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get remove --purge bcmwl-kernel-source
```

[/FONT][/COLOR]Or did this command result in an error?

---

### Post by Gia90 on 2014-10-12
```
Package bcmwl-kernel-source is not installed, so not removed
```

I think wl is still there cause I previously compiled and installed BroadcomSTA from the vendor site..

---

### Post by jeremy31 on 2014-10-12
> **Gia90 said:**
> ```
Package bcmwl-kernel-source is not installed, so not removed
```

I think wl is still there cause I previously compiled and installed BroadcomSTA from the vendor site..

I will wait on someone else then as I have not dealt with this on 12.04, but my instinct would be to blacklist wl.

---

### Post by Hadaka on 2014-10-12
```
sudo rm /etc/modprobe.d/blacklist-bcm43.conf

sudo modprobe -rf ssb
sudo apt-get remove --purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer
sudo apt-get remove --purge firmware-b43-lpphy-installer
sudo apt-get install firmware-b43-lpphy-installer
sudo modprobe -rf b43
sudo modprobe -v b43
```
PLEASE do these again, one at a time...from a working wired connection

---

### Post by Gia90 on 2014-10-13
The wireless started working as soon as I modprobed b43.
Then restarted.
It seemed to be working but the connection drop issue started again after opening some web browser tabs.
Webpages stop loading and then time out.
Ping does not respond and eventually times out.
So the issue which has plagued me since Ubuntu 11.04 is still here :(

---

### Post by jeremy31 on 2014-10-13
Might as well run the script again```
./wireless_script
```

---

### Post by Gia90 on 2014-10-13
> **jeremy31 said:**
> Might as well run the script again```
./wireless_script
```

Rerun the script and attached results.

---

### Post by Hadaka on 2014-10-13
hI this shows
##### lsmod #############################

b43                   397389  0 
mac80211              623710  1 b43
bcma                   47094  1 b43
wl**[COLOR=#ff0000]<-[/COLOR]**                   6363768  0 
cfg80211              499466  3 b43,mac80211,wl**[COLOR=#ff0000]<-[/COLOR]**
hp_wmi                 18202  0 
sparse_keymap          13890  1 hp_wmi
ssb                    62919  1 b43
wmi                    19256  1 hp_wmi

that you STILL have wl ...aka broadcom-kernel-source loading in your modules
are you being asked to load a proprietary driver..additional drivers..if so...say NO
that is the wl driver and is incorrect.
Please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -rf wl
```
your router is set to TKIP this also will cause slow downs and drops
please change it to WPA2
Also your network mgr settings are at auto
please set them like the attached
[ATTACH=CONFIG]257182[/ATTACH][ATTACH=CONFIG]257183[/ATTACH]
please make these changes and re run and post the script file
thanks.

---

### Post by Gia90 on 2014-10-13
> **Hadaka said:**
> hI this shows
##### lsmod #############################

b43                   397389  0 
mac80211              623710  1 b43
bcma                   47094  1 b43
wl**[COLOR=#ff0000]<-[/COLOR]**                   6363768  0 
cfg80211              499466  3 b43,mac80211,wl**[COLOR=#ff0000]<-[/COLOR]**
hp_wmi                 18202  0 
sparse_keymap          13890  1 hp_wmi
ssb                    62919  1 b43
wmi                    19256  1 hp_wmi

that you STILL have wl
I'm aware I still have wl loaded, but I don' think that these commands
> **Hadaka said:**
> ```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -rf wl
```
will help me getting rid of it.
**bcmwl-kernel-source is NOT installed** since it was already purged.
I already tried to explain that it is still there because** I compiled and installed BroadcomSTA** from sources downloaded from Brodcom site ([http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)) so it is not related to bcmwl-kernel-source.
So any other advice? Maybe blacklist it?

Thank you.

---

### Post by Hadaka on 2014-10-13
try this before blacklisting
```
sudo apt-get remove --purge broadcom-sta-common broadcom-sta-source
```
are you also doing the other commands, and cleaning up other areas?
```
echo 'blacklist wl' | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by Gia90 on 2014-10-13
> **Hadaka said:**
> ```
sudo apt-get remove --purge broadcom-sta-common broadcom-sta-source
```

```
Package broadcom-sta-common is not installed, so not removed
Package broadcom-sta-source is not installed, so not removed
``` 

I've done all the commands you told me to and I would like to clean other areas related to wl, but I need help with this.
I could even reinstall the OS, if it could help.
I just want to figure out how to make this wireless card work just as good as it did with older ubuntu versions and kernels..

And again, thank you for your precious help.

---

### Post by kc1di on 2014-10-13
All seems strange to me since I have the same card and wl driver works fine with it. 
never had a problem using either sta or wl  ;)

---

### Post by Gia90 on 2014-10-13
> **kc1di said:**
> All seems strange to me since I have the same card and wl driver works fine with it. 
never had a problem using either sta or wl  ;)
Well I never really liked propertary drivers, I always preferred and used the open ones.
I've always used b43 (which also supported monitoring and injection) till Ubuntu 11.04 came up.
From then issues started and, even if I tried anything I could try, I ended up downgrading to Ubuntu 10.04 which worked just fine.
But it's not supported anymore and I'm not willing to keep compiling every single package I need, so I'd like to update it and use any kind of driver which let me use wireless connections flawlessly..
Btw It seems you are on 14.04, so I suppose our experiences are not comparable.

---

### Post by Hadaka on 2014-10-13
Hi, I'm not sure if the different load...os
"My OS is BackBox 3.13" is causing some of the issue,but it very well could be,
i do know that you currently have b43 and wl in you lsmod report, while wl doesnt
seem to be loading, that combo does cause problems. Try reloading the os BlackBox 
and then see if you can get a driver working. Perhaps dave kc1di may be of more help
than i, as he currently has that card. I also just now see and apologize for not looking
that this BlackBox is defined as 
*BackBox* Linux is an Ubuntu-based distribution developed to perform penetration tests .
This forum offers ZERO support for penetration testing.
good luck

---

### Post by Gia90 on 2014-10-14
> **Hadaka said:**
> 
i do know that you currently have b43 and wl in you lsmod report, while wl doesnt
seem to be loading, that combo does cause problems.

I can guarantee that the cause of my connection issues is not related to this wrong driver combo. As already explained, I never managed to make b43 working after updating to UBUNTU 11.04, which led to me to downgrade.

> **Hadaka said:**
> 
This forum offers ZERO support for penetration testing.
good luck
I'll install Ubuntu just to confirm this is not a BackBox issue and then come back here and report.
Do you have some advice on which version of Ubuntu is more suited for my wireless card? 12.04 or 14.04?
Thanks.

---

### Post by kc1di on 2014-10-14
Either one 12.04 or 14.04 worked for me, simply use the addtional driver tool found in Sofware Center>Edit>Software Sources> Additional Driver tab.
Good Luck

---

### Post by westie457 on 2014-10-14
This post has the up to date list of b43 chips and the correct drivers to be used. [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by Gia90 on 2014-10-14
> **kc1di said:**
> Either one 12.04 or 14.04 worked for me, simply use the addtional driver tool found in Sofware Center>Edit>Software Sources> Additional Driver tab.
Good Luck
 It is what I did initially and it just caused a kernel panic (and it's not just me, just an example: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1134389](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1134389)).
I even had to disable the automatic propetary package download while installing the os to avoid the kernel panic.

> **westie457 said:**
> This post has the up to date list of b43 chips and the correct drivers to be used. [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
I did read that post before asking on the forum, but unfortunately it didn't help..

I'd like to say what I've tried untill now and what worked/didn't, just for completeness:

[LIST]
[*]**firmware-b43-lpphy-installer**:  it seemd to work but it intermittently and randomly drops the internet connection and it makes it unusable. No problems with AP scanning.
[*]**bcmwl-kernel-source**:  it produced kernel panic so discareded it.
[*]**BroadcomSTA ***(compiled from src)*: it worked but couldn't detect all the networks, including my own AP.
[/LIST]

**These trials are the same I unsuccessfully did long time ago**, when issue started. The last Ubuntu version which let me use b43 without issues was 10.04 with kernel version <2.6.35, which I've been using till last day.
I recently decided to update my os and retry to make bcm4312 work, hoping in newer and better kernels and drivers and, of course, you great help.
You already know the rest of the story.

The next step for me is to install Ubuntu, and not a derived distribution (BackBox in my case), to keep receiving your essential help.

---

### Post by kc1di on 2014-10-14
I Did have a kernel panic when you the 3.10 kernel.  But that cleared with the install of 3.13 .xx kernel.  So it's most likely kernel related. 

which kernel are you using now?  ```
uname -r 
```

---

### Post by Gia90 on 2014-10-14
> **kc1di said:**
> which kernel are you using now?  ```
uname -r 
```
3.11.0-26

---

### Post by kc1di on 2014-10-14
Try giving 3.13 a try think that will stop the kernel panics .

---

### Post by Gia90 on 2014-10-18
> **kc1di said:**
> Try giving 3.13 a try think that will stop the kernel panics .

I'm on Ubuntu 14 and indeed had no kernel panic installing bcmwl-kernel-source from "additional software" window.

But issues are still there, since it does not detect all the wireless networks (including my own AP) I can find using other devices.

Then tried installing "firmware-b43-installer", which let me connect to my AP but it dropped connection as I already described..

Now I'll keep testing and then post the wireless script results.

**UPDATE**
I've fresh installed Ubuntu 14 and didn't install any driver for my wireless card. The wireless script results are attached.

---

### Post by Gia90 on 2014-10-19
**UPDATE2**
I've been retrying all the solutions previously suggested for BackBox on Ubuntu 14 and none of them worked (connection drops/slowness with b43 and network scanning issues with wl).
Before throwing my PC out of the window, I decided to also try the last advisable solution: ndiswrapper.
It seems to be the less unstable solution so far..

---

### Post by Gia90 on 2014-10-21
I don't know why this thread was **WRONGLY **moved to "*Any Other OS"* section, since I'm now using **Ubuntu 14.04**.

Apart from this, there's nothing more I can try? no more help? 
[B]Broadcom related issues (and in particular with bcm4312 lp-phy) are still widely experienced on Ubuntu and it seems there's no more interest in fixing those faulty drivers.
It's really diappointing.

[/B]If anyone is having the same problems as me, here is how correctly configure ***ndiswrapper ***to make the wireless connection work:
[http://ubuntuforums.org/showthread.php?t=1410259](http://ubuntuforums.org/showthread.php?t=1410259)

---

### Post by slickymaster on 2014-10-21
> **Gia90 said:**
> I don't know why this thread was **WRONGLY **moved to "*Any Other OS"* section, since I'm now using **Ubuntu 14.04**.<---snip--->

All fixed. I moved it to the proper sub-forum now -> **Networking & Wireless**.

---

