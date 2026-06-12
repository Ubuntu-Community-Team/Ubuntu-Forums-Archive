---
title: "Upgrade BIOS with linux"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by bprins on 2010-12-12
Hi,

Who can help me with upgrading my BIOS in Linux. Now I know there are tons of tutorials, but I have a few handicaps:
- No floppy
- No CD rom
- No Windows/Dos boot partitions

So I am looking for a way to upgrade my bios with just:
- linux
- grub
- USB stick

Is that possible?

Please help.

Thanks, Bas

---

### Post by redbook4574 on 2010-12-12
> **bprins said:**
> hi,

who can help me with upgrading my bios in linux. Now i know there are tons of tutorials, but i have a few handicaps:
- no floppy
- no cd rom
- no windows/dos boot partitions

so i am looking for a way to upgrade my bios with just:
- linux
- grub
- usb stick

is that possible?

Please help.

Thanks, bas

wot machine is it ??

---

### Post by bprins on 2010-12-12
acer 5741g

---

### Post by VastOne on 2010-12-12
> **bprins said:**
> Hi,

Who can help me with upgrading my BIOS in Linux. Now I know there are tons of tutorials, but I have a few handicaps:
- No floppy
- No CD rom
- No Windows/Dos boot partitions

So I am looking for a way to upgrade my bios with just:
- linux
- grub
- USB stick

Is that possible?

Please help.

Thanks, Bas

Can your BIOS either boot from the USB stick or read from the USB stick while you are in the settings?

Yes to either of these and it is possible as I do it.  My Bios allows me to read from the USB and I had to flash it first with what it could read, a MS based file system

Google Update + Bios + USB + your motherboard manufacturer should give you a lot of info on this

---

### Post by bprins on 2010-12-12
Not sure if I understand you correctly, but my BIOS is not able to boot from USB (or read USB while its loaded), so I think I am bound to flash my BIOS from a running OS.

I have found a DOS emulator (xdosemu) which seems to work.

How unsafe is it to start the BIOS flash tool from within that DOS emulator?

---

### Post by bprins on 2010-12-12
Or, would it be possible to flash my ROM from within a virtual machine (I know that sounds a bit crazy :-), I am getting desperate)

---

### Post by Frogs Hair on 2010-12-12
Check the user manual for instructions and if you don't have one it is possible to download it . In my case the first bios was added with the motherboard setup cd prior to installing the operating system . This, most likely ,would have been done at the at the factory  on OEM computer . Knowing what is recommended may give you an idea what you can get away with .

---

### Post by Zill on 2010-12-12
> **bprins said:**
> Who can help me with upgrading my BIOS in Linux...
This may seem like a silly question but do you really *need* to upgrade the BIOS?

Will an upgrade provide new functionality *essential* to *you*?

If the answer is "no" then there is little point in upgrading a working BIOS.  There is also the possibility of ending up with an expensive door-stop if an upgrade goes wrong!

---

### Post by bprins on 2010-12-13
:-)

I can only agree with your comment.

Well it's not that I upgrade the BIOS just for the fun of it, but I am also not 100% sure that the problems I have will be solved. But virtualBox is throwing warnings that are supposed to be solved with BIOS upgrades.

Apart from that, in general (as software developer), I truly believe in the fact that bugfixes aren't implemented because "they had nothing better to do". So, maybe due to the same reason (being a software engineer) I have the unexplainable "need" of having the latest and greatest software available :-).

I think the latter is the biggest drive in getting this BIOS upgraded.

Which, I still haven't managed to do. I'll spend another evening in looking for ways to mimic floppy drives and using FreeDOS in order to achieve this ultimate goal :-).

Thanks for any help you guys can share with me,

Bas

---

### Post by Zill on 2010-12-13
Thanks for the explanation Bas and I wish you well :-)

If you do have any success in upgrading the BIOS using only FOSS tools then it could be very useful to others in the same situation if you would post a howto.

---

### Post by migs73 on 2010-12-13
> **bprins said:**
> :-)

 But virtualBox is throwing warnings that are supposed to be solved with BIOS upgrades.



