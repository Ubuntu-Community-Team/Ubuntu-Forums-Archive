---
title: "Ubuntu not loading past black screen"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by pk3 on 2010-06-18
Hi. I'm a first time user of Ubuntu 10.04. After installation by USB drive, I was prompted to restart. After restarting, nothing comes up after a black screen with a blinking underscore comes up. It does this every time. I have managed to get past this screen after MULTIPLE restarts, and managed to enable my video card hardware and restarted to still find the black screen. I can get into Ubuntu after unplugging and rebooting like 50 times. When trying to boot by the original installation USB and by the GRUB recovery console, if get something like this:
[0.515859] EISA bus registered
[0.517932] ACPI: bus type pci registered
[0.537720] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[0.544859] PCI: MCFG area at f0000000 reserved in E820
[0.548430] PCI: Using MMCONFIG for extended config space
[0.552430] PCI: Using configuration type for base access
[0.822574] bio: create slab <bio-0> at 0
[3.359651] ACPI: Interpreter enabled
[3.361291] ACPI: (supports S0 S3 S4 S5)
[3.393293] ACPI: Using IOAPIC for interrupt routing
[6.045940] ACPI: No dock devices found.
[6.426367] PCI Root Bridge [PC10] (0000:00)
[6.478372] pci 0000:00:01.1 : PME# supported from D3hot D3cold
[6.481084] pci 0000:00:01.1 : PME# disabled
It's like this, but not exactly sure what the top of it says. I edited the quiet splash in GRUB, but after deleting it and putting nomodeset (I have a nVidia GeForce 6150se) and rebooting, nothing changes.
Computer model: Emachines el1200

---

