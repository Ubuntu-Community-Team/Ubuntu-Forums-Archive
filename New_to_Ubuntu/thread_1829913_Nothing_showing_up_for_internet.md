---
title: "Nothing showing up for internet"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by ClientAlive on 2011-08-20
I'm a little confused about what's going on. I have another computer, a desktop, that has nothing installed on it yet (just bare hardware at this point). I'm running Xubuntu (whatever the latest release of it is) live from cd on it now. I have a wireless pci adapter (an expansion card) that I would just love to get working on it. In fact, without some form of wireless connection I'll be hard pressed to get internet access to that box. So . . . here's the thing . . .

The wireless card is a Motorola WPC810G.

~ Whether the card is inserted into the board (the mobo) or not:

lspci shows an entry for "Ethernet controller"

```

 . . . Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

but has no entry for "Network controller"

In addition,

```

rfkill list

```

does not yield any output at all (I thought it was supposed to at least show eth0, the wired connection, even if the cable is not connected/ connected to the router - I thought).

In addition; and, whether the card is inserted into the board or not, the results of

```

lshw

```

show an entry for "Ethernet interface" and what is described is that same, onboard, Realtek ethernet port (for the physical ethernet plug).

I've Googled looking for any information on this particular network card (my Motorola) but have only seen a couple of my old posts come up (to do with other issues but where I had listed it in the post) and a link to the driver for that card (which I'm pretty sure is for Microsoft only).

What I don't understand though is how the card does not show up in lspci at all. This laptop I'm typing to you on has the Broadcom wireless card in it <bcm 4318> and it would show up in lspci even before I got it working - makes me thing that Motorola card should show up, driver or not/ working or not.

Am I just confused here? Even if I got the card/ hardware recognized as part of the system, what would I have to do to get it working with Linux? I can't seem to find any useful information on it and I'm stumped.

Thanks in advance for your help. Thanks for taking the time to read this.

---

### Post by fdrake on 2011-08-21
are you sure you have properly installed the card? is there any way you can double check with windows, or with the bios? do you have any led flashing?

---

### Post by ClientAlive on 2011-08-21
> **fdrake said:**
> are you sure you have properly installed the card? is there any way you can double check with windows, or with the bios? do you have any led flashing?

I never thought of looking in bios. I didn't know something like an expansion card would show up there.

As for double checking with Windows, there is no o/s installed on the machine. In fact, neither of the two hard disks are even formatted with a file system yet. I'm in the process of resurrecting the machine (circa 2005) with the intention of compiling Gentoo; and, ultimately, Xen. If I can avoid it, I'd just as soon not install anything on it at this point. I'd like to just compile right to the disk - if I can ever get this thing prepped for it. (I say that because this thing's been one headache after another - way too many delays up to this point). So this card (maybe one other card of some kind too) are like the last remaining obstacles. Actually, if I could get this one card working (the wireless card) I'd be able to get an Internet connection and be all set to get started compiling.

I'll put the card back in and check in bios to see what I see. I'll post back with the results. Thanks for the heads up.

---

### Post by ClientAlive on 2011-08-21
I checked in bios but I don't see anything showing up for that (not sure if there is a place for it in this bios even). I've attached a couple pics if it helps any. Thanks.
-------------------------

Edit:

Well I guess there is an led light on the card. It doesn't light up though. The card came from a working PC (a different one than the one I'm trying to put it into).

I'm surprised at the incredible lack of information about this card on the Internet. Even on Motorola's site, when I do a search for that model, it comes back with "sorry . . . no results . . ."

---

### Post by fdrake on 2011-08-21
are you running a 32bit or a 64 version of ubuntu?

---

### Post by ClientAlive on 2011-08-21
> **fdrake said:**
> are you running a 32bit or a 64 version of ubuntu?


The live I'm running is Xubuntu. It's 32 bit and is whatever the latest version of it as of about 30 days ago. I could check the version for sure in the morning if it helps.

---

### Post by fdrake on 2011-08-21
> **ClientAlive said:**
> The live I'm running is Xubuntu. It's 32 bit and is whatever the latest version of it as of about 30 days ago. I could check the version for sure in the morning if it helps.

thought maybe it was the 64 bit the problem (usually it happens with driver issues not to work properly), since most of the win driver i found for your card were 32bit .  :(

the fact that it doesn't show up as a device is out of driver issues or even kernel (maybe). Maybe trying different kernel version may help to get the hardware to show up, that's the  only thing left to try. I googled too but there practically 0 info or linux-issues (beside the one you posted in the gentoo forum) related to your card.

---

### Post by ClientAlive on 2011-08-21
> **fdrake said:**
> thought maybe it was the 64 bit the problem (usually it happens with driver issues not to work properly), since most of the win driver i found for your card were 32bit .  :(

the fact that it doesn't show up as a device is out of driver issues or even kernel (maybe). Maybe trying different kernel version may help to get the hardware to show up, that's the  only thing left to try. I googled too but there practically 0 info or linux-issues (beside the one you posted in the gentoo forum) related to your card.


Thanks fdrake. I was just thinking this morning that maybe I can find a way to get it plugged into the router with a cat 5 cable. The location of the router in the house, compared to where the computer is, would make that a little challenging but not impossible. Then maybe I could do my compile and get the system up and running and worry about the card later.

If I were to look for the right thing in my kernel config, I wonder what I would be looking for, for that card. What information do I need to know or what config setting do I need to look for to make sure the kernel I compile supports it? If I were to end up with a kernel that supports it, would I have to look into ndis wrapper to get it going the rest of the way?

I still have some research to do on the partitioning scheme to use for the system I want to build, so I'll be looking at that for a bit. Maybe by then something will come to me.  :)
--------------------------

Edit:

I just ran 3 distros live and ran:

```

ifconfig

```

with each one of them. What I saw was that the ethernet shows up and the system loopback shows up, but not the card (in all of the 3 cases). These are the distros I ran:

Adriane Knoppix - uses kernel 2.6.32.6
Xubuntu - 'I think uses' kernel 2.6.32.33 (that's what Ubuntu 10.04 LTS uses)
grml - not sure what kernel it uses.

Not sure where to go from here.

---

