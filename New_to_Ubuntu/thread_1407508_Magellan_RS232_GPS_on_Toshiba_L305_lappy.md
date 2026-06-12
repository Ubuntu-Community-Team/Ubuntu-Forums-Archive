---
title: "Magellan RS232 GPS on Toshiba L305 lappy"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by zxMarce on 2010-02-15
Hi there! Noob talkin´ here, feel free to correct me.

I have a Magellan SporTrak MAP GPS unit from 2003 (NMEA capable, V1.5APA, v1.5XTE and V2.1GSA versions). Want to attach it to my Toshiba L305-S5919 (Ubuntu 9.10) thru a RS232-Serial dongle (generic chinese, has no branding).

I tried **Viking** and **GPSDrive** with no luck. Then, searching, saw some talk about something called **gpsd** (which, ending in **d** points to be a daemon, methinks). Problem is I don´t know how to start it (I warned ya I´m a noob!).

My questions:

[LIST=1]
[*]I need to know if my USB dongle is recognized: How do I achieve this?
[*]How do I know how many serial ports my machine has?
[*]How do I know which serial port corresponds to the USB - RS232 adapter?
[*]Where do I find the command-line parameters for starting **gpsd** for my device(s) (i.e: dongle and GPS)?
[*]If anyone tried a similar setup (GPS, Dongle, USB port) successfully: How did you do to make it work???
[*]Can someone tell me how the whole GPS-on-Linux (at least in Ubuntu) is supposed to work?
[/LIST]
Thanks in advance,
Marcelo.

---

### Post by gordintoronto on 2010-02-15
I can only handle the first two questions.  Open Accessories/Terminal, then paste this command in:
lsusb
you should see your usb devices listed.

sudo lshw > myconfig.txt
(you will be asked for your password)

Then this command:
gedit myconfig.txt

lshw is a program which generates several pages of details about your computer.  Gedit is a text editor so you can scroll through the file.  The USB information is near the middle, and there should be a section called "serial" just below it.

---

### Post by zxMarce on 2010-02-17
Thanks a lot!
I suspect that the **myconfig.txt** file will also have some info regarding question #3...

Just for reference for anyone that might respond further, the output for **lsusb** before plugging the dongle in is:

```
xxxxxxx@xxxxxxx:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```And, this is **lsusb** output after connecting the USB-Serial dongle:

```
xxxxxxx@xxxxxxx:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 005 Device 003: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port**
Bus 005 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```I´d say my dongle is a Prolific Tech PL2303 unit.

And the serial info from **lshw** shows, with dongle connected or not:
```
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:96706000-967060ff ioport:5000(size=32)

```So I think Ubuntu does not realize there´s a serial port plugged in. In fact, I think the detected serial port has something to do with the internal analog modem this laptop has (it features a RJ-11 port on the back), but Ubuntu did not detect and I could never use.
I´ll do a couple tests more, but I´d really need a helping hand here. Been to Windows far too long.

Thanks again, and cheers,
Marcelo.

---

### Post by gordintoronto on 2010-02-17
An internal modem always includes a serial port, so if lshw only came up with one serial port, that's where it is.

I assume you installed gpsd through Synaptic.  There is another package, gpsd-clients, programs which use the daemon. In Accessories/terminal you might get some info from:
man gpsd
or
man gpsd-clients

There's also gpsdrive, which might be a useful application.

---

