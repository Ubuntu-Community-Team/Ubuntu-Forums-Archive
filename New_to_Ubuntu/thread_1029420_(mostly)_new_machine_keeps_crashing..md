---
title: "(mostly) new machine keeps crashing."
date: 2009-01-03
forum: New to Ubuntu
---

### Post by nicesocks on 2009-01-03
I recently have been acquiring parts to construct a new computer.
New case, powers supply, mobo, cpu, ram; you name it.

After putting in all this new stuff, Ubuntu ran into some issues.  First, it wouldn't recognize the devices and their drivers.  I somehow managed to get that working though I don't really know how.  That frustration gone, there is still one persistent problem:

My computer shuts off inexplicably every twenty or so minutes.  And if I reboot, it barely makes it to logging in.  I'd assume this is a power supply issue, though I feel I have a solid one at 650.  My old machine had much the same components and was only 350.  Any help there?

The other issue is that my new disk drive isn't recognized.  It won't let me mount it.  I figure this might be part of the problem too.  But I wouldn't know how.

I do enjoy Ubuntu, but I'd enjoy it more if it was working right.

---

### Post by amauk on 2009-01-03
random reboots are usually an over-heating problem or a power supply issue

I'd suggest trying with a different PSU first

---

### Post by lswest on 2009-01-03
How about you list the hardware in your computer? (make and model where possible).  That might help someone pinpoint the problem.

---

### Post by Zill on 2009-01-03
nicesocks:  I think we could do with some more information...

1)  Which version of Ubuntu are you using?

2)  Are you running Ubuntu from the Live CD or have you installed it to your HDD?  If it is installed then this disk must be mounted.  Do you have more than one HDD?

3)  Which devices/drivers are you having problems with?

---

### Post by nicesocks on 2009-01-03
Ok, here's more information, extraneous or not:

Power Supply: Antec NeoPower 650 Blue 650W
Mobo: MSI K9A2 Platinum AM2+/AM2
CPU: AMD Phenom 9850 HD985ZXAGHBOX X4
RAM: G.SKILL F2-6400CL5D-4GBPQ 240-Pin DDR2 SDRAM 4G
Video: MSI nVidia9800GT
Network: Netgear, 802.11 wireless
HDD1: I forget it's brand, it's working though and had the original install of Ubuntu.
HDD2: (Not Mounting) Seagate Barracuda 7200.10 ST3250410AS 
Optical Drive: LITE-ON DVD Burner iHAS120-04

Ubuntu version 8.04 (Long Term) running off the smaller, older HDD.

That should be everything.  I wonder if this might be a Firefox issue.  It currently is fluctuating between responding and not-responding.  And the last time it "crashed"  I was closing a Firefox window.

---

### Post by handydan918 on 2009-01-03
> **nicesocks said:**
> Ok, here's more information, extraneous or not:

Power Supply: Antec NeoPower 650 Blue 650W
Mobo: MSI K9A2 Platinum AM2+/AM2
CPU: AMD Phenom 9850 HD985ZXAGHBOX X4
RAM: G.SKILL F2-6400CL5D-4GBPQ 240-Pin DDR2 SDRAM 4G
Video: MSI nVidia9800GT
Network: Netgear, 802.11 wireless
HDD1: I forget it's brand, it's working though and had the original install of Ubuntu.
HDD2: (Not Mounting) Seagate Barracuda 7200.10 ST3250410AS 
Optical Drive: LITE-ON DVD Burner iHAS120-04

Ubuntu version 8.04 (Long Term) running off the smaller, older HDD.

That should be everything.  I wonder if this might be a Firefox issue.  It currently is fluctuating between responding and not-responding.  And the last time it "crashed"  I was closing a Firefox window.

I would suggest posting the output of ```
lspci
``` and ```
lsmod
``` so we can see 
1) What your hardware is recognized as, and 
2) If the right modules are loaded for that hardware.

---

### Post by Zill on 2009-01-03
nicesocks:  Does the PC always reboot after *exactly* the same time period?  If so then I would take a look at the BIOS settings.

If the reboots are variable then I would think that the hardware is more likely to blame.  I would check the RAM as well as the PSU.

Re the (non!) mounting of HDD2, please confirm that this has already been formatted with a Linux filesystem such as Ext3.  If not then this needs to be done first. :-)

---

