---
title: "My computer can't start up"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by jickstar on 2011-02-02
So, I run ubuntu 10.10 on a toshiba laptop that I got some years ago. I don't really know anything about computers.

A batch of updates came in and I just clicked install and reset without checking any of them and my computer could never really start again.

When I turn it on it goes straight to a screen with options to boot. Across the top it says: GNU GRUB version 1.98+20100804-5ubuntu3

and in a box below that it says:
ubuntu, with Linux 2.6.35-23-generic
ubuntu, with Linux 2.6.35-23-generic (recovery mode)
ubuntu, with Linux 2.6.35-23-generic
ubuntu, with Linux 2.6.35-23-generic (recovery mode)
ubuntu, with Linux 2.6.35-23-generic
ubuntu, with Linux 2.6.35-23-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)


it gives me the option of editing any command or opening a command line, but I wouldn't know what to do with either.

Please help, I've been stranded offline for a few days now, only being able to use my roommate's computer now and then.

Very desperate here.

---

### Post by jickstar on 2011-02-02
What happens when I try to start it up is probably sort of important but I forgot to tell you!

If I pick regular startup, say the first option, what happens is that the screen stays black forever except for a tiny _ underline that blinks. It is impossible to type and no button makes anything happen.

If I pick a recovery mode option, a lot of letters flash across the screen and then the screen says:

fsck from util-linux-ng 2.17.2
init: udevtrigger main process (347) terminated with status 1
init: udevtrigger post_stop process (350) terminated with status 1
init: udevmonitor main process (346) killed by TERM signal
/dev/sdal: clean, 275824/4702208 files, 6535973/18786560 blocks

If I pick a memory test what happens is that the computer does a memory test and I remain ignorant of what may possibly matter during the entire thing!

Very ignorant here, very desperate!

---

### Post by schnelle02 on 2011-02-02
I am also new to Linux but if you are VERY desperate you could burn an iso disk and install a fresh copy of ubuntu booting it in the disk drive.

---

### Post by taseedorf on 2011-02-02
Try picking this one
ubuntu, with Linux 2.6.35-23-generic

and seeing if it works.

It's probably hanging with your video driver (sometimes happens when installing a new kernel)

If you pick the first one, or any of them, and it hangs... press alt + 5 or alt +6 or any number and seeing if it gives you a login (the number may have to be an f6 key or whatever...)  that switches tty

---

### Post by jickstar on 2011-02-02
you know I actually did burn a new iso disc and even when I try to boot with that disc and start over completely it takes me to that grub menu.

pressing alt and some numbers like f1 when it refused to go any further made it say: udevd-work[328]: open /dev/null failed: No such file or directory

or by pressing alt and i think f6 it said that thing it had before with the udevtriggers and the udevmonitor and the processes terminated I don't have it in front of me right now

---

### Post by jickstar on 2011-02-02
On man please somebody help me. I burned like three new ubuntu discs, each time thinking they didn't work because of some mistake.

I've burned them at all different speeds and always as an iso file and I don't know what else to do. When I insert the cds and forgo startup to pick the disc optionit takes me to that grub menu. Please help me escape that terrible grub menu, everybody!

Anybody.

---

### Post by oldfred on 2011-02-02
I think you are past boot issues and into something not loading, but lets check boot first.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

