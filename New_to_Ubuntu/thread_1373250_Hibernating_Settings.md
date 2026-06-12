---
title: "Hibernating Settings?"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by soryu on 2010-01-05
Where are The Hibernating Settings?
Power Management Gives me Sleep Settings,But my PC doesn't Sleep.:confused:
It Does Hibernate.:KS
In Karmic.

---

### Post by duanedesign on 2010-01-05
[Here]("https://help.ubuntu.com/9.10/hardware/C/pm-suspending.html") is some general information about suspending and hibernating. What exactly are you trying to do?

---

### Post by soryu on 2010-01-05
i want pc to hibernate after 10 min of not using it.

currently it is hibernating  but it takes somewhere between 15 to 30 min. sometimes it doesn't hibernate. or i takes around 1hr
 i have power management  sleep the pc in 10 minutes,but i just get a black screen and  have to come back and check every 15 to 20 min to see if it's hibernating.

trying to reduce my electric bill.:guitar:

---

### Post by Muttley99 on 2010-01-05
Try suspending instead, the power difference is almost nil. download pm-utils;

[HTML]sudo apt-get install pm-utils[/HTML]

to suspend;

[HTML]sudo pm-suspend[/HTML]

if you want it to suspend automatically after maybe 10 minutes;
download powernap;

[HTML]sudo apt-get install powernap[/HTML]

go to;

[HTML]/etc/powernap/[/HTML]

open config file

[HTML]sudo nano config[/HTML]

change the settings to show 600 seconds for powernap and comment out the following;

[HTML]MONITORED_PROCESSES = [ "^/sbin/init" ][/HTML]

save and close.

restart powernap;

[HTML]sudo /etc/init.d/powernap restart[/HTML]

Pm-utils also has pm-hibernate if you want to try!

---

### Post by SecretCode on 2010-01-05
I don't think hibernating after 10 minutes is going to reduce your electricity bill - unless you normally only use the PC once a day. Each time you resume it it has to read the hibernation image off the disk ... that is likely to use more electricity than keeping it on for an hour. (I don't have any figures for current hardware though.)

Probably best to blank the monitor and spin down the hard disks after 5-10 mins, suspend after 15-20 and hibernate only after 1 hour or so.

---

### Post by JvdBosch on 2010-01-20
Reading off disk consumes exactly as much power as normal operation. So hibernate as much as possible to save power!

---

### Post by SecretCode on 2010-01-20
> **JvdBosch said:**
> Reading off disk consumes exactly as much power as normal operation.

I think that's completely untrue. Do you have a reference?

---

### Post by Muttley99 on 2010-01-20
> **SecretCode said:**
> I think that's completely untrue. Do you have a reference?

On my system about 4w per drive increase!

---

### Post by SecretCode on 2010-01-20
But how long does it take? Remember that during hibernate and resume, you can't do anything else - so you're using the full "normal" power plus the disk required power for that time - and work out the Amp-hours of battery charge consumed. Now compare that with the Ah consumed by the machine sitting **idle** (low CPU, zero disk activity) for the same time.

---

### Post by Muttley99 on 2010-01-20
> **SecretCode said:**
> But how long does it take? Remember that during hibernate and resume, you can't do anything else - so you're using the full "normal" power plus the disk required power for that time - and work out the Amp-hours of battery charge consumed. Now compare that with the Ah consumed by the machine sitting **idle** (low CPU, zero disk activity) for the same time.

I understand your meaning. Power consumption at start and shutdown spikes! I have monitored mine. I have a very low power system NAS built from scratch.
As far as I remember;

Max spike 50w 
Normal operation with one drive 20w idle and 24w loaded
Normal operation both drives (7200) = 22w idle 29w loaded
suspended to memory = 2w
surprisingly! shutdown & Hibernate = 2w (suspect powered ethernet for wol)

..so I suspend to memory using powernap & pm-suspend.

I only wake the NAS for about 30 minutes a day so I save a LOT of power in this config, even with the start and stop spike! ;)

---

### Post by JvdBosch on 2010-01-20
Yep, it all boils down to kWh (that&#347; what you pay for). So even if my computer has a startup peak of 200Watts for 30 seconds and uses 50W under normal conditions, the spike compares to just 2 minutes of normal activity. (1.30 if you deduct the base 50W)

Muttley99, can you explain some more about your NAS and your setup using powernap in the exsisting thread abou it?I'm very interested.

---

### Post by Muttley99 on 2010-01-21
I have;

A Intel D945SEJT motherboard & Atom 270 CPU [http://www.intel.com/products/desktop/motherboards/D945GSEJT/D945GSEJT-overview.htm](http://www.intel.com/products/desktop/motherboards/D945GSEJT/D945GSEJT-overview.htm) = £80

1Gb memory
An xcase = [http://www.xcase.co.uk/X-Case-Atomic-Cube-Black-With-Psu-p/xc-atomic-cubebk.htm](http://www.xcase.co.uk/X-Case-Atomic-Cube-Black-With-Psu-p/xc-atomic-cubebk.htm) 

I've installed Ubuntu-Server

I also bought a 12v power supply even though the case came with it's own. The motherboard has the facility to take an external power supply similar to a notebook.

You can buy a much cheaper itx motherboard, but the intel uses the 945 chipset which is very low power.

Powernap places the NAS into a suspend state after no activity for a predetermined time. You can set the 'no activity' time to whatever you want. Starting the NAS by WOL.

---

### Post by JvdBosch on 2010-01-21
> **Muttley99 said:**
> 
Powernap places the NAS into a suspend state after no activity for a predetermined time. You can set the 'no activity' time to whatever you want. Starting the NAS by WOL.

I don´t want to stray too much from the original topic, but I´m having trouble myself with setting up powernap. Could you share your config files with me?

---

### Post by Muttley99 on 2010-01-22
> **JvdBosch said:**
> I don´t want to stray too much from the original topic, but I´m having trouble myself with setting up powernap. Could you share your config files with me?

I havent altered the config file other than set the no-activity time and apply it to ssh.
I noticed that using ps -ew args and applying the process into the config file didn't work so I just ssh into my NAS to keep it alive. It's a bit of a workaround but it works well for me.

---

