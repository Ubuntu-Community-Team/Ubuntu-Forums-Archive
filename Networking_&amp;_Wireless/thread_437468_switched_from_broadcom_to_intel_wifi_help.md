---
title: "switched from broadcom to intel wifi help"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by tedrampart on 2007-05-08
so today I removed my broadcom 4311 wireless adapter in my laptop (tired of using ndiswrapper, plus lack of monitor mode etc).  I replaced it with an intel 3945 card as they're supported.

I turned it on, but it doesn't detect the wireless card in there.  I have a feeling that since I used ndiswrapper and had to blacklist, its not showing up.  its not showing up with "lspci" either.

can anyone show me some links, or assist me in removing ndiswrapper and getting the intel card to work? 

I was also thinking I should just re-install 7.04 and replace everything since I've been running it since herd5 (all updated though) and then the intel card would work.. what do folks think?

---

### Post by chili555 on 2007-05-08
I would never re-install if I could easily (I hope) rescue my existing system. I would *sudo gedit /etc/modules* and remove the ndiswrapper line. Run *sudo depmod -a.*Then, I would *sudo apt-get install linux-restricted-modules.* Now, if you do *sudo modprobe ipw3945* followed by *iwconfig* you should see your new eth1 interface ready to be configured.

I don't think there is any reason to uninstall ndiswrapper, but you could, if you wish, through Synaptic.

Post back if you hit a snag. Old Chili loves his ipw3945.

---

### Post by tedrampart on 2007-05-08
okay, so I did this, and have some snags...

first, when I edited the modules, it didn't find the ndiswrapper.. so I moved on to the next step.. apt-get told me that I had the latest versions installed.. so then when I did modprobe, it said it couldn't find the wireless connection (I'd cut and paste, but I'm on a different computer typing this) ..

now, there were alot of restricted modules packages to choose from, so I did the one based on the kernel I'm using.. maybe I did the wrong one?  which one should I choose? (did -modules-2.6.20.15-generic) 

thanks for the help so far..

---

### Post by chili555 on 2007-05-08
I think you have the right restricted modules. Tell me what it said, please, when you did```
sudo modprobe ipw3945
```Thanks.

---

### Post by tedrampart on 2007-05-08
" 2007-05-08 21:43:34: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection "

---

### Post by tedrampart on 2007-05-08
okay, now when I try sudo modprobe ipw3945 it says nothing, just pauses for a second then goes to the prompt again

---

### Post by chili555 on 2007-05-08
Hmmm, never saw that in response to a modprobe, but let's press on. What does *iwconfig* tell us?

---

### Post by tedrampart on 2007-05-08
it says:

"lo        no wireless extensions.

 eth0    no wireless extensions."

(eth0 is my wired)

---

### Post by chili555 on 2007-05-08
> its not showing up with "lspci"That's certainly an issue! Does it show up in```
sudo lshw -C network
```If not, I'd suggest rechecking the installation of the card.

---

### Post by tedrampart on 2007-05-08
no, it doesn't show up with that..

I'll try checking the installation again right now.. could it be that HP is blocking it because its not the one that came in the laptop?  (I can't see this being an issue though)

---

### Post by chili555 on 2007-05-08
Could be, IBM did stuff like that. You might see if anything can be done in the BIOS.

---

### Post by tedrampart on 2007-05-08
I looked when I first booted with it in .. nothing.. its a horrible bios as far as features..

I'm off to work, so I'll plug it into the wired there, and keep looking around..

---

### Post by b_chris on 2007-05-09
Hey Ted, I'd like to know how you go as I have the same problem...

---

### Post by tedrampart on 2007-05-09
b_chris: you have the same problem?


the more I try the more its lookin like the card is being restricted by the bios...

I just tried a livecd, and it didn't pick it up... 

I'll post more as I go..

---

### Post by tedrampart on 2007-05-09
just got an email back from HP.. they implied that I could use another wireless card in replacement of the original one.. but "Changing the internal wireless card may affect the
functionality of your HP notebook" .. which doesn't actually answer my question to them.. I guess there's hope yet..

---

### Post by chili555 on 2007-05-09
What is the exact model of laptop? I'd like to research it on line.
> Changing the internal wireless card may affect the functionality of your HP notebookI'm sure it will, for the better! IMHO, the 3945 is a great wireless card.

---

### Post by tedrampart on 2007-05-09
yes, please do.. I spent 5 hours last night at work (quiet shift teehee) trying to find stuff..

its the HP pavilion DV6110CA

---

### Post by chili555 on 2007-05-09
Evidently, HP has a 'whitelist' built in to the BIOS that allows only certain  components, including wireless cards, to be installed. Please see here:  [http://joshuawise.com/Wireless-Whitelist.html](http://joshuawise.com/Wireless-Whitelist.html) and here: [http://forum.notebookreview.com/archive/index.php?t-13991.html](http://forum.notebookreview.com/archive/index.php?t-13991.html) and here: [http://www.rechner.org/b1800_bios.html](http://www.rechner.org/b1800_bios.html). 

DISCLAIMER: I do not support, endorse or suggest any of these methods. Proceed with care! Chili disavows all knowledge of your methods to trick your BIOS.

You might go back to HP and request support for a non-whitelist BIOS.

---

### Post by tedrampart on 2007-05-09
hey thanks for your help.. I saw these links last night too, but I'm not going to try these methods..

my game plan is to just put the old one back in, and probably sell it.. get myself a system76 laptop..something small with alot of power, long battery life, and full 100% linux support.. enough of this corporate b.s.

---

### Post by tedrampart on 2007-05-09
thought I would update.. seems the situation has changed a bit.. after going on the HP site, and going through the support before you buy, the guy told me to flash the bios, and after that 3rd party hardware will work.

sadly, I have to reinstall windows in order to do that.  so I'll have to install windows over my root partition keep my home partition intact, then flash the bios, and reinstall feisty after its flashed.. so hopefully it'll work..

---

### Post by chili555 on 2007-05-09
Post back and let us know so other whitelist guys will know. Good luck!

---

### Post by tedrampart on 2007-05-09
thats the plan...I hope it works!!!

---

### Post by tedrampart on 2007-05-11
****UPDATE ****

so I just tried flashing the bios.. loaded up winxp onto it, got a network setup, did the winflash thing they sent me to (HP tech support), flashed the bios and tried installing the wireless under windows.  windows couldn't find the adapter.. the flashing of the bios didn't correct this.

infact the bios version they refered me to (also the latest) is the same version packaged with the machine.  

think that solves it.

---

### Post by cryogenic on 2007-05-12
sucks that HP is doing the same thing IBM is. I had an old IBM R50 that had an 802.11-only Intel card and I bought a b/g card off ebay and swapped it out. It wouldn't even boot with the new card in. I had to download this bootable ISO and burn it then run it so it would unlock the BIOS. At that point it worked like a charm.

---

### Post by tedrampart on 2007-05-12
yea I couldn't find any solid bios flashes that would unlock it.

---

### Post by mrpeanut on 2007-05-31
I bought a 3945abg card to replace my Broadcom 4311 that came in my HP dv2125nr, and I've run into the exact problem you've described.  In fact, I thought there was a problem with the first 3945abg card I had ordered, so I ordered another one.  I'm going to check back with this thread frequently until one of us finds a solution!

---

