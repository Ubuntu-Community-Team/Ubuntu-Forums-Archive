---
title: "Where is the serial device?"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by outleradam on 2010-05-30
I bought a bluetooth ELM-327 OBD-II car code scanner and a bluetooth dongle.   I connected the scanner to the bluetooth on Ubuntu and it deteced it as a serial device.  Where is the serial device located?

I tried to cat /dev/ttyS0 & ...S1,S2 and S3, and then echo ATZ>/dev/ttyS0 1,2,3... but it was having problems connecting.  How can I communicate with this device?

Under windows it is connected as COM5 and it works well.

---

### Post by outleradam on 2010-05-30
can someone verify it is supposed to be /dev/ttyS0 and what program to use to communicate?

---

### Post by outleradam on 2010-06-05
is /dev/ttyS0 the serial device?

---

### Post by diablo75 on 2010-06-06
> **outleradam said:**
> is /dev/ttyS0 the serial device?

According to this:

[http://www.linuxselfhelp.com/HOWTO/Text-Terminal-HOWTO-6.html](http://www.linuxselfhelp.com/HOWTO/Text-Terminal-HOWTO-6.html)

That is the equivalent of the good-old "COM1" 9-pin serial ports that used to be on the back of most modern PCs.  So the short answer is "yes".  However, some motherboards have pin-outs that you can plug in PCI slot-back adapters to "add" that kind of port to the back of your PC's case.  In other words, if your motherboard is like this, and those pins are enabled by the BIOS, you might actually be trying to send communications out your unconnected pins.  Best check your BIOS to see if there is an option available to disable any serial COM1/2 ports from being seen by the OS.

I'm curious:  What software (if any) are you trying to use with this on Ubuntu?

On the side, I have seen apps for Android Linux cell phones that will communicate with specific ODB-II adapters like you are using to get error codes from cars.  Might look into that in your spare time.

---

### Post by lisati on 2010-06-06
+1 on the old-style "COM1:" ports. Both my desktops have one, and I have a USB-based expansion hub which has one. (Interesting gadget: it has 3xUSB 2xPS/2 a 25-pin printer port, a 9-pin port, and Wifi capabilities.)

---

### Post by lkraemer on 2010-06-06
Ref:
[http://ubuntuforums.org/showthread.php?t=1356750&highlight=comm+ports](http://ubuntuforums.org/showthread.php?t=1356750&highlight=comm+ports)
Posting #6

Also:
[http://ubuntuforums.org/showthread.php?t=1339775&highlight=comm+ports](http://ubuntuforums.org/showthread.php?t=1339775&highlight=comm+ports)

I haven't a clue as to the Bluetooth portion........

lk

---

### Post by outleradam on 2010-06-06
I'm getting some funky stuff...


I set up this:
```
adam@adam-netbook:/etc/bluetooth$ cat ./rfcomm.conf
#
# RFCOMM configuration file.
#

rfcomm0 {
#    # Automatically bind the device at startup
    bind yes;
#
#    # Bluetooth address of the device
    device 00:0D:18:B1:09:DA;
#
#    # RFCOMM channel for the connection
    channel    1;
#
#    # Description of the connection
    comment "CBT Bluetooth device";
}
adam@adam-netbook:/etc/bluetooth$ 

```
Then I tried this.
```

adam@adam-netbook:~$ hcitool scan
Scanning ...
    00:07:61:A5:3C:98    adam-desktop-0
    00:26:BB:FA:5A:7C    Adam Outler’s iPhone
    00:0D:18:B1:09:DA    CBT
adam@adam-netbook:~$ sudo hcitool cc 00:0D:18:B1:09:DA && sudo hcitool auth 00:0D:18:B1:09:DA
adam@adam-netbook:~$ sudo sdptool browse 00:0D:18:B1:09:DA
Browsing 00:0D:18:B1:09:DA ...
adam@adam-netbook:~$ sudo hcitool cc 00:0D:18:B1:09:DA && sudo hcitool auth 00:0D:18:B1:09:DA
adam@adam-netbook:~$ sudo sdptool browse 00:0D:18:B1:09:DA
Browsing 00:0D:18:B1:09:DA ...
adam@adam-netbook:~$ sudo hcitool cc 00:0D:18:B1:09:DA && sudo hcitool auth 00:0D:18:B1:09:DA && sudo sdptool browse 00:0D:18:B1:09:DA
Browsing 00:0D:18:B1:09:DA ...
adam@adam-netbook:~$ sudo rfcomm connect 0
Connected /dev/rfcomm0 to 00:0D:18:B1:09:DA on channel 1
Press CTRL-C for hangup
ATZ 
AT Z
^CDisconnected
adam@adam-netbook:~$
```But that didn't seem to communicate at all.

Then I noticed the /dev/rfcomm0 device was only present while I had the sudo rfcomm connect 0 command active.  

So in another window, while I was connected, I tried this
```
adam@adam-netbook:~$ cat /dev/rfcomm0
>^C327 v1.3a
```Ok...

So now I've got some form of communications...

```
adam@adam-netbook:~$ cat /dev/rfcomm0
>^C327 v1.3a
adam@adam-netbook:~$ cat /dev/rfcomm0
^C
adam@adam-netbook:~$ cat /dev/rfcomm0 &
[1] 2098
adam@adam-netbook:~$ echo ATZ >/dev/rfcomm0
adam@adam-netbook:~$ ATZ
>
adam@adam-netbook:~$ echo ATZ >/dev/rfcomm0
adam@adam-netbook:~$ ATZ
echo AT Z >/dev/rfcomm0
adam@adam-netbook:~$ AT Z
&#65533;
adam@adam-netbook:~$ killall cat
[1]+  Terminated              cat /dev/rfcomm0

```I can see some unintellegable communications but it seems to be irregular and random..  Any suggestions?

I can see the light flickering on the ELM when I send ATZ to the rfcomm0 device, but it does not seem to give the standard response which from what I read should be ">" to signify that it received data.

---

### Post by outleradam on 2010-06-06
I was able to get it working using mincom
sudo apt-get install minicom
sudo minicom -s  #to put it into setup mode and be able to save defaults

And I was able to send commands to obtain the RPMs and reset the ECU.

Now I'd really like to be able to access this info from the terminal so that I can begin processing the diagnostic information.   It is worthless in it's current form, but if I were able to manipulate the data somehow, I could really make a great program

The main bottleneck is the ability to send data to the serial port from BASH.  How do I send a CRLF over the RS232 standard?   I can send the data, but not the proper control characters.

---

