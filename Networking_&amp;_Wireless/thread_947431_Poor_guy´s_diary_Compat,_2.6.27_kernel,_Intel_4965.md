---
title: "Poor guy´s diary: Compat, 2.6.27 kernel, Intel 4965 card = iwl4965 module not found."
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by simak on 2008-10-14
Hi all,

from my point of view, posting topics on forums is the last resort for fixing issues, and I always try to avoid it, but I just couldn´t this time.

I have not found anyone with a problem identical to mine.

after hours of searching, trying different combinations and the last thing before reverting to old kernel I am asking for help!

the storry goes, I installed normal default Ubuntu with the kernel 2.6.24, and made most of the things work, except my intergrate camera ( which is supposed to work out of the box ). It was very sketchy and my skype bugged a lot as well, and since I really need skype + webcam to work out of the box

I installed the new kernel via Kernelcheck ( found it on these forums ) and rebooted my computer.

After that, my wireless card dissapeared. **iwconfig** doesn´t show it, **ifconfig** doesn´t show it. 
**dmesg** sees it.

**lshw -C network** shows that it IS there but not configured;
decription: Network controller
product: PRO/Network 4965 AG or AGN Network Connection
physical id: 0
bus info: pci@0000:0b:00.0
version: 61
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0

.

I downloaded Compat-wireless, and installed, and after loading the modules something strange occures in the list.
It lists the loading of all the modules BUT the iwl4965. It does not copy/install it in the /lib...../update/drivers/net/wireless/. there is only iwl3945.ko, in the iwlwifi subfolder.
I find this strange really strange. And I **DID FIND** the iwl4965 modules files in the tar file I downloaded.

So basically when I run the sudo make load, i get a list of ALL drivers loaded and than when it comes to iwl4965.
it says..

Loading.. iwl4965.
FATAL MOdule iwl4965 not found.

I was thinking of copyin the iwl4965 module manually to the directory but i couldnt find the file iwl4965.ko

I need help :lolflag:

all the best =)

p.s. sorry for not copying pasting stuff, i had to write everything by hand because I posted from friends laptop.

---

### Post by sherlock12 on 2008-10-14
[align=left][align=left][font=Tahoma][size=36pt][**[size=12pt][color=#0000ff]Warhammer gold[/color][/size]**](http://www.mmogarden.com/war-all/cheap-gold-5-all.html)[/size][/font][font=Tahoma][size=12pt], as the currency in the Warhammer world, plays an important role in the economic system. The experience plays take in game kinda depends on how much **Warhammer gold **they have.  To amateur players, they do not have much time to play the game, not even farming [/size][/font][font=Tahoma][size=36pt][**[size=12pt][color=#0000ff]Warhammer online gold[/color][/size]**](http://www.mmogarden.com/)[/size][/font][font=Tahoma][size=12pt]. So most of Warhammer players would like to purchase *Warhammer gold*.[color=#282827] [/color][/size][/font][font=Tahoma][size=9pt][/size][/font][/align][/align][align=left][align=left][font=Tahoma][size=12pt][[color=#282827]Warhammer online CD-key[/color]](http://www.3zoom.com/uswarhammer-all/warhammer-cdkey-5-all.html) [/size][/font][font=Tahoma][size=12pt]are the codes which be used to active your Warhammer Accounts. [/size][/font][font=Tahoma][size=36pt][[size=12pt][color=#0000ff]Warhammer online Timecard [/color][/size]](http://www.mmogarden.com/war-all/cheap-cdkey-5-all.html)[/size][/font][font=Tahoma][size=12pt]then will be needed after your **Warhammer Accounts **have been activated. That means you have to use both **Warhammer CD-key **and **Warhammer Timecard **after you creat an **Warhammer account**, so that you can access to the **Warhammer** world.Buy **Warhammer CD-key **and** Warhammer Timecard **from us, experience our Instant delivery and Secure transaction.For further information about the **Warhammer CD-key **and **Warhammer Timecard**, Please keep an eye on [color=blue][[color=#282827]warhammer powerleveling[/color]](http://www.mmogarden.com/war-all/cheap-powerleveling-5-all.html)[/color][/size][/font][font=Tahoma][size=36pt][/size][/font][/align][/align]

---

### Post by Alacrity on 2008-10-21
In another post at another web site I see this:

do

Code:
sudo rmmod iwlagn
sudo rmmod iwlcore
sudo rmmod mac80211
sudo rmmod cfg80211
sudo make load

and it works..XD

for your solution...

Let me know if it works...I want to try the same thing.

A

---

