---
title: "help with a multiboot flash drive"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by xenolalia on 2009-01-01
Hi!

I'm trying to create a multiboot flash drive with ubuntu and a few rescue tools.  I've created four partitions on my flash drive: one for plain-old storage, one for ubuntu (I installed ubuntu to my flash drive because my drive is fairly large and durable), one swap partition, and one for the other misc. tools.  There are a lot of articles out there about how to put the tools I want (dban, winpe, super grub disk) on a flash drive and boot them with grub (instructions for editing a menu.lst, etc.), but being the beginner I am, I had a few questions about this procedure: a.) ubuntu already has a menu.lst -- will my flash drive work if I put another menu.lst on another partition of my flash drive?; b.) what would that look like -- would I see what looked like two separate flash drives (one for each menu.lst) when I go to boot up my flash drive, would my flash drive not boot at all, or would I just see one grub menu?; c.) does any of what I'm saying making any sense at all -- that is, do I know what the heck I'm talking about or am I totally confused 8-[?

Thanks very, very much in advance!
Xenolalia

---

### Post by mangcool on 2009-01-01
> **xenolalia said:**
> Hi!

I'm trying to create a multiboot flash drive with ubuntu and a few rescue tools.  I've created four partitions on my flash drive: one for plain-old storage, one for ubuntu (I installed ubuntu to my flash drive because my drive is fairly large and durable), one swap partition, and one for the other misc. tools.  There are a lot of articles out there about how to put the tools I want (dban, winpe, super grub disk) on a flash drive and boot them with grub (instructions for editing a menu.lst, etc.), but being the beginner I am, I had a few questions about this procedure: a.) ubuntu already has a menu.lst -- will my flash drive work if I put another menu.lst on another partition of my flash drive?; b.) what would that look like -- would I see what looked like two separate flash drives (one for each menu.lst) when I go to boot up my flash drive, would my flash drive not boot at all, or would I just see one grub menu?; c.) does any of what I'm saying making any sense at all -- that is, do I know what the heck I'm talking about or am I totally confused 8-[?

Thanks very, very much in advance!
Xenolalia
I dont really get what you're saying, but I think your point is to make a partition on Ubuntu using a flash drive.

Tell me more details. =)

---

### Post by xenolalia on 2009-01-01
I think I just need a basic explanation of using grub to boot things on a flash drive. I'm looking to find out what exactly a menu.lst is, how many of them there should be on my flash drive, and if it's possible and if so how to use the menu.lst in the ubuntu installation on my flash drive to boot things on other partitions of my flash drive.

For example, these posts: 

