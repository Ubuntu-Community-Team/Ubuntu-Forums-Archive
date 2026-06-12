---
title: "HP NX6125 Wireless Issues with 8.04"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by JootFish on 2009-01-17
Hi All,
I'm pretty much a virgin to Ubuntu, and quite inexperienced with Linux in general... 

I'm trying to get the wireless running on my laptop on a fresh install of Heron 8.04 (from CD), and am having issues.

I've searched on the web and found several references, but nothing I can follow. Unfortunately I pretty much need suggestions to work perfectly line for line as I don't have enough knowledge of nix to sort anything out myself.

So far I've seen:
1) [http://ubuntuforums.org/showthread.php?t=734003](http://ubuntuforums.org/showthread.php?t=734003) but I don't know reference the 'Gutsy method' mentions in the post, and am uncomfortable going with something I search with as it may be different. I tried it anyway, but it obviously requires it.

2) I've also seen several references to setting up b43-fwcutter, but I can't seem to install it. I get the following error:
sudo apt-get install b43-fwcutter

3) [http://www.fourlovesfour.blogspot.com/2008/05/setting-up-broadcom-b43-wireless-with.html](http://www.fourlovesfour.blogspot.com/2008/05/setting-up-broadcom-b43-wireless-with.html)
When I paste make, It gives a screen full of errors, with this at the end:
make: *** [fwcutter.o] Error 1

I get pretty much the same error when I try to run:
sudo apt-get install build-essential

Not knowing whether that mattered, I tried the rest of the commands anyway, but recieved 'Command not found' for sudo b43-fwcutter so obviously they do!

Incidentally, the keyboard light and associated dedicated button for the wireless can be switched on/off from the get go. I not sure how to confirm what type of chipset or wireless I have in Linux, though I know from Windows it is a Broadcom, and lspci reports the following which I fantasize is useful:
02:02.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)

Thanks for reading, and for your help :)

Regards,
Jason

---

### Post by mikewhatever on 2009-01-17
Any chance you can reinstall and use Intrepit Ibex (8.10) instead of 8.04? There should be a driver included and your card might just work.
sudo apt-get install b43-fwcutter is not an error, but you need to be online for it to work. I also suspect that package is already installed.

---

### Post by minsf on 2009-01-17
jootfish, do you have ethernet connection? that is, do you have internet with the CAT 5 cable? if you do, first thing i want you to try is (while the ethernet cable is connected!):
go to the System menu above, choose Administration and then Hardware, wait a few seconds for it to run, and check the Broadcom B43 wireless driver box, (it should download or install it. you may need to check "enable" bottun). then reboot. let us know how it went and we can help you more.

---

### Post by JootFish on 2009-01-17
Hi Guys, 

Thanks for your quick replies!! Yes, I have been connected via Ethernet (new to Ubuntu and Linux I am, new to networking I am not (CCISP/Firewall Spec)), however the Broadcom does not show... In the bootable CD it does though!
Anyway, I'm downloading 8.10 now, though it looks like I may run out of time before I'm throttled which may mean another day. If there are any other options, I'd love to know :)

Thanks & Cheers!

---

### Post by minsf on 2009-01-17
do you use WEP?

---