### Post by lkraemer on 2010-02-17
Information on your Serial Ports:
[http://www.linux.org/docs/ldp/howto/Serial-HOWTO-11.html](http://www.linux.org/docs/ldp/howto/Serial-HOWTO-11.html)

And a Test Program:
[http://www.comptechdoc.org/os/linux/programming/c/linux_pgcserial.html](http://www.comptechdoc.org/os/linux/programming/c/linux_pgcserial.html)

The Data Interface:
[http://www.arcelect.com/rs232.htm](http://www.arcelect.com/rs232.htm)

RS-232C The STANDARD.....:
[http://www.camiresearch.com/Data_Com_Basics/RS232_standard.html](http://www.camiresearch.com/Data_Com_Basics/RS232_standard.html)

lk

---

### Post by zxMarce on 2010-02-18
Making progress, thanks **lkraemer**!
My dongle is correctly detected as **ttyUSB0**. Here's a **ls -l ttyU*** while standing in **/dev**, before plugging it in:

```
xxxxxxx@xxxxxxx:/dev$ ls -l ttyU*
ls: cannot access ttyU*: No such file or directory

```

And, same command after plugging in the dongle:

```
xxxxxxx@xxxxxxx:/dev$ ls -l ttyU*
crw-rw---- 1 root dialout 188, 0 2010-02-18 14:08 **ttyUSB0**

```

So, now I know I have a serial port, and its name. All that's left would be to set it up correctly (unless that´s done automatically by **gpsd**), and start **gpsd** with the right parameters to make GPSDrive or Viking able to talk to my old Magellan GPS.

Will post any success... or lack of it!

Thanks and regards,
Marcelo.

---

### Post by lkraemer on 2010-02-18
It might be a good idea to try minicom before you connect the GPS.

[http://ubuntuforums.org/showthread.php?t=1389575&highlight=minicom](http://ubuntuforums.org/showthread.php?t=1389575&highlight=minicom)
Posting #2 & #4

Good Luck!

lk

---

### Post by zxMarce on 2010-02-26
Thanks lkraemer.

I tried the **minicom** tutorial at OpenManiak; I think my dongle's either dead, or it won't work with my machine. My reasoning is backed by the machine's response to the following command:

```
xxxxxxx@xxxxxxx:~$ dmesg | grep tty
[    0.001415] console [tty0] enabled
[ 3893.515047] usb 5-2: pl2303 converter now attached to ttyUSB0
[ 3893.579973] pl2303 ttyUSB0: **pl2303_open - failed** submitting read urb, error **-22**

```Now... Where can I find info on this **error -22**, and where does it come from?
I tried minicom with and without hardware handshaking, always with pins 2 & 3 shorted in the DB-9 RS232 connector, and it never returned any echoes.

Thanks,
Marcelo.

---

### Post by zxMarce on 2010-02-26
Well, looking for the above error, I found a *[page that sez]("http://blog.zugschlus.de/archives/707-Serial-Console-Server-for-the-Poor-I.html")*:

> [...]
If you have an USB 2.0 hub connected to an USB 2.0 port of the host, you might see error messages like “**pl2303_open - failed submitting interrupt urb, error -28**” in your log, while the serial ports plagued by this message are not going to work. This is due to an issue in the USB 2.0 code in the kernel (see the thread starting with *[my message on linux-kernel]("http://blog.zugschlus.de/exit.php?url_id=2349&entry_id=707")*), Greg KH says that running USB 1.1 devices behind a USB 2.0 hub is a very difficult thing to do. A possible remedy is using an USB 1.1 hub, which is quite hard to obtain these days. But one can also unload the EHCI driver, disabling USB 2.0 completely, or do[INDENT] ```
echo P >/sys/class/usb_host/usb_hostB/companion
``` [/INDENT]to force port P of the EHCI controller on Bus B to run at low/full speed (so, Alan Stern says in the linux-kernel thread). After a few tries, I found out that my test notebook needs P=1 and B=1 for the correct port. If you have found the correct port, you’ll see your devices disconnect and reconnect below the USB 1.1 root hub in lsusb and the urb error messages should be gone.[...]Well, it looks like I'm outta luck here. I don't know the exact line I have to enter to make my USB port(s) drop down to USB 1.1, and even if I knew it, I also don't know how to get back to USB 2.2 once I'm done with my dongle.
I think I'll try a different chinese unit when I get back to the office next monday.

Thanks for all the fish!

Stay tuned,
Marcelo.

---

### Post by zxMarce on 2010-02-27
HA! Think I did it!!!

I googled **unloading EHCI driver ubuntu 9.10**, and got [*a promising page*]("http://wiki.ubuntuusers.de/Benutzer/BigMc/Tascam_US-144"). It said to unbind my USB hubs from EHCI with a "simple" command. If needed, the unbind could be undone with another command.

The commands were actually three:

[LIST]
[*]One to check USB Hubs identifiers,
[*]One to unbind them from EHCI,
[*]One to re-bind them to EHCI once USB 2.0 was again needed.
[/LIST]
(with all this binding-unbinding, the phrase from The One Ring comes to mind... Is EHCI the Darkness?)

Well, to say the truth, I unbound my hubs (both of them) and tried to look for errors with the old **dmesg** command. The same error as before popped up, so I sighed and rebound them. To my surprise, once rebound, I entered **dmesg** again. There were NO ERRORS this time, and the GPS started spitting NMEA codes to **minicom**!!! Hell yeah!

The commands I used:


[LIST=1]
[*]Check USB IDs (the ones with **0000:00:**.***):```
xxxxxxx@xxxxxxx:~$ ls /sys/bus/pci/drivers/ehci_hcd
**0000:00:1a.7**  **0000:00:1d.7**  bind  module  new_id  remove_id  uevent  unbind

```
[*]Unbind USB Hubs from EHCI:```

xxxxxxx@xxxxxxx:~$ echo -n 0000:00:1a.7 | sudo tee -a /sys/bus/pci/drivers/ehci_hcd/unbind
xxxxxxx@xxxxxxx:~$ echo -n 0000:00:1d.7 | sudo tee -a /sys/bus/pci/drivers/ehci_hcd/unbind
```
[*](here I switched to another console to check **dmesg **to see if errors dissappeared; as they did not, I switched back and rebound EHCI with this command):```
xxxxxxx@xxxxxxx:~$ echo -n 0000:00:1a.7 | sudo tee -a /sys/bus/pci/drivers/ehci_hcd/bind
xxxxxxx@xxxxxxx:~$ echo -n 0000:00:1d.7 | sudo tee -a /sys/bus/pci/drivers/ehci_hcd/bind
```
[*]Then, I doublechecked the hubs returned to normal with the command:```
xxxxxxx@xxxxxxx:~$ ls /sys/bus/pci/drivers/ehci_hcd
**0000:00:1a.7  0000:00:1d.7**  bind  module  new_id  remove_id  uevent  unbind

```
[*]This is where I switched to the other console and saw that the errors dissappeared. Then, started **minicom** and to my surprise the USB dongle started echoing characters back. As a last step, I removed the dongle´s jumper for pins 2 & 3 and connected the GPS, which started transmitting NMEA to **minicom**.
[/LIST]
Only problem now is how to start **gpsd** since **GPSDrive** does not seem to be configurable regarding serial ports, and it always says **No GPS** in the lower-right corner. Next in my list would be to check for **gpsd**´s man pages.

Again, thanks to you all. I wanted to make this post so others with my setup may find it useful.

Regards,
Marcelo.

---

