---
title: "ndiswrapper problems in Edgy beta"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by funkadelic on 2006-10-17
I had my Netgear WG111T working fine in Dapper, but I can't get it working in Edgy beta...

**ndiswrapper -l output:**
```
athfmwdl        driver present, hardware present 
netwg11t        driver present 
```


**modprobe ndiswrapper output:**
```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
```

Any idea what is wrong here?

---

### Post by peebly on 2006-10-17
having the same problem.

worked with dapper, is it going to work with edgy.

if not its back to windows i am afraid.

---

### Post by funkadelic on 2006-10-17
No suggestions at all??

I know this is beta software -- should I report this as a bug?

**peebly** are you getting the exact same errors? Please tell me if you learn anyhing...

---

### Post by peebly on 2006-10-17
Hello

I have since got mine to work.](*,) 

What I did was go into Synaptic Package Manager, go to search and type ndis.

Arrow key down and make sure the following 4 packagers are installed.

NdisWrapper-common 1.18

NdisWrapper-utils 1.1-5

NdisWrapper-utils-1.1  1.15

NdisWrapper-utils-1.8

One of the above was not installed on my computer, Sorry but I forgot which one.:-k 


I did this then reinstalled the two inf files and then restarted the computer and it worked.

---

### Post by funkadelic on 2006-10-17
Still no luck!


I have even tried compiling ndiswrapper myself... I don't understand - this was so easy in Dapper!

---

### Post by peebly on 2006-10-17
Hi

Yes I agree, I also had no problem what so ever in dapper, It worked first time every time.

My new problem is, every time I switch of the computer the wireless card does not start on the first boot, I have to restart the computer at login to get it to work.

I think I will go back to dapper.

---

### Post by funkadelic on 2006-10-23
I started over from scratch with a clean install of RC1 -- I followed these instructions EXACTLY:
[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)

...and I get the exact same error.


I have also tried installing the very newest version of ndiswrapper from source. More info here:
[http://www.ubuntuforums.org/showthread.php?t=279469&highlight=WG111T](http://www.ubuntuforums.org/showthread.php?t=279469&highlight=WG111T)

Sorry for the multiple threads, I wasn't sure where to post this, or if I was giving enough info.

Thanks.

---

### Post by atrus123 on 2006-10-26
> **peebly said:**
> Hello

I have since got mine to work.](*,) 

What I did was go into Synaptic Package Manager, go to search and type ndis.

Arrow key down and make sure the following 4 packagers are installed.

NdisWrapper-common 1.18

NdisWrapper-utils 1.1-5

NdisWrapper-utils-1.1  1.15

NdisWrapper-utils-1.8

One of the above was not installed on my computer, Sorry but I forgot which one.:-k 


I did this then reinstalled the two inf files and then restarted the computer and it worked.

Just for the record, this worked for us.

---

### Post by TrendyDark on 2006-10-27
When I tried Ndiswrapper in Edgy beta, I didn't get it to work. Apparently it's not edgy, but the new kernel?

---

### Post by detour on 2006-10-27
> **atrus123 said:**
> Just for the record, this worked for us.

Worked for me too. For anyone else in the same boat as me: if you can't get internet without wireless, the packages can be downloaded and installed manually from here: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ndiswrapper&searchon=names&subword=1&version=edgy&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ndiswrapper&searchon=names&subword=1&version=edgy&release=all")

---

### Post by javaJake on 2006-10-27
Guys, make sure gcc is at version 4.0 (you should find that a /usr/bin/gcc symlink pointing to gcc-4.1). That's why I got this error...

---

### Post by Neobuntu on 2006-10-27
Darn, darn, darn, darn DARN! (to put it nicely)

I can't BELIEVE I'm having to do this!

Thank you for the tips though. I was going to download the whole Alternate CD (not too fast right now).

