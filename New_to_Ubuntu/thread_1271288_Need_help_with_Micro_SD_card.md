---
title: "Need help with Micro SD card"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by fignig on 2009-09-20
just got a 2gb micro sd card and it has the adapter that allows it to fit into the card slot. for some reason it doesn't seem to be mounting, and it doesn't show that it is reading the card slot. would there be something wrong with the card slot or what is it in general?

---

### Post by Paqman on 2009-09-20
If regular SD cards work in that slot then the problem is either you microSD or the adaptor. Have you got another machine you can try it in?

What type of computer have you got?

---

### Post by Jose Catre-Vandis on 2009-09-20
I got fed up with try to get my SD cards to read in a reader, and bought a USB key that takes SD cards off eBay for a £1.

Your problem probably lies with it being a Micro SD card or the newer standard of SD cards about at present. If you have a particularly oldish reader it won't read any of them.

---

### Post by fignig on 2009-09-20
my laptop is a dv5 1017nr, and it goes into the sd card reader.

---

### Post by The Cog on 2009-09-20
I believe that some card readers can be problematic, although I have been lucky with mine. Those little USB adapters are neat. Trouble is, micro SD cards are too small to write a decent label on so how are you supposed to know what's in them if you have a pile of them?

---

### Post by hambone79 on 2009-09-20
I don't know if this will help, but my Acer Aspire One won't read anything in the SD card reader unless a card is present when the computer is booted. It's almost like the card has to be there so that Linux will load the drivers for the reader.

---

### Post by sandyd on 2009-09-20
manufacturer of car dreader?
if its ricoh, download
[http://sourceforge.net/projects/sdricohcs/files/sdricohcs/0.1.4/sdricoh_cs-0.1.4.tar.gz/download](http://sourceforge.net/projects/sdricohcs/files/sdricohcs/0.1.4/sdricoh_cs-0.1.4.tar.gz/download)

extract it, and cd to the folder that you extracted it to using the terminal
```

make
make install
sudo modprobe sdricoh_cs

```

---

### Post by Rockroehre on 2009-11-04
Hi,

I have a similar problem on a ThinkPad R500.

When inserting an SD card into the card reader AFTER booting, there is a light for a moment, but then it switches off again.

This is what I get on entering blkid -L in the terminal:
> device     fs_type label    mount point    UUID[FONT=monospace]
[/FONT]-------------------------------------------------------------------------------[FONT=monospace]
[/FONT]/dev/loop0 squashfs         (not mounted)  [FONT=monospace]
[/FONT]/dev/sda5   ext3                         /karmic                                da77ff30-ee31-41c6-8fbf-c0209ff9fee3[FONT=monospace]
[/FONT]/dev/sda6   ext3                         /                                     6e247157-cca7-462a-8ce0-5a53e8747afe[FONT=monospace]
[/FONT]/dev/sda7   swap                         <swap>          f3371cc0-0e03-4cbb-9e80-f14127c66673[FONT=monospace]
[/FONT]/dev/sda8   ext3                         /ext3_data        41b61641-147b-4fcb-90df-ede2360cb4cb[FONT=monospace]
[/FONT]/dev/sda1                    (not mounted)
lspci gives the following:
> 
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)When inserting the card BEFORE booting, it is recognized and I can work with the data, but as soon as I unmount and eject it, it won't remount (blkid -L and lspci give the same results as above).


I wasn't sure whether the link above might help me, too...? I'm pretty new to Ubuntu, so I am a little reluctant to download it and find out via trial and error.

---

