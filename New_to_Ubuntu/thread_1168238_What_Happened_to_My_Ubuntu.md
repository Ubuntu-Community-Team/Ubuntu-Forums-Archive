---
title: "What Happened to My Ubuntu?"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by daniell59 on 2009-05-23
For some time I have been dual booting Ubuntu and Vista. Suddenly when I tried to boot into Umbutu, I get a long list of errors. After quite some time, it finally boots into Ubuntu. What is going on, and how can I fix it?

---

### Post by Ms_Angel_D on 2009-05-23
To get proper help your going to need to provide a bit more information ;)

Try either taking a picture of or writing down the errors and posting them here.

Angel

---

### Post by daniell59 on 2009-05-23
> **Ms_Angel_D said:**
> To get proper help your going to need to provide a bit more information ;)

Try either taking a picture of or writing down the errors and posting them here.

Angel

There is page after page of errors

---

### Post by camper365 on 2009-05-23
I started to get problems like that at one point. I did a reinstall and it was fine.
Are they GRUB errors or Ubuntu errors.
When GRUB starts try typing "e" then find the line that starts with "kernel" and hit "e" again. Go to the end and remove the word splash. Post the output of that. If you need to view the output, it should appear when you hit Ctrl+Alt+F8 (I can't figure out how to scroll up though).

---

### Post by daniell59 on 2009-05-23
> **camper365 said:**
> I started to get problems like that at one point. I did a reinstall and it was fine.
Are they GRUB errors or Ubuntu errors.
When GRUB starts try typing "e" then find the line that starts with "kernel" and hit "e" again. Go to the end and remove the word splash. Post the output of that. If you need to view the output, it should appear when you hit Ctrl+Alt+F8 (I can't figure out how to scroll up though).

Why should it have gone bad so fast? I only installed it about a week ago.

---

### Post by daniell59 on 2009-05-23
> **daniell59 said:**
> Why should it have gone bad so fast? I only installed it about a week ago.

What I see are /read errors, whatever that means

---

### Post by pbpersson on 2009-05-23
please write one error onto a piece of paper and type it here

---

### Post by daniell59 on 2009-05-23
> **pbpersson said:**
> please write one error onto a piece of paper and type it here

Would it be helpful if I took a photo of the page and uploaded?

---

### Post by daniell59 on 2009-05-23
Here is a sample of the errors.

---

### Post by RetchingRabbit on 2009-05-23
If you have an external USB device of any sort, disconnect it and see if anything changes...

---

### Post by daniell59 on 2009-05-23
> **RetchingRabbit said:**
> If you have an external USB device of any sort, disconnect it and see if anything changes...

If I do that, I wont have a mouse or keyboard.

---

### Post by balaknair on 2009-05-23
Don't worry about the mouse and keyboard. Leave those connected. I'm assuming you've got a USB Bluetooth dongle that you've got connected at boot up, unplug it upon next boot and see how it goes. 

It looks like Ubuntu is searching for the USB device at start up and not finding it(which gives you the error). 

Edit:
It might be a hardware error, probably the USB BT dongle you're using.

---

### Post by stwschool on 2009-05-23
Does it ever give you the little orange bar that moves accross the screen or go straight to the errors? Normally that comes up only if it's taking too long, kinda to show you what might be happening so you can figure out a fix if you need to. Most of that looks like fairly normal output but for some reason it's having trouble with a usb device. Now, you say you've got a keyboard and mouse on USB. Nothing else? Do they work once you finally reach desktop? Also can you test without them, yes I know you'll have no mouse and keyboard, but purely for diagnosis. Try with neither, with mouse only, with keyboard only and with both, to test all 4 possible conditions and let us know what happens.

---

### Post by daniell59 on 2009-05-24
> **balaknair said:**
> Don't worry about the mouse and keyboard. Leave those connected. I'm assuming you've got a USB Bluetooth dongle that you've got connected at boot up, unplug it upon next boot and see how it goes. 

It looks like Ubuntu is searching for the USB device at start up and not finding it(which gives you the error). 

Edit:
It might be a hardware error, probably the USB BT dongle you're using.

I do not have a Bluetooth dongle.

---

### Post by balaknair on 2009-05-24
OK
What about other USB devices such as an external hard drive or a webcam?

I assumed it could be a BT dongle cos of the picture you provided, but it could be any USB device.
To get a list of USB devices in use, open a terminal(Applications menu> Accessories> Terminal) and type in the command ***lsusb***

You could also try booting from a LiveCD- if the error message is seen there as well, it is more likely a hardware error than a software error.

Try booting without any USB devices(except for mouse and keyboard), plug them in one by one to see which device is causing the problem.

---

### Post by daniell59 on 2009-05-24
> **balaknair said:**
> OK
What about other USB devices such as an external hard drive or a webcam?

I assumed it could be a BT dongle cos of the picture you provided, but it could be any USB device.
To get a list of USB devices in use, open a terminal(Applications menu> Accessories> Terminal) and type in the command ***lsusb***

You could also try booting from a LiveCD- if the error message is seen there as well, it is more likely a hardware error than a software error.

Try booting without any USB devices(except for mouse and keyboard), plug them in one by one to see which device is causing the problem.

The only USB devices present are the keyboard and mouse. I will boot from the CD and see what happens, then report back.

---

### Post by daniell59 on 2009-05-24
> **daniell59 said:**
> The only USB devices present are the keyboard and mouse. I will boot from the CD and see what happens, then report back.

I just booted Ubuntu from the CD without a problem.

Ideas Please!

---

### Post by balaknair on 2009-05-24
Could you post the output you get when you type the command ***lsusb*** in a terminal?

---

### Post by daniell59 on 2009-05-24
> **balaknair said:**
> Could you post the output you get when you type the command ***lsusb*** in a terminal?

The command, is that an i or L

---

### Post by balaknair on 2009-05-24
l= lower case L

(you can also just copy-paste the command into a terminal)

---

### Post by Bölvaður on 2009-05-24
you should copy and paste commands

but this is L for list (ls = list)
(lsusb = list usb)

---

### Post by daniell59 on 2009-05-24
daniel@daniel-desktop:~$ lsusb

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 046d:c30e Logitech, Inc. UltraX Keys (X)
Bus 007 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
daniel@daniel-desktop:~$ 
daniel@daniel-desktop:~$

---

### Post by balaknair on 2009-05-24
Hmmm.
Sorry for the delay in replying.

Hunting around, I found this
[http://primalcortex.wordpress.com/2009/04/06/kubuntuusb-errors-slow-boot/](http://primalcortex.wordpress.com/2009/04/06/kubuntuusb-errors-slow-boot/)

This *might* solve your problem, but I recommend checking your hardware before trying it(if at all). Messing around with the kernel isn't everybody's cup of tea. I know that I'd rather go in for a fresh install than do that.



1) Power off the PC, disconnect the mouse and keyboard, clean the USB ports and connectors. Check the mouse, keyboard cables for damage. Reconnect the devices and boot.

2) Try plugging in the devices to a different USB port.

3) Try using a PS-2 adapter for the mouse, keyboard, or try using a different mouse, keyboard if you can get one

