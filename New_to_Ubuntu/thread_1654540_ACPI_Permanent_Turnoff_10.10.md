---
title: "ACPI Permanent Turnoff 10.10"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by IWantFroyo on 2010-12-28
I need to turn off ACPI permanently. I found an outdated thread that got me into Ubuntu again, but then it stops working. I tried sudo gedit /boot/ grub, but I couldn't edit the file (vmlinuz-2.6.35-22-generic). Can someone help me?
What I'm trying to do is edit the kernel /boot/vmlinuz-2.6.35-........=/dev/sda1 to
..................................=/dev/sda1 ro acpi=off noapic
[CENTER][LEFT][LEFT]
[CENTER][LEFT][LEFT]           





[/LEFT]
[/LEFT]
[/CENTER]
     
   
     
         
              [/LEFT]
     [/LEFT]
 [/CENTER]
    
     [CENTER]     [LEFT]         [LEFT]                                                    [CENTER]         [URL="http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2048616"]
[/URL][/CENTER]
  
                       
                  [/LEFT]
[/LEFT]
[/CENTER]

---

### Post by davidmohammed on 2010-12-28
not really enough info to diagnose...


why?  what happens when you dont  - error messages displayed when booting?

what computer specs are you using?

Have you tried any specific boot options other than acpi=off and noapic?

---

### Post by IWantFroyo on 2010-12-28
I'm editing the command line to insert the ro acpi=off noapic in gedit, but it won't open it. Do you know something that could open and edit (and save) command line?
I'm using a Toshiba (T235D S1360). Toshiba has problems with acpi, which I didn't know when buying. Ubuntu just won't start with acpi, even if just from a live disk or usb. I tried 4 different cds and a usb. Gparted worked though...

---

### Post by davidmohammed on 2010-12-28
if you want to permanently add those options then

gksudo gedit /etc/default/grub

then change the line
GRUB_CMDLINE_LINUX=""

GRUB_CMDLINE_LINUX="noapic acpi=off"

save

then run

sudo update-grub

---

