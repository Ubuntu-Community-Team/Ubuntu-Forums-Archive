---
title: "Ubuntu 10.10 won't boot after installing"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by bamman1108 on 2011-03-08
I've been trying to get Ubuntu to work for a while now, but every time I try to install it, the same thing happens. I use Wubi, and then install it, then when I try to boot it, it will say

```
Completing the Ubuntu installation
Press esc now for more boot options
5...4...3...2...1...0
_
```

And it won't do anything. To fix this, I can press esc during the countdown, and press ACPI Workaround, which will get to the homescreen and allow Ubuntu to finish installing. It's currently finished with the installation, but now I can't get Ubuntu to boot at all. When I get to the Windows bootloader, I press ubuntu, and if I just try to start up Ubuntu, it just shows a blank screen with a blinking cursor at the top left. I tried pressing 'e' at the menu and then deleting the last two lines (the part that does the quiet splash) and everytime I seems fine but then it will always stop at this step and never move past it:

```
NET: Registered protocol family 1
```

Since that didn't work, I tried some of the options that I used to get into the LiveCD, so I deleted the quiet splash lines, then at the bottom of the thing I typed in

```
noapic acpi=off nomodeset
```

because those things let me boot into the LiveCD. Whenever I try this, I get a message that says it can't find sda2 (even though that's the correct partition) and then says kernel panic and then stops completely.

I really need help with this. I have no prior experience in Ubuntu and it really sucks having this problem the first time I try to use it.

---

### Post by migrate from windows on 2011-03-08
When you get the blinking cursor at top left try pressing ctrl+alt+F1 and see if you get command mode screen. then enter your username , passwd, and then type startx see if you get any error messages, post them if any.

---

### Post by bamman1108 on 2011-03-08
Pressing ctr+alt+f1 didn't have any effect at all. I can't press any keys at all when it's trying to boot.

---

### Post by nickleboyblue on 2011-03-08
I doubt this will help, but my parents have a desktop with a faulty motherboard.  Every time the computer gets shut down incorrectly, it changes BIOS settings at random.  There might be a BIOS setting somewhere, something like "Allow software to configure hardware" vs. "Allow bios" to do it.  Probably won't help, but it's worth looking at.

---

### Post by cprofitt on 2011-03-08
Hmm...  Do you know what kinds of sata disk controller the computer has? I wonder if it is how that is setup.

---

### Post by bamman1108 on 2011-03-08
> **cprofitt said:**
> Hmm...  Do you know what kinds of sata disk controller the computer has? I wonder if it is how that is setup.

I'm not sure what a sata disk even is to be honest. I'm really unfamiliar with how the inside of a computer functions and how an OS works, so I'd need step-by-step instructions to find out what kind of sata disk controller I have.

---

### Post by bamman1108 on 2011-03-08
> **nickleboyblue said:**
> I doubt this will help, but my parents have a desktop with a faulty motherboard.  Every time the computer gets shut down incorrectly, it changes BIOS settings at random.  There might be a BIOS setting somewhere, something like "Allow software to configure hardware" vs. "Allow bios" to do it.  Probably won't help, but it's worth looking at.

I haven't experience this issue before, so it didn't affect anything. Thanks for offering your input, though.

---

### Post by drs305 on 2011-03-08
> **bamman1108 said:**
> 
Since that didn't work, I tried some of the options that I used to get into the LiveCD, so I deleted the quiet splash lines, then at the bottom of the thing I typed in

```
noapic acpi=off nomodeset
```

because those things let me boot into the LiveCD. Whenever I try this, I get a message that says it can't find sda2 (even though that's the correct partition) and then says kernel panic and then stops completely.

The blinking cursor certainly sounds like a video issue. Just for clarification, when you say you added **nomodeset** "*at the bottom*" do you mean at the end of the *linux* line or do you literally mean as the last line in the edited menuentry. It would need to be placed at the end of the "linux" line, as would any other kernel options, then CTRL-x to boot.

If you aren't editing the menuentry at boot, you get into the edit mode at the Grub2 menu by pressing "e".

---

### Post by bcbc on 2011-03-08
> **bamman1108 said:**
> I've been trying to get Ubuntu to work for a while now, but every time I try to install it, the same thing happens. I use Wubi, and then install it, then when I try to boot it, it will say