---

### Post by daniell59 on 2009-05-24
> **balaknair said:**
> Hmmm.
Sorry for the delay in replying.

Hunting around, I found this
[http://primalcortex.wordpress.com/2009/04/06/kubuntuusb-errors-slow-boot/](http://primalcortex.wordpress.com/2009/04/06/kubuntuusb-errors-slow-boot/)

This *might* solve your problem, but I recommend checking your hardware before trying it(if at all). Messing around with the kernel isn't everybody's cup of tea. I know that I'd rather go in for a fresh install than do that.



1) Power off the PC, disconnect the mouse and keyboard, clean the USB ports and connectors. Check the mouse, keyboard cables for damage. Reconnect the devices and boot.

2) Try plugging in the devices to a different USB port.

3) Try using a PS-2 adapter for the mouse, keyboard, or try using a different mouse, keyboard if you can get one

Thanks
But my question is. How come all the hardware functions properly in Vista?
If I do a fresh install, will I be able to put the Ubuntu back in the partition it is now in?

---

### Post by albinootje on 2009-05-24
> **daniell59 said:**
> 
If I do a fresh install, will I be able to put the Ubuntu back in the partition it is now in?
Yes, but first back up your important data in Ubuntu, or better :
create a separate /home partition.

See here for more info :
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by balaknair on 2009-05-24
From my limited understanding, it seems to do with the order in which the modules are loaded during the boot process. Once all modules are loaded, the hardware works normally. So by the time Ubuntu gets to the desktop, the error has been compensated for, and your keyboard and mouse work normally.
In Vista you won't see an error because it's all hidden away in the boot process, and you see error messages only if the error persists when the desktop loads. Which apparently isn't the case.

