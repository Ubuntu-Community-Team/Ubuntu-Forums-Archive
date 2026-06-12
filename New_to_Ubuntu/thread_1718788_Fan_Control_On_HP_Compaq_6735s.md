---
title: "Fan Control On HP Compaq 6735s"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by dougguod on 2011-03-31
Hi I'm a bit of a newbie and would love some help getting my computer to run a bit cooler. I have a HP Compaq 6735s. I have install sensor applet. sensor detect loads k10temp. At the moment it idles at around 55-60 C, which I think is relatively high as sensors says

acpitz-virtual-0
Adapter: Virtual device
temp1:       +73.0°C  (crit = +105.0°C)                  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +73.8°C  (high = +70.0°C, crit = +100.0°C)  

I have installed acpi
when heavily loaded it doesn't get over 80 C which is good but I want to know if I can make it run a bit cooler as it seems to idle quite high

anybody got any ideas?
Cheers
D

---

### Post by dougguod on 2011-03-31
P.S
My laptop has an AMD athlon 64 bit x2 and a radacpieon HD 3200

---

### Post by dougguod on 2011-04-01
just found this post [http://ubuntuforums.org/showthread.php?t=1709127](http://ubuntuforums.org/showthread.php?t=1709127)

I changed /etc/default/grub
by running sudo nano /etc/default/grub

from ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\"" 
but still idles at the same temperature. going to try running sensors detect again.

It seems to me  that it would be easier to use fan control and pwmconfig but as pwmconfig returns no pwm enabled sensors I cant.

I'm just talking to myself now but I figure its a good way to keep a record of what you've done to your comp

Damn You Hewlett Packard
D

---

### Post by dougguod on 2011-04-01
also found I have the bug that turns the fan on full speed after suspend

---

### Post by dougguod on 2011-04-01
going to try 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\" 			 		
```

and also going to try 
```

 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=copy_dsdt"  
```

---

### Post by dougguod on 2011-04-01
installing acpitool

---

### Post by dougguod on 2011-04-01
I'm Stabbing in the dark I wish someone could help!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Hedgehog1 on 2011-04-02
Hey there!

You are CLOSE but not quite there!

```
gksudo gedit /etc/default/grub
```

```
GRUB_CMDLINE_LINUX_DEFAULT=**"**quiet splash **acpi_osi=\\\"Linux\\\""**
```

There are a total of **4 double quotes** in this line (2 side-by-side at the end)

Then do:

```
sudo update-grub
```

And reboot.

My HP C50 notebook runs cooler this way.

***The Hedge***

:KS

p.s. Don't you just hate talking to yourself? :D

---

### Post by Hedgehog1 on 2011-04-02
In case you are wondering WHY all these slashes, it is because this text string gets processed twice before it is used to boot the kernel:

In /etc/default/grub it looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""
```

Which gets converted by the update-grub in /boot/grub/grub.cfg as:
```
linux /boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi=\"Linux\"
```

The command is then passed to the kernel when run by grub as:
```
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-8-generic root=UUID=78b161e2-4d82-4df7-a423-8289fe6cc704
ro quiet splash acpi_osi="Linux"
```

See how easy that (isn't) to follow?


***The Hedge***

:KS

---

### Post by dougguod on 2011-04-02
Cheers for the tip hedge, it does work it gets it only slightly cooler than the other scripts I used but It is colder, Do you get the bug where after suspend you're fan picks up speed? I know its a bug but I'm idling at 40C now when I was at 50C before I suspended.

Thanks again hedge, much appriciated

---

### Post by Hedgehog1 on 2011-04-02
The HP C50 is 'new' to me (it needed a new hard drive and new battery; original owner just replaced the laptop with a faster one).  I ran 10.10 on it for about 4 hours (to verify operation), then it became my 11.04 testing system.  I have only used Suspend in 11.04 (and then just for my 'standard' round of testing) but did not look for fan speed changes.

I will check it after the next round of 11.04 updates.  My machine and yours have different BIOS(s), so I don't know if my system even had that particular bug.


***The Hedge***

:KS

p.s. Can I ask a favor of you?  Would you use Disk Utility and find the operating temperature of the hard drive in your laptop after it has been running for 15 minutes?  I want to get a feel what want is 'normal' for these units.  Thanks!

p.p.s. the old hard drive smelled like burning bacon when it was powered up, and gave this lovely error when I booted it from my USB 'Ubuntu-On-A-Stick!':

[IMG]http://img146.imageshack.us/img146/7057/diskfail03.png[/IMG]

---

### Post by dougguod on 2011-04-02
OK I've just turned it on. Does you laptop fan change speed when it gets to 60C because mine just stays constant whatever temperature which I don't think is right? Shouldn't it be dynamic? In terms of bios I did an update recently and It didn't seem to change much it was F.03 and I updated to F.0E. I did take it apart and hover up though that made a big difference, because before it kept overheating and shutting down. Ok so it was 42C with the processor temp at 60C. I'm guessing the fact that my fan speed has something to with my bios, but when I had windows on it, the fan speed did change dynamically. Thanks
D

---

### Post by Hedgehog1 on 2011-04-02
My i7 based HP laptop with Windows 7 does change fan speed dynamically as well. The little HP C50 with 11.04 seems to run at a more constant speed, and stays cool enough.

Thanks for posting the HDD data.  My Western Digital Blue drive runs a little warmer then yours, but is still in the 'safe' zone.  


***The Hedge***

:KS

---

### Post by andiwakefield on 2011-04-03
Hi there, im having the same trouble with my HP 6735s. The fan just won't slow down. And the CPU is running at nearly 90c.

Can I please ask you what program I need to download in order to put in those commands?? Can you send me a link, as I've tried to download ACPI but I've hit a brick wall.

Thanks in advance.

Andrew :-)

---

### Post by dougguod on 2011-04-03
Hi Andy, It could be that you're fan is blocked or dusty, do you have lm-sensors installed? you can install lm-sensors and acpi through synaptic package manager in system>administration. once you have installed lm-sensors run sensors in the terminal by typing ```
sensors
``` in the terminal. you could also run ```
sudo sensors-detect
``` which should load the appropriate sensor driver thingy.

I also have sensors applet installed which tells me my cpu temp in the panel.

My laptop was the same until I did a bios update and took it apart and hovered the insides, it's not a very well designed laptop in terms of heat dissipation. If you don't want to take it apart, which is relatively scary you could get a hover and hold it up to the heat sink on the right hand side as this connects directly to the fan. this should get rid of some of the dust if it the fan is blocked. do this when switched off. it might be worth checking if you can feel air coming out of this vent. what bios revision do you have?

just reread you post and it sounds like a hardware problem. to get acpi or any other program through terminal you can type ```
sudo apt-get install acpi
```

Doug

---

### Post by andiwakefield on 2011-04-03
Ahh, sorry if I am being a little ambiguous in my post. I am running Windows Vista x32 bit.

I didn't realise this post was dicussing Linux.

I think I will try the hoover part and also I will try the use of an air duster too. I know what you mean about the air flow, the HP 6735s is very hard to get into.

Will let you know the outcome....

I also have the latest BIOS update which made NO change whatsoever. :((

:)

---

### Post by dougguod on 2011-04-03
there's a guide on taking it apart on the net. google it

---

### Post by dougguod on 2011-04-03
you should try ubuntu its grand

---

### Post by andiwakefield on 2011-04-03
I'm certainly considering the thought.....:P

---

### Post by dougguod on 2011-04-05
andi, did you hover you're laptop, did it work?

---