### Post by nicesocks on 2009-01-03
@handydan
I'm at work right now.  I'll pop on at home and post the results.  Thanks for the idea.

@Zill
1. The time periods appear to be random.  This afternoon it was about thirty minutes.  Sometimes it's five.  After it happens it permits less and less time each successive reboot; e.g. if it crashes after twenty minutes, i reboot, it crashes in five, i reboot it doesn't even load before it turns off.

2. I'll check the RAM when I get home.
I am not sure about the PSU, I've tried removing devices and booting up to the same error.  And I worry that I might be passed my window to return the PSU... >_<  That, and I've got a habit of removing packaging as soon as possible.  /sigh

3. The HDD2 has NOT been formatted to Ubuntu, which I imagine is the problem.  I tried downloading 8.11 to install that, but the disk presumes I want to install from Windows.  I think I'll try to download the 64bit version though, as my AMD64 should prefer that, right?

Apparently I still get confused about obvious things.  ~_^  'Specially when so much isn't working right.

---

### Post by nicesocks on 2009-01-03
```
lspci
```
```
00:00.0 Host bridge: ATI Technologies Inc RD790 Northbridge only dual slot PCI-e_GFX and HT3 K8 part
00:05.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port B)
00:09.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port E)
00:0b.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx1 port A)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
02:00.0 RAID bus controller: Promise Technology, Inc. Unknown device 3f20
03:00.0 VGA compatible controller: nVidia Corporation Unknown device 0605 (rev a2)
04:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
04:02.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
```
~~~
```
lsmod
```
```
Module                  Size  Used by
af_packet              23812  4 
nls_cp437               6656  1 
isofs                  36388  1 
udf                    88612  0 
ipv6                  267780  14 
binfmt_misc            12808  1 
video                  19856  0 
output                  4736  1 video
dock                   11280  0 
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
aes_i586               33536  0 
dm_crypt               15364  0 
dm_mod                 62660  1 dm_crypt
ac                      6916  0 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
snd_hda_intel         344856  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wlan_scan_sta          14720  1 
ath_rate_sample        14336  1 
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia               7825536  34 
ath_pci               101024  0 
ati_agp                 9996  0 
psmouse                40336  0 
wlan                  207728  4 wlan_scan_sta,ath_rate_sample,ath_pci
serio_raw               7940  0 
i2c_piix4               9612  0 
wmi_acer                9644  0 
button                  9232  0 
soundcore               8800  1 snd
i2c_core               24832  2 nvidia,i2c_piix4
shpchp                 34452  0 
ath_hal               192592  3 ath_rate_sample,ath_pci
agpgart                34760  2 nvidia,ati_agp
pci_hotplug            30880  1 shpchp
evdev                  13056  3 
pcspkr                  4224  0 
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
atiixp                  5648  0 [permanent]
sd_mod                 30720  3 
ide_core              113996  1 atiixp
ata_generic             8324  0 
pata_atiixp             8960  2 
floppy                 59588  0 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
r8169                  33156  0 
ehci_hcd               37900  0 
pata_acpi               8320  0 
ahci                   28548  1 
ohci_hcd               26640  0 
libata                159344  4 ata_generic,pata_atiixp,pata_acpi,ahci
usbcore               146412  3 ehci_hcd,ohci_hcd
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
thermal                16796  0 
processor              37384  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  1 
```
~~~
Thanks for all the help.  I'll check this again in the morning.

---

### Post by -kg- on 2009-01-03
> My computer shuts off inexplicably every twenty or so minutes. And if I reboot, it barely makes it to logging in. I'd assume this is a power supply issue, though I feel I have a solid one at 650. My old machine had much the same components and was only 350.

> 1. The time periods appear to be random. This afternoon it was about thirty minutes. Sometimes it's five. After it happens it permits less and less time each successive reboot; e.g. if it crashes after twenty minutes, i reboot, it crashes in five, i reboot it doesn't even load before it turns off.

2. I'll check the RAM when I get home.
I am not sure about the PSU, I've tried removing devices and booting up to the same error.

Among other things, I'm a consummate hardware man and former Electronics Technician (Ground Radio Communication Equipment Repair in the Air Force).  I have basically built my last three desktops, the last (and current) one from the ground up much the same as you have.

I'm sorry, but it sounds to me like a power supply problem...specifically, something heating up in the power supply to the point of auto-shutdown.  Of course, each time you try to reboot, the unit is already hot and takes less time to heat back up to that point.

