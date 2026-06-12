---
title: "Ubuntu 14.04 and Intel 7265 - connected to working wifi but &quot;network is unreachable&quot;"
date: 2015-05-13
forum: Networking &amp; Wireless
---

### Post by beth3 on 2015-05-13
Hi, I'm new to Linux/Ubuntu so please forgive me if I ask any stupid questions.

I'm running ubuntu 14.04 and my computer keeps cycling through connecting and disconnecting to the wifi- but even when it's "connected", the internet still doesn't work. I have tried sending pings via the terminal but it comes back with "Network is unreachable". The wifi network definitely works as I'm currently connected on my phone. My laptop was also able to successfully connect to wifi a couple of days ago so I'm not sure why it's stopped working now. 

I'm unable to run wireless info as I have no wired connection and no second computer with which to transfer the files. 

If anyone is able to offer any suggestions, I'd be supremely grateful. 

Thanks :)

---

### Post by Hadaka on 2015-05-13
Hi, please post the  output of..
```
lspci -n | awk '/0280/{print $3}'
```
this will tell us the type of wireless card you have.
thanks

---

### Post by beth3 on 2015-05-14
> **Hadaka said:**
> Hi, please post the  output of..
```
lspci -n | awk '/0280/{print $3}'
```
this will tell us the type of wireless card you have.
thanks

It says 8086:095a

---

### Post by coffeecat on 2015-05-14
> **beth3 said:**
> It says 8086:095a

Google hits suggest that this is an Intel 7265. Just so that we can be sure, please post the output of this command:

```
lspci -nnk | grep -iA2 net
```

Assuming that it is an Intel 7265, I found this thread:

