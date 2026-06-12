---
title: "Bios problems, 1st build"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by Garthhh on 2009-11-15
I'm trying to do my 1st build on an old used custom built machine [CBM]:
microstar 6368 version 5 MOBO
celeron 3 processor
500mb ram
maxtor 40g diamond plus8 HDD
tigerpro PSU
Award bios v6,00pg

[Gratitutious history paragraph]
CBM was a xp sp3 machine & just stopped about a year ago
I figured PSU & scrounged up an old 
dell optipex gx1.  
tried the dell PSU in the CBM, no joy
Tried to transplant the maxtor HDD in to the dell & do a XP repair install, got hung on the validation [damm dell built in product key]
Tried the tigerpro PSU in the dell, no power up at all
jumpped the enable bit on the tigerpro 20 pin & reinstalled in the CBM
IT'S ALIVE!:p

Back to the the CBM build
Set Bios to boot from CD
I get stuck in an endless loop, not booting from the 8.04 iso I burned on a HP vista laptop [which is a different tale of woe], I'm seeing xp start up screen...[must be booting from secondary device, which is HDD]
towards the beginning on a B/W screen I see 
PXE-E61 Media test fail

Help Please!:mad:

---

### Post by ktmom on 2009-11-15
I'm not sure, but try this - go into the BIOS-> BOOT options. Hit Shift+1 to disable the Realtek boot option.

---

### Post by falconindy on 2009-11-15
PXE is a network boot protocol. Have you checked the BIOS to make sure 'network' or 'pxe boot' isn't listed in the boot order?

---

### Post by arochester on 2009-11-15
Sounds like a bad burn. Check out "BurningIsoHowto" at [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Does the BIOS allow you to boot from a USB stick? The application called Unetbootin is available for Linux or Windows.

---

### Post by Garthhh on 2009-11-15
I'm not gonna have access to a working CD for several hours so I can't check or give more details about the iso burner program I used.

These are the same results I get when using a retail XP install disc 

The XP laptop I'm on doesn't have a working CD
I'm never sure if anything is working on the POS vista... I hate vista!!!!!!!!!!!!

---

### Post by Garthhh on 2009-11-15
I'm on the boot menu & don't see any choices other than hardware.
there are 
!st, 2nd & 3rd boot device choices
I see I can use usb devices.
I have a seagate 250g usb external, I store my music on [backed up to cd too]
let me read the guide & see if I can put the boot file on the seagate.

---

### Post by Garthhh on 2009-11-15
ok I don't understand
I'm using firefox 
download manager doesn't seem to give me a choice of where to save
unetbootin-windows-377.exe
I can't screw up this computer [xp laptop] it's the only one I understand & can keep working.  Screwing up my music back up [external HDD] means about 12hrs to reload the files & get everything back in order

all that said I'm not giving up, gotta do a few hrs work around the house , but i'll be back this afternoon

---

### Post by CharlesA on 2009-11-15
It's saved whatever you downloaded to either a downloads folder in My Documents or the desktop in Ubuntu.

---

### Post by ktmom on 2009-11-15
on Firefox, there is a setting under Preferences (either Tools menu or Edit menu depending on OS) on the Main tab where you define where a download goes.  You can configure Firefox to ask every time if you want.

---

### Post by Garthhh on 2009-11-15
oh thanks Charles
yeah I'll move it where I want it.
gotta clean that folder up

---

### Post by Garthhh on 2009-11-15
thanks
Yeah you right,
I remember now

---

### Post by Garthhh on 2009-11-16
I can't [or won't] use the usb drive, since it will wipe out my [music] backup.

I been trying to follow along on the vista machine, [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

my connection speed is pretty slow, so a regular download takes 8+ hours

I installed the infra recorder, I saved the bittorrent version of file how do I unpack it?

pinche vista ain't helping

---

### Post by bkratz on 2009-11-16
> **Garthhh said:**
> I can't [or won't] use the usb drive, since it will wipe out my [music] backup.

I been trying to follow along on the vista machine, [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

my connection speed is pretty slow, so a regular download takes 8+ hours

I installed the infra recorder, I saved the bittorrent version of file how do I unpack it?

pinche vista ain't helping




Do you a usb thumb drive at least 1 gig in size?  If so, it is quite easy to use unetbootin-windows-377.exe to create an equivalent to your cd you tried to make earlier and unplug the usb drive you are concerned about.   Does the file you downloaded have an extension of .iso? Bit torrents check themselves fairly well and you probably have a good download. If all these conditions apply just let me know.

---

### Post by Garthhh on 2009-11-16
Nope don't have a thumb drive
unemployed & am down to 3 blank cd's can't make anymore coasters...

the file reads:
unbuntu-8.04.3-desktop-i386.iso.torrent  
27kb-unbuntu.com

I thought I burned this once already, but mr vista can't open it, so I can't confirm the burn.
I don't get how I check the file or the burn?

---

### Post by Garthhh on 2009-11-16
ok got it
downloaded bitorrent6.3
unpacking [8.04] now
I don't do peer to peer so I haven't run into that stuff before
music sites are poison in windows 
& I've converted a bunch of lp's to mp3's
never came up 
learned something, cool

---

### Post by Garthhh on 2009-11-17
oh yeah,
install under way
Should have the link to:
[http://www.bittorrent.com/](http://www.bittorrent.com/)
and maybe a short explanation that it is like a zipped folder
switched CD writers & made the new one a slave & cooking right along

Thanks for all your help

---