```
Completing the Ubuntu installation
Press esc now for more boot options
5...4...3...2...1...0
_
```

And it won't do anything. To fix this, I can press esc during the countdown, and press ACPI Workaround, which will get to the homescreen and allow Ubuntu to finish installing. It's currently finished with the installation, but now I can't get Ubuntu to boot at all. When I get to the Windows bootloader, I press ubuntu, and if I just try to start up Ubuntu, it just shows a blank screen with a blinking cursor at the top left. I tried pressing 'e' at the menu and then deleting the last two lines (the part that does the quiet splash) and everytime I seems fine but then it will always stop at this step and never move past it:

```
NET: Registered protocol family 1
```

Since that didn't work, I tried some of the options that I used to get into the LiveCD, so I deleted the quiet splash lines, then at the bottom of the thing I typed in

```
noapic acpi=off nomodeset
```

because those things let me boot into the LiveCD. Whenever I try this, I get a message that says it can't find sda2 (even though that's the correct partition) and then says kernel panic and then stops completely.

I really need help with this. I have no prior experience in Ubuntu and it really sucks having this problem the first time I try to use it.

The wubi ACPI workaround option adds the following boot overrides: acpi=off noapic nolapic

So maybe you need the *nolapic* as well. If it got you through the installer slideshow it should get you booting as well.

---

### Post by bamman1108 on 2011-03-08
> **drs305 said:**
> The blinking cursor certainly sounds like a video issue. Just for clarification, when you say you added **nomodeset** "*at the bottom*" do you mean at the end of the *linux* line or do you literally mean as the last line in the edited menuentry. It would need to be placed at the end of the "linux" line, as would any other kernel options, then CTRL-x to boot.

If you aren't editing the menuentry at boot, you get into the edit mode at the Grub2 menu by pressing "e".

> **bcbc said:**
> The wubi ACPI workaround option adds the following boot overrides: acpi=off noapic nolapic

So maybe you need the *nolapic* as well. If it got you through the installer slideshow it should get you booting as well.

From what both of these are saying, those are probably my two mistakes then. I was just putting them at the last line of the entire menuentry. Which line is the linux line that I should put the commands under? Next time I try booting into ubuntu, I'll make sure to add nolapic as well then.

---

### Post by drs305 on 2011-03-08
> **bamman1108 said:**
> Which line is the linux line that I should put the commands under? Next time I try booting into ubuntu, I'll make sure to add nolapic as well then.

It would be the line that starts with "linux" and would look something like this (different UUID) after you make the change (add any other options such as **nolapic** you may need):

> 
linux	/vmlinuz root=UUID=c9101109-b746-464e-b9ec-5c62d9958c8d ro nomodeset 


---

### Post by bcbc on 2011-03-08
Also check P4man's great guide [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) - section "How to temporarily set kernel boot options on an installed OS (not wubi)"

(note although it says "(not wubi)" the instructions in post #1 work the same for an *installed* Wubi. (Overrides on the Wubi install are shown in post #8.)

---

### Post by bamman1108 on 2011-03-08
Awesome! I'm extremely happy to say that I'm posting this message from Ubuntu! It took a while to get it up, but I guess both not adding nolacpi and putting the commands in the wrong area were causing my problems the whole time, so now I can finally run the OS.

However, I now have another problem! In Windows 7, I could easily connect to my wireless internet because it automatically detected it, but now I can't seem to find my wireless networks at all, which is making it impossible to get on the internet without using an ethernet cable, which sucks because I have a laptop and want to be able to be mobile with it. What can I do to make Ubuntu find and connect to my wireless networks?

---

### Post by bcbc on 2011-03-08
What computer brand, model, graphics card and wireless card do you have?

I think you should also see if you can get it to work without acpi workarounds as these affect other things - e.g. battery/power management, fans etc. 

There are some stickies in the [networking and wireless forum]("http://ubuntuforums.org/forumdisplay.php?f=336") that can help with the wireless issue as well if you just want to focus on that.

---

### Post by bamman1108 on 2011-03-08
> **bcbc said:**
> What computer brand, model, graphics card and wireless card do you have?

I think you should also see if you can get it to work without acpi workarounds as these affect other things - e.g. battery/power management, fans etc. 

There are some stickies in the [networking and wireless forum]("http://ubuntuforums.org/forumdisplay.php?f=336") that can help with the wireless issue as well if you just want to focus on that.

Computer model: Tobisha satellite L675D-S7040
Graphics card: ATI Mobility Radeon HD4200 I think (just installed the proprietary driver)
Wireless card: No clue, but I googled and found someone with the same laptop model who has a "Realtek RTL8188CE Windows Wireless LAN 802.11n PCI-E NIC" wireless card.

I'd like to know how to avoid acpi workarounds if they'll ultimately damage my computer, so I wouldn't mind trying to fix that problem in the future (as of now, I can't see a battery indicator on the ubuntu top panel, but i'm not sure if that's what's causing the problem or if ubuntu just doesn't have a battery monitor)

