---
title: "will now halt"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by metaemployee on 2011-08-24
on system shutdown I'm getting 
Will now halt
[<time>]Power down.

And cooler spins & monitor is on.

Every thread I read not helped me. Hope someone here will.

Ubuntu 11.04

---

### Post by e79 on 2011-08-24
I encountered this little bug couple of times on my 11.04 laptop, nothing worrying though.

All I needed to do though is press Enter (or any key for that matter) and it properly shuts down.

Hope your issue is the same as mine  =P

---

### Post by decoherence on 2011-08-24
> **metaemployee said:**
> on system shutdown I'm getting 
Will now halt
[<time>]Power down.

And cooler spins & monitor is on.

Every thread I read not helped me. Hope someone here will.

Ubuntu 11.04

Sounds like ACPI isn't working properly. Have you configured GRUB to boot with acpi=off by any chance?

In any case, the system is halted. If pressing 'enter' like the other poster suggested doesn't work, it's perfectly safe just to kill the power on it. The "power down" message is actually an instruction (as opposed to slightly comical self-contradiction.)

---

### Post by metaemployee on 2011-08-24
> Sounds like ACPI isn't working properly. Have you configured GRUB to boot with acpi=off by any chance?

acpi=off -> system doesn't stat at all

> 
In any case, the system is halted. If pressing 'enter' like the other poster suggested doesn't work, it's perfectly safe just to kill the power on it. The "power down" message is actually an instruction (as opposed to slightly comical self-contradiction.)

pressing enter not working, and I'm not pressing "Power button" for 6 seconds to shut down computer, it worked on Windows it should work on Linux. There is a problem and I need a fix.

Still waiting for suggestions. 
If you need any logs, just tell me where to find them and I will post them.

---

### Post by metaemployee on 2011-08-27
bump

---

### Post by metaemployee on 2011-08-28
bump

---

### Post by metaemployee on 2011-08-29
bump

---

### Post by JKyleOKC on 2011-08-29
> **metaemployee said:**
> pressing enter not working, and I'm not pressing "Power button" for 6 seconds to shut down computer, it worked on Windows it should work on Linux. There is a problem and I need a fix.For some reason, your system is ignoring the "power off" command that the shutdown command is sending to it. Once you see that "Power down" message on the screen, nothing on the keyboard will have any effect because the CPU itself is halted and cannot respond.

The problem has to be in your system configuration somewhere; it could be in the BIOS setup, or in one of the rather arcane configuration files in the /etc directory. It's definitely **not** a generic *buntu flaw, since if it were the forum would be flooded with other complaints about it.

The "Power down" message is telling you to turn off the power manually. If you don't want to hold the button down for six seconds (incidentally all of my systems need only four seconds when I need to power down manually after a non-Linux freeze-up) to do so, you can simply unplug the power cord from the wall.

---

### Post by scottstensland on 2011-08-29
I also have same symptom when using ubuntu (11.04 and 11.10)
interestingly, my laptop works fine using openSUSE 11.4
so I also feel its a software issue (fixable)

issue ;

cat /etc/default/grub|grep GRUB_CMDLINE_LINUX

to see if you are using any kernel modifiers, wording like :


    acpi=force
    acpi=off
    apm=power_off
    pci=noacpi

these are also shown for instance by hitting F6 during a Live CD boot up initial screen
My machine will freeze on boot up unless I use :   acpi=off
so would be good to know if you are modifying your kernel on boot up

---

### Post by metaemployee on 2011-08-29
> cat /etc/default/grub|grep GRUB_CMDLINE_LINUX
GRUB_CMDLINE_LINUX_DEFAULT=""
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

> acpi=force
no difference

> acpi=off
system does not boot

> apm=power_off
pci=noacpi
will try in couple hours

---

### Post by Johnb0y on 2011-08-29
> **JKyleOKC said:**
> > For some reason, your system is ignoring the "power off" command that  the shutdown command is sending to it. Once you see that "Power down"  message on the screen, nothing on the keyboard will have any effect  because the CPU itself is halted and cannot respond.the CPU never really halts until power is off! *technically! thats where the message partly comes from.

[QUOTE]The problem has to be in your system configuration somewhere; it could  be in the BIOS setup, or in one of the rather arcane configuration files  in the /etc directory. It's definitely **not** a generic *buntu flaw, since if it were the forum would be flooded with other complaints about it.this is true, as it is probably your BIOs setting under power management *if i remember correctly! as i have had this issue on old machines before. if need be update your BIOs firmware... remembering to back things up!

> The "Power down" message is telling you to turn off the power manually.  If you don't want to hold the button down for six seconds (incidentally  all of my systems need only four seconds when I need to power down  manually after a non-Linux freeze-up) to do so, you can simply unplug  the power cord from the wall.holding the power button is the best/safest way to shut down your machine once the message appears. please dont just unplug it, this could cause damage to your machine.
[/QUOTE]

best thing is just check BIOs before doing anything. also. p.s. make sure you system is up to date on all software. :P

---

### Post by metaemployee on 2011-08-29
System is up to date.

Bios has only CPU state C4 end/dis, clock & boot sequence. Nothing more to configure.

As my laptop is barebone, I don't have any references where to download updated bios & I've never updated one. Just not willing to brick my laptop by experimenting.

apm=power_off
no effect

pci=noacpi
computer doesn't boot at all

---

### Post by Johnb0y on 2011-08-29
> **metaemployee said:**
> 
pci=noacpi
computer doesn't boot at all

please tell me, you have backed everything up before you did that? :(

---

### Post by metaemployee on 2011-08-29
no need, I can change grub parameters in recovery mode.

---

### Post by Johnb0y on 2011-08-29
:KS for you! :P

go you! \\:D/

glad your not in a s*** state of: ](*,)

as i know i was like: ](*,) when i had this issue on an old machine!

---