[http://www.911cd.net/forums//index.php?showtopic=18657&pid=122741&mode=threaded&start=](http://www.911cd.net/forums//index.php?showtopic=18657&pid=122741&mode=threaded&start=)

explain how to place/boot windows pe on/from a flash drive by creating and editing a menu.lst.  I want to know if it's possible to accomplish the same thing by editing the menu.lst in the ubuntu installation already on my flash drive.

---

### Post by caljohnsmith on 2009-01-02
If you are using Grub on your flash drive, then you only need to have one menu.lst, although you can actually have multiple menu.lst files and link to them in whichever is the main menu.lst that Grub uses on start up. For your case though it sounds like having one menu.lst is the way to go though, and it's fine to let Ubuntu stay in charge of the booting process and thus use Ubuntu's menu.lst. You should be able to just add entries in your Ubuntu menu.lst to boot the other tools that you mentioned, and it looks like you are all ready on the right track about figuring out how to do that. 

In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by xenolalia on 2009-01-22
Dear caljohnsmith,

Thank you so much for your speedy reply.  I've been having some weird (unrelated) monitor problems, and this is the first chance I've had to respond in several days.

Firstly, thanks very much for that script.  It's helped me to understand what's going on when I boot my flash drive.  I think though that where I'm still a little fuzzy is on the boot process itself -- things like: what does it mean to chainload something?  how is the way windows recovery utilities boot (with ntdlr and such) related to the way linux boots?  I find myself doing more and more googling, but I'm glad to know I'm on the right track.

Thanks again, and I'll be back with more shortly,
Xenolalia

---

### Post by xenolalia on 2009-01-22
Hi!

Since last I posted, I've been playing around with my flash drive a little, and I think I have a better idea of exactly what I want to do with it, so here it goes.  Here is basically how my flash drive looks right now:

Partition #1 (10.0 GB): storage
Just storage and a few misc. portable windows apps

Partition #2 (4.0 GB): boot
Contains a half-dozen or-so tools (e.g. super grub disk, ophcrack, ubuntu live) which I installed via unetbootin and am booting with syslinux.

What I'd like to do is replace the ubuntu live that I installed with unetbootin with a full-scale ubuntu installation (I've heard that it's possible and I think my flash drive is up to it).  Now ideally, I'd like to keep the tools I've installed with unetbootin, and I was wondering if anyone had any suggestions as to how to configure my flash drive such that: a.) a storage partition windows can see, and b.) a menu on boot through which I can have access to my bootable tools and a ubuntu installation.

Thanks very, very much!

Best,
Xenolalia

---

### Post by caljohnsmith on 2009-01-22
I think it would help to get a clearer picture of exactly how you have things setup on your flash drive, including the boot loaders, so how about running the Boot Info Script from my previous post, and let me know the results. We can work from there if you want.

---

### Post by djbushido on 2009-01-22
Also, just from a position of durability: is this a true flash drive, or usb hard disk? because if this is a flash drive, you might get a few years use new from it before it dies.

Also, as to the booting, a quick overview:
One partition in the filesystem can be marked bootable, that is, that the computer BIOS knows to boot from this.

GRUB is installed, which handles booting after the BIOS gives control to it. GRUB can be configured to boot multiple areas, i currently have a dual-boot of FC10 and Xubuntu.

UNetBootin, as far as i know, overwrites the boot record of the primary hard drive, so you should be able to uninstall this from the drive, install GRUB to your flash drive, and not have to worry about anything getting deleted.

The "menu.lst" file is a file that tells GRUB what to boot, how to boot it, and where to boot from.

The "chainloader" option tells GRUB to give complete control to the other partition's bootloader. This is necessary for Windows, because windows can only be booted via windows. If all the tools you are using are Linux-compliant, i.e. not windows or mac, then you shouldn't need a chainloader option, you should be able to use GRUB to handle these.

I understand that this isn't the most clear, so please respond with the script info, and any other questions you have.

---

### Post by xenolalia on 2009-01-22
Thank you both for your speedy replies!

I have attached the text file containing the results of the boot info script as well as a copy of the syslinux configuration file.

Also, here is a complete list of the tools I have on my flash drive (I was experimenting with a bunch ;)):

[LIST]
[*]Ubuntu Live
[*]Super Grub Disk
[*]Ophcrack (Windows XP & Windows Vista versions)
[*]Windows XP Recovery Diskette
[*]Memtest86+
[*]DBAN (preset in syslinux.cfg to "gutmann" mode)
[/LIST]
Thanks very much again!
Xenolalia

P.S. My flash drive is a true flash drive: Patriot XT 16 GB (which when converted to binary from decimal is really only about 14 GB).

P.P.S. I should also mention (just to clarify some of the details of the results of the boot script) that my desktop is an HP, I have XP installed on the main hard drive, and I'm booting ubuntu linux from a removable hard drive.

---

### Post by caljohnsmith on 2009-01-23
You've got me confused, because in your original post you mentioned that you have 4 partitions on your flash drive, i.e. storage, Ubuntu, swap, and other tools; yet the script results only show 2 partitions on your sdb flash drive. Is your goal to boot everything on the flash drive with Grub installed to the flash drive, or did you want to boot everything on the flash drive from your Ubuntu Grub on the sdg drive? Also, please post the output of:
```
sudo mkdir /mnt/sdb1 /mnt/sdb2
sudo mount /dev/sdb1 /mnt/sdb1 && ls -l /mnt/sdb1
sudo mount /dev/sdb2 /mnt/sdb2 && ls -l /mnt/sdb2
```

