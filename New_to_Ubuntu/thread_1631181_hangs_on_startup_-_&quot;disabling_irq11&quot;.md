---
title: "hangs on startup - &quot;disabling irq11&quot;"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by meermatt on 2010-11-26
Hello,

Have new install of Xubuntu 10.10 on my nearly geriatric toshiba tecra a4.

It boots well until it gives the message "disabling irq #11" where it hangs for about 30 seconds before continuing.

Everything seems to be working after that and there are no other symptoms (none noticed yet anyway).

Have Googled and searched this forum for any answers and have found nothing that works yet.

Any clues - directions - hints - tips will be greatfully accepted.

thanks

---

### Post by Rubi1200 on 2010-11-26
Hi and welcome to the forums :)

We need to know what graphics card you have installed and how much RAM.

Thanks.

---

### Post by meermatt on 2010-11-26
Hello, thanks for the welocme.

according to lspci this what i have.  

01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]

having to rely on system lists rather than knowledge as it is an inherited laptop and i am still trying to figure out exactly what i have.

weirdly i have 768Mb of ram (i checked that and yes i have a 512 and a 256)

thanks

---

### Post by Rubi1200 on 2010-11-26
Hi,
here are some things you can try to see if it makes a difference.

1. disconnect any USB devices, boot and see if you still get the error message

2. post the output of ```
cat /proc/interrupts
``` both with and without external devices plugged in (as a comparison)

3. try booting and editing at the GRUB menu and adding noapic:
when the entry is highlighted press "e" to edit. Navigate with the cursor to the line that ends with quiet splash and append the noapic parameter. Then, "Ctrl" + "x" to boot.

Let us know what happens.

---

### Post by meermatt on 2010-11-26
without usb device
matt@matt-TECRA-A4:~$ cat /proc/interrupts
           CPU0       
  0:     654300    XT-PIC-XT        timer
  1:       4207    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  3:          2    XT-PIC-XT      
  4:          2    XT-PIC-XT      
  5:          0    XT-PIC-XT        tifm_7xx1
  6:          1    XT-PIC-XT        firewire_ohci
  7:          1    XT-PIC-XT        parport0
  8:          1    XT-PIC-XT        rtc0
  9:        341    XT-PIC-XT        acpi
 10:         55    XT-PIC-XT        ehci_hcd:usb1, uhci_hcd:usb2, Intel ICH6
 11:     159373    XT-PIC-XT        uhci_hcd:usb3, uhci_hcd:usb4, uhci_hcd:usb5, mmc0, mmc1, mmc2, sky2@pci:0000:02:00.0, yenta, ipw2200
 12:     815081    XT-PIC-XT        i8042
 14:      19306    XT-PIC-XT        ata_piix
 15:      63479    XT-PIC-XT        ata_piix
 19:          0   PCI-MSI-edge      radeon
NMI:          0   Non-maskable interrupts
LOC:          0   Local timer interrupts
SPU:          0   Spurious interrupts
PMI:          0   Performance monitoring interrupts
PND:          0   Performance pending work
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
MCE:          0   Machine check exceptions
MCP:         14   Machine check polls
ERR:          0
MIS:          0


with usb floppy drive 

matt@matt-TECRA-A4:~$ cat /proc/interrupts
           CPU0       
  0:     702453    XT-PIC-XT        timer
  1:       4494    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  3:          2    XT-PIC-XT      
  4:          2    XT-PIC-XT      
  5:          0    XT-PIC-XT        tifm_7xx1
  6:          1    XT-PIC-XT        firewire_ohci
  7:          1    XT-PIC-XT        parport0
  8:          1    XT-PIC-XT        rtc0
  9:        369    XT-PIC-XT        acpi
 10:         57    XT-PIC-XT        ehci_hcd:usb1, uhci_hcd:usb2, Intel ICH6
 11:     162287    XT-PIC-XT        uhci_hcd:usb3, uhci_hcd:usb4, uhci_hcd:usb5, mmc0, mmc1, mmc2, sky2@pci:0000:02:00.0, yenta, ipw2200
 12:     863987    XT-PIC-XT        i8042
 14:      19775    XT-PIC-XT        ata_piix
 15:      66806    XT-PIC-XT        ata_piix
 19:          0   PCI-MSI-edge      radeon
NMI:          0   Non-maskable interrupts
LOC:          0   Local timer interrupts
SPU:          0   Spurious interrupts
PMI:          0   Performance monitoring interrupts
PND:          0   Performance pending work
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
MCE:          0   Machine check exceptions
MCP:         15   Machine check polls
ERR:          0
MIS:          0
matt@matt-TECRA-A4:~$ 

will tyr the reboo / edit 

thanks

---

### Post by meermatt on 2010-11-27
have tried noapic and makes no difference.

---

### Post by Rubi1200 on 2010-11-27
Hi meermatt,
I have not really found any more information about this "issue."

As far as I can tell, it might be something to do with interrupt requests:
[http://en.wikipedia.org/wiki/IRQ](http://en.wikipedia.org/wiki/IRQ)

I saw some posts which talked about unplugging USB devices or using boot parameters (which we have now tried and seen it makes no difference).

However, my next question is this:
what is the device here?: > sky2@pci:0000:02:00.0, yenta, ipw2200

If it is a modem, which I think it might be, you may want to try investigating in that direction.

---

### Post by Yetisaurus Akjas on 2012-06-22
Got rid of that message that freezed the startup by enabling in BIOS the "ACPI APIC support" option. :) 

'Hope this helps. ;)

---