Would that mean that Virtualbox requires a new BIOS?

---

### Post by Green_Bean on 2010-12-18
I just updated the bios on my Dell 4550 (circa 2002) which I have been running Ubuntu exclusively for the past 2 years. I needed to do that so I can add more memory. I found this link and followed the instructions there, it was very easy and my machine seems to be fine. No usb or cd needed, just internet access.

[http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate)

---

### Post by migs73 on 2010-12-19
> **Green_Bean said:**
> I just updated the bios on my Dell 4550 (circa 2002) which I have been running Ubuntu exclusively for the past 2 years. I needed to do that so I can add more memory. I found this link and followed the instructions there, it was very easy and my machine seems to be fine. No usb or cd needed, just internet access.

[http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate)

I've been looking for something like this for a while, great link, thanks.
I just need to be brave enough to try it!!!

---

### Post by bprins on 2010-12-20
I've cheated. I didn't manage to succeed with Linux so I installed win7 on a partition and upgraded the BIOS there (shame on me).

I'll close the thread.

---

### Post by Zill on 2010-12-20
> **bprins said:**
> ...But virtualBox is throwing warnings that are supposed to be solved with BIOS upgrades...
So, did your BIOS upgrade remove the VirtualBox warning messages?

---

### Post by gbestrada on 2010-12-20
> **Green_Bean said:**
> I just updated the bios on my Dell 4550 (circa 2002) which I have been running Ubuntu exclusively for the past 2 years. I needed to do that so I can add more memory. I found this link and followed the instructions there, it was very easy and my machine seems to be fine. No usb or cd needed, just internet access.

[http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate)


I followed the instructions of the link up to step of  [B]update the bios 
[/B]
**but** on the next step instead of :
# dellBiosUpdate -u -f ./bios.hdr-2.3.2 

I did this  sudo dellBiosUpdate -u -f Desktop/bios.hdr.
because i downloaded the bios file to my desktop,and if you do it the
 way the tutorial shows you'll get an error message.

hope it helps.;)

by the way this thread made my day

---

### Post by bprins on 2010-12-20
> **Zill said:**
> So, did your BIOS upgrade remove the VirtualBox warning messages?

piix4_smbus 0000:00:07.0: SMBus base address uninitialized - upgrade BIOS or use force_addr=0xaddr

Not really the expected end result. 

I guess the host BIOS is protected from within a VirtualMachine,  otherwise servers running virtual clients could mess up the host BIOS  pretty bad, so upgrading the BIOS to get rid of errors in VirtualMachine  was a pretty dumb idea I guess. 

But then again, I don't know what I am talking about :-). Just a dumb VirtualBox user.

---

### Post by bprins on 2010-12-20
> **bprins said:**
> piix4_smbus 0000:00:07.0: SMBus base address uninitialized - upgrade BIOS or use force_addr=0xaddr

Not really the expected end result. 

I guess the host BIOS is protected from within a VirtualMachine,  otherwise servers running virtual clients could mess up the host BIOS  pretty bad, so upgrading the BIOS to get rid of errors in VirtualMachine  was a pretty dumb idea I guess. 

But then again, I don't know what I am talking about :-). Just a dumb VirtualBox user.

I COULD have google-d to begin with.... :-)

[http://forums.virtualbox.org/viewtopic.php?f=2&t=21226](http://forums.virtualbox.org/viewtopic.php?f=2&t=21226)

And there I have confirmation that upgrading my BIOS was not the brightest choice of the day. :)

---

### Post by Zill on 2010-12-20
bprins:  On the plus side, at least you don't *seem* to have ended up with an expensive door-stop :-)

---

### Post by oldfred on 2010-12-20
A day late & a Dollar short, but just to provide a link for others that may find this thread:

HOWTO: Flash BIOS, The Ubuntu Way
[http://ubuntuforums.org/showthread.php?t=318789&highlight=usb+boot](http://ubuntuforums.org/showthread.php?t=318789&highlight=usb+boot)

---

