---
title: "Where to start diagnosing random freezes &amp; crashes in Ubuntu 8.10?"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by merekat on 2008-12-09
I could really use some help figuring out where to start diagnosing freeze and crash problems in 8.10.

I'm using a fresh install of 8.10 on a newly built desktop machine (new mobo, CPU, and memory, other hardware purchased within the last year), with a small number of packages installed. I've been experiencing random freezes and some application crashes on a somewhat regular basis (not enough to really compromise my use of the machine). I suspect that the it's the graphical user interface that's freezing, not necessarily the whole system, but I can't be sure. The application crashes don't seem to be limited to any one app in particular.

I've submitted some bug reports to Launchpad (though every one I've submitted replicates another bug report already submitted and I haven't seen any resolution for those). I ran one full mem test using the live cd with no errors, though somewhere I saw a recommendation to let mem test run 10 full cycles, so I will try that. 

Last night I uninstalled compwiz (as it seems there are a lot of folks on the forums having issues with it). I also deactivated the proprietary driver for my graphics card. So far today, I've not experienced a system freeze (tho it's only been a few hours and it seems to usually takes at that long for a freeze to occur), but there has been at least one application crash.

At the moment I'm considering doing a complete fresh install, and adding packages slowly one at a time to try to identify the problem. However, I'm kind of lost as to where to start diagnosing the problem. Does anyone have any suggestions or recommendations? I'd greatly appreciate it.

-----
System specs:

mobo: ASRock 4CoreDual-SATA2 Intel ATX (chipset is VIA Apollo PT880 Pro/ PT880 Ultra / PT 894)
BIOS: American Megatrends P2.00, up to date (5/22/08), 512KB
CPU: Intel Core2Duo E7200 (2.53 GHz)
video card: ATI Radeon 9600 (AGP 8x)
audio adapter: VIA 8237A/8251 High Definition (on board)
memory: dual channel, Kingston 2GB (2x1GB) DDR2 667
HD: Western Digital 80GB SATA
OS: Ubuntu 8.10

---

### Post by wizard10000 on 2008-12-09
First two places I'd look are /var/log/messages and /var/log/Xorg0.log - you should find something.

Good luck -

---

### Post by northern lights on 2008-12-09
What does running ```
dmesg
``` shortly after crashing yield?

Also check /var/log/messages and /var/log/syslog

---

### Post by merekat on 2008-12-09
Most of the logs are gobbledygook to me, and it would appear there are a plethora of errors in the messages log. However two recurring themes in the messages log that stand out to me are that everyday except for the first (the day of install, 12/04/08) kernel says:

Dec  6 10:44:46 GALAPAGOS kernel: Inspecting /boot/System.map-2.6.27-9-generic
Dec  6 10:44:47 GALAPAGOS kernel: Cannot find map file.

(Ummm, that seems like a big problem.)

and 

Dec  9 12:43:00 GALAPAGOS python: hp-makeuri[7479]: warning: hp-makeuri should not be run as root. 

(My HP printer I assume, which was automatically installed.)


Nothing really stands out in xorg.0.log that I can tell.

Ideas anyone? :confused:

---

### Post by merekat on 2008-12-09
I will try running dmesg next time I crash.

Also, syslog today says:

