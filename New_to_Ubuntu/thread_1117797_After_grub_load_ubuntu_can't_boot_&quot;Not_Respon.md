---
title: "After grub load ubuntu can't boot &quot;Not Responding&quot;"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by Neonenon on 2009-04-06
Hi Ubuntu Team,
I recently switch to ubuntu :p on my new desktop quad pc
After I successfully managed to install/update and configure Ubuntu 8.10 Ibex (Dual boot with vista) on..
500 SATA (ntfs) (loader)
500 SATA (ntfs)
320 SATA2 (linux ext3/swap)

Everything seemed to work fine until the next reboot when grub loads
I choose the first kernel 2.6.27-11 ..starting..
then I receive a message [0000000] Not responding maybe a couple of times and the pc restarts..
Next I try the recovery kernel..same.
Then I try the other older kernel 2.6.27-7..still the same
After another 3-5 tries the system randomly manage somehow to boot into ubuntu 8.10 ibex (<3) and workin..(both kernel boot at randomly 3-5)
If I try to boot into Vista,it boots fine but sometimes it doesn't boot to.
Also I once managed to get to the recovery kernel but now every time that "not responding" and restarting..
Ive been using the system like this for a week now and since i dont wanna use vista system anymore ):P just for video/media applications. 
After all this troubleshooting I really don't know what to do..
If any member of the community knows something I would like some advice on this "not responding" issue..I attached the hw info and dsmeg file here
for more infos any help would be great.thanks.

---

