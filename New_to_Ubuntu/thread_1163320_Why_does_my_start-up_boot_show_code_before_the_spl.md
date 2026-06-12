---
title: "Why does my start-up boot show code before the splash screen"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by listerdl on 2009-05-18
Hi, I had a **really helpful** response when I first asked but unfortunately the tips they gave didnt work for me...(that thread is here: [http://ubuntuforums.org/showthread.php?t=1161846](http://ubuntuforums.org/showthread.php?t=1161846))

I was wondering if I might get lucky with someone reading this - basically, every time I start my ubuntu interpid - I have a "Reading Files to Reboot" and I receive loads of code that tells me that various things are [OK]

I have tried the trick of:

```
sudo gedit /boot/grub/menu.lst
```

I changed the settings to 'spalsh quiet' but unfortunately that didnt work.

THANKS I APPRECIATE ALL HELP!!!!

---

### Post by bswilson on 2009-05-19
Have you tried using the [Start-up Manager]("http://thedarkmaster.wordpress.com/2007/05/14/lets-customize-the-boot-sequence-with-start-up-manager/") to see if modifying those options helps?

---

### Post by Mornedhel on 2009-05-19
On the splash and quiet options :

'splash', when present, enables the pretty boot sequence (Ubuntu logo)
'quiet', when present, disables the verbose diagnostics scrolling

'splash quiet' is the default, with just the Ubuntu logo showing

Removing splash and quiet (I don't know what quiet without splash does, never tried) shows the "ugly" verbose diagnostics scrolling, console-style.

'splash' (no quiet) shows the Ubuntu logo and diagnostics in a prettier font than the console style, and has the added benefit that you can interrupt disk checking with ESC (I don't know how to do that with the ugly or the splash quiet styles).

However, when something goes wrong (wrong ranging from kernel panic to "hey, I have this mild warning that won't impact anything but maybe you should see it anyway"), the boot sequence may revert to the ugly style.

That being said, I don't know how to return to the other styles, other than fixing whatever causes a warning in the first place.

---

### Post by Didius Falco on 2009-05-19
> **listerdl said:**
> Hi, I had a **really helpful** response when I first asked but unfortunately the tips they gave didnt work for me...(that thread is here: [http://ubuntuforums.org/showthread.php?t=1161846](http://ubuntuforums.org/showthread.php?t=1161846))

I was wondering if I might get lucky with someone reading this - basically, every time I start my ubuntu interpid - I have a "Reading Files to Reboot" and I receive loads of code that tells me that various things are [OK]

I have tried the trick of:

```
sudo gedit /boot/grub/menu.lst
```I changed the settings to 'spalsh quiet' but unfortunately that didnt work.

THANKS I APPRECIATE ALL HELP!!!!

Hi,

I'd like you to check something: Open a Terminal shell and type ```
sudo blkid
```

then type ```
sudo cp /etc/fstab /etc/fstab.backup

```

I ***always*** back up system files before I edit them.

Then type ```
gksudo gedit /etc/fstab
```

Compare the UUID number for your swap partition in fstab to the output from blkid. If they are different, change the fstab UUID to match the blkid output and save. Be careful of the single quotes in blkid, you don't need those. That had me ready to tear my hair out once until I finally spotted it. <G>

Reboot and see if that fixes it.

I hope it helps...

Regards,

Didius

---

### Post by listerdl on 2009-05-19
Thanks for all replies - I dont have the time to try these fixes now but I am very appreciative of all help- Ill let you know how I get on in case this helps someone with the similiar issue.

---

