---
title: "Ralink RT5592 drivers not installing"
date: 2014-07-05
forum: Networking &amp; Wireless
---

### Post by lonnez on 2014-07-05
I purchased an Asus PCI wireless card a couple weeks ago and I can't seem to install the drivers properly. I am very new to linux and I apologize in advance if I leave information out.

I first attemped to install the drivers via the driver disk it came with, but I keep getting a Linux 2 error whenever I try to "make" (if that is the correct terminology). I then found [this]("http://ubuntuforums.org/showthread.php?t=370108") thread and did the first two commands. Those successfully completed and then I created the "wireless-info.txt" file which can be found [here]("http://pastebin.ubuntu.com/7750037/").

I also attached the Linux drivers that came on the disk. There were other folders, but it was 200-300MB so I just uploaded what was inside of the Linux folder (a tar.bz2 file and a .txt file).

---

### Post by squakie on 2014-07-05
Is this an internal card or a USB dongle?  It's also important to understand the drivers aren't so much by brand, but rather by the chip(s) used on the adapter (chipset).  To know what we are dealing with, please do the following:

- open a terminal window (ctrl/alt/F1)
- at the text prompt, enter your userid and press enter
- at the password prompt, enter your password and press enter - note that nothing is echoed to the screen as you type the password

Eventually you should get to a prompt that ends in a dollar sign($).

For an internal card:

- type lspci | grep Network and press enter.  Copy the output and post it back here in a reply.

For a USB dongle:

- type lsusb and press enter. Copy the output and post it back here in a reply.

That will help us get started.  While not *always* the case, normally there is a way to get these things working without using a driver download like that.

I suspect what it may be, given that "STA" appears in the name of the download, but without that information we really have no way to start without assumptions - and we know what ususally happens with assumptions ;)

---

### Post by ajgreeny on 2014-07-05
I suggest you use Ctrl+Alt+T for a terminal, not Ctrl+Alt+F1 (which will take you to a tty command line, from which it is not as simple to copy text).  From the terminal highlight the text with your mouse then right click to copy; much easier!

---

### Post by squakie on 2014-07-05
> **ajgreeny said:**
> I suggest you use Ctrl+Alt+T for a terminal, not Ctrl+Alt+F1 (which will take you to a tty command line, from which it is not as simple to copy text).  From the terminal highlight the text with your mouse then right click to copy; much easier!

I take back everything I had here - I wasn't using ctrl/alt/F1 - I've been using terminal from the menus - the exact one same thing you get if you ctrl/alt/T.  I was just helping (well, *hopefully* ;) ) someone with a boot problem where they couldn't get the desktop, and wasn't away from that thinking when I posted here.  Thanks ajgreeny!   I suspect I've done this same thing in several other posts when it wasn't what I was thinking at all :(

---

### Post by varunendra on 2014-07-06
We made this card work with kernel 3.2 with the same driver supplied by Asus (**[this]("http://ubuntuforums.org/showthread.php?t=2203226&p=12918562#post12918562")** particular post after some discussion/testing), but the newer kernel code is no longer compatible to that driver's source code.

praseodym here has linked to a driver that is patched to compile on the newer kernels, but I am yet to see a success post using that driver. The ones I have seen are either incomplete threads or report freezing problem after trying that driver. If you wish to try, here's the post with instructions to compile it : [http://ubuntuforums.org/showthread.php?t=2217996&p=12997915#post12997915](http://ubuntuforums.org/showthread.php?t=2217996&p=12997915#post12997915)

Alternatively, you may try installing the much older 3.2 series kernel and try the first link above to get a tested solution. But probably a much more sensible alternative is to just get a cheap, compatible USB adapter if the patched driver suggested by praseodym doesn't work.

---

