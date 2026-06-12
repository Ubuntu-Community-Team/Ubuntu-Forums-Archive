---
title: "Slow machine, system logs bursting"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by madnessjack on 2009-12-19
Hey guys,

I'm on Karmic, 32 bit. My CPU is silly high and the machine is being slow. The log files keep growing over and over with the following lines. These logs are also hundreds of meg in size. It also makes it hard to type commands using only a terminal.
```
Dec 13 13:54:51 bulbasaur kernel: [ 1783.512447] ata4.01: configured for PIO4
Dec 13 13:54:51 bulbasaur kernel: [ 1783.513091] ata4: EH complete
Dec 13 13:54:51 bulbasaur kernel: [ 1783.516020] ata4: drained 32768 bytes to clear DRQ.
Dec 13 13:54:51 bulbasaur kernel: [ 1783.584267] ata4.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec 13 13:54:51 bulbasaur kernel: [ 1783.584275] ata4.01: ST_FIRST: DRQ=1 with device error, dev_stat 0x59
Dec 13 13:54:51 bulbasaur kernel: [ 1783.584289] ata4.01: cmd a0/00:00:00:24:00/00:00:00:00:00/b0 tag 0 pio 36 in
Dec 13 13:54:51 bulbasaur kernel: [ 1783.584291]          cdb 12 00 00 00 24 00 00 00  00 00 00 00 00 00 00 00
Dec 13 13:54:51 bulbasaur kernel: [ 1783.584293]          res 59/00:01:00:24:00/00:00:00:00:00/b0 Emask 0x2 (HSM violation)
Dec 13 13:54:51 bulbasaur kernel: [ 1783.584298] ata4.01: status: { DRDY DRQ ERR }
Dec 13 13:54:51 bulbasaur kernel: [ 1783.584332] ata4: soft resetting link
```
I have no idea literally no idea what they mean.

Could anyone give us any hints as to where I should be looking, or fire some magic commands to make it stop or fix it?

Many thanks in advance :)

---

### Post by btmiller on 2009-12-19
Do you have an ATA hard drive in the machine? It looks to me like it or the controller is potentially going bad. I'd suggest making a back-up copy of your data before proceeding further. Can you give us some specs on your machine?

---

### Post by madnessjack on 2009-12-19
Yeah sure,

I've got a 2 harddrive, one connected via IDE and one via SATA. Sorry, not sure what command I need to spit out a more detailed hardware report.

---

### Post by madnessjack on 2009-12-19
Sorted!

Unplugged internal CD/DVD drive. Must be duff. Don't really use it much these days.

Oh joy, everything is so smooth. :P

Thanks anyway :)

---

