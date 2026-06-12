---
title: "[BTC Reward] Ubuntu14.04-&gt;Samba-&gt;OpenPS2Loader Config Problem"
date: 2015-10-06
forum: Networking &amp; Wireless
---

### Post by AnCapGamer on 2015-10-06
So, I really REALLY hate resorting to this, but I've tried everything that I can think of, and I simply can't get this PS2 Softmod feature to work properly, no matter what I do!

So, the idea is that I SHOULD be able to use this open-source piece of software for my PS2 called Open PS2 Loader to load game data from a shared folder on my computer directly into the PS2 without using the disc tray (a useful feature since my PS2's disc tray motor is broken). I've already gotten OPL installed and set-up on my PS2, but I can't seem to get it to connect to the shared folder on my computer.

I understand that if the problem is with the OpenPS2Loader program then it will be beyond the abilities of anyone on this forum to help, and that's fine, but at this point, I'm so frustrated from trying to get this thing to work that I'm willing to offer a $10 BTC reward to whoever ends up helping me track down the problem that I'm having.

So, here's what I've got so far:

Got my PS2 softmod with OpenPS2Loader installed: check

Ethernet cable connecting my PS2 through my router to my PC: check
(I later tried switching both cables out, as well as testing them with  other devices to ensure that the cables are good, they are)

Created a folder on my computer with the following directory substructure:
PS2->
->CD
->CFG
->DVD->
->->SLPM_655.55.DragonQuestV.iso
->->SLPM_667.50.FF12International.iso
->->SLUS_200.35.BaldursGate1.iso
->->SLUS_206.75.BaldursGate2.iso
->->SLUS_214.31.SMTDSRaidouVSSoulless.iso
->->SLUS_216.03.SoulNomadWorldEaters.iso
->->SLUS_218.90.ManaKhemia2.iso
->VMC
(This is the directory structure and file-naming scheme required by OpenPS2Loader. I've also replicated this substructure onto a USB drive and plugged  that in directly, and it worked fine, OPL was able to see and play them,  so I'm pretty sure this part is good too)

Installed Samba: Check

In Nautilus, I right-click the "PS2" folder and under the "Local Network Share" tab, checked "Share this  folder," "Guest access," and "Allow others to create and delete files in  the folder"; Check

Went into samba's smb.conf and put in the following settings (most of which probably aren't necessary, but I've been tinkering with it):
[global]
    lanman auth = yes
    read only = no
    guest ok = yes
    security = share

On my PS2 under OPL's Network Settings:
-PS2-
IP: 192.168.1.104
(pinged this IP from my computer, so I know it can see it)
Mask: 255.255.255.0
Gateway: 192.168.1.254
(pulled up my Gateway page to make sure this was the right address)
DNS Server: 192.168.1.254
(wasn't sure what to put here, so I set it the same as my Gateway address)
Ethernet speed and duplex settings: Auto
-PC-
IP: 192.168.1.65
(set this as a static IP for my computer, double-checked it after restart)
Port: 445
(went into my router and created a pinhole in the firewall for this port)
Share: PS2
User: Guest
Password: (Blank)


Okay, so far so good; Took a little trial-and-error to get this far, but  so far everything's good; I load up OpenPS2Loader, and cross my fingers.

A few seconds later, I get the following message:

301: Cannot log into SMB server

I've been working with the people on the forum dedicated to OpenPS2Loader, and at the moment the best lead I have is that my guest account needs to have permission to access and list the contents of the folder that I have set up - but that's just a guess. I don't know how to tell if that is a problem, and I wouldn't know how to fix it if it was.

If anyone has any advice, it would be greatly appreciated.

Edit/Update: After re-installing and updating Samba, and double-checking that all my login credentials and passwords match, I have managed to to get past the initial login problems. Unfortunately, I am now met with a different problem: while I seem to be able to connect just fine, the program doesn't seem to "see" any of the games I have loaded. Does anyone have any thoughts of things I should try?

---

