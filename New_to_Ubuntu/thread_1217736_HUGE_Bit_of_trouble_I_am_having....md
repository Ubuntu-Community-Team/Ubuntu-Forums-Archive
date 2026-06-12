---
title: "HUGE Bit of trouble I am having..."
date: 2009-07-19
forum: New to Ubuntu
---

### Post by aperture123 on 2009-07-19
Hello forum helpers, here is my problem for the day.....well actually, week.
I have used the acer aspire one and have installed Ubuntu netbook remix on it. However, I was forced to delete the partition, and as a result grub pretty much wouldn't let me in. So what do i do next: reinstall UNR. The next problem was I didn't create a new partition and so XP had been overwritten. Yea, AWESOME I thought. Now, I created a partition about 80 GB of unallocated space. I then serched online to find how to install XP from usb. I have a 8GB flash drive, and my other computer running vista. I came across two site:
[http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html](http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html)
[http://myeeeguides.wordpress.com/2008/11/15/winsetupfromusb-install-windows-xp-from-usb-flash-drive/](http://myeeeguides.wordpress.com/2008/11/15/winsetupfromusb-install-windows-xp-from-usb-flash-drive/)

After debating, I choose link #2.
So: (doing this all on vista) I configured my 8GB (runnning everything on admin of course) formatted to NTFS (it said it was faster to do it as that) and then PEToUSB wasn't working. So, I selected files (which I mounted, explained below) and it worked fine. I then booted from usb, and setup WORKED! I choose the first step and it said "DO NOT REMOVE USB FROM COMPUTER DURING SETUP". Well, suffice to say, I did. I then tried to boot back up and lo and behold, it said it was on "step two and told me to pick what to do, but no choice or F8 menu option works because of "hal.ll" error. I then googeled what to do for that error and got the message to just copy/paste and replace curropted one with new one.
FYI: Didn't work.
SO!
I then booted my OTHER 8GB with ubuntu install live usb on it and selected partition editor, scanned for any bad stuff in the unallocated partition that files were being written on, nothing bad, merged with Ubuntu, then re-unmerged.
IT WAS TIME TO TRY OPTION #1.
However, it involved PEToUSB. I found why it did not work: max is 2GB usb to use. 8 being bigger than 2 (look at me doing math ^_^) I used gnome partition editor to partiton my 8 to 2. The result was that vista pretty much saw it and all, but none of the installations worked. :( I even formated to fat16 which is what PEToUSB was supposed to do so I could skip it. FYI: everything was run as admin.

At this point in time I would LOVE to not go through with XP but, I need it. Not need as in want, but need as in NEEEEEED.

Anyone have any ideas, because I am out of em'
Also: maybe boot.ini is the problem, I hit display on ubuntu when I put usb in and was in ubuntu and it had the menu showing the whole menu thing that I cannot do anything in, but the SETUP txt had what was originally run the first time.......?


I also (since I had no xp install cd because none was provided for acer) used this:
[http://thepiratebay.org/torrent/4152774/Microsoft.Windows.XP.Home.Edition.SP3.OEM-_Untouched_](http://thepiratebay.org/torrent/4152774/Microsoft.Windows.XP.Home.Edition.SP3.OEM-_Untouched_)

I then used daemon tools to mount and selected the virtual drive to get files from.
Its the legal version (I think) and I do own my key still, so I am able to install from any XP home install cd.

:(HELP THIS POOR UNLUCKY SOUL UBUNTU COMMUNITY!!!:(

---

### Post by esalnoj on 2009-07-19
If you're having this much trouble getting an XP install, why don't you just install ubuntu fulltime and run XP in virtualbox3?

Are any of the programs you used in XP not easily repersonalized?

Also, it sounds like you already have an island OS with vista.

---

### Post by sandyd on 2009-07-19
he isn't capable of a virtual machine.
that computers a netbook.
1GHz, 1GB ram if im not mistaken.

---

### Post by themusicalduck on 2009-07-19
I used a program on Ubuntu that worked really well putting XP onto a usb stick. It was a while ago.. but I'm pretty sure it was UNetbootin.

It's in the repository and all you need to do is load up an iso file and select a USB drive. It's a bit awkward if you can't boot into anything at the moment.. If you have a spare usb stick you could boot into a live environment and do it from there. Or maybe reinstall Ubuntu first (or just grub if the last install is still there) then do it from that.

Also XP virtualmachine is possible with 1GB of ram. It ain't that quick but it's alright..

---

### Post by aperture123 on 2009-07-20
I think I have tried UNetbootin with the install before, but I cannot remember. I will try this. One reason for me wanting xp is because I can't seem to get any overclocking programs to work with the exception of GMABooster. I also have not tried any "virtual" applications, but I hear you can use programs like VMWare. Could that still run my games, having my pc overclocking??? It would seem kinda wierd inside of Ubuntu. Also, if I do get this virtual os kinda stuff, what program would you recommend? thnx:):popcorn:

EDIT: so far I clicked UNetbootin, the distro didn't show, but I had the iso, and the usb didn't show up. however, I could see it to the right on my screen, so I opened partition manager and saw that it was located in /dev/sdb1. I clicked show all drives (use with car) on the UNetBootin and clicked sdb1. It then started the writing. Interestingly enough, my usb wasn't showing any files copied, and I saw two new folders in the media directory. One was HOME/040Usb and the other NEW/040Volume. My usb used to be named HOME USB so I think thats where the first came from, and my usb is now called New Volume. Why is Ubuntu doing this???
Also I am unable to reformat or resize my usb, I think because its a "NTFS" format. I will edit again when its finished, and I think I will just drag the files over.

EDIT: ok, so, UNetbootin made a little bit of files in the home usb 040 directory and the same files and more in the New040Volume. I copied New040Volume files into the real usb New Volume. Restarted the computer, usb loaded first, and it said "BootMGR is missing. press Control+Alt+Delete to restart. Did that, and nothing happens. HOWEVER, this happened last time, it might be because of format, with WINSETUPFROMUSB. So, I don't think thats the problem. Interestingly enough, I checked the files and I found a "setup.exe" that looked really wierd, and couldn't install in Ubuntu. Maybe might boot manager is all messed up because I might have changed somthing......I dunno. Any help would be appreciated.

MORE EDITS: I have now reformatted the usb to default allocation size and fat32 format. Then I ran as admin on windows vista unetbootin and selected the iso and the usb (before I used unetbootin on Ubuntu). It ran EXTREMELY slow. I then opened my bios in ubuntu and set it to default settings, then enabled f12 to change boot order. I then plugged in my Live OS ubuntu (on my other usb) to test the f12. It worked, so I turned off the system, input the UNETbootin usb, and loaded it. I an interface which its only choice was to pick "default". However, when I clicked enter nothing would happen, but the automatic time until launch would reset to 10. I then waited 10 seconds, and it would just refresh back to 10. I hit f8 which launched a cmd at the bottom, but I don't know what to launch or write. I am at wits end, and will try to partiton my 8GB to 2, format to fat16, then use UNetbootin, then try again and hope for the best. If that doesn't work....I will put the Ubuntu Live iso on the usb to see if the usb is the problem.

FINAL EDIT: the ubuntu live iso worked on the usb, so that wasn't the problem. I then used the usb that had Ubuntu live already on it and used WInSetupfrom usb and it worked perfectly! unfortuanatlly, it wanted to install xp on the usb, and not my unallocated partition. I am left with no options left to try. I tried the 2GB partition on my usb and formatted to fat16, but that didn't work. Looks like the only way to install it is to either buy a 2GB usb (what will be my 3rd usb) or buy a external cd-drive (way too expensive). I recommend not to go through the trouble I went through, and perhaps I can use the vitual emulator....

Thank you everyone for your help...looks like I'm going shopping...

---

### Post by aperture123 on 2009-08-02
I bought a 1GB usb, installed xp, all went well, but now sound and internet doesn't work in XP. Wonderfull.....anybody know what to do?

EDIT: okay, downloaded drivers, but it asks for me to launch from usb everytime to make windows start, but I can take the usb out afterwards and its fine....did linux mess up the bootloader, cause I get this weird error saying xp can't launch from disk, check blah blah blah..any ideas?

---