### Post by kestrel1 on 2009-04-06
Sounds like a hardware fault. Possibly your RAM. 
Remove one stick (if you have more than one & try it for a while. If not then remove another stick & replace the one you had removed previously.
Could also be overheating. Make sure all fans are working & that the system isn't getting too hot.
Also make sure all connections are connected OK.

---

### Post by Neonenon on 2009-04-06
Hi,
I followed the steps of your advice above
Checked RAM is ok.
Checked Cables connected OK.
I have huge CoolerMaster Fan should be OK
Temperatures for the system are:
33*c System Temperature OK
41*c CPU Temperature OK

Continuing the troubleshooting because..  
I can write you from my Ubuntu installation at the moment
But the problem remains at boot up as i have to restart my computer 4-7 times to properly login to ubuntu 8.10.
Sometimes the pc stall at "DMI POOL DATA" maybe that can explain something.
The issue thing is that my "Vista" also boots "Randomly"..no "Not Responding" message there it just restart automatically.
And When it finally manage to boot its working normally as ubuntu did.

At this point im thinking if updating the BIOS Motherboard its a X48-DS5
Gigabyte Tech BIOS version: 	F5 (03/06/2008)
Any Other suggestion with the help is welcome.
Thanks for your time.

---

### Post by kansasnoob on 2009-04-06
I can not open your tar.gz.

But it sounds like you're having some trouble booting both Ubuntu and Vista. Yes or no?

Try running the Ubuntu Live CD. How does that run?

Maybe try posting your system specs in a different format??????

Some ideas  of commands that'll produce needed results here:

[http://tombuntu.com/index.php/2008/01/31/dig-up-system-information-using-the-terminal/](http://tombuntu.com/index.php/2008/01/31/dig-up-system-information-using-the-terminal/)

A thought: I've run across this a lot! What's your power supply capability? You should never load a power supply beyond 75% of it's capability!

People pile in more RAM, a higher usage CPU, GPU, etc. without thinking about the power supply!

Some power supply basics:

Each GB of RAM requires as much as 70 Watts!

A CPU can vary greatly in demands - 20 Watts to 200 Watts (remember the Quad)!

GPU's can be very hungry! especially if you're going 3D! Any number of peripherals!

So physically look at the wattage of your power supply!

---

### Post by kestrel1 on 2009-04-07
You may have a bad PSU or it could be failing.
Are you able to swap it out with another one? I have a PSU tester which you can pick up at a reasonable price or ask you local computer shop if they could test it for you.

---

### Post by Neonenon on 2009-04-07
Hi,
Thank you for the quick reply and your usefull infos
My PSU is a Type R II 680W (HPU-5K680)
8+1 USB 2.0 ports.
Chipset by NEC.
High Efficiency at >85%
NVIDIA® SLI™-certified.
Rated wattage: 680 Watts
Peak load: 890 Watts

And the only move i did with it..was to plug the 4 pin cpu fan to a power cable of the PSU with the aid of a 2 pin "T" adaptor on.
I did this to lower the dbs of the cpu fan (temperature are as listeded above).I also connected the 4 pin normaly on the motherboard but still no booting.I cant replace PSU atm and dont have meter it could be usefull when stumbling on those "weird" issues.
But I wonder as the PC boots and operates normaly after it randomly boot both Vista and Ubuntu,
Is that sometimes possible even with a failing PSU?
Im resending the information about my hardware and dmseg zipped.
Some info there for the message "Not Responding" that appears in the boot sequence.
I still think a bios update may do the trick.. I will tell you about the result after i figure out how to upgrade it.
Thanks again.

---

### Post by Neonenon on 2009-04-07
Here are the Hardware Information attachement..
Thanks.

---

### Post by kestrel1 on 2009-04-07
If your PSU is failing you can get some very random symptoms & can be one of the hardest things to pin down. If you are getting varying power on the motherboard it can look like many things. I would sooner try a new PSU than risk doing potential damage to the motherboard with a BIOS upgrade. If a BIOS upgrade goes wrong your system will be a big paper weight.

---

### Post by unutbu on 2009-04-08
Neonenon,  I don't know the solution, but does this problem sound identical to yours?
[http://ubuntuforums.org/showthread.php?p=7035055#post7035055](http://ubuntuforums.org/showthread.php?p=7035055#post7035055)

---

### Post by theozzlives on 2009-04-08
> **kestrel1 said:**
> You may have a bad PSU or it could be failing.
Are you able to swap it out with another one? I have a PSU tester which you can pick up at a reasonable price or ask you local computer shop if they could test it for you.

A multimeter should do the trick.

---

### Post by kestrel1 on 2009-04-08
> **theozzlives said:**
> A multimeter should do the trick.
Yes a multimeter could be used, but you may not get the correct results & you need to know how to use the meter with the PSU. A PSU tester checks the rails & determines any faults or possible faults. Much easier & quicker.

---

### Post by Neonenon on 2009-04-08
OK Team,
I finally had second thoughts about upgrading that BIOS.. Since the latest for this motherboard X48-DS5 is still Beta.
I would use that tricky multimeter even if its gettin more and more technical just for the troubleshooting but more likely will manage to get an other powerfull PSU.If its power I'll fix it.
For now Im still playing the bootstrap "Lotto" to get into Ubuntu and that other crappy OS...
I was experimenting before installin intrepid Ibex 8.10 using the exact same setting of SATA HardDrives with other versions of Ubuntu like Ubuntu Studio or Ubuntu Ultimate 2.1 both Intrepid Based.
There again same history..
Ubuntu Installation successfull ..
Upgrade successfull..but then at reboot..
My Random "Lotto" Booting issue. "There Patience is the key"
> Neonenon, I don't know the solution, but does this problem sound identical to yours?
[http://ubuntuforums.org/showthread.php?p=7035055#post7035055](http://ubuntuforums.org/showthread.php?p=7035055#post7035055)
I don't know if its the same problem but its definitely the same symptoms, Although in his issue he could boot normally before he upgraded to kernel 2.6.27 using the 9.04 Jackalope a not so stable version yet have I heard.

At this point I consulted a h/w technician friend about why sometimes the PC stops booting at the "DMI POOL DATA.." message
When i told him that i got a CREATIVE PCI FATAl1TY card, and sometimes when i boot into ubuntu, Im hearing randomly "screechy",distorted sound when im playing music mp3 or radio..He said that creative cards always had IRQ issues(?).And since I also connect the soundcard Frontpanel to a pin connector adaptor on one the PSU cables, I think he could have a point there..
Thanks again for the quick replies.I'll be back with more information after I install the NEW Power Supply Unit.

---

