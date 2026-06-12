---
title: "GMAMEUI Help"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by Devin_Smith on 2009-11-29
Hey I know people have probably asked for help with this only about a million times, but I've been trying for quite some time now to get my GMAMEUI to run some roms for me...
To make things easy, I'll just tell you what it says when I try to play Killer Instinct 2:
The following ROMs were not found:
ki2-l14.u98 NOT FOUND
ki2_l1.u10 NOT FOUND
ki2_l1.u11 NOT FOUND
ki2_l1.u12 NOT FOUND
ki2_l1.u13 NOT FOUND
ki2_l1.u33 NOT FOUND
ki2_l1.u34 NOT FOUND
ki2_l1.u35 NOT FOUND
ki2_l1.u36 NOT FOUND

I am currently trying to download a kinst2.chd file which I looked up somewhere as maybe being the problem... 
Please help, and thanks.

---

### Post by Devin_Smith on 2009-11-29
Bump

---

### Post by Devin_Smith on 2009-11-29
Bump

---

### Post by Devin_Smith on 2009-11-29
Bump

---

### Post by Devin_Smith on 2009-11-29
Bump

---

### Post by Devin_Smith on 2009-12-04
Bump

---

### Post by Devin_Smith on 2009-12-06
Bump

---

### Post by WishMaster on 2009-12-11
Your missing roms can be found here: [http://www.rom-world.com/file.php?id=23031](http://www.rom-world.com/file.php?id=23031)

I can't get mame running... Installed xmame, gmameui,... but it asks for executables??

---

### Post by Devin_Smith on 2009-12-11
It still says those files are not found... perhaps I am not putting them in the directory correctly? I apologize for being a GMAMEUI and Linux Nooblet... ^.^;;

---

### Post by Devin_Smith on 2009-12-12
Bump

---

### Post by nch0930 on 2009-12-20
I'm trying to play Killer Instinct too.
Under Options > Directiories I've added the folders where I placed the downloaded roms.
I downloaded this [http://www.rom-world.com/file.php?id=23032](http://www.rom-world.com/file.php?id=23032)

But I just don't find it anywhere on the program.

If I click under Originals, I can find many Killer Instinct games but, after right clicking on it and choosing Play, I get the same error as Devin, "ki2_l1.u11 NOT FOUND".

How do you download this games that appear on the lists?

Thanks.

---

### Post by Devin_Smith on 2009-12-23
Bump

---

### Post by irfanrahman on 2009-12-24
I think I can answer your question regarding MAME ROMs in general.

Killer Instinct is one of the games that requires both ROM and HD image (.CHD files contains additional graphics and sounds). You can't play without one or the other.

Many ROMs (found as ZIP archives) contains files usually end with *.uxx as well as some bios file if needed.

Also, with each update of MAME, rom file changes for that particular release (i.e. 135 is current). So, you may need that .uxx file in version 109, but not with 135.

I just installed SDLMame with GMAMEUI on Ubuntu 9.10, loaded all ROMs and ran, but could not get out of the fullscreen. I guess, I gotta look for keyboard keymaps. I also have X-Aracde dual controller which I have to test.

---

### Post by dunkirk on 2010-01-02
You have to tell MAME the directory where you put your ROM's. This is done on the command line with `-rp </path/to/roms>'. Various GUI's deal with passing this information to your chosen MAME executable in different ways. I don't see an option for specifying where to put the CHD files in gmameui, so I think it's expecting to find the CHD's in a "chd" subdirectory underneath the directory where you put your ROM's. Just a guess though. I haven't played many CHD games because they're usually too slow on machine. However, that being said, Area 51 -- with mouse support -- WIN!

---

### Post by Devin_Smith on 2010-01-02
I finally got it to run but it runs very slowly and is not even what you would call playable. When you first boot it up it says one or more files is corrupt or missing but my friend suggested that i just might not have the hardware to run it. 
I have an Intel Celeron processor 540 (1.86 GHz, 533 MHz FSB, 1MB L2 Cache)
Up to 252MB Mobile Intel Graphic Media Accelerator X3100
2GB DDR2
Let me know what you think.
Thanks

---

### Post by Devin_Smith on 2010-01-16
Bump

---

### Post by Devin_Smith on 2010-01-21
Bump

---

### Post by Devin_Smith on 2010-01-23
Bump

---

### Post by Devin_Smith on 2010-02-03
Bump... Again!

---

### Post by Devin_Smith on 2010-02-12
Bump once more!

---

### Post by 80aless on 2012-10-27
in options > gmameuipreferences > DO NOT "use mame default options"!

---