I have these on flash (If you guys don't have a flash stick spend $10 and get you one) and I'm off to REPAIR my Edgy upgrade.

My thinking was, I have waited patiently for the release (no beta) and I'll try upgrading (Kubuntu) to Edgy and get the CD later. I guess I should have done a clean install but I thought that thrill was a Windows requirement.

If you can't guess. A RELEASE SHOULD UPGRADE (online) OR NOT BE A RELEASED YET! 

I consider myself a major Kubuntu fan so sorry if the truth hurts. I respect everything going good with edgy but upgrading is JOB ONE! Just call it a pre-release otherwise. Please.

---

### Post by nbound on 2006-10-27
Theres no such thing as an upgrade disk... if you want to upgrade you do it online through your current operating system. The disks are only for clean installs

---

### Post by Neobuntu on 2006-10-27
First, I am trying to upgrade online and that flatly did not work (update: Now Edgy is working and hopefully newbie friendly very soon.); Leaving me with no ndis wireless net and yes, it's not easy to get a cat5 to THIS box.

Second, according to Ubuntu forum posts, the Alternate CD indeed can upgrade an old release and do it off-line (if I had one). [B]UPDATE: I downloaded and tried this (on my notebook) and it left me in the cold not knowing if I should let it continue; THREE times! That's a day I'll NEVER get back. So I'd say forget "saving bandwidth" and trying to UPGRADE from working Dapper and using the "Kubuntu 6.10 Alternate" CD; off line. This (md5 checked OK) iso MIGHT be bad, as several burns would never self validate (from their boot menu.)
[/B]
The above ndis files REQUIRE COMPILING which requires stuff I don't have ON-LINE access to. Accept via XP :P

Didn't ANYONE think of this?

(Me thinks if the upgrade went smoothly ndis would work. So we a need smoother dist-upgrade within the next few hours for the newbie.)

---

### Post by Neobuntu on 2006-10-27
Alright, I'm up in Edgy and on line but only after opening a major can of uber-geek woop arse on this box and that's just sad for the newbies.

I grabbed an old XP laptop, wireless NIC PCcard and Wired NIC PCcard and ran through XP net wizard to set up ICS (and had to update windows XP SEVERAL TIMES) so with the addition of a crossover cable, I have temporay WIRED internet into the wired LAN port of this remote computer; since wireless is down until on line upgraded. (That's a wireless client bridge, kids. A "gaming adapter" would do/are the same thing.)

It turns out, many Edgy upgrades were still needed and I'm still sorting it all out. NDIS was one of the upgrades.

Dear newbie, DO NOT UPGRADE TODAY. (October 27 2006)

Things I THINK I need to do next.

o Set up ndiswrapper. (Check. It is working.)

o Install a K7 Kernel and set ndiswrapper again. (Nope. It looks like "generic" kernel replaces the K7 kernel. Is this better?)

o See what's good and what's broke. (Edgy Firefox 2.0, that's what. I am ironically using Firefox-for-Windows via WINE...and Linux Ice Weasel...and Swiftfox...and the 2.0 till it crashes again. I had used Win Firefox for Flash 9 sites and because super easy and fast Windows Firefox instructions were found for Dapper. Automatix made WINE install easy. So all was EASY.) I hope Kubuntu Firefox 2.0 will be fixed very soon. Rumor has it, 2.0 crashes loading certain site elements.

[B]Update: I've since fixed Firefox 2.0 by adding the line suggested in the forums to stop it from crashing. I also had to run a command to reinstall Nvidia correctly, also found in the forums (perhaps that added the right lines in "xorg.conf". I'm not sure but 3D works again. I had to reinstall kxmame for some reason but it works too.

Now I'm struggling with my notebook computer.[/B]

---

### Post by mjritchie on 2006-10-28
I've got the ndiswrapper 1.8 packages installed, and the kernel module loads cleanly, ndiswrapper -l indicates the drivers are installed AND it can find my hardware, but still no wlan device is created.  

Is this related to problems other people are having with Edgy, or is it something different?


$ dmesg|grep ndiswrapper
[17179602.776000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)

$ ndiswrapper -l
Installed drivers:
mrv8ka51                driver installed, hardware present

---

### Post by Neobuntu on 2006-10-28
Whew, see added notes above.

After selecting your XP driver with ndiswrapper (try installing ndisgtk for easy menu access) and then remember to:
```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
sudo /etc/init.d networking restart
```
and in Kubuntu
> System Settings > Network Settings > (Scroll down and Click) Administrator Mode > (Click the wireless interface and) Configure Interface > (When done) Enable Interface (It will remind you to save/apply your changes).

...worked for me.

---

### Post by Tux Aubrey on 2006-10-29
> **Originally Posted by atrus123**:
Just for the record, this worked for us.

me too - for a Netgear W511v2 (PCMCIA).  

NdisWrapper-utils-1.8 does not get picked up by Synaptic with the common files or the gui utility.  Just select it manually.  I had uninstalled my previous ndiswrapper before reinstalling the complete set and it works with the "generic" kernel.

---

### Post by mjritchie on 2006-10-29
I am already using ndiswrapper 1.18, but since everyone else seems to be working with that, I suspect my problem is a more general ndiswrapper/udev issue rather than an Edgy problem so I've posted on the ndiswrapper list.

Thanks.

---

### Post by maksym on 2006-10-30
> **peebly said:**
> having the same problem.

worked with dapper, is it going to work with edgy.

if not its back to windows i am afraid.

i have the same prob as well. as I am a linux newbe it makes the life even more difficult....:-k

---

