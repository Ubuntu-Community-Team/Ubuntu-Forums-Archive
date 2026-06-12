---
title: "Exactly what is GRUB?"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by gobberpooper on 2009-07-29
Every time I boot I see this message about pressing ESC to start GRUB. This update installed last night disabled my NVidia accelerated graphics driver and just getting to the log-in screen was a major headache. So I decided to use GRUB to see if it was some sort of recovery tool. I used it and I could boot using previous versions of Jaunty 9.04, and now my driver is enabled and I can play Oblivion, Guild Wars, Savage 2 etc perfectly.

Because GRUB completely saved my system, I'd like to know what it actually is and how I can use it. Can anybody explain it to me or point me to an in-depth guide?

---

### Post by W4l0ck on 2009-07-29
GRUB is like a boot loader, it is the same as boot.ini in windows.

---

### Post by decoherence on 2009-07-29
GRUB is the GRand Unified Bootloader. It allows you to pick which system you would like to boot. If you had a Windows dual-boot setup, you would use GRUB to decide between Ubuntu and Windows.

[http://en.wikipedia.org/wiki/GNU_GRUB]("http://en.wikipedia.org/wiki/GNU_GRUB")

---

### Post by W4l0ck on 2009-07-29
You wouldn't use GRUB at all.

---

### Post by CaptainMark on 2009-07-29
Why does grub have two kernels of the same version of ubuntu on it, i think it loads this as standard, whats the difference

---

### Post by wojox on 2009-07-29
It's an acronym :D

---

### Post by W4l0ck on 2009-07-29
I know. n00b!

---

### Post by decoherence on 2009-07-29
> **CaptainMark said:**
> Why does grub have two kernels of the same version of ubuntu on it, i think it loads this as standard, whats the difference

They aren't two kernels of the same version. One is the default boot and the other is a recovery boot. Same kernel, just different boot arguments to put the system in 'recovery mode.'

Ubuntu also keeps several of the previous kernels (and their recovery modes), as the OP discovered.

---

### Post by W4l0ck on 2009-07-29
They are all seperate parts of the kernel.

---

### Post by niteshifter on 2009-07-29
Hi,

In depth about GRUB [here]("http://www.gnu.org/software/grub/") (gnu.org).

You've already discovered one of it's handier features: lifesaver ;)

---

### Post by W4l0ck on 2009-07-29
Lifesaver?

---

### Post by CaptainMark on 2009-07-29
So these others are old kernels, even though they are both for 9.04? ```

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        757e303a-9af3-4ade-8fe4-5b50df0e3cea
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=757e303a-9af3-4ade-8fe4-5b50df0e3cdr ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        757e303a-9af3-4ade-8fe4-5b50df0e3cea
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=757e303a-9af3-4ade-8fe4-5b50df0e3cdr ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        757e303a-9af3-4ade-8fe4-5b50df0e3cea
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=757e303a-9af3-4ade-8fe4-5b50df0e3cdr ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        757e303a-9af3-4ade-8fe4-5b50df0e3cea
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=757e303a-9af3-4ade-8fe4-5b50df0e3cdr ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        757e303a-9af3-4ade-8fe4-5b50df0e3cdr
kernel        /boot/memtest86+.bin
quiet
``` Sees, they seem to be different kernels but what does that mean exactly

---

### Post by Zorael on 2009-07-29
*nod*

With some minor terminal knowledge, using recovery mode you can restore/repair or at the very least salvage an installation when it's borked to hell and back.

If you're using the proprietary Nvidia driver and one day X doesn't load after doing some upgrades, you could just start up in recovery mode, hit 'fix X', and get it to load the non-accelerated nv driver instead. Then you can work on getting the proprietary driver working again from inside the desktop environment, as opposed to just hacking away at a terminal.

So while you *could* remove all other kernels than the one you're using, and remove recovery entries from GRUB completely, you get less leeway in case you upgrade to a bad kernel (for your hardware), and you'd need to know how to boot into recovery/single mode by modifying your normal boot option. So, advised against.

---

### Post by philinux on 2009-07-29
Installing startupmanager can tidy grub up to your liking. I always like having 2 kernels showing just in case a new one plays nasty.]

[apt://startupmanager](apt://startupmanager)
[URL="http://apt/"]
[/URL][ ]("http://apt/")

---

### Post by W4l0ck on 2009-07-29
What is lifesaver?

---

### Post by decoherence on 2009-07-29
> So these others are old kernels, even though they are both for 9.04?

Technically they're the same kernels, but older releases.

For instance, your first entry is for version 2.6.28-13 while the third one down is 2.6.28-11

That means they are the same version of the kernel, but different releases, usually for bug/security fixes.

---

### Post by decoherence on 2009-07-29
> You wouldn't use GRUB at all.

is that directed at me?

for dual booting windows and linux, yes you would use grub. or you could use the BIOS to select a startup disk, but that doesn't relate to OP's question.

> What is lifesaver?

a joke. as in; grub's best feature is that it can 'save your life'

---

### Post by philinux on 2009-07-29
I set up a laptop to dual boot ubuntu. Vista was on it.

I used easybcd to modify it's bootloader.

---

### Post by W4l0ck on 2009-07-29
Whatever works.

---

### Post by niteshifter on 2009-07-29
> **W4l0ck said:**
> What is lifesaver?

Ok, in more precise language: time saver. 

As others have pointed out, sometimes a kernel update doesn't do well. Graphics can break, sound can break for example. However, the system used to work - right up to when the new kernel started being used.

So via GRUB you roll back by booting into the previous kernel and you have a working system again, one you can use to search around (google, this forum) to see if others are having the same problem (and maybe a fix for it). Or work on the problem yourself, try the repair boot - you restart into the new to test fixes.

---

### Post by W4l0ck on 2009-07-29
My sound broke, you wanna tell me how I was to fix that?

---

### Post by philinux on 2009-07-29
> **W4l0ck said:**
> My sound broke, you wanna tell me how I was to fix that?

Please start a thread of your own with a specific problem.

---

### Post by GailGaby on 2009-07-29
Where can I find a Grub that works with Vista

---

### Post by W4l0ck on 2009-07-29
I don't think you can.

---

### Post by philinux on 2009-07-29
> **GailGaby said:**
> Where can I find a Grub that works with Vista

Grub is grub what exactly do you mean?

---

### Post by llamabr on 2009-07-29
> **W4l0ck said:**
> I don't think you can.

Grub works just fine with vista, by default.

---

### Post by W4l0ck on 2009-07-29
Oh, ok then.

---

### Post by Ji Ruo on 2009-07-29
> **GailGaby said:**
> Where can I find a Grub that works with Vista

Yes it does work fine with Vista. - But - it's much easier if Vista is installed before anything else. If you have ubuntu or another linux distribution on your computer and then try to add Vista, it will be more complicated to get it to work, whereas if you have Vista first then add ubuntu, it will be almost automatic. This is true with all Microsoft operating systems. You might say that they don't always play nice with others - they will kick up a fuss if they're not first in line (on the first partition). GRUB is like the smart teacher who knows how to get an unruly student to behave, by playing to their whims a little :)

---

### Post by SirBismuth on 2009-07-30
GRUB saved me when I had 8.04, and upgraded my Nvidia drivers.  This annoyed X for some reason, which then promptly refused to load.  Used recovery mode, removed the drivers, and all was well again, and X was happy.

SuperGRUB also saved me a lot of hassle once.

B

---

### Post by W4l0ck on 2009-07-30
Never heard of supergrub..

---