It sounds to me like you have a good power supply (I have an Antec in mine as well) and it sounds like the wattage is more than enough to run what you have.  That doesn't mean that you can't get a brand new lemon, but it also doesn't necessarily mean that what you have *IS* a lemon, either.

First, if you have access to your former 350 watt supply, try swapping them out (if you can) and trying it.  If you have a lot of high-power peripherals, just don't use them.  If you can successfully boot and maintain the boot beyond the point that you experience now, then it's likely an issue with the power supply itself.

But if you experience the same problem with the old PS, there is something in your system that is drawing *far more power* than it is supposed to.

Are you *absolutely sure* that everything is connected as it is supposed to be?  Are you sure that you have a sufficient CPU cooling fan (think I don't know about AMD processors? :P )?  Does your graphics card require it's own power connection to the power supply?

If you continue to experience these problems, I would boot with the computer cover off and let it run until it experiences shutdown.  While the computer is booted up and running with the cover off, watch the insides.  Do you hear anything unusual (like popping and cracking due to something heating up, or an unusual whirring or grinding noise due to a fan or a hard drive going out...and thinking about fans, are the fans all running properly)?  See anything unusual (like maybe a thin stream of smoke coming from somewhere, or "heat distortion" like you sometimes see rising from a hot pavement in the summer)?

If you see or hear none of the above, then (after unplugging the computer, of course) physically feel around for hot spots...like, is the CPU cooler excessively hot?  How about the extra power wire to the Graphics card (if there is one)?  Perhaps one of the hard drives?  Is the power supply itself excessively hot?  One (or more) of the wires leading from it (and if so, where does that wire or wires go)?

You didn't mention what type of a case you have.  It may be something as simple as insufficient airflow in the case.  You might try running the computer with the cover off and never experience the shutdown.  This isn't a problem with my computer...my case holds 4 case fans, I have two fans in my PS, and I have a slot fan right over my video card (sounds like a 747 taking off! :P ).

Sometimes I like the old style of power supplies better.  In those, you would have a fuse blow and then you would know that either the power supply was bad or something powered by the power supply was drawing too much power.

You said that you removed some peripherals:

> I am not sure about the PSU, I've tried removing devices and booting up to the same error.

Which devices did you remove and, even more importantly, which ones did you *not* remove?  As you said, your last computer had basically the same components, but was powered with a 350 Watt supply.  Are they the *same* components (i.e., cannibalized from the old computer and used in the new?) or are they similar new components?

Is one (or both) of your hard drives from the old computer?  The video card (some video cards with a separate power connection draw quite a bit of power themselves. If it goes, then it starts drawing *significantly* more power)?

The RAM *might* be it, but your original statement...

> My computer **shuts off** inexplicably every twenty or so minutes. <emphasis mine, of course>

tells me that it's unlikely that a RAM problem would be causing it.  RAM problems usually cause instability, freezing, or crashing (in Windows, the dreaded BSOD) rather than completely shutting the computer off.

I'll be following this thread.  This is one of my "areas," and I'm extremely interested in the outcome (especially, to find what the actual causative factor was).

<edit>  As for your 2nd hard drive problem:

> Re the (non!) mounting of HDD2, please confirm that this has already been formatted with a Linux filesystem such as Ext3. If not then this needs to be done first.

> The HDD2 has NOT been formatted to Ubuntu, which I imagine is the problem. I tried downloading 8.11 to install that, but the disk presumes I want to install from Windows.

Well, that's not *quite* the problem, but...

If you have a file system formatted on your 2nd hard drive at all, it would likely be mountable, or at least viewable.  Since you say it's a new hard drive, it's very likely that there isn't any partition on it at all.

You could probably do with a good crash course on partitioning, and I've got just the thing for you.  This site has very good Documentation pages, and as far as straight partitioning, I'll point you to:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

This page and it's sub-pages will give you a real good idea what you're dealing with and what to do in that department (besides being a shameless plug...I recently re-wrote this page and it's sub-pages ;) ).  You can check out the entire Community Documentation project at:

[https://help.ubuntu.com/community/]("https://help.ubuntu.com/community/").

Just about everything is covered in this documentation and:

[The Ubuntu Official Documentation]("https://help.ubuntu.com/")

We all will get you up and running yet! :D

---

### Post by nicesocks on 2009-01-04
I've been watching the time it takes before it shuts down.  I've been going almost fourty minutes this time.  Who knows!?!

@kg
Wow, Thanks!  Looks like you will be a lot of help!  Let's see if I can get everything addressed:

My old 350 is partly why I'm doing this upgrade.  It popped, loudly and with smoke and all, in my old case.  I unplugged everything, and my intent was to cannibalize until I had everything new again.

My case is a nice, new and large Antec P180.  It has three fans of it's own, and the air flow keeps things cool.  Though I should check that, I'll open it back up tomorrow.  Can't say I've noticed high heat.

I got the new PSU first.  I chose it because it was modular, and I could basically add the amount of cords and cables I need.  This is the second machine I've built, so I have a sense of what I'm doing, and was expecting some hardships...  But I know this isn't my area of expertise.  Want a garden?  I can do that.  Computers; well I know more than enough not to fail.  In fact, I know more than enough to use Ubuntu,  ~_^
But yeah, I chose that to keep the amount of random wires to a minimum.

I haven't noticed any smoke or odor, though sometimes it sounds like a fan isn't as happy as it should be.  Haven't figured out which one that is...
It could be the PSU's fan itself.  In which case maybe I need to see if I can still return that unit...  >_<  A headache I don't really want to deal with.  Hah hah.

The video card has a power wire.  It's a six pronged one.  The downside; I can't really take that device out, as the mobo doesn't have it's own video connection.  A mistake on my part, but the mobo has everything else I'd ever want, and it was a good price.
Specifically: I took out the wireless card (from the old system), the HHD2 (which wasn't running anyway) and the DVD (which seemed irrelevant to run the machine).  I figured that would at least take some of the power down.  But it still happened anyway.
I left the HDD1 (from the old system) the video card (for the aforementioned reasons) and of course the mobo with it's CPU and RAM.  I also left all the fans, didn't consider taking them out.

I'll work on the HDD2 tomorrow.  I fear this machine will shut off before I finish posting.  So I'll see what you all have to say then.  Too bad I'll be at work, and won't be able to update you guys/gals.  Thanks again for the help!
I know that enough thinking will break through this.

---

### Post by lswest on 2009-01-04
About the unhappy-sounding fan, I would check to see if the PSU unit's fan (if the whole unit is hanging upside down) might be hitting a loose wire in the PSU?  If that's the case, you can probably fix it by sticking the loose cable in the heatsink of the PSU (of course, remove the PSU from the computer first, and allow any excess charge to dissipate before sticking anything in there to move the cable).  Otherwise, it might mean the fans themselves aren't getting enough power.  What would be useful to do would be to go through the components' information and tally up the wattage required in total (including the fans on the case).  See if it might be too much?

---

### Post by theozzlives on 2009-01-04
> **nicesocks said:**
> I recently have been acquiring parts to construct a new computer.
New case, powers supply, mobo, cpu, ram; you name it.

After putting in all this new stuff, Ubuntu ran into some issues.  First, it wouldn't recognize the devices and their drivers.  I somehow managed to get that working though I don't really know how.  That frustration gone, there is still one persistent problem:

My computer shuts off inexplicably every twenty or so minutes.  And if I reboot, it barely makes it to logging in.  I'd assume this is a power supply issue, though I feel I have a solid one at 650.  My old machine had much the same components and was only 350.  Any help there?

The other issue is that my new disk drive isn't recognized.  It won't let me mount it.  I figure this might be part of the problem too.  But I wouldn't know how.

I do enjoy Ubuntu, but I'd enjoy it more if it was working right.

Could be PS, RAM, mobo, overheating... should have a tech look at it

---

### Post by Zill on 2009-01-04
nicesocks:  I have a similar background to -kg- and fully agree with his comments - there is lots of good advice there. :-)

You said the last PC "popped, loudly and with smoke".  Did you identify *exactly* which components did this?  Hopefully, they did not make it into the new PC!

The reboots do seem to be heat-related so you need to establish if this is due to a fault or a lack of cooling air.  Trying the old PSU, as suggested, would be a useful test.

Are you intending to install the Ubuntu OS on HDD1, HDD2 or both?  Usually, only one HDD has the OS installed, with any other HDDs being used purely for data.

I didn't quite understand your comment that "I tried downloading 8.11 to install that, but the disk presumes I want to install from Windows."  Unless you are using WUBI, the standard Ubuntu install does *not* "install from Windows".  It can be installed alongside an existing Windows installation, or can be installed (preferably!) as the sole operating system but it certainly does not *need* Windows!  [This link]("https://help.ubuntu.com/community/GraphicalInstall") may help.

If you intend to keep your OS on HDD1 with your data on HDD2 then you do not need to install Ubuntu on HDD2.  You just need to partition and format it for data.  The partitioning link provided by -kg- explains how to do this.

---

### Post by theozzlives on 2009-01-04
WOW, smoke! That's not good, did you use CPU grease? Try to swap your RAM from the old box (if it's compatible), if not run memtest. You could be hitting a bad chip in your RAM.

---

### Post by nicesocks on 2009-01-04
Thank you everyone!  It's fantastic to me that the Ubuntu community is not just active, but helpful.  Far better than calling up tech support and getting more problems than corrections...
I appreciate all this help, but it seems I'm confusing people.  Probably my fault, I don't think in a linear fashion and my tenses can (and will) change on a whim.  Let me line up events so you know what's working and what isn't.  As well as which parts are from the [COLOR="Gray"]old machine[/COLOR] and what happened to it.  And which parts are from the [COLOR="Green"]new machine[/COLOR] that keeps crashing.

I had a machine that was getting close to ten years old.  We will be referring to this as the "[COLOR="Gray"]old machine.[/COLOR]"  In fact, the case was ten years old, remember back when computers were beige?  It melted down once, about five years ago, a hot summer day and one of the fans got stuck; not a pretty sight.  I replaced most of the parts on that and got it up and running again.
I was still using windows at that time.

About a year ago now, if not a little longer (year and a half?), I finally decided to switch to Ubuntu.  I was done with windows.  Too many viruses, too much corrosion, too much of a headache with all these remnant parts from such an [COLOR="Gray"]old machine[/COLOR].  Even reformatted it three times... Still a nuisance.

I've been happy since the switch.  I've even impressed my friends with a rotating desktop, and the idea of free software.  Too bad most of them are mac users and wouldn't switch regardless.

**So, let's catch up to the recent.**
I was intending to upgrade my computer this year.  It was [COLOR="Gray"]old[/COLOR], if we recall.
I had plans to purchase a new case; since the case and the mouse were the two oldest parts of my [COLOR="Grey"]old machine[/COLOR].  The [COLOR="Green"]new case[/COLOR] arrived and was everything I'd hoped for.  It was huge, with plenty of room inside.  I put on some jazz and got surgical.  I had moved my [COLOR="Grey"]old machine[/COLOR] into my [COLOR="Green"]new machine[/COLOR]'s case.

I fired it up and all was well.  But...  a few days after getting it all set up it made an audible "pop!"  Like something tripped or snapped, but in a very inorganic way.  I unplugged everything from the back of the machine, and opened it up.  The [COLOR="Gray"]old 350 PSU[/COLOR] had worn out.  I don't think it was up to the task of [COLOR="Green"]three new fans[/COLOR] keeping the cool, and boy did it.
[COLOR="Red"]*This was the PSU that smoked and smelled metallic and singed.*[/COLOR]  It's dead, done, gone, kaput.
So my [COLOR="Green"]new machine[/COLOR] was on hiatus.

I wasn't sure what was still good, or what wasn't.  But I first ordered a [COLOR="Green"]new PSU[/COLOR].  This was about a month and a half ago; in November.  This is the 650 PSU that might be a lemon.

I placed it in the [COLOR="Green"]new case[/COLOR] and when I went to hook it up to the [COLOR="Gray"]old mobo[/COLOR], it wanted more pins...  I now know that this part is modular, so when I get home I'll rebuild the [COLOR="Gray"]old machine[/COLOR] and see if this [COLOR="Green"]new PSU[/COLOR] still gives me grief there.

In any case, I looked at my savings and went for it.  I got everything new.  I mean, I was intending to get a [COLOR="Green"]new machine[/COLOR], right?
So I did: [COLOR="Green"]new mobo[/COLOR], [COLOR="Green"]new CPU[/COLOR], [COLOR="Green"]new RAM[/COLOR], [COLOR="Green"]new DVD[/COLOR], and a [COLOR="Green"]new HDD[/COLOR].

Once all of these arrived I put the [COLOR="Green"]new machine[/COLOR] together.  Mind you, this [COLOR="Green"]650 PSU[/COLOR] hadn't given me grief yet, because I hadn't hooked it up to anything at this point.

Well, I built everything and noticed that I overlooked one component to the [COLOR="Green"]mobo[/COLOR]...  No place to plug in my monitor.  Hah hah, I made sure everything else was ok, but apparently not that.
And my [COLOR="Gray"]old video card[/COLOR] was AGP, I don't think they even make that kind of connection any more.  So I ordered a [COLOR="Green"]new video card[/COLOR].  Thinking, what the ham and goose, why not?
That took it's sweet time.  Never order anything over Chrismahaunnakwanzika.  So, I sat down over this last week and hashed things out.
Mind you, this is the first time this [COLOR="Green"]new machine's[/COLOR] really been set up.

I presumed there would be things I'd have to deal with.  No way would I have the drivers for the [COLOR="Green"]new video card[/COLOR].  I wasn't expecting that it wouldn't recognize the [COLOR="Gray"]old network card[/COLOR].

I should take a moment to mention this:  The only old components in my new machine are:  [COLOR="Gray"]HDD1[/COLOR] and the [COLOR="Gray"]network card[/COLOR].  The peripherals; monitor, speakers, keyboard and mouse are still from the old.

So, after frustrations of getting the machine to recognize it's parts, in addition to it randomly crashing.  I'm finally here:

**If you read nothing else above, read this:**
My [COLOR="Green"]new machine[/COLOR] works with the caveat that it shuts off randomly.  I was watching the time last night, it stayed up and running for an hour and sixteen minutes!  A record!
It recognizes all it's components, even knows that the HDD2 is connected, just not formatted.  And thanks for the info regarding the HDD2 (by the way); I'll check that out once I figure out this power issue.  If it's due to a busted PSU, then I'll look to get a new one and this frustration will be past. 

@theozzlives
I'll run memtest when I get home.

---

### Post by -kg- on 2009-01-04
> The only old components in my new machine are: HDD1 and the network card.

I have a question regarding the above.  How old is HDD1?  Is it 10 years old?  10 years is a *long time* for a hard drive!  I've never had one that lasted that long.

Even if it never "ran" (i.e., you used it for storage and didn't access it much), they still spin up and down, and the mechanical parts age.  Lubricants eventually dry up over time.

Though the last hard drive that I had to replace was run heavily, with the OS installed to it and all, it was only 6 or 7 years old.  My symptoms of impending failure was what I mentioned previously; I would boot up and over a short period of time the response would slow down and eventually freeze.  The hard drive was making strange whirring noises and all.

I bought a new hard drive (a nice 400 GB Seagate) and cloned the partitions off the old and onto the new.  I'm still using it (and the old 160 GB drive, which I used for experimentation...I created the partitions and screenshots for the "How To Partition" page with it...and which I expect to go next) and have since installed a SATA TB drive and an external WD TB drive.

Anyway, I would look long and hard at that old HD, *especially* if it is anywhere *near* 10 years old.  You might want to consider cloning your installation off of it and on to the newer one or, if you don't have much installed on the old one, do a fresh install on the new one.

As matter of fact, that would be a good and easy to perform experiment.  You say HDD2 is not yet formatted...completely disconnect HDD1...ribbon and power connector...and reconfigure HDD2 as master (if these drives are IDE and not SATA, of course), then pop in your Ubuntu Live CD and install Ubuntu on the second hard drive, using the "Guided-Whole Disk" installation method.

See what happens with the new install.  If it runs and doesn't shut down any more, then you've found what was causing the problem.  If not, then you have more troubleshooting to do, and when it comes time, you can just wipe HDD2 and re-partition it the way you like, or leave it as is and clone the OS from the old drive to the new, just in case.

For cloning, you can use the terminal and the "dd" command, but I like the [Clonzilla Live CD]("http://clonezilla.org/") for cloning and backing up.  A nice GUI environment, and automatically handles a number of backup/cloning operations and situations.

---

### Post by nicesocks on 2009-01-04
@kg
The HDD1, who I affectionately call "Eusmilus," is about three or four years old.  It replaced a prior HDD "Link" who was a mere 30GB or so.  That one died then, a slow rattle ~tick-tick-tick~ that suggested it's impending doom.  That's when I got Eusmilus.

It would be sad to see it go.  I need to stop naming my parts.

The prior was drive the second HDD to go into that old case.  The first one was a pathetic 10GB (which I was amazed by at the time).  It survived the summer meltdown, but didn't last much longer after that, a slave to next.  
What's really fascinating is that my cell phone has a removable MicroSD that's 8GB; and is the size of my fingernail...  
Oh times, they are a-changing.

---

### Post by -kg- on 2009-01-05
> It would be sad to see it go. I need to stop naming my parts.

Every time I say to myself, "Now I've seen it all!"...

I've known many who named their computers, but their computer parts?!

[IMG]http://img.photobucket.com/albums/v634/kg5uc/lmao4.gif[/IMG]

Anyway, that would be my suggestion.  Take the power connection and ribbon cable off of "Eusmilus", change the new one (any name for that one? :D ) to master drive, and install Ubuntu on it.  Then see if you have the same problem.

Hey, if you still have the problem, then you won't have to do Eusmilus in!  It will be one of the other guys.

---

### Post by lswest on 2009-01-05
This is slightly off-topic, but I do call my hard drive Hyperion after the titan that is the son of Gaia and Uranus (greek mythology)..  I haven't named any other parts though :P

Slightly more on-topic:

I would suggest doing what -KG- has outlined, and if possible I would also try to borrow a PSU off a friend for a short time period to test if it is the PSU, or else take it to a computer shop and see if they'll let you borrow a PSU for an hour (in the shop of course) to see if that's the cause of the hang-ups.

---

### Post by quicknick_26 on 2009-01-15
If you haven't already done it, I would highly recommend a thorough inspection of every circuit board in your computer in some good light. My computer made a scary popping sound one day. Ubuntu continued to run just fine after the noise. I immediately shut everything down. I know very little about hardware, but just by taking everything apart and looking at it all I discovered a small capacitor (or something that looked like one) had obviously been blown on my video card. A quick trip to Best Buy had me up and running again.

---

### Post by nicesocks on 2009-01-18
ok, here's an update:  
i haven't really been using the machine, and it does indeed seem like the new 650 PSU is the main culprit.  the other day i fired it up and it was indeed making an odd "whirring" sound.  i opened the case to realize that the sound came from the new PSU unit.

so, i called the online vendor where i got it from.  bad news: i had waited too long (one week too long) *and* tossed the original packing.  good news: they gave me a number to call antec support.

called antec, and the guy told me to fill stuff out and send the PSU to them.  that works, sure is better than buying another new PSU.

thank you all so much for the help!  i don't think i would have supposed it was the new PSU that was causing the trouble without this thread.  and i think i learned a lot more about my machine here.  i really do appreciate it!

---

### Post by nicesocks on 2009-02-04
final update:

antec got me a new PSU.  very nice.  i'm utterly pleased with that company at this point.

so i plug it in to my machine, make sure everything is plugged in right, fire it up.  and...  it powers down in eight minutes.  >_<

so i think, maybe if i have an ubuntu disc in the drive that might help me iron out some errors.  go to download it on my roommate's computer.  she comes home twenty minutes into the download and flips out.  i shouldn't be using her machine, too many people do, it's less than a year old and it hangs up...  all kinds of irrational ignorant-to-computers nonsense.  i start asking her what hangs up, why "the spinning death wheel" of course.  >_<  personally, i think she should get to upgrading her mac, reformatting it (do they even call it that with macs?) or take it to a frickin' apple store.  regardless, with out that option i had to try something else.  perhaps this was a blessing?

i went back to my computer, opened the case, pulled out the manuals and learned two things:
one.  i never plugged a power connection from my PSU to a component on the MB that was some sort of fan regulator.  not the CPU fan itself, just some other four pronged plug.  that seemed to do the trick, the machine ran for two and a half hours before shutting down.  /sigh.
so i called my brother-in-law who was a comp.sci major and works for google.  he suggested things, and it occurred to him and i, that my RAM wasn't actually loaded right.  the MB was color coded, but the way the manual was written suggested i load my RAM on one green, one orange.  i though this was odd when i was building it, but i did it that way.  now they are both on the greens and i have no issues.

i think we can chalk this up as "solved."  man, i learned a lot in this process.  mostly, that it's the little things you can over look that cause the greater issue...

thanks again to all!

---

