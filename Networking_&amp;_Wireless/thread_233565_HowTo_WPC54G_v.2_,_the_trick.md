---
title: "HowTo: WPC54G v.2 , the trick"
date: 2006-08-10
forum: Networking &amp; Wireless
---

### Post by Kobalt on 2006-08-10
This trick is for **Edgy (Ubuntu 6.10) only**.

The **open source acx drivers do not support WPA encryption**. If you want that, you should use the windows drivers + ndiswrapper. In order to do this, follow [dmizer's guide]("http://ubuntuforums.org/showthread.php?t=324148").

Hello everyone,

I've been using my Linksys WPC54G v.2 WiFi (PCMCIA) card for a while now and I thought some people using the same card, or willing to get one that works great, would be interested in this HowTo. 
The WPC54G v.2 card is based on an acx111 chipset. Unfortunately the version of acx driver provided by Dapper is a new one but is not working.

At first, you need to check that your card is built on the right chip so check it with : 
```
lspci
```
If you are given something close to this bellow you can go on (otherwise this trick won't work for you) : 
> 0000:03:00.0 Network controller: **Texas Instruments ACX 111** 54Mbps Wireless Interface


Ok now, here is the trick. 
1. Type this command line : 
```
sudo ln -s -f /lib/firmware/`(uname -r)`/acx/1.2.1.34/tiacx111c16 /lib/firmware/`(uname -r)`/acx/default/tiacx111c16
```

2. Then : 
```
sudo modprobe acx
```

3. Plug out and then in your card.

Now you should have your "Power" led on and the "Link" one blinking, it works ! Otherwise, you can try this to activate it : 

4. ```
sudo ifdown eth0
```
5. ```
sudo ifup wlan0
```

**IMPORTANT : You will need to do the steps 1, 2 and 3 at every new update of the kernel.**

And now you can enjoy your working WiFi card on Ubuntu, without using Ndiswrapper. 
Isn't it great ? 

Cheers ! :rolleyes:

---

### Post by dmizer on 2006-08-11
this works for me.

but i get this in dmesg:
```
[4294843.893000] acx: Loaded combined PCI/USB driver, firmware_ver=default
[4294843.893000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[4294843.894000] PCI: Enabling device 0000:06:00.0 (0000 -> 0002)
[4294843.895000] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294843.895000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[4294843.895000] acx: found ACX111-based wireless network card at 0000:06:00.0, irq:11, phymem1:0x26020000, phymem2:0x26000000, mem1:0xc8adc000, mem1_size:8192, mem2:0xc8b80000, mem2_size:131072
[4294844.940000] acx: form factor 0x01 ((mini-)PCI / CardBus), radio type 0x16 (Radia), EEPROM version 0x05, uploaded firmware 'Rev 1.2.1.34' (0x03010101)
[4294844.941000] acx v0.3.21: net device wlan0, driver compiled against wireless extensions 19 and Linux 2.6.15-23-386
[4294844.943000] usbcore: registered new driver acx_usb
[4294845.021000] wlan0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
```

---

### Post by Kobalt on 2006-08-12
This is normal because we actually use an older version of acx driver in the kernel, while there's a newer avaliable but not working... As long as your card is working, how is that anoying ? :) 

Cheers ! :rolleyes:

---

### Post by dmizer on 2006-08-13
works for me.  only down side i can see is that network manager isn't saving my wireless settings.  so i have to go in and configure the card every restart.  still, it's better than what i was doing with ndiswrapper.

could be because i'm still set up to load ndiswrapper by default though.  i'll get rid of that tonight and see if that makes a difference.

edit:
it did.  it now loads up on boot with 0 configuration.

btw, the ifdown wlan0 and ifup wlan0 are not needed if you use network manager to configure your network settings instead.

---

### Post by holycoww74 on 2006-08-20
thanks for the tip man, this worked just right for me

---

### Post by DrMoxie on 2006-08-22
Perfect!  The only thing I needed to do different was reboot (go figure).  Thanks! :KS

---

### Post by chester on 2006-08-23
THis doesn't seem to be working for me. Will trying indiswrapper (sp) work instead? the power light comes on the adapter but i am not getting any packets shipped back and forth. any ideas?

---

### Post by Kobalt on 2006-08-23
Did you make sure you have the right chip : WPC54G V.2 ? 
Did you enter your ESSID and WEP key without mistakes ? 

Cheers !

---

### Post by Roastbill on 2006-08-23
this worked for me last night- then when i powered back up tonight- nothing!

---

### Post by tardisx on 2006-08-24
Excellent! Works great on a Mac G3 powerbook, where of course ndiswrapper is not an option.

Much appreciated!

---

### Post by CoreyE on 2006-09-03
hmm, i cant get it working. granted ive only been using linux 1 day and am probably typing somethin wrong... but im getting:
ln: invalid option -- r

EDIT: ok nvm, got through that. But now im getting: No Such File Or Directory, and its still not working :(

---

### Post by Kobalt on 2006-09-04
Hello,

When typing this command : 
```
sudo ln -s -f /lib/firmware/`(uname -r)`/acx/1.2.1.34/tiacx111c16 /lib/firmware/`(uname -r)`/acx/default/tiacx111c16
```
You need to replace 'uname -r)' by you system's kernel version. To do so, type this in command line : 
```
uname -r
```
You will be given figures such as : 2.6.15-26-386
Replace '(uname -r)' by this figures, so that the first command looks like : 
```
sudo ln -s -f /lib/firmware/2.6.15-26-386/acx/1.2.1.34/tiacx111c16 /lib/firmware/2.6.15-26-386/acx/default/tiacx111c16
```

Then it should work !

Cheerios !

---

### Post by nobios on 2006-09-20
Confirmed working with

```
0000:05:06.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
```

---

### Post by Melcar on 2006-09-20
I'm using the exact same card and I can't get it to work.  This method is actually the one that "works" best for me.  I can scan networks but for some reason it does not connect.

---

### Post by Kobalt on 2006-09-23
If you can scan the networks then it means your card is recognised and working. Check your ESSID and wep key, there may be a mistake here...

---

### Post by valleyman7 on 2006-10-01
After many many attempts I finally got Ubuntu 6.06 LTS to install, now if I can get the wireless card to work I believe the battle to be won. Can someone tell me if there is something I need to do special to find where the network manager resides. I have looked at  ever possible place I can and I cannot seem to locate it. I am hoping these instructions will get me up and running. I hope it was ok to add here.

Lyle Hensley
Enjoying Every Breath
Retired  US Army
1957 - 1978:KS 


:confused:

---

### Post by NetworkGuy on 2006-10-01
Network Manager needs to be installed via Synaptic or from apt-get if you like the terminal better.

---

### Post by valleyman7 on 2006-10-01
Dumb ? number 2 does wireless need to be working to install Network Manager. As you can tell I am a OLD newbie.:)  

Lyle Hensley
Enjoying Every Breath
Retired  US Army
1957 - 1978:KS

---

### Post by Kobalt on 2006-10-02
No, you don't need internet to install the Network Manager. 
I suppose your WiFi card is a WPC54G v.2 (because you're posting into this thread) ? If so, once you plug it, you should see an icon appear in you upper right corner of the screen, an icon representing two screens and a green jauge : this is your place to configure everything you need. Right click on it and select Properties. From there you'll be able to configure your ESSID, WEP key, etc. You can do it before or after the little trick explained here, it will be saved once and for all.

Cheerio !

---

### Post by valleyman7 on 2006-10-03
I tried to run the commands provided here and I ran most with some sucess. I was able to get the kernel version. but some where not sure where as I was getting pretty tired one of the codes I ran came up with permission denied. I gave up for the night. I will make it work. As for the icons in the upper right coner I did not see that at any time. even after I had tried the plug in and out of the card. I will try again when I receive the new Ausu card I ordered from Newegg. Thank to all who have tried to get me up and running. I will not give up. I wish I could get the internet to work this easy I am running Ubuntu Lived CD on my Dell 9300. I did nothing and I am connected, why does it have to be so difficult to get a wireless card to work. Also yes I have the WOC54G v.2, Thanks again for your help Kolbalt. Bed time for this old man. :KS

---

### Post by Coronet on 2006-10-07
Here is a real newstarter!
Just managed to get my Dapper Drake installed, but my Wireless Linksys wireless chard does not work.
It is the same WPC54G as mentioned in this thread.
My problem is I was lost in the first line.

Where do you write these "Code Commands"

Also I do not get the mentioned icon in the top right corner of the screen. I am sure that is because I cannot activate my chard, but that is what I am trying to fix!!

Thanks Alot.

---

### Post by eddyh on 2006-10-12
You enter those commands in a Terminal window.  Select Applications/Accessories/Terminal.

ed

BTW:  Has anyone figured out how to keep from having to run these commands each and every time you reboot/powerup?  Gives my windoz friends cause for comment.

---

### Post by valleyman7 on 2006-10-12
I gave up on the linksys card and bought the recommended Ausu card and as stated worked right out of the box. Now to get my sound working and then to the next challenge. Thanks to all who responded.

---

### Post by Coronet on 2006-10-13
HI Again.

Tryed in the Terminal as described.
The repply I got was:
"bash: Ispci: Command not found"

I have a feeling that I have done something wrong!

---

### Post by dmizer on 2006-10-14
@Coronet
try a different shell (you should have several to choose from).

i find it very strange that you can't run that command. so, if you can't find another shell, or you have the same problem in a different shell, try this:
```
whereis lspci
```
and paste the output here.

@eddyh
> **eddyh said:**
> BTW:  Has anyone figured out how to keep from having to run these commands each and every time you reboot/powerup?  Gives my windoz friends cause for comment.
you sould only need to enter those commands once.  it should work without intervention on your part unless you do a kernel update.

---

### Post by eddyh on 2006-10-14
Well, before I did a kernal update I had to re-enter the commands each time and after a kernal update, same thing (after I changed the kernal ver.).  For some reason it's not saving the config change.  I'm running an installed version, not live off the DVD.  It's not a big deal since Terminal saves the entered commands and I also keep a text file handy to copy off if necessary.  Spelling is very important (obviously) - spelled firmware, firmaware and the power light on the card went out and would not come back on until I fixed it.  Running the logfile in background is great since it tells me exactly what's going on with the config as it's happening.

eddy

---

### Post by dmizer on 2006-10-15
there is no way to avoid changing the firmware after a kernel update.

if you watch for them (kernel updates), just change your firmware for the new kernel before you reboot (as you noted ... just make sure everything is typed correctly), and you shouldn't have to worry about it again until the next kernel update.

you should only have to change your firmware once every time you do a kernel update.  the reason for this is that each time the kernel comes out, it's packaged with the newer, and therefore broken, firmware (linux-restricted-modules).  there's really no way to avoid this unless you roll your own kernel.

btw: most of your windows friends who "give comment" will recall having similar problems during the change between xp sp1 and sp2.  it happens more frequently with linux because linux does updates more frequently than windows.  so maybe they don't have to update their drivers and firmware so often, but that's precicely why windows is so full of holes (they're never patched).

---

### Post by eddyh on 2006-10-15
dmizer:

Well I'm confused.  Before my kernal upgade I had to reload the firmware each time.  After my kernal upgrade, only had to load it once.  Possible I missed something during the first times, who knows, but all is well in linux land now.  Thanks for the help.

ed

---

### Post by dmizer on 2006-10-16
perhaps you tried to update the firmware before "linux-restricted-modules" had been installed?  the change will not work until the restricted modules for the new kernel are installed.

---

### Post by echomikeromeo on 2006-10-31
I typed the code as suggested, and now my power light is on and my link light is flashing, but I still can't seem to connect to the internet. When I tried the "ifdown eth0" and "ifup wlan0" commands, I got the following error message:

"iup: failed to open statefile /var/run/network/ifstate: Permission denied"

Can anyone help me fix this?

---

### Post by eddyh on 2006-10-31
I got the same error's, I'm guessing they are due to your user account not really being a "root" account (Ubuntu doesn't configure you that way).  Just click on the double monitor icons in the top bar to get to the connection properties window.  Make sure that your wlan0 is selected.  Check out the properties for it, select your vlan id, etc. and you should be good to go.  Hope that helps.

ed

---

### Post by echomikeromeo on 2006-10-31
I don't see a double monitor icon. But if I go into the network settings window, as far as I can see all the settings are correct.

---

### Post by echomikeromeo on 2006-10-31
I've been doing some reading - would it be possible that prefacing the "ifdown" and "ifup" commands with sudo would prevent that error?

---

### Post by dmizer on 2006-11-03
> **echomikeromeo said:**
> I've been doing some reading - would it be possible that prefacing the "ifdown" and "ifup" commands with sudo would prevent that error?
sorry it took me so long to get around to this, i have neglected to mark this thread as watched.

yes ... by doing sudo ifup/down wlan0, you are temporarily assigning root rights to the command.  but if you are rebooting and your network isn't connecting, there's probably something else wrong.

what is the output of:
```
uname -r
```
and post the contents of your /etc/network/interfaces

---

### Post by dmizer on 2006-11-03
further ... according to this thread: [http://www.ubuntuforums.org/showthread.php?p=1639926#post1639926](http://www.ubuntuforums.org/showthread.php?p=1639926#post1639926)

this card now works with no configuration in edgy, so your best bet might be to simply upgrade to edgy.

---

### Post by echomikeromeo on 2006-11-04
```
uname -r
``` produces "2.6.15-26-386".

/etc/network/interfaces:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid [my ssid]
wireless-key [my WEP key]


Yes, I could just upgrade, but I'd really like to see if I can fix this problem - then I'll learn about the system at the same time, as I've been doing thus far.:)

---

### Post by dmizer on 2006-11-05
well, upgrading may be the only way to make this thing work right because i've recently had trouble with my card.

anyway ... what exact line did you use to change the firmware according to this howto?

---

### Post by echomikeromeo on 2006-11-05
I used

```
sudo ln -s -f /lib/firmware/`(uname -r)`/acx/1.2.1.34/tiacx111c16 /lib/firmware/`(uname -r)`/acx/default/tiacx111c16
```

and then

```
sudo modprobe acx
```

Just like it says in the howto.

I actually tried upgrading today, but I think I might have had an error in downloading or burning the iso because it wouldn't boot properly. I'll try it again at some point.

---

### Post by dmizer on 2006-11-05
you'll have to replace the '(uname -r)' sections with your kernel number found by typing uname -r ... for example from your earlier post, the command should be this:
```
sudo ln -s -f /lib/firmware/2.6.15-26-386/acx/1.2.1.34/tiacx111c16 /lib/firmware/2.6.15-26-386/acx/default/tiacx111c16
```

---

### Post by echomikeromeo on 2006-11-06
No, still nothing.:( 

Thanks so much for your ongoing help... next time I have free time I'll try to download the upgrade again, and hopefully it will work.

---

### Post by dmizer on 2006-11-06
reboot with the card removed. once you've completely booted, plug the card in, and then type "dmesg" in the command line.  post the output of dmesg here. please be sure to contain dmesg in [code] or [quote] tags.

---

### Post by echomikeromeo on 2006-11-06
```
[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d0000 - 00000000000d4000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e6400 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000017e70000 (usable)
[17179569.184000]  BIOS-e820: 0000000017e70000 - 0000000017e7fc00 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000017e7fc00 - 0000000017e80000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 0000000017e80000 - 0000000018000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 382MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 97904
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 93808 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6710
[17179569.184000] ACPI: RSDT (v001 PTLTD         RSDT   0x06040000  LTP 0x00000000) @ 0x17e7bbd7
[17179569.184000] ACPI: FADT (v001 INTEL  OSPREY2  0x06040000 ROYZ 0x00000001) @ 0x17e7fb64
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x17e7fbd8
[17179569.184000] ACPI: DSDT (v001  PTLTD   L2 1.3 0x06040000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 18000000:e7f00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (012ff000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 797.674 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.296000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.296000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)[17179569.344000] Memory: 377396k/391616k available (1976k kernel code, 13612k reserved, 606k data, 288k init, 0k highmem)
[17179569.344000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.424000] Calibrating delay using timer specific routine.. 1596.79 BogoMIPS (lpj=3193586)
[17179569.424000] Security Framework v1.0.0 initialized
[17179569.424000] SELinux:  Disabled at boot.
[17179569.424000] Mount-cache hash table entries: 512
[17179569.424000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.424000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.424000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179569.424000] CPU: L2 cache: 128K
[17179569.424000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[17179569.424000] mtrr: v2.0 (20020519)
[17179569.424000] CPU: Intel Celeron (Coppermine) stepping 0a
[17179569.424000] Enabling fast FPU save and restore... done.
[17179569.424000] Enabling unmasked SIMD FPU exception support... done.
[17179569.424000] Checking 'hlt' instruction... OK.
[17179569.440000] checking if image is initramfs... it is
[17179571.476000] Freeing initrd memory: 6840k freed
[17179571.524000] ACPI: Looking for DSDT ... not found!
[17179571.528000] ACPI: setting ELCR to 0200 (from 0220)
[17179571.528000] NET: Registered protocol family 16
[17179571.528000] EISA bus registered
[17179571.528000] ACPI: bus type pci registered
[17179571.540000] PCI: PCI BIOS revision 2.10 entry at 0xfd9ca, last bus=1
[17179571.540000] PCI: Using configuration type 1
[17179571.540000] ACPI: Subsystem revision 20051216
[17179571.548000] ACPI: Interpreter enabled
[17179571.548000] ACPI: Using PIC for interrupt routing
[17179571.548000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.548000] PCI: Probing PCI hardware (bus 00)
[17179571.556000] Boot video device is 0000:00:02.0
[17179571.556000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179571.556000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[17179571.556000] PCI: Transparent bridge - 0000:00:1e.0
[17179571.556000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.564000] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[17179571.564000] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[17179571.564000] ACPI: PCI Interrupt Link [LNKC] (IRQs *5)
[17179571.564000] ACPI: PCI Interrupt Link [LNKD] (IRQs *5)
[17179571.568000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 12 14 15) *0, disabled.
[17179571.568000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 12 14 15) *0, disabled.
[17179571.568000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 12 14 15) *0, disabled.
[17179571.568000] ACPI: PCI Interrupt Link [LNKH] (IRQs *5)
[17179571.576000] ACPI: Embedded Controller [EC0] (gpe 28) interrupt mode.
[17179571.576000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[17179571.576000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.576000] pnp: PnP ACPI init
[17179571.588000] pnp: PnP ACPI: found 11 devices
[17179571.588000] PnPBIOS: Disabled by ACPI PNP
[17179571.588000] PCI: Using ACPI for IRQ routing
[17179571.588000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.592000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179571.592000] PCI: Bus 2, cardbus bridge: 0000:01:03.0
[17179571.592000]   IO window: 00002800-000028ff
[17179571.592000]   IO window: 00002c00-00002cff
[17179571.592000]   PREFETCH window: 20000000-21ffffff
[17179571.592000]   MEM window: 24000000-25ffffff
[17179571.592000] PCI: Bus 6, cardbus bridge: 0000:01:03.1
[17179571.592000]   IO window: 00001400-000014ff
[17179571.592000]   IO window: 00003000-000030ff
[17179571.592000]   PREFETCH window: 22000000-23ffffff
[17179571.592000]   MEM window: 26000000-27ffffff
[17179571.592000] PCI: Bridge: 0000:00:1e.0
[17179571.592000]   IO window: 2000-2fff
[17179571.592000]   MEM window: f4100000-f41fffff
[17179571.592000]   PREFETCH window: 20000000-23ffffff
[17179571.592000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179571.592000] **** SET: Misaligned resource pointer: d7dc75e2 Type 07 Len 0
[17179571.592000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[17179571.592000] PCI: setting IRQ 5 as level-triggered
[17179571.592000] ACPI: PCI Interrupt 0000:01:03.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[17179571.592000] PCI: Setting latency timer of device 0000:01:03.0 to 64
[17179571.592000] ACPI: PCI Interrupt 0000:01:03.1[B] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[17179571.592000] PCI: Setting latency timer of device 0000:01:03.1 to 64
[17179571.592000] Simple Boot Flag at 0x37 set to 0x1
[17179571.596000] audit: initializing netlink socket (disabled)
[17179571.596000] audit(1162790586.596:1): initialized
[17179571.596000] VFS: Disk quotas dquot_6.5.1
[17179571.596000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.596000] Initializing Cryptographic API
[17179571.596000] io scheduler noop registered
[17179571.596000] io scheduler anticipatory registered
[17179571.596000] io scheduler deadline registered
[17179571.596000] io scheduler cfq registered
[17179571.596000] isapnp: Scanning for PnP cards...
[17179571.952000] isapnp: No Plug & Play device found
[17179572.012000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[17179572.020000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.024000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.024000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179572.024000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.032000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.032000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.032000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.032000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.036000] mice: PS/2 mouse device common for all mice
[17179572.036000] EISA: Probing bus 0 at eisa.0
[17179572.036000] Cannot allocate resource for EISA slot 1
[17179572.036000] Cannot allocate resource for EISA slot 2
[17179572.036000] Cannot allocate resource for EISA slot 3
[17179572.036000] EISA: Detected 0 cards.
[17179572.036000] NET: Registered protocol family 2
[17179572.068000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.076000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179572.076000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179572.076000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[17179572.076000] TCP: Hash tables configured (established 16384 bind 16384)
[17179572.076000] TCP reno registered
[17179572.076000] TCP bic registered
[17179572.076000] NET: Registered protocol family 1
[17179572.076000] NET: Registered protocol family 8
[17179572.076000] NET: Registered protocol family 20
[17179572.076000] Using IPI Shortcut mode
[17179572.076000] ACPI wakeup devices:
[17179572.076000]  LID  HUB USB1 USB2
[17179572.076000] ACPI: (supports S0 S1 S4 S5)
[17179572.076000] Freeing unused kernel memory: 288k freed
[17179572.240000] vga16fb: initializing
[17179572.240000] vga16fb: mapped to 0xc00a0000
[17179572.352000] Console: switching to colour frame buffer device 80x25
[17179572.352000] fb0: VGA16 VGA frame buffer device
[17179573.524000] Capability LSM initialized
[17179573.632000] ACPI: CPU0 (power states: C1[C1] C3[C3])
[17179573.632000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179575.248000] ICH2M: IDE controller at PCI slot 0000:00:1f.1
[17179575.248000] ICH2M: chipset revision 3
[17179575.248000] ICH2M: not 100% native mode: will probe irqs later
[17179575.248000]     ide0: BM-DMA at 0x1800-0x1807, BIOS settings: hda:DMA, hdb:pio
[17179575.248000]     ide1: BM-DMA at 0x1808-0x180f, BIOS settings: hdc:DMA, hdd:pio
[17179575.248000] Probing IDE interface ide0...
[17179575.536000] hda: IBM-DJSA-210, ATA DISK drive
[17179576.220000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.240000] Probing IDE interface ide1...
[17179576.976000] hdc: TEAC CD-ROM CD-224E, ATAPI CD/DVD-ROM drive
[17179577.648000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.668000] hda: max request size: 128KiB
[17179577.688000] hda: 19640880 sectors (10056 MB) w/384KiB Cache, CHS=19485/16/63, UDMA(66)
[17179577.688000] hda: cache flushes not supported
[17179577.692000]  hda: hda1 hda2 < hda5 >
[17179577.748000] hdc: ATAPI 24X CD-ROM drive, 128kB Cache, UDMA(33)
[17179577.748000] Uniform CD-ROM driver Revision: 3.20
[17179578.204000] usbcore: registered new driver usbfs
[17179578.204000] usbcore: registered new driver hub
[17179578.212000] USB Universal Host Controller Interface driver v2.3
[17179578.212000] **** SET: Misaligned resource pointer: d653a4e2 Type 07 Len 0
[17179578.212000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[17179578.212000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17179578.212000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179578.212000] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[17179578.212000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[17179578.212000] uhci_hcd 0000:00:1f.2: irq 5, io base 0x00001820
[17179578.216000] hub 1-0:1.0: USB hub found
[17179578.216000] hub 1-0:1.0: 2 ports detected
[17179578.320000] **** SET: Misaligned resource pointer: d653a1e2 Type 07 Len 0
[17179578.320000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[17179578.320000] ACPI: PCI Interrupt 0000:00:1f.4[C] -> Link [LNKH] -> GSI 5 (level, low) -> IRQ 5
[17179578.320000] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[17179578.320000] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[17179578.320000] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[17179578.320000] uhci_hcd 0000:00:1f.4: irq 5, io base 0x00001880
[17179578.320000] hub 2-0:1.0: USB hub found
[17179578.320000] hub 2-0:1.0: 2 ports detected
[17179578.656000] Attempting manual resume
[17179578.736000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.776000] kjournald starting.  Commit interval 5 seconds
[17179601.168000] Linux agpgart interface v0.101 (c) Dave Jones
[17179601.184000] agpgart: Detected an Intel i815 Chipset.
[17179601.708000] agpgart: AGP aperture is 64M @ 0xf8000000
[17179602.664000] **** SET: Misaligned resource pointer: d28a3f22 Type 07 Len 0
[17179602.664000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[17179602.664000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179602.664000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179602.700000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179602.752000] Real Time Clock Driver v1.12
[17179602.776000] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[17179602.888000] input: PC Speaker as /class/input/input1
[17179603.024000] Synaptics Touchpad, model: 1, fw: 5.7, id: 0x8146b1, caps: 0x804793/0x0
[17179603.024000] serio: Synaptics pass-through port at isa0060/serio1/input0
[17179603.040000] intel8x0_measure_ac97_clock: measured 114542 usecs
[17179603.040000] intel8x0: clocking to 48000
[17179603.044000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179603.084000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179603.092000] hw_random hardware driver 1.0.0 loaded
[17179603.392000] ACPI: PCI Interrupt 0000:01:03.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[17179603.392000] Yenta: CardBus bridge found at 0000:01:03.0 [1028:00c9]
[17179603.392000] Yenta O2: res at 0x94/0xD4: c8/00
[17179603.392000] Yenta O2: enabling read prefetch/write burst
[17179603.416000] parport: PnPBIOS parport detected.
[17179603.416000] parport0: PC-style at 0x378, irq 7 [PCSPP]
[17179603.520000] Yenta: ISA IRQ mask 0x0818, PCI irq 5
[17179603.520000] Socket status: 30000006
[17179603.520000] Yenta: Raising subordinate bus# of parent bus (#01) from #01 to #05
[17179603.520000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[17179603.520000] cs: IO port probe 0x2000-0x2fff: clean.
[17179603.520000] pcmcia: parent PCI bridge Memory window: 0xf4100000 - 0xf41fffff
[17179603.520000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
[17179603.568000] ACPI: PCI Interrupt 0000:01:03.1[B] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[17179603.568000] Yenta: CardBus bridge found at 0000:01:03.1 [1028:00c9]
[17179603.696000] Yenta: ISA IRQ mask 0x0818, PCI irq 5
[17179603.696000] Socket status: 30000006
[17179603.696000] Yenta: Raising subordinate bus# of parent bus (#01) from #05 to #09
[17179603.696000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[17179603.696000] cs: IO port probe 0x2000-0x2fff: clean.
[17179603.696000] pcmcia: parent PCI bridge Memory window: 0xf4100000 - 0xf41fffff
[17179603.696000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
[17179603.888000] ts: Compaq touchscreen protocol output
[17179604.016000] Floppy drive(s): fd0 is 1.44M
[17179604.032000] FDC 0 is a National Semiconductor PC87306
[17179604.080000] ltmodem: module license 'Proprietary' taints kernel.
[17179604.088000] Loading Lucent Modem Controller driver version 8.26-alk-8
[17179604.092000] PCI: Enabling device 0000:01:0b.0 (0100 -> 0103)
[17179604.092000] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17179604.092000] Detected Parameters Irq=255 BaseAddress=0x2000 ComAddress=0x2400
[17179604.092000] ttyLTM0 at I/O 0x2000 (irq = 255) is a Lucent/Agere Modem
[17179604.192000] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17179604.192000] Detected Parameters Irq=255 BaseAddress=0x2000 ComAddress=0x2400
[17179604.196000] ttyLTM0 at I/O 0x2000 (irq = 255) is a Lucent/Agere Modem
[17179604.772000] cs: IO port probe 0x100-0x3af: clean.
[17179604.776000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179604.776000] cs: IO port probe 0x820-0x8ff: clean.
[17179604.776000] cs: IO port probe 0xc00-0xcf7: clean.
[17179604.776000] cs: IO port probe 0xa00-0xaff: clean.
[17179604.780000] cs: IO port probe 0x100-0x3af: clean.
[17179604.784000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179604.784000] cs: IO port probe 0x820-0x8ff: clean.
[17179604.784000] cs: IO port probe 0xc00-0xcf7: clean.
[17179604.784000] cs: IO port probe 0xa00-0xaff: clean.
[17179605.688000] lp0: using parport0 (interrupt-driven).
[17179605.844000] Adding 433712k swap on /dev/hda5.  Priority:-1 extents:1 across:433712k
[17179606.016000] EXT3 FS on hda1, internal journal
[17179606.404000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179606.404000] md: bitmap version 4.39
[17179607.372000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179608.224000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[17179608.224000] hdc: packet command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17179608.224000] ide: failed opcode was: unknown
[17179608.224000] cdrom: open failed.
[17179611.092000] NET: Registered protocol family 17
[17179618.292000] ACPI: AC Adapter [AC] (on-line)
[17179618.372000] ACPI: Battery Slot [BAT0] (battery present)
[17179618.540000] ACPI: Power Button (FF) [PWRF]
[17179618.540000] ACPI: Lid Switch [LID]
[17179618.540000] ACPI: Sleep Button (CM) [SLPB]
[17179618.808000] ibm_acpi: ec object not found
[17179618.876000] pcc_acpi: loading...
[17179619.120000] ACPI: Video Device [GCH0] (multi-head: yes  rom: no  post: no)[17179629.692000] ppdev: user-space parallel port driver
[17179630.324000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179630.324000] apm: overridden by ACPI.
[17179636.592000] Bluetooth: Core ver 2.8
[17179636.592000] NET: Registered protocol family 31
[17179636.592000] Bluetooth: HCI device and connection manager initialized
[17179636.592000] Bluetooth: HCI socket layer initialized
[17179636.624000] Bluetooth: L2CAP ver 2.8
[17179636.624000] Bluetooth: L2CAP socket layer initialized
[17179636.652000] Bluetooth: RFCOMM socket layer initialized
[17179636.652000] Bluetooth: RFCOMM TTY layer initialized
[17179636.652000] Bluetooth: RFCOMM ver 1.7
[17179649.104000] NET: Registered protocol family 10
[17179649.104000] lo: Disabled Privacy Extensions
[17179649.104000] IPv6 over IPv4 tunneling driver
```

Is it safe to be posting all this info about my computer online?

---

### Post by dmizer on 2006-11-06
i've posted dmesg plenty of times.  that doesn't make it safe, but i doubt you have much to worry about unless you've made someone very very angry.

wait ... that dmesg was done after you pluged your card in?  it doesn't even show that the card is there at all.

what's the output of:
```
cardctl ident
```

---

### Post by echomikeromeo on 2006-11-06
```
Socket O:
no product info available
Socket 1: 
no product info available
manfid: 0x0007, 0x0082
```

After rebooting and doing dmesg again, I got one error repeatedly, preceded by a different number in each instance. Here's an example:

```
[17179735.744000] wlan0: association FAILED: peer sent response code 12 (Assoc denied (reason outside of 802.11b scope), maybe MAC filtering by peer?)
```

---

### Post by dmizer on 2006-11-06
well, is there mac filtering on your network?  obvious question i know but ... you never know.

what is the output of lspci, and 'sudo iwlist wlan0 scan' (you can feel free to sensor the critical details of wlan0 scan).

---

### Post by dmizer on 2006-11-06
by the way, this is the problem i've been having since the linux-restricted-modules-2.6.15-27-386 linux-restricted-modules-common updates:
```
acx: BUG: no free txdesc left
```
i'm going to try installing the 686 kernel to see if this will correct the problem.

edit: failed.  this trick just isn't working anymore.  i'll have to go back to ndiswrapper.

edit 2: okay, i got this card working with ndiswrapper again, but only at the sacrifice of usb 2.0 ... if anyone is interested, i'll write up another howto for it.

---

### Post by echomikeromeo on 2006-11-06
I think I'll be installing 6.10, then.

---

### Post by wajvpitt on 2006-12-21
I used this guide back in September to get my wireless card working - it seemed a lot simpler than ndiswrapper etc.

I've been away at college on a wired network and now I'm back home in a wireless environment.  I'm running 32 bit Dapper.  As soon as I got home, the signal strength showed up on Wifi Radar as 76% but it said 'not connected.'  

I re-did this 'trick' and it came up as 'connected' but then my computer still didn't seem to be sending and receiving - it said it couldn't get an ip address. 

Now everytime I reboot the card seems to disconnect.   

So....

1 - Any suggestions?
2 - How do I find out which driver I'm using?
3 - I'd like to switch to 64-bit - will there be more or less problems?
4 - I might also switch to Edgy, again, more or less problems?

I've had a quick look around the forum but can't find definitive answers too quickly...

Thanks

---

### Post by Kobalt on 2006-12-21
Hello, 
1. using 64 bits or 32 bits kernels makes no difference, the trick works on both.
2. if you use Edgy, the card is working out of the box, without this trick. 
3 concerning your probelm, I'm guessing your wireless interface is conffigured in dhcp while your router is set to attribute a unique IP adress. You might want to check this (by typing 192.168.0.1 in firefox, logging into your router and checking the settings) and et back at us with the result. 

Cheerio !

---

### Post by wajvpitt on 2006-12-21
Ok - I've done a few things.  Checked the router was on DHCP - yes.  Reset the router (192.168.1.1).  Did the 'trick' again.  All seem to be getting me steps closer: here is iwconfig:

```
wlan0     IEEE 802.11b+/g+  ESSID:"BTVOYAGER2091-70"  Nickname:"BTVOYAGER2091-70"
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:11:F5:FC:5D:70
          Bit Rate:1 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=31/100  Signal level=3/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

And it does appear as 'connected' now rather than 'disconnected'.  However, I think it's all one way traffic and I'm still not getting an IP address.  

I suppose this would suggest that the key is wrong (althought it's not) but I'll try with no security at all.  I seem to remember some thread a long time ago about not liking keys.  

Any suggestions if this doesn't work?

---

### Post by wajvpitt on 2006-12-21
Ok - a bit more progress without any security.  I can pick up the router with the wireless card and it gets the ip 192.168.1.3.   I'm also wired in at the moment on 192.168.1.2.  With the wireless device I can ping 192.168.1.2 and 192.168.1.1 (the router).  
My router also tells me that there's a wired (sent packets: xxx, received: xxx) and a wireless connection (sent: xxx, received 0).  So my router and the wireless device can see each other.  

Now: wireless deactivated + wired activated = internet works
wireless activated + wired activated = no internet (I'm sure this can work)
wireless activated + wired deactivated = no internet (this is what I want)  

I think I can't send out from the wireless device at the moment - any suggestions?

Thanks all.

---

### Post by vroomfondel on 2007-01-03
[QUOTE=Kobalt;1914498]
2. if you use Edgy, the card is working out of the box, without this trick. 
...[QUOTE]

No it doesn't and the /lib/firmware directories with alt acx driver aren't even there on my install. 
Why is everything so messy with Ubuntu? hardly anything worked out of the box; video, sound and worst of all no network.
yes, the basic install was a lot quicker than windoze but after 3 days of hacking around its only working 1/4 as good as XP.

---

### Post by rljacobson on 2007-01-16
What does "Plug out and then in your card" mean?

---

### Post by Kobalt on 2007-01-16
> **vroomfondel said:**
> [QUOTE=Kobalt;1914498]
2. if you use Edgy, the card is working out of the box, without this trick. 
...[QUOTE]

No it doesn't and the /lib/firmware directories with alt acx driver aren't even there on my install. 
Why is everything so messy with Ubuntu? hardly anything worked out of the box; video, sound and worst of all no network.
yes, the basic install was a lot quicker than windoze but after 3 days of hacking around its only working 1/4 as good as XP.
Did you have your card plugged in before your started that install ? :)

---

### Post by Kobalt on 2007-01-16
> **rljacobson said:**
> What does "Plug out and then in your card" mean?
Plug out then plug in your card.

---

### Post by echomikeromeo on 2007-01-16
> **rljacobson said:**
> What does "Plug out and then in your card" mean?

Your card plugs into a slot in the computer - I have a laptop so it's on the side, but yours might be on the front. Remove the card - there's a little button that you push for it to pop out - and then pop it back in again.

---

### Post by ogomoe on 2007-01-22
Does the WPC54Gv2 need to be out (not in the laptop) during the Ubuntu installation?

---

### Post by Kobalt on 2007-01-22
Actually I think it would be better : some have experienced the miss of acx modules in their kernels (with edgy), even though they are avaliable on the install CD. I suggest you plug it in before booting your computer and starting the install process : you card will be recognized and the acx modules installed properly.

---

### Post by karachuonyo on 2007-03-22
I have one of these cards made by safecom. Its a pcmcia card for my old laptop with kubuntu edgy. The card has the ACX 11 chip and works out of the box with the latest kernel update. However i have only ever managed to connect to WEP secured networks. Does anyone know if the card supports WPA in ubuntu. With XP WPA works without any issues from the same card.

---

### Post by Kobalt on 2007-03-22
The card does support WPA, I have been using it with Network-manager and it works flawlessly...

---

### Post by Cherry Cotton on 2007-03-30
This is going to sound kind of whiny, but is there any way to do this without plugging out and then in your card? My brother installed my card into the back of the computer--yes, it uses the Texas Instruments ACX 111 chipset--and it's good and stuck, and I can't guarantee I wouldn't accidentally void my warranty trying to get it out (or blow up the computer, or something).

I tried simply turning off and then on the _computer_... but, that didn't work. By the way, I'm using the Feisty Fawn beta (don't mention Edgy Eft to me, it would not install). What should I do to complete this trick?

---

### Post by mmmpancakes on 2007-04-08
This tutorial works beautifully in Edgy as well. I followed it verbatim, and my card came to life today after almost a 1-year battle with wireless on my notebook (Gateway 600yg2). Can't thank you enough.

---

### Post by Sniper99 on 2007-04-09
hi, i have read and followed all of the instructions on all the pages, and nothing seems to work, i am on an older sony vaio and have the card plugged in, i have done all of the lines of code shown on the first post, and nothing really happens, when i hit enter, nothing happens, a new empty line shows up, so i did the bottom two "ifup" lines, and nothing happened, i plugged in and out the card, nothing happened, i rebooted, nothing happened, i have done just about everything and i dont have the $ to buy a new card right now (freshman=no good job) i really need some help, i installed a wireless card on my ubuntu desktop, and it was totally pain free, and unfortunately this "trick" is not working

---

### Post by darkhacker902 on 2007-04-13
In step 3. I pulled it out, popped it in, and then the Power LED came on, but the link doesnt blink.


Then i tried the other commands to get it going, and it says eth0 not configured.

Pulled up network settings, and my Wlan Card isnt there, and eth0 is assigned to My Ethernet Connection card. Not my Wlan Card.

so i did iwconfig
lo      No wireless extensions.

eth0   No wireless extensions.

sit0      No wireless extensions.


ifcongfig gives me this:

lo link encap:Local Loopback
inet addr:127.0.0.1   Mask:255.0.0.0
inet6 addr: ::1/128 scope:Host
UP LOOPBACK RUNNING  MTU:16436   Metric:1
RX packets:9 errors:0 dropped:0 overruns:0 Frame:0
TX packets:9 errors:0 dropped:0 overruns:0 Carrier:0
collisions:0 txqueuelen:0
RX Bytes:472 (472.0 b) TX Bytes:472 (472.0 b) 


Im kind of new to linux, but I learn fast, please help,


Ryan

---

### Post by dmizer on 2007-04-13
@darkhacker902

instead of this command:
```
sudo ln -s -f /lib/firmware/`(uname -r)`/acx/1.2.1.34/tiacx111c16 /lib/firmware/`(uname -r)`/acx/default/tiacx111c16
```
use this command:
```
sudo ln -s -f /lib/firmware/2.6.15-26-386/acx/1.2.1.34/tiacx111c16 /lib/firmware/2.6.15-26-386/acx/default/tiacx111c16
```

your link light will not work as a link light, it will work like an activity light, so don't worry if the link light does not come on.

---

### Post by darkhacker902 on 2007-04-13
> **dmizer said:**
> @darkhacker902

instead of this command:
```
sudo ln -s -f /lib/firmware/`(uname -r)`/acx/1.2.1.34/tiacx111c16 /lib/firmware/`(uname -r)`/acx/default/tiacx111c16
```
use this command:
```
sudo ln -s -f /lib/firmware/2.6.15-26-386/acx/1.2.1.34/tiacx111c16 /lib/firmware/2.6.15-26-386/acx/default/tiacx111c16
```

your link light will not work as a link light, it will work like an activity light, so don't worry if the link light does not come on.Ok, all the commands went well.

But Eth0 Is still registered as my ethernet adapter, not my wlan card and it is not activated or configured, wlan doesnt show up in the Network settings, and i still cant open any page in mozilla :(.



Ryan

---

### Post by dmizer on 2007-04-13
try this: [http://www.ossgeeks.co.uk/?p=20](http://www.ossgeeks.co.uk/?p=20)

then reboot with the card removed.  log in.  insert the card, then check networking

---

### Post by darkhacker902 on 2007-04-13
Nope doesnt appear in networking now either, and ipv6 is disabled....




Ryan

---

### Post by dmizer on 2007-04-13
what's the output of lsmod

---

### Post by darkhacker902 on 2007-04-13
Not sure which to look for but the ones related to Pcmcia are


pcmcia_core                   Size: 42640 Used by: 3 pcmcia,yenta_socket,rsrc_nonstatic

and pcmcia            40508 size: 0.




Ryan

---

### Post by dmizer on 2007-04-13
was axc listed in there anywhere? if not, what is the output if you do this:
```
sudo modprobe acx
```

---

### Post by darkhacker902 on 2007-04-13
no acx, but modprobe asks me for my password, then directs me back to 

ryan@ryan-laptop:~s$.

after I enter the password.



ryan

---

### Post by dmizer on 2007-04-13
now see if acx appears in lsmod ... and if so, again ... can you see it in networking?

---

### Post by darkhacker902 on 2007-04-13
There is an ac, dev_acpi pcc_acpi, Sony_acpi,i2c_acpi_ec,AND acx Size: 101132 Used By: 0.



Ryan

---

### Post by dmizer on 2007-04-13
okay ... any errors or such in dmesg?

---

### Post by darkhacker902 on 2007-04-13
A couple of Buffer I/O errors on device sdb1 on different logical blocks.


Other than that no.


I also tried Restarting, and forcing a relaod of networking, which informs me that wlanctl-ng: no such device
Failed to enable device, exitcode= 1.

and

SIOCSIFADDR: no such device.

Wlan0: ERROR while getting interface flags: no such device.

(twice)

Bind socket to interface: no such device.
copyright....blah...blah.

:(



Ryan

---

### Post by dmizer on 2007-04-13
try adding this module to your blacklist as well:

blacklist ehci_hcd

reboot ... try again.

---

### Post by darkhacker902 on 2007-04-13
Done.
Rebooted.
Nothing.
Its not there, and nothing has changed.

It USED to be in networking, and i could activate it (Which did no good)
But lately since i have tried the tutsm it doesnt work :(.



Ryan



EDIT: I did lsmod, and noticed acx wasnt there again after i rebooted, so i sudo modprobe acx again and it is there.



Ryan


Edit2:

I did ndiswrapper -l to see what drivers are loaded and got this:


bcmwl5.sys   Invalid Driver!
lsbcmnds       Invalid Driver!
lstinds          Driver Present

---

### Post by dmizer on 2007-04-14
check your inbox.

edit:
wrong chipset.

---

### Post by Sniper99 on 2007-04-15
yeah, so none of this has brought me any closer to achieving this....if anybody has some time to spare please help me...email me @ [email]geegenflaben@gmail.com[/email], i have gotten nowhere in about 2 weeks......any help is appreciated

---

### Post by dmizer on 2007-04-15
@sniper99

post the output of:
```
uname -r
```

as well as the output of
```
lspci
```

---

### Post by wfn on 2007-05-13
Same thing happened to me - did you find a workaround ?

---

### Post by echomikeromeo on 2007-05-13
Folks still struggling with WPC54G cards in Feisty could try [this]("http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm43xxfirmware") howto. It worked really well for me.

---

### Post by dmizer on 2007-05-13
> **wfn said:**
> Same thing happened to me - did you find a workaround ?
since you didn't quote the post you are referring to, could you please elaborate on what "same thing" you are referring to?

> **echomikeromeo said:**
> Folks still struggling with WPC54G cards in Feisty could try [this]("http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm43xxfirmware") howto. It worked really well for me.

the above howto will not work for the card discussed in this thread.  the above howto is for a broadcom chipset, the card discussed in this thread has an acx chipset.

---

### Post by echomikeromeo on 2007-05-14
I've been following the progress of this thread, according to which I have an acx chipset - this howto worked for me in Edgy. The other one worked for me in Feisty, despite (I would assume) having the other chipset.

I'm really a noob at this, so let the usual caveat accompany anything I say.

---

### Post by whoKnew on 2007-05-21
hi everyone.

 i have the proper chipset, but when i enter step #1 i get:

> ln: creating symbolic link '/lib/firmware/2.6.17-10-generic/acx/default/tiacx111c16' to '/lib/firmware/2.6.17-10-generic/acx/1.2.1.34/tiacx111c16': No such file or directory.

i've tried searching for the tiacx111c16 file and i can't find it on my computer.
would this have anything to do with the fact that i've installed edgy from an alternate install cd?

is there somewhere i can find these files? 
would they be on the windows install cd? the whole process kind of confuses me.

thanks!

---

### Post by whoKnew on 2007-05-21
ps:
i'm using Edgy..
and i'm very new to linux/ubuntu/wireless configuration in general.

:)
i can still return my new card within the next few days to maybe get a different model/version. i'm wondering if this card requires the least amount of confusion to get running?

---

### Post by nidhogg16 on 2007-06-08
I just got a laptop (new to me, compaq armada e500) so this is my first experience using wireless... I have the WPC54G v2 with the acx chipset running Feisty and all that jazz, unfortunately ndiswrapper has issues on my comp for some reason, tells me ndiswrapper-common is installed but sudo ndiswrapper tells me command not found.  So i found this, and went through the original walkthrough and it worked great... I can see all the wireless networks around, but I can't connect.  When i put in the WEP key it tells me "Waiting for Network Key for the wireless network ..."  I read in another thread that this driver does not support WEP, so i disabled security and it still won't connect to anything.  From the looks of it it doesn't pull anything from DHCP, but it won't do anything static, either.  I'm not much of a network guy much less a wireless, so any help would rock.  iwconfig comes up with wlan0 with no ESSID, but when i try sudo ifup wlan0, it says 
ignoring unknown interface wlan0=wlan0
I've also now tried it on another wireless access point with no security and it doesn't work their either.

---

### Post by dmizer on 2007-06-08
@nidhogg16

if you're interested in trying ndiswrapper again, i wrote a beast of a howto on it for this card: [http://ubuntuforums.org/showthread.php?t=324148](http://ubuntuforums.org/showthread.php?t=324148) last i tested feisty, it was still in beta but the howto did work.

---

### Post by Kobalt on 2007-06-10
The open source acx drivers do support WEP but not WPA. And I could even see better results in terms of connection speed with ndiswrapper. Ever since I use the windows drivers+ndis for this card. 
In other words, you should follow dmizer's advice and his HowTo.

---

### Post by nidhogg16 on 2007-06-15
Thanks for ya'lls help, I tried the ndiswrapper method again but to no avail.  Drake was the first version I came in on, and still have a nice big manual for that one so I just reverted to 6.06 and got this method to work with no problems :).

---

### Post by dmizer on 2007-06-18
if you had posted in my howto with a description of what problems you were having, i would have been more than happy to help you out.

though dapper is not a bad choice if you want reliabilty.  i still use it for all my servers, as well as my work machine.

---

### Post by SeeYa32 on 2008-06-27
Ok. I know full well that this post is bringing it out of the dead, but i really need assistance. I have tried and tried to get my WPC54G v.2 Card working for Ubuntu 8.04 LST, but to no avail. I have read through this post many many countless times, but only to meet failure. Thanks in advance. 

              --Bobby

---

### Post by dmizer on 2008-06-28
> **SeeYa32 said:**
> Ok. I know full well that this post is bringing it out of the dead, but i really need assistance. I have tried and tried to get my WPC54G v.2 Card working for Ubuntu 8.04 LST, but to no avail. I have read through this post many many countless times, but only to meet failure. Thanks in advance. 

              --Bobby

this thread deals with making this card function in dapper.  if you want to make the card work in hardy, take a look at this link: [http://ubuntuforums.org/showthread.php?t=324148](http://ubuntuforums.org/showthread.php?t=324148) i have confirmed that this link works for hardy.

---

