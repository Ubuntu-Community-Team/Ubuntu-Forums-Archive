---
title: "Really Major Problem - Sudden Random Logouts"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by Andy06 on 2009-07-12
While watching a movie on VLC (which I had then installed recently), Ubuntu just logged out and dropped back to the GDM without any wierd pop ups, notifications or error messages. Just the standard darkening of the screen, then the momentary shut down/log out white on black text and then bam, GDM.

Happened 2-3 times then, then I din't use Ubuntu for a few days (was on windows) and today it happened again (I had removed vlc completely right after the first time). I lose a lot of data, open windows, unsaved files etc everytime this happens.

What's going on?

Is this the kernel panic I keep reading about?

---

### Post by philinux on 2009-07-12
Have a look in /var/log/messages

scroll to the bottom for the latest error messages from the system.

---

### Post by LewRockwell on 2009-07-12
equipment?
operating system(s)?
versions?

"Things a technician might ask for on a trouble-call?"


.

---

### Post by decoherence on 2009-07-12
In answer to your question, no this is not a kernel panic. 

Hopefully the cause is logged to /var/log/messages. It can be checked through the GUI... simply navigate to File System > var > log > messages if you're using Ubuntu or Root > var > log > messages if you're using Kubuntu.

---

### Post by Andy06 on 2009-07-12
> equipment?
operating system(s)?
versions?

HP dv6281ea
Ubuntu 9.04/Windows Vista SP2 dual boot
Intel Core 2 Duo
2.5 GB RAM
120GB SATA HDD
Nvidia Go 7400 (version 180 driver installed)

> Have a look in /var/log/messages

scroll to the bottom for the latest error messages from the system. 

