---
title: "How do I remove a line from grub2?"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by josephellengar on 2010-01-07
For some reason my grub2 has an entry for windows vista, when this computer only has Windows 7 and Ubuntu 9.10 on it.  I was wondering if anyone knew how I could remove the line for the Vista loader.  Thank you!

---

### Post by skatinjj on 2010-01-07
> **rossholley said:**
> For some reason my grub2 has an entry for windows vista, when this computer only has Windows 7 and Ubuntu 9.10 on it.  I was wondering if anyone knew how I could remove the line for the Vista loader.  Thank you!

[This]("https://wiki.ubuntu.com/Grub2") should have the information you are looking for plus some.

---

### Post by llawwehttam on 2010-01-07
Run ```
sudo update-grub
``` it should remove it.

---

### Post by josephellengar on 2010-01-07
> **llawwehttam said:**
> Run ```
sudo update-grub
``` it should remove it.

I did that.  It doesn't remove it.  For some reason it says that I have a windows vista loader on my /dev/sda2, when I definitely don't.  Windows Vista has never even been on this computer.  It's brand new.

---

### Post by ibuclaw on 2010-01-07
> **rossholley said:**
> I did that.  It doesn't remove it.  For some reason it says that I have a windows vista loader on my /dev/sda2, when I definitely don't.  Windows Vista has never even been on this computer.  It's brand new.

It probably can't differentiate Windows Vista from Windows 7.

When you type in:
```
sudo update-grub
```
What gets outputted into the Terminal?

Regards
Iain

---

### Post by josephellengar on 2010-01-07
> **tinivole said:**
> It probably can't differentiate Windows Vista from Windows 7.

When you type in:
```
sudo update-grub
```
What gets outputted into the Terminal?

Regards
Iain

I get this:
```

Generating grub.cfg ...
Found Debian background: grub-splash-wide.png
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done
ross@ross-laptop:~$ 

```

---

### Post by josephellengar on 2010-01-08
So, do you have any other ideas?  Not that it's incredibly important, it's just a little annoying- you know.  And the computer gives me an error if I select that option- it's not like it boots W7 or something.  Just a little weird.

---

### Post by benfindlay on 2010-01-08
The Vista entry is usually for Windows 7, but you report an error. You can edit the grub config file so that it is no longer present. I would imagine this is the same for grub2

---

### Post by Igniteflow on 2010-01-08
I'm not in Ubuntu right now, but type sudo nautilus into the terminal, then in nautilus navigate to the root directory, go to /boot/grub/ find menu.lst.  Right click this file, click edit and scroll down.  Towards the bottom you'll find the entry for Vista, just edit this text to Windows 7, save and exit.  

Ps. before editing menu.lst you should always make a backup

---

### Post by llawwehttam on 2010-01-08
> **Igniteflow said:**
> I'm not in Ubuntu right now, but type sudo nautilus into the terminal, then in nautilus navigate to the root directory, go to /boot/grub/ find menu.lst.  Right click this file, click edit and scroll down.  Towards the bottom you'll find the entry for Vista, just edit this text to Windows 7, save and exit.  

Ps. before editing menu.lst you should always make a backup


You have obviously used GRUB2 ITS CHANGED lol. I had a bit of a shock too when i tried to change the same sort of thing.


And to answer the earlier question I have a very stron suspicion that windows 7 uses the vista bootloader as well as its own.
Don't worry about it.

---

### Post by running_rabbit07 on 2010-01-08
> **Igniteflow said:**
> I'm not in Ubuntu right now, but type sudo nautilus into the terminal, then in nautilus navigate to the root directory, go to /boot/grub/ find menu.lst.  Right click this file, click edit and scroll down.  Towards the bottom you'll find the entry for Vista, just edit this text to Windows 7, save and exit.  

Ps. before editing menu.lst you should always make a backup

Grub2 doesn't have menu.lst.

---

### Post by Igniteflow on 2010-01-08
Thanks for the heads up guys, I need to get up-to-scratch obviously, has been a while since I've had to tinker with GRUB - which can only be a complement to the developers I suppose

---

### Post by running_rabbit07 on 2010-01-08
Hakuna Matata. I think Grub was much better with menu.lst when one wanted to fine tune their systems bot menu. Grub2 makes it easier for newer people who aren't into altering files.

---

### Post by llawwehttam on 2010-01-08
> **running_rabbit07 said:**
> Hakuna Matata. I think Grub was much better with menu.lst when one wanted to fine tune their systems bot menu. Grub2 makes it easier for newer people who aren't into altering files.

But to be fair GRUB2 is also a bit safer.lol i have screwed up grub too many times lol

---

### Post by oldfred on 2010-01-08
The brute force way is to copy your windows entry to 40_custom and in grub turn off the prober so it does not look for other systems. You would only need to turn the prober back on if you added new systems in the future.
add this entry to this file.
/etc/default/grub 
GRUB_DISABLE_OS_PROBER=true

I have seen where drs has modified the logic in the prober to ignore certain entries but never saved a link.

If you want to see what is installed in the boot sectors of sda2 this script is the best. If you really do not want what is in the boot sector then it may be possible to erase it so the prober does not find it.
Boot Info Script 0.44 courtesy of forum member meierfra.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions:  louieb's
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 
or as example if on desktop or  downloads directory from liveCD download:
sudo bash ~/Desktop/boot_info_script*.sh
or depending on where it downloaded
sudo bash ~/Downloads/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here, it can be big. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text, to make it easier to view.

---

### Post by josephellengar on 2010-01-08
All of this sounds a bit dangerous, so I think that I'll just leave it as is.  But thank you everyone for your help.

---

