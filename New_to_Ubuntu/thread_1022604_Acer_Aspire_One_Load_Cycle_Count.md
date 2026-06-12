---
title: "Acer Aspire One Load_Cycle_Count"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by OutOfReach on 2008-12-27
Hello there, I am having trouble with the Acer Aspire One.

On AC the hdparm -B value 254 works fine. But on battery, the suggested 128 value does not work. I have tried everything from 128 to 240 but suspiciously, the value 254 works alright. But of course I cannot use the value 254 on battery.


I am using the Aspire One w/ 1gig of RAM and a 120 GB HDD (so not the SSD version).

Help is appreciated. :)

EDIT: Oh yeah of course, silly me, I am using Ubuntu Intrepid. Latest update. With added Netbook Remix packages (but I don't think that makes a difference).

---

### Post by Aearenda on 2008-12-27
You CAN use 254 on battery so long as you don't plan to drop the computer :-)

After all, what's to say you won't drop it when plugged in? E.g., when somebody catches their foot in the power cable...

I just don't see the logic in the commonly accepted theory that laptops only get dropped when running on battery!

---

### Post by OutOfReach on 2008-12-27
True a laptop can be dropped while plugged in, but it doesn't happen as often.

Anyways, I just thought that 254 would be too high a number offering close to no head parking etc.

---

### Post by Aearenda on 2008-12-27
254 should turn off the head parking altogether, so that it is definitely less safe if subjected to shock. However, it is unsafe whenever it is running, and if you are using the laptop, then it's probably running :-)

It's all a trade-off in exposure to danger versus extra drive wear.

---

### Post by OutOfReach on 2008-12-27
Well that is true, If I set it at any other value besides 254 the Load_Cycle_Count increases several times per minute and I worry about that since I (we) use this netbook on battery for quite a while.

---

### Post by OutOfReach on 2008-12-27
Bump.

---

### Post by Aearenda on 2008-12-27
Maybe you should replace the drive with a solid-state one!

By the way, I just tested my AA1 with hdparm -B 1 , 128, 253 and 254, and I too found the same behaviour for 1, 128 and 253 - it repeatedly unloads the heads and then reloads them. The Specs on the WD site give hints about 3 idle and low-power modes as well as standby and sleep, but no clues about the commands used to trigger them or how safe they are if dropped. 254 is the only setting that stops the load cycling.

---

### Post by OutOfReach on 2008-12-28
Aha, so I am not alone. Can you give me the link to that page? I would like to see what they say about it.

---

### Post by Aearenda on 2008-12-28
I think it was [http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=1410&p_created=1138291119&p_sid=AtU2gomj&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MSwxJnBfcHJvZHM9JnBfY2F0cz0mcF9wdj0mcF9jdj0mcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1XRDEyMDBCRVZTLTIyVVNUMA**&p_li=&p_topview=1](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=1410&p_created=1138291119&p_sid=AtU2gomj&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MSwxJnBfcHJvZHM9JnBfY2F0cz0mcF9wdj0mcF9jdj0mcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1XRDEyMDBCRVZTLTIyVVNUMA**&p_li=&p_topview=1)

Long URLs are hidden by the forum, click on it and it should work :-)

---

### Post by OutOfReach on 2008-12-30
Hmm, that's right it doesn't say any appropriate value. I'm suprised this hasn't been mentioned before...

---