```
Jul 13 01:40:55 F22 kernel: [37230.424095] usb 3-1: USB disconnect, address 56
Jul 13 01:40:55 F22 kernel: [37230.676096] usb 3-1: new low speed USB device using uhci_hcd and address 57
Jul 13 01:40:55 F22 kernel: [37230.864466] usb 3-1: configuration #1 chosen from 1 choice
Jul 13 01:40:55 F22 kernel: [37230.885787] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input62
Jul 13 01:40:55 F22 kernel: [37230.901497] generic-usb 0003:045E:0084.0035: input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.1-1/input0
Jul 13 01:41:19 F22 kernel: [37254.480148] usb 3-1: USB disconnect, address 57
Jul 13 01:41:19 F22 kernel: [37254.732102] usb 3-1: new low speed USB device using uhci_hcd and address 58
Jul 13 01:41:19 F22 kernel: [37254.909203] usb 3-1: configuration #1 chosen from 1 choice
Jul 13 01:41:19 F22 kernel: [37254.926571] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input63
Jul 13 01:41:19 F22 kernel: [37254.960596] generic-usb 0003:045E:0084.0036: input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.1-1/input0
Jul 13 01:41:53 F22 kernel: [37288.710959] usb 3-1: USB disconnect, address 58
Jul 13 01:41:53 F22 kernel: [37288.964110] usb 3-1: new low speed USB device using uhci_hcd and address 59
Jul 13 01:41:53 F22 kernel: [37289.141065] usb 3-1: configuration #1 chosen from 1 choice
Jul 13 01:41:53 F22 kernel: [37289.156659] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input64
Jul 13 01:41:53 F22 kernel: [37289.173202] generic-usb 0003:045E:0084.0037: input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.1-1/input0
Jul 13 01:42:09 F22 kernel: [37304.576092] usb 3-1: USB disconnect, address 59
Jul 13 01:42:09 F22 kernel: [37304.828091] usb 3-1: new low speed USB device using uhci_hcd and address 60
Jul 13 01:42:09 F22 kernel: [37305.009289] usb 3-1: configuration #1 chosen from 1 choice
Jul 13 01:42:09 F22 kernel: [37305.025140] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input65
Jul 13 01:42:09 F22 kernel: [37305.059773] generic-usb 0003:045E:0084.0038: input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.1-1/input0
Jul 13 01:42:10 F22 kernel: [37305.816115] usb 3-1: USB disconnect, address 60
Jul 13 01:42:10 F22 kernel: [37306.072080] usb 3-1: new low speed USB device using uhci_hcd and address 61
Jul 13 01:42:11 F22 kernel: [37306.251294] usb 3-1: configuration #1 chosen from 1 choice
Jul 13 01:42:11 F22 kernel: [37306.272414] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input66
Jul 13 01:42:11 F22 kernel: [37306.316183] generic-usb 0003:045E:0084.0039: input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.1-1/input0
Jul 13 01:42:11 F22 kernel: [37306.808142] usb 3-1: USB disconnect, address 61
Jul 13 01:42:11 F22 kernel: [37307.052102] usb 3-1: new low speed USB device using uhci_hcd and address 62
Jul 13 01:42:12 F22 kernel: [37307.233073] usb 3-1: configuration #1 chosen from 1 choice
Jul 13 01:42:12 F22 kernel: [37307.255402] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input67
Jul 13 01:42:12 F22 kernel: [37307.292163] generic-usb 0003:045E:0084.003A: input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.1-1/input0
Jul 13 01:44:25 F22 kernel: [37440.481077] usb 3-1: USB disconnect, address 62
Jul 13 01:44:25 F22 kernel: [37440.724125] usb 3-1: new low speed USB device using uhci_hcd and address 63
Jul 13 01:44:25 F22 kernel: [37440.920365] usb 3-1: configuration #1 chosen from 1 choice
Jul 13 01:44:25 F22 kernel: [37440.936854] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input68
Jul 13 01:44:25 F22 kernel: [37440.950541] generic-usb 0003:045E:0084.003B: input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.1-1/input0
Jul 13 01:44:27 F22 kernel: [37442.960123] usb 3-1: USB disconnect, address 63
Jul 13 01:44:28 F22 kernel: [37443.225120] usb 3-1: new low speed USB device using uhci_hcd and address 64
Jul 13 01:44:28 F22 kernel: [37443.465294] usb 3-1: configuration #1 chosen from 1 choice
Jul 13 01:44:28 F22 kernel: [37443.486673] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input69
Jul 13 01:44:28 F22 kernel: [37443.518024] generic-usb 0003:045E:0084.003C: input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.1-1/input0
Jul 13 01:44:31 F22 kernel: [37446.680111] usb 3-1: USB disconnect, address 64
Jul 13 01:44:31 F22 kernel: [37446.949063] usb 3-1: new low speed USB device using uhci_hcd and address 65
Jul 13 01:44:31 F22 kernel: [37447.139031] usb 3-1: configuration #1 chosen from 1 choice
Jul 13 01:44:31 F22 kernel: [37447.154767] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input70
Jul 13 01:44:31 F22 kernel: [37447.188196] generic-usb 0003:045E:0084.003D: input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.1-1/input0
Jul 13 01:44:34 F22 kernel: [37449.656104] usb 3-1: USB disconnect, address 65
Jul 13 01:44:34 F22 kernel: [37449.909039] usb 3-1: new low speed USB device using uhci_hcd and address 66
Jul 13 01:44:34 F22 kernel: [37450.107980] usb 3-1: configuration #1 chosen from 1 choice
Jul 13 01:44:34 F22 kernel: [37450.123674] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input71
Jul 13 01:44:34 F22 kernel: [37450.160192] generic-usb 0003:045E:0084.003E: input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.1-1/input0
Jul 13 01:52:18 F22 kernel: [37913.425996] usb 3-1: USB disconnect, address 66
Jul 13 01:52:18 F22 kernel: [37913.684068] usb 3-1: new low speed USB device using uhci_hcd and address 67
Jul 13 01:52:18 F22 kernel: [37913.880567] usb 3-1: configuration #1 chosen from 1 choice
Jul 13 01:52:18 F22 kernel: [37913.899897] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input72
Jul 13 01:52:18 F22 kernel: [37913.929040] generic-usb 0003:045E:0084.003F: input,hidraw0: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.1-1/input0
```

Have that all over like a million times, lemme guess, my mouse is malfunctioning? My mouse crashed Ubuntu??

I'm attaching the messages file if someone wants a peek. The latest crash/logout was on the night of July 12th between 2100 and 2330. I had to zip the file since it was 1008 KB in size and it began from 2046 so I could not delete any of it out.


Thanks a lot

---

### Post by AndThenWhat on 2009-07-12
You could try unplugging the mouse and see if it crashes again.  If that process in the logs continues the usb address might get high enough to cause a kernel panic.

---

### Post by Andy06 on 2009-07-12
Two things,

