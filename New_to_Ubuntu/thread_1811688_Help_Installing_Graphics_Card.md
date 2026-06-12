---
title: "Help Installing Graphics Card"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by doppel.ganger on 2011-07-25
I just got this graphics card from my uncle. I thought it might enable me to use Unity, which my computer can't run alone. I have absolutely no idea what company made it or what driver I should get. Do I need a driver? When I pop this into my PCI slot (it fits perfectly) and turn on my computer, the monitor turns on (not in sleep) but remains blank. I hear the computer working, but I left it alone for a minute and nothing happened. I have uploaded some photos of the graphics card and the PCI slot. Any help you can provide would be GREATLY appreciated.

---

### Post by doppel.ganger on 2011-07-25
Additional pics.

---

### Post by sadaruwan12 on 2011-07-25
Well, it seems like your computers monitor can't handle the refresh rate that given out by the VGA card.

Normally this happens when the driver that got installed doesn't detect monitor correctly.

Do this let the computer to get booted and after that press ctrl+alt+F1 and see you get a terminal interface.

If you can please post a photo of that white colored sticker on the back of you VGA card.

---

### Post by seawolf167 on 2011-07-25
> **sadaruwan12 said:**
> Do this let the computer to get booted and after that press ctrl+alt+F1 and see you get a terminal interface.

If you can get to a command line - please enter and post the output of the following command.

```
sudo lshw -class display
```

---

### Post by doppel.ganger on 2011-07-25
What is it and where is it?

---

### Post by doppel.ganger on 2011-07-25
```
thomas@Thomas-Dell-DE051:~$ sudo lshw -class display
[sudo] password for thomas: 
  *-display               
       description: VGA compatible controller
       product: 82865G Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:e8000000-efffffff memory:feb80000-febfffff ioport:ed98(size=8)
thomas@Thomas-Dell-DE051:~$ 
```
That's without the new graphics card.

---

### Post by sadaruwan12 on 2011-07-25
> **doppel.ganger said:**
> What is it and where is it?

It's a sticker on the other side of your VGA card white colored it contains some manufacturer details but first try the command and post the out put if you can get there.

---

### Post by seawolf167 on 2011-07-25
Was the PCI card inserted and running when you got this result? This is showing an integrated graphics card, not a stand-alone card.

Do you have that PCI slot turned on in BIOS? Can you disable your integrated graphics card in BIOS and force your computer to use the stand alone card?

EDIT: didn't notice the bottom statement in your post - please insert your PCI card and see if you can get to the terminal and enter the command with it running

---

### Post by sadaruwan12 on 2011-07-25
OK, You've another VGA out that comes from your motherboard?

I think the the issue is the BIOS doesn't auto switch to the PCI that might be the issue change it manually might fix the issue.

---

### Post by doppel.ganger on 2011-07-25
Do I need to  turn off and unplug the computer before putting in the card?

---

### Post by doppel.ganger on 2011-07-25
Be back in about 5 mins, going to test new card...

---

### Post by seawolf167 on 2011-07-25
> **doppel.ganger said:**
> Do I need to  turn off and unplug the computer before putting in the card?

YES. Turn off the computer, remove the power cable, ensure you don't touch any sensitive electronic components, ensure you don't discharge any static electricity, put the part it, enable it in BIOS (if needed), disable the onboard graphics in BIOS (if needed), then boot.

---

### Post by doppel.ganger on 2011-07-25
AH HA! Needed to connect the monitor to the card, not the built-in port :)

```
thomas@Thomas-Dell-DE051:~$ sudo lshw -class display
[sudo] password for thomas: 
  *-display UNCLAIMED     
       description: Display controller
       product: 82865G Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: memory:e8000000-efffffff memory:feb80000-febfffff ioport:ed98(size=8)
  *-display
       description: VGA compatible controller
       product: NV6 [Vanta/Vanta LT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 15
       width: 32 bits
       clock: 66MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=64 maxlatency=1 mingnt=5
       resources: irq:21 memory:fd000000-fdffffff memory:f8000000-f9ffffff memory:fea00000-fea0ffff
thomas@Thomas-Dell-DE051:~$ 

```

---

### Post by doppel.ganger on 2011-07-25
Time to see if my computer can handle 11.04 now... be back soon, I'll start a new thread if I have problems with Unity. Thank you everyone for all the help! SOLVED!

---

### Post by seawolf167 on 2011-07-25
> **doppel.ganger said:**
> AH HA! Needed to connect the monitor to the card, not the built-in port :)

Hehe, glad everything is working! :P

---

