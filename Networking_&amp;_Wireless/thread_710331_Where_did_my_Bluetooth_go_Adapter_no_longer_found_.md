---
title: "Where did my Bluetooth go? Adapter no longer found [Gutsy]"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by bopomofo on 2008-02-28
**I used to have Bluetooth working in Gutsy**. I was able to connect to my phone (an LG Shine) to my computer (an ASUS U6) using the Bluetooth File Sharing app, and send and receive files. **Bluetooth is built-in** on this laptop.


But now, when I search for a paired device from my phone, I get "No devices found." 


I am not sure when it stopped working, as I have not paired them in over a month. I only noticed after also failing to get a Bluetooth mouse to work.


[B]What is very strange is that now if I select System > Preferences > Bluetooth Preferences > General > Notification area > o Only display when adapter present

The Bluetooth icon does [SIZE="2"]not[/SIZE] show up on my top Panel (it used to,[/B] but after I first started using Ubuntu I changed this setting to Never display icon, since Bluetooth is built-in, so I'm not sure when it disappeared)


So it seems as if I've lost my Bluetooth!



I've tried:

christopher@U6:~$ sudo /etc/init.d/bluetooth restart
[sudo] password for christopher:
 * Restarting Bluetooth services                                         [ OK ] 

christopher@U6:~$ sudo hcitool scan
Device is not available: No such device

christopher@U6:~$ sudo hidd --search
Searching ...




I tried using Blueman, but it also reports "No adapter found," so I uninstalled it.


I've looked at my logs:

christopher@U6:~$ dmesg | grep -i bluetooth
[   26.584000] Bluetooth: Core ver 2.11
[   26.584000] Bluetooth: HCI device and connection manager initialized
[   26.584000] Bluetooth: HCI socket layer initialized
[   26.644000] Bluetooth: L2CAP ver 2.8
[   26.644000] Bluetooth: L2CAP socket layer initialized
[   26.740000] Bluetooth: RFCOMM socket layer initialized
[   26.740000] Bluetooth: RFCOMM TTY layer initialized
[   26.740000] Bluetooth: RFCOMM ver 1.8


According to Synaptic, I have these packages installed:
bluez-cups
bluez-gnome
bluez-utils
gnome-bluetooth
libbluetooth2
python-bluez


Any help is appreciated. When something doesn't work in Ubuntu I'm quite forgiving, but when something **stops** working?!

---

### Post by JGJones on 2008-02-28
You saved me the hassle of typing all that. I have **exactly** the same issue as you. Just suddenly disappeared and I only noticed when I decided to test my mobile connection again (it did work in the past with same phone).

I figured that maybe my bluetooth module *might* be broken so I bought a new bluetooth module (a USB device) and dmesg shows this:

```
[  177.532000] usb 3-2: new full speed USB device using uhci_hcd and address 2
[  177.760000] usb 3-2: configuration #1 chosen from 1 choice
[  177.864000] Bluetooth: HCI USB driver ver 2.9
[  177.868000] usbcore: registered new interface driver hci_usb
[  817.504000] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[ 1035.120000] CAPI Subsystem Rev 1.1.2.8
[ 1035.140000] Bluetooth: CMTP (CAPI Emulation) ver 1.0

```

It's working but still not working with Ubuntu (this USB module was tested to be working on a Windows desktop in the office).

Can't figure out what to do next to get it working.

---

### Post by bopomofo on 2008-02-29
> **JGJones said:**
> You saved me the hassle of typing all that. I have **exactly** the same issue as you. Just suddenly disappeared and I only noticed when I decided to test my mobile connection again (it did work in the past with same phone).

I figured that maybe my bluetooth module *might* be broken so I bought a new bluetooth module 


Were you using a module before? My Bluetooth is bulit-in to an ASUS U6 laptop. What is your hardware?


Further, I might ask, when did your Bluetooth cease functioning? I last paired my phone and laptop around mid-January. Wireless still works, though.


I've been upgrading regularly via Software Update. Did something change in the distro that may have broken Bluetooth support on some machines?

---

### Post by JGJones on 2008-02-29
My original bluetooth is also a built-in one (laptop is a Dell Vostro 1500) and I selected the option to include a bluetooth module.

---

### Post by bopomofo on 2008-02-29
I followed the advice on another thread. From Synaptic, I uninstalled every package having to do with Bluetooth, and then I tried installing Blueman.


Blueman still says, "No Adapters Found."


I know I'm not the only one having this problem. Again, I'm on an ASUS U6 with bulit-in Bluetooth. Bluetooth **was** working through the "Bluetooth File Sharing" app until some weeks ago. But when did it stop working, and why?

---

### Post by JGJones on 2008-02-29
Having seen mentions of Blueman - prior to this I've not heard of it - it's not in repo's - I googled for it and found the website.

I've now installed Blueman. It does say no adaptor found.

But as soon as I plug in my USB bluetooth module, it immediately list my USB bluetooth module and everything works. It does not however find my laptop bluetooth module. I must stress that **without** Blueman, nothing works even with the USB bluetooth module. With Blueman, it works.

I'm wondering if this is just a case of a broken hardware in laptop? As this is a work laptop, I'll see if I can get a replacement bluetooth module for my laptop and see if I have the same issue or not however it not working without Blueman does make me wonder if it actually really just a broken hardware?

---

### Post by dernwine on 2008-02-29
Having the same problem with a Dell XPS M140. I erroneously posted following message in Absolute Beginner Talk:

[http://ubuntuforums.org/showthread.php?t=708043](http://ubuntuforums.org/showthread.php?t=708043)

I have same bluetooth apps installed, dmesg shows bluetooth found with no errors, but I get "device not found" errors when using hcitool, hidd, etc.

Any headway on this? I don't have dual boot system, just v7.04. Someone mentioned they needed to uninstall hardware on MS before Ubuntu would recognize it....

Regards,

---

### Post by bopomofo on 2008-03-04
> **dernwine said:**
> 

Any headway on this? I don't have dual boot system, just v7.04. Someone mentioned they needed to uninstall hardware on MS before Ubuntu would recognize it....

Regards,


I likewise only have Ubuntu [7.10] on my system. Bluetooth connection (to a phone and an external mouse) did work on Vista for the 10 minutes I left it on my laptop. After installing 7.10 from the CD, I was able to connect my phone using Bluetooth File Sharing.


I will reiterate, at some point this stopped working. "No Adapters Found." How can I get Ubuntu to recognize my Adapter, as it did before?

---

### Post by alesastre on 2008-04-15
I have the same problem with my laptop HP nx8220.

I cannot find any solution yet.

is it possible the "Quick Launch keys" is not working propertly? Because in windows, I can enable and disable my wirelless and bluetooth with one key, I don't now, really, because my wirelless is working well, And I can enable and disable with this key the wireless,  but with dmesg I can see something worng.

There are the alerts when I press the button to disable de wireless and bluetooth

[48778.772000] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[48778.772000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[48778.924000] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[48778.924000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.

And there are the alerts when I press the same button to enable the wirelless and bluethooth.

[48778.772000] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[48778.772000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[48778.924000] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[48778.924000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.

Do anybody know anything about this?

---

### Post by avpap on 2008-05-02
Same here no bluetooth adapter in my Dell XPS M1330 in bluetooth-applet on Hardy-Heron. Someone with an answer;

---

### Post by oiper on 2008-05-05
Same here. It's gone. I'm using Blueman.

---

### Post by oiper on 2008-05-05
Just a quick FYI:

You may be able to do soemthing like the following to turn bluetooth back on.

```
sudo echo "enabled" > /proc/acpi/ibm/bluetooth
```

---

### Post by kaushd on 2008-05-05
oh no! i've just dicovered the same problem on my laptop too!

I did a 
# tail -f /var/log/messages

then pressed the bluetooth button on my laptop, and got the following output:
May  6 05:33:54 ubunts kernel: [ 8139.812000] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
May  6 05:33:54 ubunts kernel: [ 8139.812000] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.

so it's not recognsing the button on my laptop??? blueman also shows 'no devices'.

Any ideas?

---

### Post by srllorente on 2008-05-14
Hi there. I have had the same problem of bluetooth device "disappearing". It does disappear when I turn on my Windows XP VirtualBox Virtual Machine (looks like windows takes control of it and the virtual box is not able to return it to linux after you close the virtual machine... probably a bug in the virtual box software).

In any case, I am able to overcome the problem by just using the Fn+F5 key combination in my laptop, which conmutes my bluetooth/wlan radios on/off.

might not help everyone but at least some ...

cheers

---

### Post by cdoebbler on 2008-06-16
I have same problem on Vaio PCG-TR3A. It has bluetooth but the device is not recognized.

Running Ubuntu Hardy.

Here are some responses I get form dmesg, hcitool, etc.

~$ dmesg

...
[  145.742681] Bluetooth: Core ver 2.11

[  145.746620] NET: Registered protocol family 31

[  145.746629] Bluetooth: HCI device and connection manager initialized

[  145.746639] Bluetooth: HCI socket layer initialized

[   87.558298] Bluetooth: L2CAP ver 2.9

[   87.558305] Bluetooth: L2CAP socket layer initialized

[   87.683932] Bluetooth: RFCOMM socket layer initialized

[   87.683953] Bluetooth: RFCOMM TTY layer initialized

[   87.683956] Bluetooth: RFCOMM ver 1.8

[  396.630011] Bluetooth: BNEP (Ethernet Emulation) ver 1.2

[  396.630020] Bluetooth: BNEP filters: protocol multicast


~$ sudo hcitools scan

sudo: unable to resolve host FB-Old-Vaio-Laptop

sudo: hcitools: command not found


~$ sudo hcitool scan

sudo: unable to resolve host FB-Old-Vaio-Laptop

Device is not available: No such device


~$ sudo hidd --search

sudo: unable to resolve host FB-Old-Vaio-Laptop

Searching ...


~$ sudo /etc/init.d/bluetooth restart

sudo: unable to resolve host FB-Old-Vaio-Laptop

 * Restarting bluetooth                                                  [ OK ] 


~$ sudo /etc/init.d/bluez-utils restart

sudo: unable to resolve host FB-Old-Vaio-Laptop

sudo: /etc/init.d/bluez-utils: command not found


~$ sudo hciconfig hci0 inqmode 0

sudo: unable to resolve host FB-Old-Vaio-Laptop

Can't get device info: No such device

---

### Post by hjlane3 on 2008-07-03
Same problem, I have a bluetooth adapter with my new U405 toshiba laptop. Haven't gotten it to work.

# hcitool scan
Device is not available: No such device
~# hidd --search
Searching ...

# dmesg | grep -i bluetooth
[   53.214480] Bluetooth: Core ver 2.11
[   53.214920] Bluetooth: HCI device and connection manager initialized
[   53.214927] Bluetooth: HCI socket layer initialized
[   53.261787] Bluetooth: L2CAP ver 2.9
[   53.261795] Bluetooth: L2CAP socket layer initialized
[   53.351432] Bluetooth: RFCOMM socket layer initialized
[   53.351446] Bluetooth: RFCOMM TTY layer initialized
[   53.351447] Bluetooth: RFCOMM ver 1.8
[ 7113.956928] platform bluetooth: uevent: unsupported action-string; this will be ignored in a future kernel version
[ 7126.848660] Bluetooth: HIDP (Human Interface Emulation) ver 1.2

---