Reinstalling: yes, it is possible to install Ubuntu to the same partition when reinstalling. Just choose 'manual partitioning' when you get to the partitioning step, and choose the current Ubuntu partition, set it to mount as / 

I suggest you check the hardware before reinstalling however.

---

### Post by ChaiTan on 2009-05-24
After pressing enter on the ubuntu entry in grub, do you see the ubuntu bar for some time or does it directly go to text mode. I had a similar problem where the ubuntu bar went back and forth for 3 seconds and then switched to text mode, the problem was that I had changed my swap partition. Changing the swap entry in /etc/fstab fixed the problem

---

### Post by daniell59 on 2009-05-24
> **ChaiTan said:**
> After pressing enter on the ubuntu entry in grub, do you see the ubuntu bar for some time or does it directly go to text mode. I had a similar problem where the ubuntu bar went back and forth for 3 seconds and then switched to text mode, the problem was that I had changed my swap partition. Changing the swap entry in /etc/fstab fixed the problem

I see the Ubutu bar before going to text.

---

### Post by daniell59 on 2009-05-24
> **daniell59 said:**
> I see the Ubutu bar before going to text.

I plugged the keyboard and the mouse into different USB ports. It made no difference. I also get text with error messages when I shut Ubuntu down. Once I get past the few pages of text (some with error messages) Ubuntu seems to be ok. I would appreciate any and all ideas.

---

### Post by daniell59 on 2009-05-24
I changed to an old (forgot the term) non USB mouse and keyboard. Problem solved. So far.

Please explain. How do I determine whether it is the USB ports or the hardware.

Thanks

---

### Post by daniell59 on 2009-05-24
I replaced the USB mouse, and I am still using the old non USB keyboard. All is well. From this, should I say that the problem is the keyboard?

Thanks

---

### Post by balaknair on 2009-05-24
> **daniell59 said:**
> I replaced the USB mouse, and I am still using the old non USB keyboard. All is well. From this, should I say that the problem is the keyboard?

Thanks

Most probably.

I don't know if this is relevant in your case, but a fair number of Error 110 bug reports I found while searching for a solution to this issue, involved Logitech mice(mostly gaming mice).

---

### Post by daniell59 on 2009-05-24
> **balaknair said:**
> Most probably.

I don't know if this is relevant in your case, but a fair number of Error 110 bug reports I found while searching for a solution to this issue, involved Logitech mice(mostly gaming mice).

Thanks for the effort that you made on my behalf. Speaking of mice, my wife just saw one un under the table. It is time for the trap.

---

### Post by balaknair on 2009-05-24
Good luck with that.

:D

---

### Post by Volt9000 on 2009-05-24
Out of curiosity, what kind of keyboard is it? i.e. what make and model?

---

### Post by albinootje on 2009-05-24
> **daniell59 said:**
> Suddenly when I tried to boot into Umbutu, I get a long list of errors. After quite some time, it finally boots into Ubuntu.

Are you saying that the only problem was a longer boot time ?
Which Ubuntu release are you using ?
Can you post the output of :
```

dmesg

```

---

### Post by daniell59 on 2009-05-24
> **Volt9000 said:**
> Out of curiosity, what kind of keyboard is it? i.e. what make and model?

Logitech UltraX Media Keyboard

Why did it work for the first week without a single problem?

---

### Post by daniell59 on 2009-05-27
I started getting the same error messages even with the PS2 keyboard. I observed one thing however. If I power down completely, then reboot, I get no error messages.

Someone please explain what is going on.

---

### Post by pbpersson on 2009-05-28
[This page]("http://www.bhcblog.com/2009/02/11/fix-for-device-descriptor-read64-error-71/") has information on this error.

I Googled the error and it hs happening across all distros on some machines, it is apparently a kernel issue

On another page they offered the following hint:

> What appears to be going on is that after so many entries in a USB table
(which is the SCSI Stub) the High Speed Devices no longer can create an
entry in the appropriate time.

Therefore, it is a hardware design "feature" coupled with the timeout value in Linux - how long will Linux wait before it says "I am not getting a reply from this device"....when you do a cold boot you clear out that USB table.  I don't know if any of this makes any sense, I am just telling you what I read.

---

### Post by daniell59 on 2009-05-28
Thanks for your reply. I need time to digest what you said.

---

### Post by daniell59 on 2009-05-30
I just noticed something else. When I am in Vista, then boot into Ubuntu, my USB keyboard will not function. Only when I completely power off then on, will it function. Can someone explain to me what is happening?

Thanks

---

