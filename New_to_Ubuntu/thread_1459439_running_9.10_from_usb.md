---
title: "running 9.10 from usb"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by Garthhh on 2010-04-21
I managed to install 9.10 on a 8gb usb flash drive
my laptop doesn't have a cd or the option to boot from usb
I've done a install by plugging in the new HDD into my desktop  & reinstalling in my notebook.
there are some problems, so I would like to do a fresh install from the stick [USB]

How do I get it to start?

---

### Post by Homicide on 2010-04-21
Your laptop's BIOS should have an option that will allow you to change the boot device. For instance, on my computer I can either press escape during boot to choose a boot device, or reset it through my CMOS settings.

---

### Post by WinterRain on 2010-04-21
If your laptop won't boot from usb, then you can't do it. Does it have a boot from removable device option?

---

### Post by Garthhh on 2010-04-21
> **WinterRain said:**
> If your laptop won't boot from usb, then you can't do it. Does it have a boot from removable device option?

I don't need to boot from it I need to run it like a live CD
as if I want to take a test drive.

my install has some issues, that I can't resolve, like no sound

I can't install across my network, since my ISP won't give me a static address, unless I pay them a fee every month
Is there a way to use a simple work group switch for this?

is there a way to do an install off the internet?

I'll try stuff, any suggestions?

---

### Post by Garthhh on 2010-04-21
the notebook is a gateway 7330gz
the bios is american megatrends [nor will gateway being linux now], but they won't support it being a custom version

there is a boot from floppy option, but no idea what port to access it from

the available ports are:
4-usb2.0
1-network
1-phone
1-for a cd
the cd has been bad for a few years, I have several fullsized cd/dvd's, but have not found a card extender adapter to allow this, plenty to do the opposite [use a laptop dvd in a desktop]

---

### Post by WinterRain on 2010-04-21
> **Garthhh said:**
> I don't need to boot from it I need to run it like a live CD
as if I want to take a test drive.


I realize that. You need to boot from the usb to be able to use it like a live cd. What boot options do you have in the BIOS?

---

### Post by Garthhh on 2010-04-21
> **WinterRain said:**
> I realize that. You need to boot from the usb to be able to use it like a live cd. What boot options do you have in the BIOS?

so why can I stick the cd in my wife's vista laptop & have it take me for a test run?  cause of wubi?

some updates only partially install

I have the 9.10 iso on the notebook & on the USB that is mounted...

boot options:
hdd
floppy
network

---

### Post by Homicide on 2010-04-21
> **Garthhh said:**
> so why can I stick the cd in my wife's vista laptop & have it take me for a test run?  cause of wubi?

Live sessions boot and run everything off the CD. They all do that. USB is no different, assuming you can boot from it.

---

### Post by achase79 on 2010-04-21
I know it is kinda old school, but if you have a floppy drive you can make a bootloader disk to boot your usb just so you can install.

---

### Post by Garthhh on 2010-04-21
> **achase79 said:**
> I know it is kinda old school, but if you have a floppy drive you can make a bootloader disk to boot your usb just so you can install.

I do have a old floppy & a floppy disc, but I don't have a way to plug in an ide cable to the notebook or I would use a fullsized cd.

---

### Post by Garthhh on 2010-04-21
did a new install 9.10 by installing hdd in my desktop machine & booting from disc
this time I reinstalled it in the notebook before the final restart

still no sound,
but that's a different thread

I'll mark this one solved

---

### Post by gridd on 2010-04-22
> **Garthhh said:**
> I don't need to boot from it I need to run it like a live CD
as if I want to take a test drive.

my install has some issues, that I can't resolve, like no sound
[B]
I can't install across my network, since my ISP won't give me a static address, unless I pay them a fee every month[/B]
Is there a way to use a simple work group switch for this?

is there a way to do an install off the internet?

I'll try stuff, any suggestions?

you could try joining New Net  static ip and cheap as chips.

---

### Post by Garthhh on 2010-04-22
> **gridd said:**
> you could try joining New Net  static ip and cheap as chips.

tell me more
or at least define "cheap as chips"

---

### Post by amsterdamharu on 2010-04-22
If the laptop is a dual boot you might use unetbootin in windows. It will unpack the iso to C: and temporary change something in the boot record. When you start the computer off the harddisk it will give you a menu with the option to "boot from the cd" the cd is on your c: drive and now you can install it on any partition but C: (because that's the "cd").

Next time you start windows unetbootin will ask you to remove the unetbootin stuff or you can remove it under "add remove programs".

Unetbootin is allso available for linux (in synaptec package manager??) but it doesn't work so good there and you cannot install on the same parttition as where unetbootin unpacked the cd.

As for booting from usb a rule I found is the smaller the better, some pc's would boot from 512M but not from 2G drive while others boot off all of the usb drives.

---

### Post by Garthhh on 2010-04-22
> **amsterdamharu said:**
> If the laptop is a dual boot you might use unetbootin in windows. It will unpack the iso to C: and temporary change something in the boot record. When you start the computer off the harddisk it will give you a menu with the option to "boot from the cd" the cd is on your c: drive and now you can install it on any partition but C: (because that's the "cd").

Next time you start windows unetbootin will ask you to remove the unetbootin stuff or you can remove it under "add remove programs".

Unetbootin is allso available for linux (in synaptec package manager??) but it doesn't work so good there and you cannot install on the same parttition as where unetbootin unpacked the cd.

As for booting from usb a rule I found is the smaller the better, some pc's would boot from 512M but not from 2G drive while others boot off all of the usb drives.

when my original HDD went bad, I lost xp.
I have many more options, now that synaptic works correctly again
I suppose from what you're saying, repartitioning & dualbooting newer version would be a good plan...

when I was trying to fix the bad install, could I have put the 9.10 iso on a different partition & accessed it?

I'm still interested in getting the usb to work so I can demo unbuntu for other people,  many of these people are on older machines [xp]

the stick I have is an 8gb with only 9.10 on it, 8.15mb of files, 6.7gb free, does the overall size of the flash drive matter

---

### Post by amsterdamharu on 2010-04-22
> when I was trying to fix the bad install, could I have put the 9.10 iso on a different partition & accessed it?
Yes, you could have used unetbootin in the live cd and unpacked the iso on a partition not to be used by the install since the files used by the installer can be accessed. If you put the files on a partition to be used as swap, root or home the chances are that during the install it'll be formatted or overwritten and then they're gone

I used unetbootin to create a usb and would fit on 1GB usb. If you re-spin it and remove openoffice it would be smaller but could not get it under 512MB. I think a 1GB and 2GB flash drive go for a couple of bucks so it's not a big investment. 
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

Using unetbootin gave me good bootable usb's (can do it manually using syslinux but did not allways work).

Old bios laptop have choises what type of usb should be used namely FDD HDD and ZIP (I think) there was one pc I've tried everything on but still would not boot from usb. Disabling all the other boot options (HD CD Network) should have rendered the pc unbootable but when the usb failed it would just boot off HD so setting bios values on that pc didn't do much. Burned a CD for them and that worked fine.

---