[http://ubuntuforums.org/showthread.php?t=2261834&highlight=intel+7265](http://ubuntuforums.org/showthread.php?t=2261834&highlight=intel+7265)

Forum member chili555 can be relied on for wireless problems. But the fixes he recommends would be daunting for a newcomer to Ubuntu, so I have another suggestion which may or may not help. I am posting from Ubuntu on a machine with the (probably) slightly older Intel 7260 wireless device. When I ran 14.04 from a live session on it, the wireless was unreliable, similar to what you are experiencing. I didn't bother to install 14.04. When 14.10 was released I found that wireless was satisfactory, as it is with the Ubuntu 15.04 I am posting from.

I suggest you download the 15.04 ISO and boot up to a live session with either a DVD or USB. Try the wireless. If it works OK consider replacing your 14.04 with 15.04. But be aware that 15.04 has only 9 months support. It is not a long-term support version like 14.04.

You can get the 15.04 ISO here:

[http://releases.ubuntu.com/vivid/](http://releases.ubuntu.com/vivid/)

---

### Post by beth3 on 2015-05-14
> **coffeecat said:**
> Google hits suggest that this is an Intel 7265. Just so that we can be sure, please post the output of this command:

```
lspci -nnk | grep -iA2 net
```

Assuming that it is an Intel 7265, I found this thread:

[http://ubuntuforums.org/showthread.php?t=2261834&highlight=intel+7265](http://ubuntuforums.org/showthread.php?t=2261834&highlight=intel+7265)

Forum member chili555 can be relied on for wireless problems. But the fixes he recommends would be daunting for a newcomer to Ubuntu, so I have another suggestion which may or may not help. I am posting from Ubuntu on a machine with the (probably) slightly older Intel 7260 wireless device. When I ran 14.04 from a live session on it, the wireless was unreliable, similar to what you are experiencing. I didn't bother to install 14.04. When 14.10 was released I found that wireless was satisfactory, as it is with the Ubuntu 15.04 I am posting from.

I suggest you download the 15.04 ISO and boot up to a live session with either a DVD or USB. Try the wireless. If it works OK consider replacing your 14.04 with 15.04. But be aware that 15.04 has only 9 months support. It is not a long-term support version like 14.04.

You can get the 15.04 ISO here:

[http://releases.ubuntu.com/vivid/](http://releases.ubuntu.com/vivid/)

Yeah, it says intel 7265
Kernel driver in use- iwlwifi

Thank you for your help- I will have a go with 15.04 when I can and report back :)

---

### Post by coffeecat on 2015-05-14
I noticed from the thread I linked that chili555 is "anxious to learn its peculiarities" - its meaning Intel 7265 - so I've amended your thread title in case he wishes to get involved. 

Good luck either way. :)

---

### Post by Hadaka on 2015-05-14
1+ good advice on the os or getting the good doctor involved
thanks coffeecat.More than likely this is a kernel version issue
and will require internet access to fix. mean time please do..
```
sudo touch /etc/modprobe.d/iwlwifi.conf
echo options iwlwifi 11n_disable=1 | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
thanks.

---

### Post by beth3 on 2015-05-17
> **Hadaka said:**
> 1+ good advice on the os or getting the good doctor involved
thanks coffeecat.More than likely this is a kernel version issue
and will require internet access to fix. mean time please do..
```
sudo touch /etc/modprobe.d/iwlwifi.conf
echo options iwlwifi 11n_disable=1 | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
thanks.

It came back with
```
options iwlwifi 11n_disable=1
```

I've finally got my hands on another laptop so am going to load up 15.04- if that did fix the problem and I ended up installing it properly, am I likely to run into more difficult problems further down the line because there's less support available?

---

### Post by Hadaka on 2015-05-17
Hi, 15.04 doesnt have less support available, its just a short term os
and ends in 7 months. 1404 has several years left with full support and
ongoing security updates. Since your card is new, I would be more apt
to load ubuntu 14.04 LTS. the link for getting the wireless to work that
coffeecat posted should not be a problem for you at all and chili555 i am
sure he would be more than happy to assist you.
let us know what you decide. and you really should be doing this from
a wired connection,its pretty much the only way to get it to work.
thanks.

---

### Post by chili555 on 2015-05-17
Subscribed. I look forward to your report:> I've finally got my hands on another laptop so am going to load up 15.04- if that did fix the problem and I ended up installing it properly, If your issue is not solved, I look forward to working with you.

---

### Post by beth3 on 2015-05-20
> **chili555 said:**
> Subscribed. I look forward to your report:If your issue is not solved, I look forward to working with you.

15.04 still didn't work; 14.04 mysteriously seems to be working ok now, I'm not sure if that's it somehow fixed or it's just going through a good patch

---

### Post by Hadaka on 2015-05-20
Great ! in my opinion,14.04LTS was a better choice anyway.
if you are satisfied with your results, please sign back in and 
and mark your thread SOLVED by clicking "thread tools" -
enjoy !!

---

### Post by beth3 on 2015-05-20
Looks like I spoke too soon, it's gone again :(

---

### Post by Hadaka on 2015-05-20
Hi, ok...well..you are going to need a working wired connection to get this going.
once you get the wired connection, follow the directions on **post #6  **here
[http://ubuntuforums.org/showthread.php?t=2261834&highlight=intel+7265](http://ubuntuforums.org/showthread.php?t=2261834&highlight=intel+7265)
if you have any problems post back and chili555,myself or some one will talk you through it.
Let us know once you get that wired connection.
thanks.

---

### Post by beth3 on 2015-06-13
> **chili555 said:**
> Subscribed. I look forward to your report:If your issue is not solved, I look forward to working with you.

Hi again :)

So I'm on a wired connection. Managed the first step of post #6 here ([http://ubuntuforums.org/showthread.php?t=2261834&highlight=intel+7265](http://ubuntuforums.org/showthread.php?t=2261834&highlight=intel+7265)) but I'm stuck on the second one.

Initially the command given didn't match up with what I downloaded ([COLOR=#000000][FONT=Ubuntu Mono]cd ~/Downloads/iwlwifi-7265-ucode-23.11.10.0 given but there's nothing with that name under 7265, so I downloaded 23.25.10 which is hopefully right?) and that now seems fine, however I'm getting the error [/FONT][/COLOR]mv: cannot stat ‘iwlwifi*’: No such file or directory

---

### Post by chili555 on 2015-06-13
> I'm getting the error mv: cannot stat ‘iwlwifi*’: No such file or directoryAfter which step, exactly? And what kernel version are you running?```
uname -r
```And what does this tell us the needed firmware is?```
modinfo iwlwifi | grep 7265
```I suspect it is indeed -10.

---

### Post by beth3 on 2015-06-13
> **chili555 said:**
> After which step, exactly? And what kernel version are you running?```
uname -r
```And what does this tell us the needed firmware is?```
modinfo iwlwifi | grep 7265
```I suspect it is indeed -10.

After this step- [COLOR=#000000][FONT=Ubuntu Mono]sudo mv iwlwifi*  /lib/firmware

[/FONT][/COLOR]3.16.0-40-generic

 iwlwifi-7265-9.ucode

---

### Post by chili555 on 2015-06-13
Let's see, first, if the driver you compiled is the one that's loaded:```
modinfo iwlwifi | grep version
```It ought to say something like:```
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
```If not, reboot and try again. If still no luck, we need to re-compile backports.> iwlwifi-7265-9.ucodeIf it wants -9, you will certainly need -9 in addition to -10: [https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-25.228.9.0.tgz](https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-25.228.9.0.tgz) 

Download that file to your desktop. Right-click it and select 'Extract Here.' Now, back to the terminal:```
cd ~/Desktopiwlwifi-7265-ucode-25.228.9.0/
sudo cp iwlwifi*  /lib/firmware
```Please tell me if you get an error.

If this doesn't help, we'll start a new fix from scratch.

---

### Post by beth3 on 2015-06-13
> **chili555 said:**
> Let's see, first, if the driver you compiled is the one that's loaded:```
modinfo iwlwifi | grep version
```It ought to say something like:```
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
```If not, reboot and try again. If still no luck, we need to re-compile backports.

It says

```
version:        in-tree:srcversion:     93D664267873827B22C4309
vermagic:       3.16.0-40-generic SMP mod_unload modversions 



```
> **chili555 said:**
> 
If it wants -9, you will certainly need -9 in addition to -10: [https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-25.228.9.0.tgz](https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-25.228.9.0.tgz) 

Download that file to your desktop. Right-click it and select 'Extract Here.' Now, back to the terminal:```
cd ~/Desktopiwlwifi-7265-ucode-25.228.9.0/
sudo cp iwlwifi*  /lib/firmware
```Please tell me if you get an error.

If this doesn't help, we'll start a new fix from scratch.

It keeps saying no such file or directory but I'm not sure why- the file is there under that name

[ATTACH=CONFIG]262581[/ATTACH]

Thank you for all your help :)

---

### Post by chili555 on 2015-06-13
Let's check a little closer:```
cd ~/Desktop/iwlwifi-7265-ucode-25.228.9.0/
```And check the contents:```
ls
```Do you see the files as I have?```
iwlwifi-7265-9.ucode  LICENSE.iwlwifi-7265-ucode  README.iwlwifi-7265-ucode
```If so, transfer the firmware part only:```
sudp cp iwlwifi* /lib/firmware 
```EDIT: I see I made a typo; I'm sorry. My post mistakenly says:> cd ~/Desktopiwlwifi-7265-ucode-25.228.9.0/...but it is supposed to be:> cd ~/Desktop[COLOR="#FF0000"]**/**[/COLOR]iwlwifi-7265-ucode-25.228.9.0/> vermagic:       3.[COLOR="#FF0000"]16.[/COLOR]0-40-generic SMP mod_unload modversionsThat's not the compiled version, but let's see how far we get before we get out the power tools and start anew.

---

### Post by beth3 on 2015-06-13
> **chili555 said:**
> Let's check a little closer:```
cd ~/Desktop/iwlwifi-7265-ucode-25.228.9.0/
```And check the contents:```
ls
```Do you see the files as I have?```
iwlwifi-7265-9.ucode  LICENSE.iwlwifi-7265-ucode  README.iwlwifi-7265-ucode
```If so, transfer the firmware part only:```
sudp cp iwlwifi* /lib/firmware 
```EDIT: I see I made a typo; I'm sorry. My post mistakenly says:...but it is supposed to be:That's not the compiled version, but let's see how far we get before we get out the power tools and start anew.

Yes, I see the same files as yours. Now when I enter

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo cp iwlwifi*  /lib/firmware
```

Nothing seems to happen, it doesn't ask for my password it just repeats 

```
[/FONT][/COLOR]~/Desktop/iwlwifi-7265-ucode-25.228.9.0$
```

If I enter it in a new terminal, it says

```
 cp: cannot stat ‘iwlwifi*’: No such file or directory
```

---

### Post by beth3 on 2015-06-13
> **chili555 said:**
> Let's check a little closer:```
cd ~/Desktop/iwlwifi-7265-ucode-25.228.9.0/
```And check the contents:```
ls
```Do you see the files as I have?```
iwlwifi-7265-9.ucode  LICENSE.iwlwifi-7265-ucode  README.iwlwifi-7265-ucode
```If so, transfer the firmware part only:```
sudp cp iwlwifi* /lib/firmware 
```EDIT: I see I made a typo; I'm sorry. My post mistakenly says:...but it is supposed to be:That's not the compiled version, but let's see how far we get before we get out the power tools and start anew.

Yes, I see the same files as yours. Now when I enter

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo cp iwlwifi*  /lib/firmware[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

Nothing seems to happen, it doesn't ask for my password it just repeats

[/FONT][/COLOR]```
~/Desktop/iwlwifi-7265-ucode-25.228.9.0$
```

If I enter it in a new terminal, it says

```
 cp: cannot stat ‘iwlwifi*’: No such file or directory
```

---

### Post by chili555 on 2015-06-13
> Now when I enter

Code:
sudo cp iwlwifi*  /lib/firmware


Nothing seems to happen, it doesn't ask for my password it just repeatsPerfect. Now check to see if the file is present where we need it:```
ls /lib/firmware | grep 7265
```On my machine, it says:```
iwlwifi-7265-10.ucode
iwlwifi-7265-12.ucode
iwlwifi-7265-8.ucode
iwlwifi-7265-9.ucode
iwlwifi-7265D-10.ucode
iwlwifi-7265D-12.ucode

```Reboot and tell me if the performance is improved.

---

### Post by beth3 on 2015-06-13
> **chili555 said:**
> Perfect. Now check to see if the file is present where we need it:```
ls /lib/firmware | grep 7265
```On my machine, it says:```
iwlwifi-7265-10.ucode
iwlwifi-7265-12.ucode
iwlwifi-7265-8.ucode
iwlwifi-7265-9.ucode
iwlwifi-7265D-10.ucode
iwlwifi-7265D-12.ucode

```Reboot and tell me if the performance is improved.

Mine says the same but I've rebooted and the performance is still patchy.

---