---

### Post by bcbc on 2011-03-08
The wireless is described here... [http://ubuntuforums.org/showthread.php?p=10213706](http://ubuntuforums.org/showthread.php?p=10213706)

Or at least it should show you how to confirm what you have.

I did see another thread that mentioned that 10.04 worked better on this computer. [http://ubuntuforums.org/showthread.php?t=1604756](http://ubuntuforums.org/showthread.php?t=1604756)

The missing battery icon is likely due to the acpi workarounds.

---

### Post by bamman1108 on 2011-03-08
> **bcbc said:**
> The wireless is described here... [http://ubuntuforums.org/showthread.php?p=10213706](http://ubuntuforums.org/showthread.php?p=10213706)

Or at least it should show you how to confirm what you have.

I did see another thread that mentioned that 10.04 worked better on this computer. [http://ubuntuforums.org/showthread.php?t=1604756](http://ubuntuforums.org/showthread.php?t=1604756)

The missing battery icon is likely due to the acpi workarounds.

I finally got wireless to work, I installed the correct realtek driver and it's connecting fine now. I wasn't aware that Ubuntu didn't have the driver even though Windows 7 did on the same partition...

Now the only thing I have left to do is to get Ubuntu to boot without ACPI workarounds, but I wouldn't even know where to start with that.

Thanks for getting me this far though. It's the only reason I can even get into Ubuntu in the first place.

---

### Post by bcbc on 2011-03-08
> **bamman1108 said:**
> I finally got wireless to work, I installed the correct realtek driver and it's connecting fine now. I wasn't aware that Ubuntu didn't have the driver even though Windows 7 did on the same partition...

Now the only thing I have left to do is to get Ubuntu to boot without ACPI workarounds, but I wouldn't even know where to start with that.

Thanks for getting me this far though. It's the only reason I can even get into Ubuntu in the first place.

Ubuntu is completely separate from Windows when you boot using Wubi (except for the virtual disk which is on window's ntfs file system). So no drivers shared - windows not running at all.

Regarding the acpi stuff. I would first apply all updates, then try booting with various workarounds and see which ones you need. Start with nothing, and add the first one e.g. nolapic. See what happens (make sure you remove quiet splash so you can see any messages).

Also, it might be a good idea to check if there are any bios updates available for you computer (check your regional toshiba site and search on your model there).

I haven't found any specific posts on getting 10.10 and l675d to boot. If all else fails, it apparently worked well on 10.04 so that might be an option.

Here's a thread for an L655 (but it sounds like there is a lot in common between these toshibas): [http://ubuntuforums.org/showthread.php?t=1641931](http://ubuntuforums.org/showthread.php?t=1641931)

---

### Post by bamman1108 on 2011-03-09
I managed to boot Ubuntu only using pci=noacpi . However, that didn't solve the battery monitor problem. What exactly is that command?

---

### Post by bcbc on 2011-03-09
> **bamman1108 said:**
> I managed to boot Ubuntu only using pci=noacpi . However, that didn't solve the battery monitor problem. What exactly is that command?

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
> pci=noacpi OR acpi=noirq
These parameters disable the PCI IRQ routing

This link looks interesting [http://en.wikipedia.org/wiki/Interrupt_request](http://en.wikipedia.org/wiki/Interrupt_request)

---