### Post by teaker1s on 2008-12-30
please see here
[https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne"). 

I wrote the load_cycle_count info for the aspireone, set to 200 not 128 if you wish to discuss s120 would be interested in some testing.

---

### Post by Aearenda on 2008-12-30
teaker1s, did you work from any manufacturer's specs for the drive in choosing -B 200? I'd be happy to see what happens with -S 120 - it should just spin down after 2 minutes, assuming it is not used, but not park the heads if -B is 254 - I guess laptop-mode would be needed to make this possible - but my AA1 is on Hardy still, if that matters.

---

### Post by OutOfReach on 2008-12-30
Yep, that's the guide that I followed when installing Ubuntu on the AAO.
I am sure that I tried 200 -S 120, but let me re-check and I'll post back here.

---

### Post by teaker1s on 2008-12-31
When I first had the aspire one there was very little info about, found the info on the fedora aspire one wiki, as linpus is fedora based-I took that as my reference.

Basically we are trying to set the load_count so that it doesn't park the heads excessively or spin down excessively-while also watching hdd temperature.

I'm using laptop mode:-

We also would like to park the heads so in event of a knock the drive is protected-thats why batt mode is different.

Depending on your intended use you may also wish to protect the hard drive more when running in ac or on travel adapter.

 ie;-value 254 is never park heads so ideally the lowest value with out increasing hard drive count and heat is optimal

S120 as you say is spin down, If you wish to investigate a more optimal settings,then I'd be interested in your findings as currently my attempt was purely to stop hard drive failure.

Out of interest do you still have linpus lite? as mine went funny when I installed the full xfce4 desktop-indicating that it no longer called a script for drive settings.

your input is appreciated.

---

### Post by OutOfReach on 2009-01-01
I too have enabled laptop-mode, but I do not think that is helping much. But as I said I'll be experimenting even more with -B and -S values, I just don't know when since I am pretty busy.

My AAO did not come with Linpus, it came with Windows XP.

---

### Post by Aearenda on 2009-01-03
Mine was a Windows XP One as well - you couldn't get them with hard disks and Linpus here then, so I had to get XP as we needed the drive space. I don't know if it's any different now. It has a Western Digital WD1200BEVS-22UST0 drive.

I have my AA1 set to run in laptop-mode when on AC as well as when on battery. I allow data writes to be delayed up to 10 minutes whether on AC or not, but I haven't tweaked much else. It's still running Ubuntu 8.04 (Hardy).

If I set -B 200 -S 120, the load cycle count goes up by 2 or 3 every 5 minutes of otherwise idle time. There is always at least one load cycle per 5 minute interval, to run smartctl to get the stats, if that doesn't happen just after a 'normal' spinup. 

The drive spindown timer (-S 120) clearly has no effect on this, since 120 is the setting for 10 minutes and the timer never expires. 

It's just the same with -B253, -B128 and -B1. The temperature is around 35/36 degrees during these tests, which I ran until the temperature settled for at least 15 minutes. I conclude that the -B setting is an on/off setting on this drive - it either unloads the heads or it doesn't. Testing over short intervals suggests a -B1 timeout of about 8 seconds when it is enabled, regardless of the -B setting so long as it is less than 254. 

With -B254 -S120, the load cycle count does not increase at all, but the drive temperature increases to 40 degrees. I believe this is still perfectly safe, though more battery power will be used while idling, until the spindown timer expires - but in practice, more tuning would be required to get the spindown time to do anything useful on this system, since there is always some activity inside 5 minutes. In fact I have yet to notice the drive spinup from a -S setting, even -S 1!

The Hitachi drive in my main laptop also runs with -B254, and is at 38 degrees today, for comparison.

I have found several threads where Macbook users are complaining of the same issue, and saying that Apple say it is 'normal' to have a ticking drive. It appears there is a GUI setting in OS X which allows them to select more aggressive power saving. I have also found threads where Windows users have the same problem, though it seems to be less often - I suspect Windows either never leaves the drive alone, or manages to 'hold its breath' for a longer interval before writing to the drive once it is stopped. I have experienced drive ticking on XP laptops in the past, depending on the drive timeout settings in the power management control panel.

If a drive lifetime is rated at 600,000 load cycles (Some say 300,000, and those for desktop drives are an order of magnitude lower but they don't have this behaviour by default) then over (say) 5 years we can allow 120000 cycles per year, which is 328 cycles per day. If we leave the computer on for 14 hours a day, this is 23 cycles per hour, roughly one every two-and-a-half minutes. This is approximately the rate I am now seeing with my AA1 in laptop mode, though it must have been worse before, since it has recorded 5604 cycles for 8820 powered-on minutes.

It seems to me that protection against shock carries too great a cost in terms of drive mechanism ageing, *unless* we use laptop-mode to reduce the number of wake-ups caused by Linux or applications, and then monitor the outcome to make sure it is acceptable. 

In the end it is a trade-off between the likelihood of being dropped when parked, against the reduced lifetime of the drive. Since I have been lucky so far with my laptops, I tend to favour not parking the head (using -B 254), but I suspect solid state drives will very soon make this whole argument obsolete!

---

### Post by teaker1s on 2009-01-03
would be interested if the 120gb linpus has same make drive as 120gb and 160gb xp version.

---

### Post by Aearenda on 2009-01-08
> Out of interest do you still have linpus lite? as mine went funny when I installed the full xfce4 desktop-indicating that it no longer called a script for drive settings.

Just came across [this]("http://macles.blogspot.com/2008/12/acer-aspire-one-recovery-dvd.html"), if it is any help: you can download a Linpus recovery DVD.

---

### Post by teaker1s on 2009-01-09
linpus refused to load to flash card. also anyone notice touchpad on linpus crippled by delay. All of this has gone since ubuntu.
If you believe in conspiracy theory's, it almost as if acer sold as a toy  so as not to be in competition with premium umpc's

---

### Post by DavidOC on 2009-01-09
I've set laptop mode on and tried the ugly fix, but the load cycle count increases every minute or so.  Are there any other workarounds for this?

---

### Post by Aearenda on 2009-01-09
There's a patch in the works (see [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)) but it will only work if your drive obeys the standard power management commands.

---

### Post by SteveNorman on 2009-01-12
sorry to pop in late,,I am a little disturbed to see that I have no idea what anyone is talking about here. I have the acer 120 gHD, 1 gb mem with xp pre installed as well so am trying to keep up with this. A couple questions (sorry not trying to hijack this thread)

1. are you guys talking about HD spin rates?
2. should I be using the ubuntu netbook remix? I am just using the desktop  version which seems fine.

thanks

---

### Post by teaker1s on 2009-01-12
what we are talking about is head parking,
Hard disc is similar to a record player, ie instead of a record it has a platter and instead of a stylus it has a head. 

Now there are a rated number of cycles that the head is tested to

(imagine the stylus coming to the centre of the record and then parking)

now if it keeps doing this excessively then you will hear a kind of wooshing and clicking sound and your load cycle will be rapidly increasing and could reach maximum rated life cycles sooner than manufacturer intended. **This will cause premature failure**

---

### Post by Aearenda on 2009-01-13
There shouldn't be any difference between the Remix and standard Ubuntu in this area.

---

### Post by DavidOC on 2009-01-17
I've updated acpi support but it hasn't fixed the load cycle issue.  I've deleted the ugly fix scripts but that hasn't fixed it.  Would laptop mode cause this?

---

### Post by teaker1s on 2009-01-17
laptop mode changes between batt and ac power management settings, it's disabled by default due to some stability issues on some computers.
Ugly fix should work if applied correctly on the Al50
**note 08/07 manufacturing date A150 AB has 120gb drive A150 AB manufacturing date 08/09 has 160gb drive even wen sold as 120gb on box.**

I too am now having problems with two of the later A150 hard drives,Duel booting linpus and ibex it appears that linpus doesn't have an effective power management script either. All we can do is hope to slow the load cycle.
[https://bugs.launchpad.net/ubuntu/jaunty/+source/linux-meta/+bug/59695]("https://bugs.launchpad.net/ubuntu/jaunty/+source/linux-meta/+bug/59695")
Please read the test instructions

It appears that WD who make the drive offer no firmware update and bios update from acer does nothing. maybe linpus will send a script in auto update-but don't hold your breath.

---

### Post by teaker1s on 2009-01-22
BUMP Update spoken to acer technical and it appears that some 120gb models fitted with 160gb wd scorpio hdd below my email to acer technical who say if I explain the issue they will resolve it.
> 
Regarding our telephone conversation.
Hard drive premature failure due to excessive load cycle
 (parking heads excessively and reaching hard drive manufacturers rated limit prematurely)

With netbook we are looking to protect the hdd when on battery from knocks by parking heads, reducing power consumption-while keeping hdd temperature within manufacturers limits.

With netbook on ac we don't spin down the hdd or park as knocks are unlikely and we don't want park count going up.

Linpus linux is fedora werewolf 8 with acer customised xfce desktop.
On unaffected version 
		      MFG DATE:0807 AOA 150 AB
		      S/N: LUS050A10583012BB02500
		      SNIB: 83007672025
		      HDD MODEL NAME: ST9120817AS
		      HDD SERIAL: 5RE0CNEE    

It appears there is a script running to set hdd parameters, as changing to full xfce4 desktop causes load cycle problems as settings are no longer loaded.
On ubuntu we can set hard drive parameters with hdparm and the excessive load cycle is eliminated

using these values (fedora documentation aspireone)
#ac#
      /sbin/hdparm -B 254 /dev/sda
#batt#
      /sbin/hdparm -B 200 /dev/sda -S120

in the script suggested in post two of this thread

[http://ubuntuforums.org/showthread.php?t=805570&highlight=load+count+cycle](http://ubuntuforums.org/showthread.php?t=805570&highlight=load+count+cycle)

So to recap unmodified linpus on unaffected A150 is perfect and ubuntu on this version we can control hard drive power management perfectly and stop excessive load cycle.

I bought 2 more A150's the plan being to create a custom ubuntu install which all aspire one features work and clone it on to the second one. Both recent A150 the box says 120gb, but they are 160gb.
The duel boot linpus/ubuntu 
MFG 0809 AOA150 AB
S/N: LUS050A 105838 315 8D2535
HDD WDC WD1600BEVT-22ZCTQ
HDD SERIAL WD-WXC70863391

Excessive load cycle count affects completely factory standard linpus, when trying to control hdd in ubuntu it fails to respond to any power management setting below- don't ever park heads (254 which is not what we want on batt)

lastly fresh out the box factory standard linpus A150 SERIAL LUS050A15838146422535 exibits excessive load cycling.

Latest motherboard bios does not correct issue!!!

hdd spec
[http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=2670&p_created=1221495702&p_sid=iZbPKzoj&p_accessibility=0&p_redirect=&p_lva=1414&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MSwxJnBfcHJvZHM9MCZwX2NhdHM9MCZwX3B2PSZwX2N2PSZwX3NlYXJjaF90eXBlPWFuc3dlcnMuc2VhcmNoX25sJnBfcGFnZT0xJnBfc2VhcmNoX3RleHQ9V0QxNjAwQkVWVC0yMlpDVFE*&p_li=&p_topview=1](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=2670&p_created=1221495702&p_sid=iZbPKzoj&p_accessibility=0&p_redirect=&p_lva=1414&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MSwxJnBfcHJvZHM9MCZwX2NhdHM9MCZwX3B2PSZwX2N2PSZwX3NlYXJjaF90eXBlPWFuc3dlcnMuc2VhcmNoX25sJnBfcGFnZT0xJnBfc2VhcmNoX3RleHQ9V0QxNjAwQkVWVC0yMlpDVFE*&p_li=&p_topview=1)

WD are aware of scorpio drive click,there is an update, but not for this model
[http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=1414](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=1414)

could rps feature be causing this? spec sheet link
[http://www.wdc.com/en/library/portable/2579-001116.pdf](http://www.wdc.com/en/library/portable/2579-001116.pdf)

To rectify this I think you need Western Digital to provide updated hdd firmware which could be offered from your support site like bios update. After hdd firmware update, a linpus live update with power management script to control hdd firmware will cure problem.

My background is ubuntu hardware/unanswered posts and beginners support, therefore I would be happy to support ubuntu users with fix when avaliable.


Regards Daniel

Ps the 10inch aspireone looks superb, any ideas on price and release date!


---

### Post by Repgahroll on 2009-02-11
Hello there. :)

I have an Aspire One 160GB, and i'm using Linpus Lite because it's very very fast, Ubuntu boots in something like 1:30min and Linpus boot in 21sec. The boot time is very important to me because i use the netbook to write down thoughts.

But i notice that even the Linpus Lite which came with the netbook is killing the HD by default, i'm a debian/ubuntu user, and i would like to apply the workaround in the Linpus Lite, to set the Power Manager level to -B 254 -S 120 while on AC, and -B 200 while on battery.

But i have no idea on how to do that, i don't know if linpus has laptop mode, and sincerely don't know how to apply the workaround script on linpus.

I know it's very unusual, because this forum is for ubuntu specific help, but i don't know any other place where people would help me.

I'm currently running the commands manually.

Thanks in advance. Sorry my english.

---