---

### Post by cwsnyder on 2009-01-23
Also, I haven't seen it mentioned here, but for a flash drive, your partition(s) for Linux should be formatted with ext2 or other (non-journal type) partition and NO, repeat NO, swap partition, unless you want your flash drive to die early.

Or at least that is what I have seen on the web.  Comments?

---

### Post by djbushido on 2009-01-23
Agreed, NO SWAP. This WILL kill the flash drive. Very fast. Also yes, use non-journal, partly the same reason as NO SWAP. Also, how are you storing utilities? Memtest86 is part of Ubuntu by default, Ophcrack can be installed to ubuntu. Don't know about super grub disk. Anyway, most of these can be installed in ubuntu. Is that what you're trying to do?

Also, as to the menu.lst (don't know if it got answered), grub boots one main menu.lst, but this can reference multiple other menu.lst(s).

And can we define what the problem is? I'm not quite sure how to answer a problem when I'm not entirely confident what the problem is.

---

### Post by xenolalia on 2009-01-23
I'm really sorry.  I should clarify: in the time since my first post, I have nixed the four partition setup in favor two partitions: one for storage (windows, misc.), one for booting (my bootable tools).  Though, I am willing to nix this setup too if there's something you think would work better.

What I'm aiming for in the end is something, anything, any configuration, that will allow me to a.) have a storage partition windows can see, and b.) a bootable menu (whether Ubuntu's menu.lst or otherwise) from which I can choose to boot ubuntu or any of my bootable tools.  At the moment, it's looking like a full-scale ubuntu installation would be the best way to go.  The only thing I need some help on is figuring out how to set up my flash drive to boot those tools I mentioned that I'm currently booting with syslinux from the menu.lst inside ubuntu.

Also, like djbushido suggested, if I end up with a full-scale ubuntu instillation, I think installing as many tools as I can in ubuntu (as opposed to booting them) would be a great idea.

And lastly, I just wanted to thank everybody who has responded for the great suggestions.  It really is helping clear up a lot of the (mis)understandings I had about how to make this happen.

Sorry for the confusion, and thanks again!

Best,
Xenolalia

---

### Post by djbushido on 2009-01-23
Okay then, now that we know what we're doing, we can help.
First of all - look at doing an ubuntu live usb. This will save a LOT of read/write cycles. Tutorial [here]("http://www.pendrivelinux.com/live-ubuntu-810-usb-persistent-install-windows/").

As to the storage, I recommend a fat32 partition at the beginning, but it looks like this has been set up.

You will need to have multiple partitions for some of the tools - super grub disk needs its own partition, but things like gparted, ophcrack, aircrack, etc. can go inside the persistent ubuntu.

So in summary, you will need more than 2 partitions. You can just set up grub to boot more than one.

Also, it would be nice to know what all tools you would like to use, so we can help with how many partitions you will need. and we here appreciate the thanks.

---

### Post by xenolalia on 2009-01-24
Hi again!

1.) Thank you all very much again.  You're posts have been *really helpful*.

2) djbushido: Thanks very much again for all the advice.  I'm curious, though -- do you think a full ubuntu installation would be bad for the flash drive?  I know very little about it, but I was thinking that the benefit of a full installation would be that I could install tools on the flash drive and keep them from session-to-session without a persistent setup.  Assuming that I do go with a ubuntu live setup, could I set it up in such a way that installed programs carried over from session to session?

3) Where did the "thank" buttons go?  I'd like to thank you all, but I can't find what I'm supposed to press!

Thanks again!

Best,
Xenolalia

P.S. I don't think super grub disk needs a separate partition, though.  As it is now my flash drive is set up with only two partitions, and I'm booting super grub disk, just like all the other tools from the second partition without any problems.

