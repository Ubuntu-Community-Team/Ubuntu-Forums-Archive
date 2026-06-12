---
title: "Mouse plugged to hub not working (Ubuntu 9.10)"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by Deniii on 2010-04-21
I have a Genius USB mouse conected to a hub and every time Ubuntu starts, I have to unplug the mouse and then plug it in again to make it work.
The thing is, on windows, I don't have any problems with it and during Ubuntu install process, it works fine as well.
The problem only apperas when Ubuntu is already installed.
Does anyone know how can I fix it?

Thanks.

---

### Post by carl4926 on 2010-04-21
Hubs are generally a Pain in the Butt.

---

### Post by Deniii on 2010-04-21
But is there a way to fix the problem or not?

---

### Post by dearingj on 2010-04-21
This is a strange problem. Have you tried any other usb mice with the same hub? Or the same mouse with another usb port or hub?

---

### Post by carl4926 on 2010-04-21
> **Deniii said:**
> But is there a way to fix the problem or not?
I have a usb mouse plugged to my keyboad on my main box. It behaves the same some of the time. But it's easy to get at.
I don't know of a solution.

---

### Post by zipperback on 2010-04-21
> **Deniii said:**
> But is there a way to fix the problem or not?

Plug it directly into your system usb port and not the usb hub.

I had a similar problem a while back with a mouse and hub, moving the mouse from the hub to the system usb port resolved the issue.

- zipperback
:popcorn:

---

### Post by P4man on 2010-04-21
Think its a problem with tolerance on the power draw of your USB ports. Linux seems to be a bit more picky on this than windows. Its a passive (non powered) hub I assume?

Not sure if it will help, but you can get detailed information about power draw and status of your usb devices by opening a terminal and typing

```
sudo lsusb -v
```

You may want to redirect the output to a text file so you can see it all:

```
sudo lsusb -v >usbinfo.txt
```

If you want to do that without mouse, press alt+f2 and then type 

```
gnome-terminal
```

Then type the above commands.

Also the output of
```
dmesg
```
might give clues.

My guess is that you have a high power USB device that connects to the same USB root hub on your motherboard as your mouse, and your USB port cant deliver the power reliably. Often happens on (cheap) laptops and like I said, linux is more picky here than windows.

---

### Post by Deniii on 2010-04-21
Thanks for the replys.

I did what p4man suggested and I have attached the output file.
I also included the output file for dmesg.

When I ran those commands, I had already unplugged and plugged in again the mouse so it was working.
If you want the output when the mouse is not working (right after Ubuntu finished starting), let me know and I'll post those outputs too.
I don't know if the hub is passive. How can I tell that?

I couldn't try what dearingj said yet because I don't have another mouse.
I'll see if I can borrow one from someone and try that as well.

Thanks again for the help.

---

### Post by HarrisonNapper on 2010-04-21
One way to do this is to open a terminal and type "tail -f /var/log/messages"

then plug the mouse in to the hub (unplug it first if you want). Notice the path to the device given in the logs. Then in the terminal type "sudo modprobe /path/to/device"

Cheers.

---

### Post by P4man on 2010-04-21
i see you have a force feedback joystick (or gamepad?) connected to the same root hub. Perhaps its worth trying if you disconnect that if the problem persists?

---

### Post by Deniii on 2010-04-21
HarrisonNapper: I did as you said.
Right after I plugged the mouse, I typed the address after the command you told me

```
sudo modprobe /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2.3/2-2.3:1.0/input/input25
```When I hit enter, I got the following line:

```
FATAL: Module /devices/pci0000:00/0000:00:1d.0/usb2/2_2/2_2.3/2_2.3:1.0/input/input25 not found.
```I'm either doing something wrong or there's a problem there.

---

### Post by Deniii on 2010-04-21
I unplugged the gamepad and the mouse is working fine now.

Perhaps if I switch the keyboard with the gamepad everything could remain conected and working fine.

The gamepad is one of those "chinese-Playstation2-replica". I never liked the force feedback so, on windows, I never installed the drivers for that feature.

Thanks everyone for the help.

Now I have 2 questions left
1) Why did the gamepad prevented the mouse from working?
2) How do I mark this thread as [SOLVED]?

---

### Post by P4man on 2010-04-21
Ubuntu already loaded the drivers for it, and its probably overloading the USB port. You could try plugging it in a different USB port, but be aware that a different USB plug on the back of your computer doesnt always mean a different root hub. Usually its one root hub per 2 or even 4 connectors. 

Another solution would be to put the joystick (and/or mouse) in a powered USB hub.

As for the solved, here you go:
[http://ubuntuforums.org/showpost.php?p=4527051&postcount=6](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

---

### Post by HarrisonNapper on 2010-04-21
Also, for future reference, you don't want to modprobe by the full address. It will usually assign a nice one like /dev/input/mouse or something along those lines. Usually, it will spit that out in the logs, but in this case with the hub, it's probably dev/input/input25 or /dev/input/input25/mouse (or MAC addy, I guess). In any case, no big deal for now, just forget I said anything about modprobe :)

---