1.It doesn't happen ALL the time, I'm guessing probably when the mouse causes enough errors to jam, overflow, clog something. So even if I unplug it, it will be very difficult for me to verify if it was due to the mouse and if it has been resolved.

2.Seriously though? A USB mouse is crashing it? :D
This same mouse I am also using on Windows, no problems there.
Can some expert determine something from the log files?

Thanks a lot

---

### Post by Andy06 on 2009-07-13
Ok happened again, this is serious and annoying. It happened at 10:54ish and Immediately logged back in and saw the time as 10:55 and then went and made a copy of my messages file.

Says something about no association with bonobo activation server.

Have attached it.
Pls let me know what is going on because this is really serious, I mean everytime this happens, I have total loss of whatever I was doing (typed documents, mail, downloads, file transfers).

Thanks

---

### Post by sleepyjon on 2009-07-13
The only things I saw different are pulse audio and bonobo between 10:54-10:55

---

### Post by ktrnka on 2009-07-13
It appears that your mouse is constantly connecting and disconnecting. Have you confirmed that this problem happens with the mouse disconnecting. There very well could be a breakage in the usb cable on your mouse that is causing the flood of connections. Please try it with another mouse.

---

### Post by ktrnka on 2009-07-13
bonobo is crash usually follows an X crash and restart. Check your syslog to confirm that X windows has crashed. This may not be bonobo at all. Some people report the crash happening while hitting multimedia buttons on the keyboard.

---

### Post by Andy06 on 2009-07-13
My message files are attached, don' take my word for it since I'm not so knowledgeable with Linux. I wouldn't be able to pinpoint the issue myself. I just mentioned some of the things in the file.

The mouse seems to work fine. It was acting up (not responding and the optical light would turn off every now and then because I guess I dropped it one too many times) couple of days ago but its been fine for the last few days. No disconnections or mouse hangs.

Here is the syslog file (attached).
Around 10:54, it says something about Fatal exception, X and screensaver. I have screensaver disabled, never used them.

---

### Post by ktrnka on 2009-07-13
Oh ok just uploaded syslog. Will check it out.

---

### Post by ktrnka on 2009-07-13
Ok well X server is crashing. It has a message related to a screensaver issue. Try disabling your screensaver and see if the issue persists. Screensaver bug crashes X. X restarts followed by bonobo.

Copied right from your syslog:

"Jul 13 10:54:50 F22 x-session-manager[9519]: WARNING: Detected that screensaver has left the bus 
Jul 13 10:54:50 F22 gdm[8847]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jul 13 10:54:50 F22 bonobo-activation-server (vineet-21479): could not associate with desktop session: Failed to connect to socket /tmp/dbus-V05z9vhKrl: Connection refused"

---

### Post by Cato2 on 2009-07-13
If you are using any proprietary video driver (Nvidia, ATI etc, installed by the restricted hardware thing in Ubuntu) you should disable it temporarily, or try a different version of the driver.  Most likely it's the video driver (used by X) that has the problem - X itself only crashes in my experience due to a driver issue.

---

### Post by ktrnka on 2009-07-13
> **Cato2 said:**
> If you are using any proprietary video driver (Nvidia, ATI etc, installed by the restricted hardware thing in Ubuntu) you should disable it temporarily, or try a different version of the driver.  Most likely it's the video driver (used by X) that has the problem - X itself only crashes in my experience due to a driver issue.

Very inclined to agree. The newest nvidia driver from their site is 185.18.14 and Andy06 is using 180. Not sure if the Ubuntu repos have the latest Nvidia driver. That would most likely fix the screen saver prob.

---

### Post by Andy06 on 2009-07-13
I never use the screensaver. It was never enabled at any point of time in history :D

Did not tinker with it recently either. What about the mouse? Can I safely discount that as a reason? It does seem to be filling up the message and syslog files with reconnect messages.

I've had the 180 drive since the day Jaunty was released, the problem only appeared now. I have not made any recent changes to the kernel or X.org.

Playing with refresh rates, tweaking compiz (a lot) and installing, uninstalling apps is all I have done. But this started happening even before I did that.

What's the usual mode of X crashing? For me it is logging out normally, except I never asked it to so it is sudden and unexpected, but there is no unresponsive screen or hang ups or anything.

---

### Post by ktrnka on 2009-07-13
Screensaver is enabled by default. BTW the dimming of your screen is a screensaver. Compiz could be affecting it as well. I find it odd that a screensaver error would be crashing X server if you are not using it. I think it is enabled.

