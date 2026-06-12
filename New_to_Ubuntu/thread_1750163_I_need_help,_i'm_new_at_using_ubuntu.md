---
title: "I need help, i'm new at using ubuntu"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by maryabudianta on 2011-05-05
Hi,

I just installed Ubuntu 3 days ago for my HP Pavilion Entertainment PC 32bit laptop. But apparently now there's a huge problem.

I was in a hurry, turned off the computer by pressing the shut down button, and ever since then my computer can't be used anymore.

When I turn it back on, there's firstly an introduction that begins with the "hp" logo, and then the screen turns purple, the table gave me several different options:

- Ubuntu, with Linux 2.6.38-8-generic
- Ubuntu, with Linux 2.6.38-8-generic (recovery mode)
- Memory test (memtest86+)
- Memory test (memtest86+, serial console 115200)

Normally, I select the first option and the computer immediately redirected me to logon, but then instead the screen turned black and these messages appeared:

BusyBox v1.17.1 (Ubuntu 1:1.17.1-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands

(Initramfs) [    3.682510] scsi 6:0:0:0 Direct-Access.   Generic-Multi-Card
1.00 PQ 0 ANSI: 0 CCS
[    3.683407]. Sd 6:0:0:0: Attached scsi generic sg1 type 0
[    3.687354] Sd 6:0:0:0: [sdb] Attached SCSI removable disk

And then I typed "help" and pressed "Enter"

Instead it didn't get to start PC right away.. And I got this long message (I can't write them all)

Built-in commands:

.: [alias break cd chdir command continue echo eval exec exit export false getopts hash help let local printf pwd read readonly.......etc

I typed "exit" and instead I got like "Kernel Panic - not syncing: Attempted to kill init!" Etc

I tried going to recovery mode but it didn't help either..

Is there a way to fix this problem without having to reinstall Ubuntu all over again? Maybe something to type in the built-in command?

This happens just after I shut off my laptop by pressing the shutdown button for a long time instead of properly shutting down..

There might be another cause I don't know :(
Anybody help please?? Thanks

---

### Post by Rubi1200 on 2011-05-05
Hi and welcome to the forums :-)

Please do the following so we can get a better overview of the current state of your system:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by leviathan8 on 2011-05-05
Do you have any kind of devices inserted in your usb hubs? Like mice, external hard drives and so? Please unplug them and try again. It also happened to me. I connected my mouse before I would boot the laptop, and after the GRUB boot loader, I got the very nice plymouth screen, looping the loading screen infinitely. Then eventually my laptop just shut down by itself...
Have a nice day.

---

### Post by EGamerHDK on 2011-05-05
> **leviathan8 said:**
> Do you have any kind of devices inserted in your usb hubs? Like mice, external hard drives and so? Please unplug them and try again. It also happened to me. I connected my mouse before I would boot the laptop, and after the GRUB boot loader, I got the very nice plymouth screen, looping the loading screen infinitely. Then eventually my laptop just shut down by itself...
Have a nice day.

I will also second this, my laptop wouldn't start because I had a USB device plugged into it. Try unplugging everything and see if it boots up

---

### Post by maryabudianta on 2011-05-05
Thanks for the reply, guys

To Rubi1200: the thing is, I don't have the Ubuntu CD with me at the moment. My guardian has it and I have no full access or ability to use it. He said it might need to be reinstalled and all but I'm not sure if the problem's that big.


And for the USB port, there isn't apparently any USB installed or such. I wondered if it was because of the SD card, but I took it out already. So there's nothing there. I wonder what's happening :(

---