P.P.S. The only tool that I'd like to put on my flash drive other than the ones I already have is Vista Recovery Disk (for all my classmates who need help fixing their broken vista setups -- go figure ;)).

---

### Post by djbushido on 2009-01-24
Thanks appreciated (circle of appreciation!)
I don't know where the "thank" and "solved" buttons went either.

And as to the persistent install/liveusb install:

Hard drives deteriorate over time because of all the read/write cycles needed for a working computer. A flash drive is no different. However, the flash drive is not built for as many read/write cycles as the hard drive, because it is only flash memory, not a platter. So imagine a hard drive being used in a computer for a while. After a while, the drive will start losing stability, etc. because it's been used a lot. Again, same with flash drive, only in a MUCH quicker timeframe. The point of the persistent install is that it boots and runs like a livecd (storing all changes in memory) then writes these changes to disk when the session is over. This way, you keep the data, and don't slaughter your flash drive with all the read/write cycles like a psychopath would with a rusty knife. Nice metaphor, I know.

Point being, if you'd like your flash drive for more than 2 years, don't do the full install.

Now, I think I've stressed that enough. The persistent install will save changes, but won't kill your flash drive. It will take a bit longer to boot, but will again not kill your flash drive (at least for a while). So if at all possible, do the persistent install. I can help if you need it, I've done these before, with Fedora, Xubuntu, and Mandrake.

As to the Vista recovery disk, are you talking about the actual cd? I don't know how one would go about doing that, but i assume that it is much the same as a live usb. Rip the *.iso, extract to seperate partition, then point GRUB to it with "chainloader +1" to give it boot control. Don't actually know how to do this, but unless you hear otherwise, this should work.

Well, I think that's about it, and wish you the best of luck. Post any further questions, and we'll try and help you the best we can.

---

### Post by xenolalia on 2009-01-24
djbushido:

Thank you very much for all the useful info.  I'm setting up the persistent flash drive now.  I'll post back if there are any problems.  As to the Vista Recovery Disc, I have not a clue as to how to go about doing this.  I've tried a few thinks -- more or less shots in the dark -- none of which have worked.  I always get a black screen that looks as if it's about to boot, but then, I get a short string of gibberish, and I end up having to reboot manually.

One question, though: what would the grub entry for Vista Recovery Disc look like?  Would it just be "chainloader +1", or would I have to specify a "kernel" or "initrd"?  Also, do you think the procedure to boot Vista Recovery Disc from a flash drive with grub would be the same as with syslinux?

Anyhow, thanks again.

Best,
Xenolalia

---

### Post by djbushido on 2009-01-24
Okay. Good point, i forgot - persistent usb usually uses syslinux over grub. Sorry, my bad.

Anyway, the configuration files are basically the same, but different things need to be done. The recovery disc should be set up much the same way a linux .iso should be done. I don't know how to tell syslinux to release boot control to the vista disk, because this has its own bootloader. Thus, when syslinux both looks for a kernel, or a bootloader in the MBR, it doesn't find something it can use, and thus crashes. The kernel and initrd are actually the same thing as well.

As to the grub question, it NEEDS to be passed the "chainloader +1" argument so grub knows to give boot control to that partition.

As to the shots in the dark, my question is this: are you sure that you are copying the MBR code? because it might be that there is nothing in that partitions MBR to boot from.

And to answer some more questions of mine:
Are you using a linux distro already? If so, can you mount your usb drive, and post the output of this command: ```
ls /dev/disk/by-uuid -lha
```
This will tell me the UUID's of the partitions, making it much easier to debug grub.
Also, can you post the grub.conf/menu.lst that you are using?

Thank you, and I hope the persistent goes well. It took me a while to get the process down, so post questions you have.

So in summary, we need to make sure that the MBR of the vista disk gets copied, and make sure grub is actually pointing to the right partition.

Good luck.

---

