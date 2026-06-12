---
title: "On fully-charged battery Ubuntu shuts down on me"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by al.adab on 2010-04-30
hello,

just installed Ubuntu 10.04. On a fully (or being charged) charged battery, when I unplug the power cord, a message pops up saying that I have less than 1% battery power. Ubuntu then shuts down. 

I checked Power Management, but I see nothing strange there. I can't figure out what the problem might be (have been on Ubuntu for some years now, and this has never happened before on the laptop I'm using now). 

Can you help? Thanks.

---

### Post by ibuclaw on 2010-04-30
Sounds like a safety mechanism gone wrong to me.

I can vouch I get something similar, but it is at [the other end of the extreme]("http://iainbuclaw.files.wordpress.com/2010/04/screenshot.png"), so I don't get the whole system shutting down.

The only advise I can say is that just live with it for the moment. The Power Manager takes a while to adjust to your system's battery.

This is because it uses an adaptive algorithm that - eventually - is able to predict how long till battery is fully charged, how long will the battery last if you start discharging at 75% full, etc, etc... As opposed to "if you continue at this constant usage, it will take "this" long to drain battery / till battery is fully charged.

Regards

---

### Post by P4man on 2010-04-30
> **al.adab said:**
> hello,

just installed Ubuntu 10.04. On a fully (or being charged) charged battery, when I unplug the power cord, a message pops up saying that I have less than 1% battery power. Ubuntu then shuts down. 

I checked Power Management, but I see nothing strange there. I can't figure out what the problem might be (have been on Ubuntu for some years now, and this has never happened before on the laptop I'm using now). 

Can you help? Thanks.

sounds like a bug not detecting your battery correctly. You may want to report that on launchpad. In the meanwhile, work around it by going to system > preferences > power management and disable the option to have it shut down on low and critical battery.

---

### Post by madjr on 2010-04-30
check if the bug has been reported on launchpad

---

### Post by ibuclaw on 2010-04-30
To defer your system from shutting down, you can set the power settings to "Suspend" when battery power is reportedly critically low.

This is only a workaround to prevent accidental data loss though. :)

---

### Post by al.adab on 2010-04-30
The "suspend" solution didn't work. If I'm not mistaken in previous editions of Ubuntu it was possible to tell the computer not to shut down if the battery had less than (example) 10% power. 
Anyway, this is a major pain. I disabled power management altogether at start-up, though I don't really know what exactly this means (I suppose the battery will still be charged when I plug in the power cord, right, just that I won't be able to see how much power the battery has left when I unplug it?). 
I'm wondering if one can by-pass power management and use alternative software - that enables putting a battery icon somewhere, for instance. Even if power management is disabled at start-up, if I tell power management to display an icon in notification area, the moment I unplug the power cord I'm back to square one. The pc shuts down. I have to tick off "never display an icon" for it to serve as a workaround. 
I'll look into reporting it as a bug. It'd be helpful if you could advise on alternative power management software, though. 
Thanks.

---

### Post by P4man on 2010-04-30
you can change all the behavior of powermanagement. press alt+f2 and run:

```
gconf-editor
```

Browse to:

/apps/gnome-power-manager/actions/critical_battery

set action to "nothing"

You can adjust tresholds in 

/apps/gnome-power-manager/thresholds/

---

### Post by P4man on 2010-04-30
btw if you click on the battery icon and select "lapto battery" menu, does it detect the battery correctly?

---

### Post by al.adab on 2010-04-30
yes it does detect the battery as laptop battery. 
I've changed action to "nothing" in gconf-editor. Now the system no longer shuts down on me, except that I still get this annoying message popping up "laptop battery critically low, etc" (if power management is enabled at start-up). Whether I click on "cancel" or "ok", the computer doesn't shut down. 
Can you please tell me how to get rid of this message?

---

### Post by al.adab on 2010-04-30
I mean the message pops up when I unplug the power cable. The battery is in good conditions, by the way.

---

### Post by ibuclaw on 2010-04-30
I still think you should wait it out a week or two, see if power manager gets better then, and if not raise a bug. As I said, it is adaptive, and may take a while to tune to your system usage.

Regards

---

### Post by P4man on 2010-04-30
I suspect this one:

/apps/gnome-power-manager/notify/low_power

If not,then "cheat" by modifying

/apps/gnome-power-manager/thresholds/percentage_critical

try setting it to 0, since it incorrectly reports 1% in your case.

---

### Post by The Cog on 2010-04-30
Do you have an MSI wind by any chance?
[http://ubuntuforums.org/showthread.php?t=1463114](http://ubuntuforums.org/showthread.php?t=1463114)
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/558627](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/558627)