### Post by minsf on 2009-01-17
what error do you get when you try "sudo apt-get install b43-fwcutter" from the terminal? (you forgot to cut and paste the error in (2) in post #1)

---

### Post by minsf on 2009-01-17
also try this
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

---

### Post by JootFish on 2009-01-17
Whoops :D

sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package b43-fwcutter

Giving the wireles kernel link you've recommended a go now!

---

### Post by minsf on 2009-01-17
> **JootFish said:**
> 
Giving the wireles kernel link you've recommended a go now!

wait wait i got a better idea i'll write it in a minute

---

### Post by minsf on 2009-01-17
i think the reason why the hardware-detection doesnt work, and why you cannot install with apt-get is that not all the repositories are enabled!

let's try this: go to System>Administration>SoftwareResources and make sure that the first 4 boxes are checked! (that is, main, universe, restriced and multiverse)

if i'm guessing right, one of them is not enabled (probably restricetd box), and that's the problem! if i'm right, then after checking this box go to hardware-detection again, and hopefully you'll have the broadcom driver there. or you can also try the "sudo apt-get b43-fwcutter" method. now that the box is checked, it should install

---

### Post by JootFish on 2009-01-17
When I try running:
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
I get command not found.
Can someone please refresh me on how to do a 'Dir /s /p' equivalent; And also whatever gets commands readable page by page eg: ls b43-fwcutter (toggles for directory/file??) | grep something?

Thankyou!!

---

### Post by minsf on 2009-01-17
> **JootFish said:**
> When I try running:
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
I get command not found.
Can someone please refresh me on how to do a 'Dir /s /p' equivalent; And also whatever gets commands readable page by page eg: ls b43-fwcutter (toggles for directory/file??) | grep something?

Thankyou!!

"Dir" is "ls" here. use "man ls" to get info on the vaious options.
i like "ls -lah"

---

### Post by minsf on 2009-01-17
> **minsf said:**
> "Dir" is "ls" here. use "man ls" to get info on the vaious options.
i like "ls -lah"
/p is |less
that is do "ls -lah |less"

---

### Post by JootFish on 2009-01-17
> **minsf said:**
> what error do you get when you try "sudo apt-get install b43-fwcutter" from the terminal? (you forgot to cut and paste the error in (2) in post #1)

> **minsf said:**
> i think the reason why the hardware-detection doesnt work, and why you cannot install with apt-get is that not all the repositories are enabled!

let's try this: go to System>Administration>SoftwareResources and make sure that the first 4 boxes are checked! (that is, main, universe, restriced and multiverse)

if i'm guessing right, one of them is not enabled (probably restricetd box), and that's the problem! if i'm right, then after checking this box go to hardware-detection again, and hopefully you'll have the broadcom driver there. or you can also try the "sudo apt-get b43-fwcutter" method. now that the box is checked, it should install


Alas all are checked... (On my system it's System/Administration/Software Sources... I assume it's same same, but as I'm so inexperienced I thought I better post it in case I've got something wrong)

PS. I'm using WPA 'TKIP PSK' as in the wimpy version of WPA

---

### Post by minsf on 2009-01-17
did you enabled the repositories (as suggested in #10)? did it work?

---

### Post by minsf on 2009-01-17
> **JootFish said:**
> Alas all are checked... (On my system it's System/Administration/Software Sources... I assume it's same same, but as I'm so inexperienced I thought I better post it in case I've got something wrong)

PS. I'm using WPA 'TKIP PSK' as in the wimpy version of WPA

oh ok. i thought i had it :(
we still need to check why apt-get doesnt let you download b43-fwcutter (and build-essential). it is important to the success. i need to go now, but i'll think about it and i'll post here later (probably in like 5 hours). good luck with that link. let me know how it went.

by the way, are you sure it's not because of your firewall? (i hope you dont mind me joking about your expertise...)

cheers :)

---

### Post by JootFish on 2009-01-17
Hey thanks for all your help minsf. You've been fabby! I too am very curious as to why I can't download these packages... As mentioned above, I did check the repositries. I have been able to download other things from the terminal such as b43-fwcutter-011.tar.bz2. Course as I can't make the exe, it's no good :(

With regards to the firewalling, I've not installed or configured any software firewall on the lappy. I'm just using a Netgear router/firewall for now which is not blocking any outbound ports... I'm assuming I don't need any inbound mappings just to do this?

Anyhoo, don't answer straight away if you happen to read this, I'll keep fiddling throughout the day and catcup with you later on if you happen to get back in. If I (as in y'all helping me and I type in what you say :P) can't get it working, Intrepid will be installable tomorrow which will hopefully improve things.

---

### Post by JootFish on 2009-01-17
Er would you believe someone hijacked my system, seemingly to do nothing more then post on this forum pretending that I'd compile an exe??!!? :P :P

---

### Post by minsf on 2009-01-18
that's weird. my apt-get cannot see bcm43xx-fwcutter, even though the latter is definitely in the universe repository. as for b43-fwcutter, it doesnt seem to be in any repository...
anyway, you may want to know that almost all packages can be found on [http://packages.ubuntu.com](http://packages.ubuntu.com)

in our case, you should download the package manually via the following link [http://packages.ubuntu.com/hardy/utils/bcm43xx-fwcutter](http://packages.ubuntu.com/hardy/utils/bcm43xx-fwcutter) or download the other package via [http://packages.ubuntu.com/hardy/utils/b43-fwcutter](http://packages.ubuntu.com/hardy/utils/b43-fwcutter)
these links assume that you are still using hardy (8.04).

after you downloaded, say, the first package, you install it with the debian manager: ```
sudo dpkg -i bcm43xx-fwcutter
```

now i think you'll be able to continue with the guide at kernel.org
this should be the ultimate guide (these guys make the linux kernel) but it skips a few steps- it assums you already have the fwcutter files where they should be... 

i'll be glad to help figuring out this guide.
let me know how it goes

---

### Post by JootFish on 2009-01-18
Hey again,
Just an update to let you know I'm still on it... I quickly tried to follow your last post minsf, but hit a snag (not sure where exactly) and decided to try out Intrepid...

Well I've just loaded that on and now having stability issues and probs with the display (windows are behaving a bit glitchy and I can't install the 'drivers' for the ATI card)...

Plus the wireless is not showing any networks (I assume they normally show automagically in the networks thingy at the top right corner when everything is working), so I think I'll go back to 8.04. And try again.

If anyone wants to have a go remote accessing the thing I'd be hwappy (Fast Internet) :P Of course I would need to figure out how to install VNC or whatever!!

Cheers all

---

### Post by minsf on 2009-01-18
sorry to hear about your experience with interpid. mine is great. but i assume your wireless problem will be the same in 8.10 and 8.04. therefore, if 8.10 means you have to fight another war about the display, and if in the 8.04 the display works fine, then go back to 8.04. 
someone once told me, dont try to shoot two birds on a tree; better focus on one of them, and not be left hungry... when the you get your wireless working, you can try fighting the display. (wish i could help you with the display, but i have nvidia)
i really think that downloading the fwcutter with a right click, and then using "dpkg -i" should at least install the fwcutter. when you are back to 8.04, let me know where you get stuck, or what errors you get from the dpkg.
cheers

---

### Post by JootFish on 2009-01-19
Hi again minsf,
I've managed to get XP running from the flash stick (using [www.usboot.org](www.usboot.org) and Grub) which'll do fine, so I'll bow out on this one. I expect the next laptop I hit with Ubuntu won't have the same problems, but I've learnt from your help and appreciate it!

Thanks for your time and follow through, it's been a nice introduction to the Ubuntu community!

R's,
Jason

---

### Post by minsf on 2009-01-19
one thing you should try when running 8.04 is to first enter
```
sudo apt-get install libc6 debconf
```
and only then download the package from
[http://packages.ubuntu.com/hardy/utils/bcm43xx-fwcutter](http://packages.ubuntu.com/hardy/utils/bcm43xx-fwcutter)
and install it with
```
sudo dpkg -i bcm43-fwcutter
```

the reason is that dpkg does not handle dependencies, and according to the link above, bcm43 depends on libc6 and debconf.

---

### Post by minsf on 2009-01-19
> **JootFish said:**
> Hi again minsf,
I've managed to get XP running from the flash stick (using [www.usboot.org](www.usboot.org) and Grub) which'll do fine, so I'll bow out on this one. I expect the next laptop I hit with Ubuntu won't have the same problems, but I've learnt from your help and appreciate it!

Thanks for your time and follow through, it's been a nice introduction to the Ubuntu community!

R's,
Jason
oh i see.
well, hope next system is going to run out of the box!
one tip: ubuntu's problem is that it will only run open source out of the box. since broadcom is closed at some point (copyrighted frimware or something like that) it is probably why it doesnt work out of the box.
so the tip is that you should try linux Mint sometime. it is based on ubuntu, but does not limit itself to open source completely, so that it is more likely to work out of the box with your hardware.
cheers!

---

