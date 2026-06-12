---
title: "BIOS Flashing With Ubuntu"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by tb75252 on 2010-09-26
Absolute beginner using Ubuntu 10.04 LTS.
I have an old Dell Dimension 4600 and would like to flash its BIOS.  (I have a hang problem when AC power is removed and the new BIOS version solves that!)

Dell provides the new BIOS file but of course it is a Windows/DOS file.

Is there an _easy_ way to launch the file from within Ubuntu?  I am hoping for some sort of utility that does not require all those obscure, complicated Terminal commands that Linux pros seem to prefer...

PS:  I am fully aware that flashing the BIOS can lead to problems, but I am resolute about it!

---

### Post by JustinR on 2010-09-26
**_This doesn't work on all Dell computers - but its the most hassle free._**

If you have a Windows install laying around (doesn't have to be your computer or a Dell, just a computer with Windows), open up a Command Prompt.

Type 'BIOSFILE.EXE -writehdrfile' then it will extract the BIOS file you need. Put the BIOS file on a flash drive, and shutdown your Ubuntu computer.

Plug the flash drive into the computer, and press **and hold** the 'END' key and press the power button. The Battery light should change to a different color (eg. Amber) and wait for it to turn off - and that's it - your BIOS should be updated.

I can clarify if needed - I've tested this and it updated my BIOS successfully without bricking the computer.

---

### Post by tb75252 on 2010-09-26
> **JustinR said:**
> **_This doesn't work on all Dell computers - but its the most hassle free._**

If you have a Windows install laying around (doesn't have to be your computer or a Dell, just a computer with Windows), open up a Command Prompt.

Type 'BIOSFILE.EXE -writehdrfile' then it will extract the BIOS file you need. Put the BIOS file on a flash drive, and shutdown your Ubuntu computer.

Plug the flash drive into the computer, and press **and hold** the 'END' key and press the power button. The Battery light should change to a different color (eg. Amber) and wait for it to turn off - and that's it - your BIOS should be updated.

I can clarify if needed - I've tested this and it updated my BIOS successfully without bricking the computer.

Thanks for your suggestion.

a)  I don't have a flash drive but I can probably purchase one.  (However my BIOS does not allow to boot up from a USB device, in case that matters.  Can this be done with a CD-R instead?)

b)  I don't understand the part "Type BIOSFILE.EXE -writehdrfile".  I imagine that I need to substitute BIOSFILE.EXE with the actual name of the BIOS file (in my case D4600A12.EXE).  But what is this "-writehdrfile" thing?  I've never seen a DOS/Windows command like that...

---

### Post by RetchingRabbit on 2010-09-26
You should be able to download a copy of [freedos]("http://www.freedos.org/"), which likely will handle a bios flash.

---

### Post by Clever_Username on 2010-09-26
I looked around for information on the -writehdrfile switch mentioned, and I came across this [link ]("http://www.symantec.com/connect/articles/properly-extracting-hdr-files-non-packaged-dell-bios-update-packages-use-dell-client-manage")to Symantec

---

### Post by the-edmeister on 2010-09-27
Most manufacturers have a BIOS flashing application that fits on a floppy disc for older PC's, along with the new BIOS, and installs the new BIOS from command line - doesn't need Windows or DOS. Hopefully you still have a floppy drive installed on that older PC.
[http://search.dell.com/results.aspx?s=gen&c=us&l=en&cs=&cat=sup&k=bios](http://search.dell.com/results.aspx?s=gen&c=us&l=en&cs=&cat=sup&k=bios)

BTW, the ability to boot from USB usually accompanies the manufacturer using a 2Mb BIOS, instead of 1MB or less that would fit on a floppy.

---

### Post by JustinR on 2010-09-27
> **tb75252 said:**
> Thanks for your suggestion.

a)  I don't have a flash drive but I can probably purchase one.  (However my BIOS does not allow to boot up from a USB device, in case that matters.  Can this be done with a CD-R instead?)

b)  I don't understand the part "Type BIOSFILE.EXE -writehdrfile".  I imagine that I need to substitute BIOSFILE.EXE with the actual name of the BIOS file (in my case D4600A12.EXE).  But what is this "-writehdrfile" thing?  I've never seen a DOS/Windows command like that...

A Floppy disk or USB flash drive would be best - most likely a CD will fail.

And BIOSFILE.exe is the actual BIOS flash file. and '-writehdrfile' is like any other command line arguement.

Trust me, it will be the easiest to do.

---

