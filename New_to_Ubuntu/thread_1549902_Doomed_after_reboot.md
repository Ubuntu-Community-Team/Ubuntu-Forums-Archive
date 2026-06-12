---
title: "Doomed after reboot"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by search66 on 2010-08-10
Been running Ubuntu 10.10 with no problems for a while... I did an update today, and when I rebooted... I get back into the OS; however my display is shot... All I see is some pixelated lines at the top of the screen.

Any ideas?

*cry*

---

### Post by Peter09 on 2010-08-10
Hold the shift key while booting, should get you to the grub menu. From there select the recovery option and when you get to the menu try the reconfigure graphics (or similar) option.

---

### Post by search66 on 2010-08-10
> **Peter09 said:**
> Hold the shift key while booting, should get you to the grub menu. From there select the recovery option and when you get to the menu try the reconfigure graphics (or similar) option.

I was able to hit SHIFT to get to Grub... however... Right after I try to get to recovery mode... it goes straight to some craziness lines at the top... 

:(

---

### Post by Peter09 on 2010-08-10
Check your cables  from the graphics card to the terminal - are they securely plugged in.

---

### Post by search66 on 2010-08-10
Yeah... I just tried... I reseated my video card (nVidia 8600gt).. I can see the GRUB fine... you'll see like the top 1/4 of the screen flash and scroll some lines, and then it sits there... a blue box with white, blue and red lines...

---

### Post by kr651129 on 2010-08-10
try booting off the cd (live version) and then you should be able to edit your settings while running that

---

### Post by search66 on 2010-08-10
Good idea... I didn't even think about that.  I'm back to a desktop (Live CD)... I wouldn't even know where to begin... Can you give me a starting block?

Thank you.

---

### Post by kr651129 on 2010-08-10
can you give me the output of lspci so I can see what hardware your working with?

---

### Post by search66 on 2010-08-10
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)
02:01.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
ubuntu@ubuntu:~$

---

### Post by kr651129 on 2010-08-10
what are you running a dell laptop?

---

### Post by search66 on 2010-08-10
I'm not sure if this has anything to do with it... But I use Cairo for my dock... I noticed this was one of the updates that was being applied.

Right when the Cairo updates were being applied, my PC bogged down like crazy... there were some failures and when I rebooted... doom.

Is there a way to remove Cairo from my system from the Live CD?

---

### Post by search66 on 2010-08-10
> **kr651129 said:**
> what are you running a dell laptop?

No, this is a desktop.  Dell Vostro 200

---

### Post by kr651129 on 2010-08-10
> **nucleuskore said:**
> [SIZE="7"]Eureka !![/SIZE]

I have a HP Pavilion SLimline s7727c

with lspci giving me
VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)

I was getting a blank screen (out of sync) on booting from the live cd.

**I worked around the problem as follows:**

[list]
[*]On first boot after install, press e on getting the GRUB bootloader.
[*]Using arrow keys navigate to and delete **quiet** and **splash** and type the word **nomodeset** in their place
[*]Press **Ctrl** and **X** to boot
[*]You should now be able to login to your Ubuntu as usual[/list]

For those of you who do not know what to do next, in the taskbar click on System->Administration->Hardware drivers, and select and activate the nvidia current driver if you have an nvidia card like I do. The driver will be downloaded and activated automatically, and you will be prompted for a reboot.


found this...you can try it, i don't know if it will work or not

---

### Post by search66 on 2010-08-10
No joy... Thanks for the try, was worth a shot.

:)

Do you know how to remove packages from Ubuntu using a Live CD?  I've Googled my butt off, and can't find anything.

---

### Post by Peter09 on 2010-08-10
Just to confirm what you have said, you are getting this error on a grub screen (recovery) - this will be before you load the graphics drivers.

---

### Post by search66 on 2010-08-10
> **Peter09 said:**
> Just to confirm what you have said, you are getting this error on a grub screen (recovery) - this will be before you load the graphics drivers.

I can see the Grub fine.  But if I select Ubuntu or recovery mode; the screen goes black (like booting) and then will flash some lines and in the very top of the screen sit there with lines and some colors.

I know my system is up, because I can get to Subsonic and Transmission... 

I'm currently looking at the Live CD desktop.

---

### Post by kr651129 on 2010-08-10
I'm sorry but I don't know off hand how to remove packages while in live.  I know you can edit files just not sure how to remove packages.

---

### Post by search66 on 2010-08-10
> **kr651129 said:**
> I'm sorry but I don't know off hand how to remove packages while in live.  I know you can edit files just not sure how to remove packages.

NP... Thank you for your help though!  :)

I did find out how to remove packages... I removed Cairo; and that must not have been the culprit... same issue.  :(

*sniff*

---

### Post by Peter09 on 2010-08-10
Boot as normal, but when you get the screen corruption try CNTRL-ALT-F3. This should give you another session (a terminal session). From there you can configure your graphics card again.

Cntrl-ALT-F7 gets you back to the normal screen.

---

### Post by search66 on 2010-08-10
> **Peter09 said:**
> Boot as normal, but when you get the screen corruption try CNTRL-ALT-F3. This should give you another session (a terminal session). From there you can configure your graphics card again.

Cntrl-ALT-F7 gets you back to the normal screen.

Thanks, Peter... However, I've tried this to no avail.  I don't get a terminal when I try CNTRL-ALT-F1 or CNTRL-ALT-F3

I may be stuck and have to reinstall.  :P

---

### Post by amauk on 2010-08-10
10.10 (maverick) is still in Alpha
and there's just been a major version change to the x-server

If you want a solid system, don't run pre-release versions

---

### Post by search66 on 2010-08-10
> **amauk said:**
> 10.10 (maverick) is still in Alpha
and there's just been a major version change to the x-server

If you want a solid system, don't run pre-release versions

Thanks.

---

### Post by kr651129 on 2010-08-10
also I've had much better luck with awn over cairo you may want to give it a try

---

### Post by search66 on 2010-08-10
Yeah no worries... Appreciate all the help.  Thank God for large USB drives.

:)

---

### Post by fslezak on 2010-08-10
Can you post a screenshot of your desktop when this happens.

---

### Post by search66 on 2010-08-10
> **fslezak said:**
> Can you post a screenshot of your desktop when this happens.

Well... I never really *see* a desktop... but here's a shot taken with my phone... it's not great at all.. but...

---

### Post by kr651129 on 2010-08-10
> **search66 said:**
> Well... I never really *see* a desktop... but here's a shot taken with my phone... it's not great at all.. but...

figure it out yet?  I'm interested

---

### Post by search66 on 2010-08-10
> **kr651129 said:**
> figure it out yet?  I'm interested

Nah... Ended up just reinstalling

---

### Post by sandyd on 2010-08-10
> **search66 said:**
> Well... I never really *see* a desktop... but here's a shot taken with my phone... it's not great at all.. but...
you need nomodeset

---

### Post by search66 on 2010-08-10
> **carlee said:**
> you need nomodeset

Tried that.. Didn't work.  :)

---

### Post by jtarin on 2010-08-10
You need peanut-butter cookies.:p

---

### Post by fslezak on 2010-08-16
Looks like the system is being patriotic ;) .

Unless you REALLY want to use a pre-release, go with the latest LTS Ubuntu (in case 10.04.)

---