---

### Post by al.adab on 2010-04-30
sorry I haven't got the faintest idea of what an MSI wind is. I have a Dell Vostro 1310 laptop...

[I]
I suspect this one:

/apps/gnome-power-manager/notify/low_power

If not,then "cheat" by modifying

/apps/gnome-power-manager/thresholds/percentage_critical

try setting it to 0, since it incorrectly reports 1% in your case.[/I]

tried this. No avail. I also tried to disable all the notifications on gconf-editor (re: power management) but I still get the damn message every time I unplug the power cable...

I could wait in principle and see if the system "adjusts itself", but practically this is going to give me a hard time, as I constantly have to unplug the power cable (unless I find one that's 20 meters long...)....

---

### Post by P4man on 2010-04-30
Then I dont know :(

The only thing I see in there that might be worth trying is one I dont quite understand what it does:

/apps/gnome-power-manager/general/use_time_for_policy
Descrption:
*If time based notifications should be used. If set to false, then the percentage change is used instead, which may fix a broken ACPI BIOS.*

Could be worth a shot?
edit: I think I understand the sentence now, and its definately worth a shot.

---

### Post by al.adab on 2010-04-30
Thanks tons P4man, it worked. I kept the value as "false" and unticked "use_time_for_policy". No more messages. 
I suppose I can leave it that way and considered this solved? Or is this to be seen as a temporary workaround?

---

### Post by P4man on 2010-04-30
> **al.adab said:**
> Thanks tons P4man, it worked. I kept the value as "false" and unticked "use_time_for_policy". No more messages. 
I suppose I can leave it that way and considered this solved? Or is this to be seen as a temporary workaround?

If you reenable default settings, except for the "use_time_for_policy", does it work properly? Just asking so I can suggest it to the guys in the bug report linked above.

feel free to mark this thread solved, but I would consider it a workaround. Im not sure if its a workaround of a bug in ubuntu or a bug in your acpi bios though (I guess the latter).

---

### Post by al.adab on 2010-04-30
it looks like it works, but I'm not entirely sure as I've changed almost every single line and a) can no longer remember what the original value was b) don't know how to re-set default settings (command in terminal, maybe?). 
Thanks again.

---

### Post by The Cog on 2010-04-30
> **P4man said:**
> Then I dont know :(

The only thing I see in there that might be worth trying is one I dont quite understand what it does:

/apps/gnome-power-manager/general/use_time_for_policy
Descrption:
*If time based notifications should be used. If set to false, then the percentage change is used instead, which may fix a broken ACPI BIOS.*

Could be worth a shot?
edit: I think I understand the sentence now, and its definately worth a shot.

Thank you, P4man.

I am one of those who found a problem with the MSI wind, where it shuts down as soon as mains is removed. 
This procedure fixed it for me:
Press Ctrl-Alt-F2 and use the pop-up to launch **gconf-editor**. 
Navigate to **Apps / gnome-power-manager / general**. 
**De-select** the option **use_time_for_policy**.

No need to restart, just close the config editor.

---

### Post by P4man on 2010-04-30
great, so we all learned something. The Cog can you post that on launchpad as workaround, as it will probably work on MSI winds as well. Perhaps add Dell Vostro 1310 is affected too.

---

### Post by chrisinspace on 2010-05-18
> **The Cog said:**
> Thank you, P4man.

I am one of those who found a problem with the MSI wind, where it shuts down as soon as mains is removed. 
This procedure fixed it for me:
Press Ctrl-Alt-F2 and use the pop-up to launch **gconf-editor**. 
Navigate to **Apps / gnome-power-manager / general**. 
**De-select** the option **use_time_for_policy**.

No need to restart, just close the config editor.

Confirmed.  I have a Vostro 1310 with this exact issue and these steps worked for me.

---

### Post by iLag!!!!! on 2010-06-12
Sorry to bump this thread, but I'm having the same issue on Kubuntu.  I've been looking through the menus and synaptic, but I can't find the KDE equivalent to this solution.  Does anybody know what it is?

---

### Post by satyapraneethr on 2010-06-18
i m not getting good battery backup in my ubuntu 10.04...
i get around 2hrs for my fully charged 9 cell bettery in my dell studio 15 laptop whereas i get nearly 3hrs on windows 7....
can anyone help me?

laptop confg:
studio 1557,  corei7 1.6GHz processor, 4 GB RAM, 500GB 7200rpm harddisk

---

### Post by ibuclaw on 2010-06-18
Creating a fresh new thread would be a start mate, rather than salvaging the scraps left here.

Closing to prevent incident.
It's a standard procedure.

---