Dec  9 12:11:17 GALAPAGOS syslogd 1.5.0#2ubuntu6: restart.
Dec  9 12:11:17 GALAPAGOS anacron[5171]: Job `cron.daily' terminated
Dec  9 12:11:17 GALAPAGOS anacron[5171]: Normal exit (1 job run)
Dec  9 12:17:01 GALAPAGOS /USR/SBIN/CRON[7125]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  9 12:42:11 GALAPAGOS -- MARK --
Dec  9 12:42:58 GALAPAGOS kernel: [ 4862.313586] usblp0: removed
Dec  9 12:42:58 GALAPAGOS hal_lpadmin: Running hal_lpadmin
Dec  9 12:42:59 GALAPAGOS hal_lpadmin: hal_lpadmin triggered by usblp kernel module
Dec  9 12:42:59 GALAPAGOS hal_lpadmin: Using device ID from HAL database entry
Dec  9 12:42:59 GALAPAGOS hal_lpadmin: remove
Dec  9 12:42:59 GALAPAGOS hal_lpadmin: Found configured printer: hp-LaserJet-3015_fax
Dec  9 12:43:00 GALAPAGOS python: hp-makeuri[7479]: warning: hp-makeuri should not be run as root.
Dec  9 12:43:00 GALAPAGOS python: hp-makeuri[7499]: warning: hp-makeuri should not be run as root.
Dec  9 12:43:00 GALAPAGOS hal_lpadmin: Found configured printer: hp-LaserJet-3015
Dec  9 12:43:00 GALAPAGOS python: hp-makeuri[7509]: warning: hp-makeuri should not be run as root.
Dec  9 13:02:11 GALAPAGOS -- MARK --
Dec  9 13:17:01 GALAPAGOS /USR/SBIN/CRON[7821]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  9 13:42:11 GALAPAGOS -- MARK --
Dec  9 14:02:11 GALAPAGOS -- MARK --
Dec  9 14:17:01 GALAPAGOS /USR/SBIN/CRON[7951]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

---

### Post by northern lights on 2008-12-09
> **merekat said:**
> Dec  6 10:44:46 GALAPAGOS kernel: Inspecting /boot/System.map-2.6.27-9-generic
Dec  6 10:44:47 GALAPAGOS kernel: Cannot find map file.

(Ummm, that seems like a big problem.)

and 

Dec  9 12:43:00 GALAPAGOS python: hp-makeuri[7479]: warning: hp-makeuri should not be run as root. 

(My HP printer I assume, which was automatically installed.)

The latter message is indeed related to your HP printer. Should you also encounter trouble printing, this would be relevant info.
However, neither of the two messages should be related to seemingly random crashes. If, for instance, crashes would occur after issuing a print job, you would have noticed and they'd thus not be random anymore.

It's getting late in mainland Europe and I got class at 7:30 in the morning - I'll check back at breakfast.

logs such as dmesg right after a freeze might just be more helpful - they'd make it easier to isolate the relevant issue.

Feel free to post more logs, but please enclose them in code tags (hash/pound/# button in the message editor). Thank you.

---

### Post by stinger30au on 2008-12-09
start with the basics first

clean the cpu fan with some compressed air. dirt/dust buildup will cause cpu heatup and lockup/freese/reset

scan the hard drive for errors, do this with a dos boot cd

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

also remove the ram and all expansion cards from the computer and clean all contacts with a standard white pencil eraser then put them all back in again

---

### Post by merekat on 2008-12-09
Thanks for the assistance and ongoing dialogue. Not having any trouble with the printer, so not relevant.

What of the kernel not finding the map file? 

I will indeed enclose logs in code tags in the future- my apologies.

Thanks again, and I will check back tomorrow. Cheers.



> **northern lights said:**
> The latter message is indeed related to your HP printer. Should you also encounter trouble printing, this would be relevant info.
However, neither of the two messages should be related to seemingly random crashes. If, for instance, crashes would occur after issuing a print job, you would have noticed and they'd thus not be random anymore.

It's getting late in mainland Europe and I got class at 7:30 in the morning - I'll check back at breakfast.

logs such as dmesg right after a freeze might just be more helpful - they'd make it easier to isolate the relevant issue.

Feel free to post more logs, but please enclose them in code tags (hash/pound/# button in the message editor). Thank you.

---

### Post by merekat on 2008-12-09
Some additional info. I have not had another application crash or freeze since starting this thread, but I did check dmesg anyway. Recent items are as follows:

```
24.802044] hda-intel: Invalid position buffer, using LPIB read method instead.
[   39.558300] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.

```

and 

```
[ 1991.005081] evolution[6110]: segfault at c ip b5f5cb19 sp bfbf9fc0 error 4 in libevolution-calendar.so[b5eed000+10d000]

```

My most recent app crash was Evolution, so clearly the second item is relevant.

---

### Post by merekat on 2008-12-09
Thanks for the reply. Many of these things have already been done, or components are brand spanking new (brand new RAM installed 5 days ago e.g.). Certainly couldn't hurt so I will still try. 

I have not scanned the hard drive... but will. (I in fact ordered a new HD today b/c I don't have a ton of faith in the one installed.)

Why use a DOS boot cd?


> **stinger30au said:**
> start with the basics first

clean the cpu fan with some compressed air. dirt/dust buildup will cause cpu heatup and lockup/freese/reset

scan the hard drive for errors, do this with a dos boot cd

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

also remove the ram and all expansion cards from the computer and clean all contacts with a standard white pencil eraser then put them all back in again

---

### Post by northern lights on 2008-12-10
Stinger's got a valid point - issues might be hardware related also.
 
If you should for instance be trouble by overheating, *sensors* should show you. Run ```
sudo apt-get install lm-sensors
```to install, run ```
sudo sensors-detect
``` once pre-first-run and check with```
sensors
```when the system seems unstable.

---

### Post by merekat on 2008-12-10
Ok, got the sensors app and installed. Sensors detect ended with: 

```
Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `w83627hf' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x290
    Chip `Winbond W83697HF/F/HG Super IO Sensors' (confidence: 9)

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
w83627hf
coretemp
#----cut here----

Do you want to add these lines automatically? (yes/NO)yes
```

As it says above, I choose "yes to enter lines automatically. Then when I try to run sensors it says:

```
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

```

What am I missing? Entering lines automatically doesn't load the drivers? (NOOBIE I am.)

Thanks again for your persistence.

---

