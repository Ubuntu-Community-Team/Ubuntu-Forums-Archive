---
title: "[SOLVED] Stupid wireless Q of the day..."
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by bobmct on 2008-10-08
OK - its great that an open Broadcomm driver is now available.  As my laptop has a 4311 in it I quickly downloaded and installed this new driver per the instructions with it.

But - as I am not a kernel technical wizard it appears that either it doesn't work or I must have built and installed it wrong (twice).  If I do a lsmod I see two B43 mods listed.  Not the new one that is supposed to be there (by using insmod wl.ko).  Unless, of course, the new one also uses the B43 name.

If it is there then when I use network manager to configure it I only see WEP as the security option.

Soooo, anyone who has any savvy with this new module, please advise because I'm sure I'm not the only one who has been waiting and is having difficulty with this installation.  It would be nice to be able to run Kubuntu on my laptop finally without the inconsistent ndiswrapper that I could NEVER get to run.

Any knowledge/advice/suggestions appreciated by me and others.

Thanks -Bob :(

---

### Post by Ayuthia on 2008-10-09
> **bobmct said:**
> OK - its great that an open Broadcomm driver is now available.  As my laptop has a 4311 in it I quickly downloaded and installed this new driver per the instructions with it.

But - as I am not a kernel technical wizard it appears that either it doesn't work or I must have built and installed it wrong (twice).  If I do a lsmod I see two B43 mods listed.  Not the new one that is supposed to be there (by using insmod wl.ko).  Unless, of course, the new one also uses the B43 name.

If it is there then when I use network manager to configure it I only see WEP as the security option.

Soooo, anyone who has any savvy with this new module, please advise because I'm sure I'm not the only one who has been waiting and is having difficulty with this installation.  It would be nice to be able to run Kubuntu on my laptop finally without the inconsistent ndiswrapper that I could NEVER get to run.

Any knowledge/advice/suggestions appreciated by me and others.

Thanks -Bob :(

Try the following:
```
sudo modprobe -r b43 ssb ndiswrapper bcm43xx wl
sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko
```
This will only work for the session.  You might have to wait a few seconds for network manager to catch up.

---

### Post by bobmct on 2008-10-09
:D THANK YOU!!!

Believe it or not, this is the FIRST TIME I've been able to get the wireless working under linux on this laptop in over a YEAR!!!

Now - seeing that you stated this is for the session only, how does one make it permanent???

Thanks - Bob

---

### Post by Ayuthia on 2008-10-09
The first thing that you will need to do is move the wl.ko file over to a place in /lib/modules:
```

echo blacklist b43|sudo tee -a /etc/modprobe.d/blacklist
echo blacklist ssb|sudo tee -a /etc/modprobe.d/blacklist
sudo update-initramfs -u
sudo mkdir /lib/modules/`uname -r`/wl_hybrid
sudo cp wl.ko /lib/modules/`uname -r`/wl_hybrid
sudo depmod -a
echo wl | sudo tee -a /etc/modules

```
Hopefully that should do it.

---

### Post by tamalatamala on 2008-10-09
I have a similar question about my wireless.

I have a Broadcom 4322 for which I dowloaded the driver at [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
and followed the instructions in
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)
(using sudo in front of every command, not to mention that I lost a lot of time not noticing that I wrote 'pwd' instead of `pwd`)
Anyway, I managed to get the wireless working using KNetworkManager. Then I rebooted and it fails to work.
If I do the following two steps:

sudo modprobe ieee80211_crypt_tkip
sodo insmod <path>/wl.ko

it works again util the next reboot. I tried improvising and did the last three lines of your last post but it didn't help. I am pretty unexperineced in linux so I would appreciate the help.

---

### Post by Ayuthia on 2008-10-09
> **tamalatamala said:**
> I have a similar question about my wireless.

I have a Broadcom 4322 for which I dowloaded the driver at [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
and followed the instructions in
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)
(using sudo in front of every command, not to mention that I lost a lot of time not noticing that I wrote 'pwd' instead of `pwd`)
Anyway, I managed to get the wireless working using KNetworkManager. Then I rebooted and it fails to work.
If I do the following two steps:

sudo modprobe ieee80211_crypt_tkip
sodo insmod <path>/wl.ko

it works again util the next reboot. I tried improvising and did the last three lines of your last post but it didn't help. I am pretty unexperineced in linux so I would appreciate the help.

If those are the only commands that you need to do, you just need to do the following:
```
sudo mkdir /lib/modules/`uname -r`/wl_hybrid
sudo cp <path>/wl.ko /lib/modules/`uname -r`/wl_hybrid
sudo depmod -a
echo wl | sudo tee -a /etc/modules
```
That hopefully will do it for you.  What this does is move the wl module over to where the system can find it.  Then the depmod will go through the /lib/modules/ directory and build all the dependencies for it.  The final part will have the system load the wl module when the system boots up.

Hopefully that will help.

---

### Post by bobmct on 2008-10-09
Ayutha;

You've been a great help on this.  But could you please tell us how/where the module loader knows where to look for the wl.ko module?  I still cannot get mine to start automatically but if done manually, it starts.  Therefore there must be a misdefinition someone.

Awaiting your answer!  Thanks

---

### Post by tamalatamala on 2008-10-09
echo wl | sudo tee -a /etc/modules

says

tee: etc/modules: No such file or directory

:(

---

### Post by bobmct on 2008-10-09
tamalatamala;

I think my last question will solve this issue for BOTH of us and anyone else that reads this post.  Now - we just wait for the answer...

Bob

---

### Post by Ayuthia on 2008-10-09
> **bobmct said:**
> Ayutha;

You've been a great help on this.  But could you please tell us how/where the module loader knows where to look for the wl.ko module?  I still cannot get mine to start automatically but if done manually, it starts.  Therefore there must be a misdefinition someone.

Awaiting your answer!  Thanks

When you use:
```
sudo modprobe <module>
```
the system will look through /lib/modules/`uname -r`/ directory for the .ko module.

Are you saying that you are able to use sudo modprobe wl to get it to load now or are you still using the insmod version?

Can you do the following:
```
sudo updatedb
locate wl.ko
```
This will update the search database and then look for all the places where wl.ko can be found.

---

### Post by Ayuthia on 2008-10-09
> **tamalatamala said:**
> echo wl | sudo tee -a /etc/modules

says

tee: etc/modules: No such file or directory

:(
Can you do me a favor and show the results of:
```
ls /etc/modules
```
/etc/modules is a file that is used to store modules to load when the system boots up.  They are typically modules that are not built in the kernel.

EDIT:By the way, did you have the first / in /etc/modules?  Your error message shows that it did not.

---

### Post by bobmct on 2008-10-09
Ayuthia;

I just redid the steps.  After a reboot I needed to manually run the insmod command to get it working.  The wl line is definitely at the end of the /etc/modules file and I currently have created three directories in the /lib/modules/..../ tree.  They are wl, wl_hybrid and hybrid_wl because I cannot tell which is being used.  I have wl.ko in each of them.

Hope you have another trick to get this module automatically loaded properly.

Bob

---

### Post by bobmct on 2008-10-09
More Info - booted and wireless is still not available.  However, if I run lsmod I wee that "wl" and "i33380211_crypt" are moth listed and associated.

Now I'm stumped!!!

---

### Post by Ayuthia on 2008-10-09
> **bobmct said:**
> More Info - booted and wireless is still not available.  However, if I run lsmod I wee that "wl" and "i33380211_crypt" are moth listed and associated.

Now I'm stumped!!!

Ok.  You should take two of them out of the /lib/modules directory.  You only need one out there.

As for the wl and ieee80211_crypt being in lsmod, my guess is that you have other wireless modules out there that are still causing conflicts.  Please post the folowing:
```
lsmod | grep -e b43 -e ssb -e ndiswrapper -e wl -e bcm43xx
sudo updatedb
locate wl.ko
```
This will list out all the possible modules out there and let us see where the wl.ko files are located.

After you post that information, you can try the following to get the wireless back:
```
sudo modprobe -r b43 ssb ndiswrapper bcm43xx wl
sudo modprobe wl
```

If that does not work, try:
```
sudo modprobe -r b43 ssb ndiswrapper bcm43xx wl
sudo modprobe ieee80211_crypt_tkip
sudo <path>/insmod wl.ko
```Just replace <path> with the actual wl.ko file that you compiled the first time (exclude the <> also).

---

### Post by bobmct on 2008-10-09
OK - here the output:

for the lsmod command the ONLY two modules that appeared were wl and ieee80211_crypt which is what is should be, right?

As for where the wl.ko files are:
/home/<mydir>/hybrid_wl/wl.ko    (this is where I "made" it.
/lib/modules/2.6.24-19.generic/wl/wl.ko
/lib/modules/2.6.24-19.generic/hybrid_wl/wl.ko
/lib/modules/2.6.24-19.generic/wl_hybrid/wl.ko

And, that's it!  So, which one is it using and/or is the loader searching ALL the subdirectories in the /lib/modules/<version>/ tree?

I am going to try and eliminate the two directories with the "hybrid" in their name and leave the "wl" one to see if that works.

Thanks - we'll get there and others will follow this (or perhaps we'll post a sticky topic.
Bob

---

### Post by Ayuthia on 2008-10-09
> **bobmct said:**
> OK - here the output:

for the lsmod command the ONLY two modules that appeared were wl and ieee80211_crypt which is what is should be, right?

As for where the wl.ko files are:
/home/<mydir>/hybrid_wl/wl.ko    (this is where I "made" it.
/lib/modules/2.6.24-19.generic/wl/wl.ko
/lib/modules/2.6.24-19.generic/hybrid_wl/wl.ko
/lib/modules/2.6.24-19.generic/wl_hybrid/wl.ko

And, that's it!  So, which one is it using and/or is the loader searching ALL the subdirectories in the /lib/modules/<version>/ tree?

I am going to try and eliminate the two directories with the "hybrid" in their name and leave the "wl" one to see if that works.

Thanks - we'll get there and others will follow this (or perhaps we'll post a sticky topic.
Bob

It will be searching all the subdirectories in the /lib/modules/<version>/ tree.  I am not for sure what happens when there are duplicates and that might be where the problem is.

---

### Post by bobmct on 2008-10-09
OK - here's what I see so far (and thanks for ALL your help so far!!!)

I've eliminated the redundant directories of different names.  That way there is only ONE directory in the /lib/modules path containing the wl.ko module.

However, following a boot if I do a lsmod I see the wl module AND the ieee80211_crypt module but the rightmost column on the ieee80211 line only shows "wl".  If I then rmmod wl and insmod for the same followed by the lsmod again, I see the two BUT the ieee80211_crypt now shows in its rightmost column "ieee80211_crypt_tkip,wl".

So, that MUST be a key as to what might NOT be happening.  There IS a difference in the loading somehow, someway.  If you or anyone has any other idea, please advise.  I too will continue my quest to locate this.

Thanks - Bob

---

### Post by Ayuthia on 2008-10-09
> **bobmct said:**
> OK - here's what I see so far (and thanks for ALL your help so far!!!)

I've eliminated the redundant directories of different names.  That way there is only ONE directory in the /lib/modules path containing the wl.ko module.

However, following a boot if I do a lsmod I see the wl module AND the ieee80211_crypt module but the rightmost column on the ieee80211 line only shows "wl".  If I then rmmod wl and insmod for the same followed by the lsmod again, I see the two BUT the ieee80211_crypt now shows in its rightmost column "ieee80211_crypt_tkip,wl".

So, that MUST be a key as to what might NOT be happening.  There IS a difference in the loading somehow, someway.  If you or anyone has any other idea, please advise.  I too will continue my quest to locate this.

Thanks - Bob

Can you post the results of:
```
modprobe --show-depends wl
```
This will tell us what wl is trying to load when the wl module is getting loaded.

---

### Post by tamalatamala on 2008-10-09
You were right, I forgot / before etc/modules.

Besides this I also have some problems with graphics, every second time I reboot I run into trouble and need to reload ati driver to get things working the next time. So everything takes a lot of time...

So, I tried what you proposed and now I cant get wireless working at all. Not even if I try to redo the steps that used to work.

locate wl.ko gives

/lib/modules/2.6.24-19-generic/wl_hybrid/.wl.ko.cmd
/lib/modules/2.6.24-19-generic/wl_hybrid/wl.ko

modprobe --show-depends wl
gives:
insmod /lib/modules/2.6.24-19-generic/kernel/net/ieee80211/ieee80211_crypt.ko
insmod /lib/modules/2.6.24-19-generic/volatile/wl.ko

Also,
lsmod | grep -e wl -e ssb -e ndiswrapper -e b43 -e bcm43xx
says:
wl                   1062164  0
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,wl

---

### Post by Ayuthia on 2008-10-09
> **tamalatamala said:**
> You were right, I forgot / before etc/modules.

Besides this I also have some problems with graphics, every second time I reboot I run into trouble and need to reload ati driver to get things working the next time. So everything takes a lot of time...

So, I tried what you proposed and now I cant get wireless working at all. Not even if I try to redo the steps that used to work.

locate wl.ko gives

/lib/modules/2.6.24-19-generic/wl_hybrid/.wl.ko.cmd
/lib/modules/2.6.24-19-generic/wl_hybrid/wl.ko

modprobe --show-depends wl
gives:
insmod /lib/modules/2.6.24-19-generic/kernel/net/ieee80211/ieee80211_crypt.ko
insmod /lib/modules/2.6.24-19-generic/volatile/wl.ko

Also,
lsmod | grep -e wl -e ssb -e ndiswrapper -e b43 -e bcm43xx
says:
wl                   1062164  0
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,wl

Can you try the following:
```
sudo ifconfig eth1 down
sudo iwconfig eth1 mode Managed
sudo ifconfig eth1 up
sudo iwlist scan
```
The modules loaded look correct so I am curious why it is not working.

EDIT: I forgot to post why I ask for this information.  The wl module tends to go to ad-hoc mode when it starts out.  The commands I am asking will change it back to Managed mode and then scan for wireless sites.  I want to see if you can see any sites or not.

---

### Post by bobmct on 2008-10-09
:guitar:
OK guys - GOT IT!

Following all the steps above I needed to manually run the "modprobe ieee80211_crypt_tkip" command immediately prior to the "insmod wl" command.
Then followed it with the command "depmod -a" and finally edited /etc/modules to be sure that ieee80211_cript-tkip and wl were BOTH entered.

A reboot then STARTED MY WIRELESS - HOORAY!!!

Thanks to those who helps.

Bob

---

### Post by tamalatamala on 2008-10-10
Well, I thought a night would clear things out, but...

lsmod | grep -e wl -e ssb -e b43
says:
wl                   1062164  0
ieee80211_crypt         7040  1 wl

sudo ifconfig eth1 down
says:
eth1: ERROR while getting interface flags: No such device

It just doesnt work... :( But at least my graphics does. :)

---

### Post by tamalatamala on 2008-10-10
Ok, I am back to start. I decided to have a fresh start so I reinstalled the system. Now I'm trying to follow something that worked for most users.

[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

I am a total newbie on Kubuntu (I know a bit more about SUSE which I used) so I have a couple of questions regarding the procedure.

I have a broadcom 4322 adapter, Kubuntu 8.04 KDE4 Remix (HP compaq 6735b, AMD Turion)

It sais:

1) Deactivate any ndiswrapper installed drivers. There should be a remove option for ndiswrapper.

Should I use Adept to do this? If I open Adept and type ndiswrapper, I get three things, all not installed.

2) Activate Hardy proposed.
Select System->Administration->Software sources. Check the box for proposed updates. Hit close and let it refresh.

How do I select System? Where is that? I can only find System Settings, there is Computer Administration but no Software sources.
Or, I have Applications -> System and no Administration.


3) Open up Synaptic. Search for the package entitled "linux" and mark it for update. This should also automatically mark linux-image-2.6.24-21-generic, linux-ubuntu-modules-2.6.24-21, and linux-restricted-modules-2.6.24.

Should I use Adept instead of Synaptic?

4) Search for the package entitled "jockey" and mark it for update. Perform the updates.

5) Reboot your machine

6) Click System->Administration->Hardware Drivers

I have Applications -> System -> Hardware Drivers Manager which so far has only one device listed (ATI).

7) Click the "Broadcom STA wireless driver" in the Hardware Drivers tool.


I would really appreciate the help to get things started.

---

### Post by bobmct on 2008-10-10
:guitar:
Thanks Ayuthia for your help and suggestions.

There was ONE step that was not on the installation list that made the difference between correct and not correct prior to running depmod.  That was the command "modprobe ieee80211-crypt_tkip" after which I entered the command "insmod wl" and the wireless came up.
Now running depmod resulted in a correct <path>/modules.dep which resulted in an autostarting wireless network upon boot.

Hooray - Thanks again!  Bob

---

### Post by tamalatamala on 2008-10-10
I also managed to get things working. I was very close to switching to SUSE linux and decided to give it another try ;)
Thank you for your help.

---