### Post by k3lt01 on 2010-06-18
Read [this page in Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566379")

---

### Post by pk3 on 2010-06-18
> **k3lt01 said:**
> Read [this page in Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566379")

This does not make much sense to me. I've just started using this OS.

---

### Post by pk3 on 2010-06-18
anyone?

---

### Post by ieee488 on 2010-06-18
[http://ubuntuforums.org/showthread.php?t=1463294](http://ubuntuforums.org/showthread.php?t=1463294)

---

### Post by Naggobot on 2010-06-18
Open terminal and type

```
lspci | grep -i vga
```

if your output contains something like

```
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM  Integrated Graphics Device (rev 02)

```

now the crucial part is 855GM if you have that check

[http://ubuntuforums.org/showthread.php?t=1476769](http://ubuntuforums.org/showthread.php?t=1476769)

I have not suffered personally from this but I ran in to this in other threads. The problem is that there is some sort of incompatibility with 855GM hardware. 

I admit that I do not have capacity to understand it my self either.

---

### Post by pk3 on 2010-06-18
> **Naggobot said:**
> Open terminal and type

```
lspci | grep -i vga
```if your output contains something like

```
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM  Integrated Graphics Device (rev 02)

```now the crucial part is 855GM if you have that check

[http://ubuntuforums.org/showthread.php?t=1476769](http://ubuntuforums.org/showthread.php?t=1476769)

I have not suffered personally from this but I ran in to this in other threads. The problem is that there is some sort of incompatibility with 855GM hardware. 

I admit that I do not have capacity to understand it my self either.

i've got nVidia not intel

---

### Post by k3lt01 on 2010-06-18
What people are trying to tell you through giving you links to read is that this is an issue that affects more than nvidia. You tried a nomodeset setting and it hasn't worked so now if you read through the links and try the settings in them it may work.

---

### Post by k3lt01 on 2010-06-18
As Naggobot asked could you please post the output of
```
lspci | grep -i vga
``` this will tell us exactly what nvidia you have.

---

### Post by pk3 on 2010-06-18
> **k3lt01 said:**
> What people are trying to tell you through giving you links to read is that this is an issue that affects more than nvidia. You tried a nomodeset setting and it hasn't worked so now if you read through the links and try the settings in them it may work.
I have read the links. There is any settings in there that apply to me or that I can try or that I have already tried.

---

### Post by pk3 on 2010-06-18
> **k3lt01 said:**
> As Naggobot asked could you please post the output of
```
lspci | grep -i vga
``` this will tell us exactly what nvidia you have.


nVidia GeForce 6150se

---

### Post by pk3 on 2010-06-18
this is ridiculous. I can't even use my windows disk or boot from USB with Fedora without getting this stupid black screen with a flashing underscore.

---

### Post by pk3 on 2010-06-18
new: 
[0.515859] EISA bus registered
[0.517932] ACPI: bus type pci registered
[0.537720] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[0.544859] PCI: MCFG area at f0000000 reserved in E820
[0.548430] PCI: Using MMCONFIG for extended config space
[0.552430] PCI: Using configuration type for base access
[0.822574] bio: create slab <bio-0> at 0
[3.359651] ACPI: Interpreter enabled
[3.361291] ACPI: (supports S0 S3 S4 S5)
[3.393293] ACPI: Using IOAPIC for interrupt routing
[6.045940] ACPI: No dock devices found.
[6.426367] PCI Root Bridge [PC10] (0000:00)
[6.478372] pci 0000:00:01.1 : PME# supported from D3hot D3cold
[6.481084] pci 0000:00:01.1 : PME# disabled

---

### Post by pk3 on 2010-06-18
anyone

---

### Post by pk3 on 2010-06-18
Hi. I'm a first time user of Ubuntu 10.04. After installation by USB  drive, I was prompted to restart. After restarting, nothing comes up  after a black screen with a blinking underscore comes up. It does this  every time. I have managed to get past this screen after MULTIPLE  restarts, and managed to enable my video card hardware and restarted to  still find the black screen. I can get into Ubuntu after unplugging and  rebooting like 50 times. When trying to boot by GRUB recovery console, or any other boot method, i'll occasionally get something like  this:
[0.515859] EISA bus registered
[0.517932] ACPI: bus type pci registered
[0.537720] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 -  63
[0.544859] PCI: MCFG area at f0000000 reserved in E820
[0.548430] PCI: Using MMCONFIG for extended config space
[0.552430] PCI: Using configuration type for base access
[0.822574] bio: create slab <bio-0> at 0
[3.359651] ACPI: Interpreter enabled
[3.361291] ACPI: (supports S0 S3 S4 S5)
[3.393293] ACPI: Using IOAPIC for interrupt routing
[6.045940] ACPI: No dock devices found.
[6.426367] PCI Root Bridge [PC10] (0000:00)
[6.478372] pci 0000:00:01.1 : PME# supported from D3hot D3cold
[6.481084] pci 0000:00:01.1 : PME# disabled
It's like this, but not exactly sure what the top of it says. I edited  the quiet splash in GRUB, but after deleting it and putting nomodeset (I  have a nVidia GeForce 6150se) and saving it, nothing changes during boot process.
Computer model: Emachines el1200

---

### Post by k3lt01 on 2010-06-18
> **pk3 said:**
> this is ridiculous. I can't even use my windows disk or boot from USB with Fedora without getting this stupid black screen with a flashing underscore.If your BIOS is set to boot from USB then there is no reason why you shouldn't be able to boot from your USB.

What are you referring to with "my windows disk"? a hard drive? or a cd/dvd? if it is a cd/dvd then you should have your BIOS set to boot from cd.

---

### Post by k3lt01 on 2010-06-18
[Google search]("http://www.google.com/search?hl=en&q=nVidia+GeForce+6150se&as_q=ubuntu&btnG=Search%C2%A0within%C2%A0results")

---

### Post by pk3 on 2010-06-19
> **k3lt01 said:**
> If your BIOS is set to boot from USB then there is no reason why you shouldn't be able to boot from your USB.

What are you referring to with "my windows disk"? a hard drive? or a cd/dvd? if it is a cd/dvd then you should have your BIOS set to boot from cd.

I no longer should have to boot by USB, since Ubuntu is already installed. But, since the I always get the black screen or the sequence mentioned in the above post, i've tried booting serveral ways. Those include using a windows disk, USB, hard drive alone, etc.
None of these methods work to get me past the black screen.

---

### Post by pk3 on 2010-06-19
anyone

---

### Post by yetiman64 on 2010-06-19
> **pk3 said:**
> Hi. I'm a first time user of Ubuntu 10.04. After installation by USB  drive, I was prompted to restart. After restarting, nothing comes up  after a black screen with a blinking underscore comes up. It does this  every time. ...

It sounds as though you have delayed loading of the splash screen (Plymouth problem).

Check here, [http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html ]("http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html"), and see if the section, "To fix the delayed loading of the splash:" is of any help to your situation.
Most of this link is about customizing Plymouth, so use with caution.

---

### Post by k3lt01 on 2010-06-19
> **pk3 said:**
> I no longer should have to boot by USB, since Ubuntu is already installed. But, since the I always get the black screen or the sequence mentioned in the above post, i've tried booting serveral ways. Those include using a windows disk, USB, hard drive alone, etc.
None of these methods work to get me past the black screen.I don't think you understand what I am trying to do. I am trying to separate an OS problem from a computer problem.

If your BIOS settings allow booting to a cd or a usb BEFORE the hard drive and it is set to do this and it is STILL not working then your computer is at fault. If your BIOS is not set to allow this then Ubuntu is the problem.

Now that is explained is your BIOS set properly to allow booting to both a cd or usb BEFORE the hard drive?

---

### Post by cariboo on 2010-06-19
Please don't create multiple threads on the same subject. I have merged your two threads.

---

### Post by pk3 on 2010-06-19
> **k3lt01 said:**
> I don't think you understand what I am trying to do. I am trying to separate an OS problem from a computer problem.

If your BIOS settings allow booting to a cd or a usb BEFORE the hard drive and it is set to do this and it is STILL not working then your computer is at fault. If your BIOS is not set to allow this then Ubuntu is the problem.

Now that is explained is your BIOS set properly to allow booting to both a cd or usb BEFORE the hard drive?

Please just stop bothering, i'm tired of explaining something over and over.

---

### Post by k3lt01 on 2010-06-19
> **pk3 said:**
> Please just stop bothering, i'm tired of explaining something over and over.I wasn't bothering, anyhow it's your choice.

---

### Post by anewguy on 2010-06-19
> **pk3 said:**
> Please just stop bothering, i'm tired of explaining something over and over.

You have just officially stopped ANYONE from wanting to help you.  You HAVEN'T explained everything or people wouldn't keep asking.  People are asking you to start at some very basic debugging steps until the problem can be isolated, but you want them to quit bothering you?????

Lotsa luck.

We're are volunteer here, and some of us like myself have a TON of learning to do, so when I have a problem and post it, I PAY ATTENTION to what people are saying and asking.  You think you're the only one who has ever had a problem and been frustrated??  You think you're the only one with your problem??  There are TONS of posts in this forum regarding your problem with nVidia chipsets.

Just so you know so you don't accuse someone else of it, I have reported your last thread that I have quoted here.  Such posts aren't welcomed here and are not in the fluid of the forum.

Dave

---

### Post by lisati on 2010-06-19
> **pk3 said:**
> Please just stop bothering, i'm tired of explaining something over and over.

Thread closed. Forgive me if I seem blunt, but I suggest that the OP comes back again once they've read [this]("http://www.catb.org/~esr/faqs/smart-questions.html").

---