---

### Post by Andy06 on 2009-07-13
I disable screensaver the very first day I install and configure. Haven't touched it since. The darkening I was referring to is not a dimming but more like the DOS prompt, the sort of screen that you get when you boot in verbose mode with text on it. I get it momentarily anyway when I log out normally or shut down even though I don't have verbose enabled.

I checked and rechecked the Screensaver settings and it is not enabled. In power management settings, I have it set to dim and turn off when Idle after about 10 minutes. Problem is none of those could have affected my case since I was actively typing, doing something at the time.

Thanks. What about the mouse? Out of the picture safely? 

Thanks a lot

---

### Post by Andy06 on 2009-07-14
Ok happened again. 
Have attached Messages and syslog files.

Says nothing about X or screensaver this time. But both mention volume, mix control etc. Was not doing anything that required sound. Just web browsing (no flash videos loaded).

What's going on, is the OS itself having trouble figuring out what is causing this? Or are the error messages just coincidence? And stuff with non enabled screensavers and sound control happens all the time in the background anyway and it was just coincidence?

Thanks a lot

---

### Post by Andy06 on 2009-07-15
*bump*

Anyone willing to take a shot at the latest uploaded sys and messages files?

I've had to stop using Ubuntu and am currently on Windows. (So I guess that makes this a Code Red :P)

---

### Post by ktrnka on 2009-07-16
Not sure if you've solve the problem or not but when you get a chance, please post /var/log/Xorg.0.log

It seems related to the nvidia driver and the 7400 "turbo cache" card. To test this, you will need to manually install the latest driver from Nvidia's website. [http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us") and get the Go 7 series driver.

You will need the build-essential package installed. Then press ctl+alt+F1 and login. Stop X from running with ```
sudo /etc/init.d/gdm stop
```  Run the nvida package with ```
sudo sh NVIDIA-Linux*
``` Follow the onscreen instructions. Then start X again ```
sudo /etc/init.d/gdm start
``` You should be running the updated nvidia driver. Check to see if you are having the same problem and get that Xorg.0.log up asap.

If you could also amuse me by unplugging that Micosoft Optical Mouse(for the rest of this troubleshoothing) so that only the X crash/gdm restart appears in the log, it would help a bunch. Thanks and good luck!

---

### Post by Cato2 on 2009-07-16
As already mentioned, this is almost certainly an Nvidia driver problem.  I recommend you do what ktrnka says.  Installing build-essential means running in a terminal:
```

sudo apt-get install build-essential

```

If his steps don't help you could also try Envy - this is an easy installer for the latest Nvidia drivers.  See [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Sorry it's taking so long to get this working - however, my Nvidia card does work really well with Ubuntu, and Nvidia generally works pretty well once you get the right driver, so I'm pretty confident you will get this sorted out.

The mouse issue is a distraction - if you can plug in another mouse temporarily, or plug this one into a different USB port, that might help as mentioned above.

---

### Post by Andy06 on 2009-07-19
Sorry for the delay, was out of station for a while.

Here is the X.org log. I don't see time stamps so I can't make sense of it :D

Have a look and see if it matches the occurrences in the messages log and sys log.

Regarding the mouse, I disconnected it and connected another one (which is the exact same make and model but a different one) and Ubuntu hasn't crashed yet. Should I be worried? Is the mouse thing something to check out? It really shouldn't be connecting and disconnecting that frequently right?

Thanks a lot for your help

---

### Post by ktrnka on 2009-07-19
Interesting. You are correct that the mouse should not be connecting and disconnecting. Xorg.txt looks good. It appears to be directly related to that mouse. Hmmmm.

Let us know if it crashes again. I still say it could have a breakage in on one of the data wires in the usb cable (the old mouse) causing it to connect and disconnect.

---

### Post by Andy06 on 2009-07-19
Yeah I think the mouse is trouble, it did act up a little while ago (non responsive with the lights out) but was fully active when the logs show it connecting and disconnecting. I tried it a full day on another system but it was fine there. Then again sometimes Ubuntu is full of mysterious, stuff mysteriously acts up, then goes away, then acts up again :D

Could the whole OS be crashing because of the mouse though? Like what would the mouse be doing? Flooding or overflowing some critical memory buffer? Is it inadvertently triggering some security mechanism to shut things down to avoid and over flow/denial of service attack?

Thanks a lot

---

