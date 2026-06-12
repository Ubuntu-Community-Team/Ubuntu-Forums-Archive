---
title: "Installing Ubuntu on a 'clean' Dell"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by yzoldowl on 2009-02-08
I am trying to install Ubuntu on a Dell which has been stripped of _all_ software.  It will not boot from the CD/DVD drive; I tried to change the BIOS so that it would, but didn't get any results.  So I went looking, and found that 1) I need to make a 3.5 floppy boot disk, and 2) I need to use that disk to boot the 'clean' machine.  One of the files I need is NTRawrite.exe but I found the link to [http://prdownloads.sourceforge.net/n...1.zip?download](http://prdownloads.sourceforge.net/n...1.zip?download) was broken, at least I could not access the site.  So I googled, but did not find this file anywhere else.  The other file, sbm.bin from the Ubuntu DVD, is too large to put onto a 3.5 floppy disk.  So now what do I do?

---

### Post by Osamabingandhi on 2009-02-08
How old is the computer? sounds like an old bugger. If it isn't too old you could try to start ubuntu with usb. Try the bios again, surely it have to be able to start from a cd. Boot Order where cd is first....

---

### Post by yzoldowl on 2009-02-09
Not very old, maybe a couple of years.  It does have USB ports, and is labeled '... for WinXP'.  Has Intel (R) Boot agent 4.0.17 and Intel Base-Code PXE-2.0 build 083.  From there I get "PXE-E61: Media test failure; check cable (But which one, do I need to take the cover off and take a physical look-see?  Or ... ?), and PXE-M0F:  Exiting Intel PXE ROM <new line> "Boot failure: System halted."

I am no rank beginner with computers in general but this one has me mystified!  BIOS _says_ its boot order is CD-ROM then everything else in order, but the CD-ROM does not respond with the Ubuntu DVD in it.  

Hmmmm, I think I just answered one of my own questions!  ;) I will "open the hood" and see if everything is tight inside.

---

### Post by snowpine on 2009-02-09
> **yzoldowl said:**
> the CD-ROM does not respond with the Ubuntu DVD in it.

I think you answered your own question here; if it is a CD-ROM drive, it won't be able to boot from a DVD. Try burning Ubuntu onto a CD instead of a DVD. :)

---

### Post by boof1988 on 2009-02-09
> **yzoldowl said:**
>  beginner with computers in general but this one has me mystified!  BIOS _says_ its boot order is CD-ROM then everything else in order, but the CD-ROM does not respond with the Ubuntu DVD in it.

Is the CD-ROM able to read both CD and DVD?  If it can only read CD-ROMs, and the install media is on DVD that could possibly be an issue (though you drive is probably a CD/DVD drive).

---

### Post by yzoldowl on 2009-02-09
Thanks, Snowpine; I'm _hoping_ that Ubuntu will soon be with me!  I'm getting heartily sick and tired of Windoze with all its "buy this, buy that" dreck...

Boof, yes:  it's labeled as a CD/DVD drive.  When I insert _any_ sort of disk in it, it does not respond, except to light up and spin, then stop.  I tried to put DOS 6.2 into the machine with my set of 3.5 floppies, and it did boot to the "A" drive, but told me my DOS disk 1 (of 3) was non-system or system disk error.  So I tried reverse order (Disk 3 first), and got the same thing.  

One of the things that's confusing me:  when I went to the BIOS, the "A" drive wasn't even mentioned!  Yet it boots first in the queue?!

---

### Post by lkraemer on 2009-02-09
Does your Ubuntu LiveCD boot in another machine?

You should always:
1.  Verify the downloaded ISO MD5SUM to what is published.  That
    will verify it downloaded properly.
2.  Burn as DAO (Disk at Once).
3.  Burn at 4x or 8x or as slow as possible.
4.  Use good media and try it on more than one machine.

lkraemer

---

### Post by mc4man on 2009-02-09
Dells usually have a boot menu, the bios setting is ineffectual.
It's tends to be F12, try tapping that when you power up.

---

