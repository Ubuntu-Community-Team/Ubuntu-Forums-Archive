---
title: "DELL D420 With DELL Wireless 350"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by depill on 2007-03-06
I have a DELL D420 laptop and it has an built-in Dell Wireless 350 Bluetooth module, and from the windows version I suspect that is some kind of a Toshiba fork. I got wireless working great, but ubuntu won't detect my bluetooth module, I have read on other web pages that it is no problem. I think this is connected to that you can disable or enable the module by hand in Windows. The switch on the side of the computer does not seem to work, and reseting the BIOS config to default settings didn't do the trick either.

Can you recommend anyway to turn on the bluetooth module on my computer ? I am going completely nuts because I really like my bluetooth mouse.

This is my lsusb output, I can't be sure which one it is. 
```
lsusb
Bus 005 Device 003: ID 413c:9001 Dell Computer Corp.
Bus 005 Device 004: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 009: ID 413c:8105 Dell Computer Corp.
Bus 001 Device 004: ID 413c:a005 Dell Computer Corp.
Bus 001 Device 005: ID 0b97:7761 O2 Micro, Inc.
Bus 001 Device 008: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 001 Device 007: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000

```

Any ideas ?

---

### Post by slestak on 2007-03-13
I have the same problem with an e1505.

lsusb -v does not appear to list the Dell 350 bt adapter.

hcitool dev just shows "Devices:"

This seemed to work better abt 2 months ago, but i stopped working on it.  

Is the kernel config used to build the latest kernels available to see what bluetooth options were compile in and which are modules?

Do we need to update a restricted-modules package.  Im learning the debian/ubuntu way and im not always sure what provides which modules.

additional info:
I dual boot this laptop with Vista and the bluetooth works fine, so I know the adapter is installed and functional.

---

### Post by slestak on 2007-03-15
bump.

Is bt-sco still a vialble driver for bluetooth?  Mot reading Im doing looks like its depracated.

---

### Post by petebarron on 2007-03-16
I'm having the same here with the internal bluetooth on the D420.

I may be wrong here, but as far as I can tell the "413c:8105 Dell Computer Corp"  is the internal bluetooth device. However,  it does not appear to recognized it as such. You can determine this by first typing lsusb, then using the switch on the side to turn off the bluetooth, and then typing lsusb again. The above device is then missing from the lsusb listing.

From doing a bit of hunting around the DELL Wireless 350 is normally identified as 413c:8103 and not  413c:8105. So, I can only assume that it is a new version or something. I'm not sure how address the problem so if anyone has any ideas....

pete

---

### Post by Topogigi on 2007-03-29
The weird thing is that after booting into Win Vista, the adapter is correctly recognized by linux and it works perfectly (I have a Dell Precision M65 with Dell BT 350 module too). 

It seems to me that the initialization of the module is done at low-level by Vista (loading a piece of firmware at boot time???). 

By the way, after booting into Vista and restarting into Linux (not switching off the laptop) the adapter is recognized as 0x413c:0x8103 as it should be.... :confused:

---

### Post by petebarron on 2007-03-29
mmm that's interesting Topogigi.  

I also noticed that in dmesg that the device is recognized as a HID device ie as a mouse and keyboard (see below).

usb 1-2.4: new full speed USB device using uhci_hcd and address 12
ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
usb 1-2.4: configuration #1 chosen from 1 choice
input: HID 413c:8105 as /class/input/input6
input: USB HID v1.11 Keyboard [HID 413c:8105] on usb-0000:00:1d.0-2.4
input: HID 413c:8105 as /class/input/input7
input: USB HID v1.11 Mouse [HID 413c:8105] on usb-0000:00:1d.0-2.4

Seeing this I tried hid2hci -0 with no luck. Got a "No devices in HCI mode found" error.

pete

---

### Post by Topogigi on 2007-04-08
Ok, after a lot of efforts I finally found a workaround.

The problem rises only for the people that have bought a laptop with Windows Vista preinstalled. The bluetooth Vista driver actually loads a piece of firmware upgrade from CSR (the bluetooth chip manufacturer) that enables the "Vista profile pack" i.e. a set of utilities developed for the Microsoft Bluetooth stack and api. These utilities, among other things, are used to initialize the bluetooth chip in a way that allows a bluetooth mouse or keyboard to be enabled via the bios before the boot phase. Obviously the Microsoft bluetooth stack is aware of this kind of initialization while the bluez stack simply ignore it.

So, here comes the workaround:

1) Boot into Vista and download from the Dell support site the last BT 350 driver for Windows XP and unzip it in a folder
2) Find a directory in that folder called "DFU"
3) Find the file called "DFU.exe", right click it and choose "Run as administrator"
4) Wait until the firmware downgrade has finished, then reboot into Vista and you will find that the bluetooth chip is now not recognized. Go to Device manager and manually reinstall the Vista BT driver (don't use the setup.exe provided by the driver pack, simply install it using the "have disk" way and load the .inf file directly from the Vista driver directory).
5) Reboot into Linux. Voilà

I know this is a dirty workaround (you'll lose the Vista advanced features of "Vista Profile Pack", but it is useful to have a working BT adapter in linux until the Bluez people will make the drivers compatible with the new Vista features).

Bye
:popcorn:

---

### Post by petebarron on 2007-04-11
Thanks Topogigi for that but unfortunately my vista partition is long gone. :-/ So if you figure out another way to downgrade the fireware through linux let me know. thanks pete

---

### Post by Topogigi on 2007-04-12
Hi Pete, if your windows partition has gone, you can always boot from a BARTPE cd (google for it if you don't already know about it...) and perform the downgrade from the win xp environment.

Alternatively, you can use a virtual machine with windows on it to perform the downgrade (didn't try it, but it should work).



Bye

---

### Post by petebarron on 2007-04-16
cool, I'll give that a go. pete

---

### Post by Steve White on 2007-04-25
I have the same issue, with my D420, which I recently bought with Vista installed.

I wrote to Dell customer support about the problem today citing this thread, in the hopes of keeping the problem in front of them.

---

### Post by KyleYankan on 2007-04-28
> **Steve White said:**
> I have the same issue, with my D420, which I recently bought with Vista installed.

I wrote to Dell customer support about the problem today citing this thread, in the hopes of keeping the problem in front of them.

I also experience this issue. when i do `hcitool cc xx:xx:xx:xx:xx` it disconnects in less than a second
i string `hcitool cc 00:17:84:7C:D3:38 && hcitool auth 00:17:84:7C:D3:38A` and get this:
HCI authentication request failed: Connection timed out


bluetooth has never worked for me on my laptop. Dell Insipiron E1405, with Wireless 355

---

### Post by fdoving on 2007-05-06
I have this problem too, testing the workaround now.

---

### Post by fdoving on 2007-05-06
Yep, workaround works for me too. Didn't bother installing the bluetooth driver in vista after downgrading the firmware. Works in linux, that's what's important.

Thanks for the workaround Topogigi.

---

### Post by aneas on 2007-05-14
Gaah, this issue got me going nuts! I have a d620. 

The workaround doesnt work with BartPE windows xp disc (I even added all the dlls from a working windows system32 dir), I tried using qemu (and kvm) but the damn bluetooth module wont be passed to it (Warning: could not add USB device host:413c:8105), the other dell usb thing is passed though. I dont have windows installed on my machine anymore us you understand by now.

Any other suggestions before I go to resizing my root drive, install winxp on a small partition, do the workaround and then get rid of xp again? :(

---

### Post by melman101 on 2007-05-18
Laptop: Dell D420

Ok I was also in this quandry. I was like damnnnnn VISTA!!!!

So, ok I tried to install the driver in Virtualbox and then all of a sudden the device popped up in my ubuntu. The installation failed in Windows and the DFU tool said could not find a compatible chip. If I ran the install again it would try DFU getting further but still not working.

Back in ubuntu, the bluetooth device now showed up in hcitool dev. However, when I ran an hcitool scan it would show no devices and the light wasn't on. So then I was like, hmmm let me try to BartPE thing, but I couldn't get avifil32.dll to load up for the DFU.exe program.

So then I took that dfu file from the dell drivers and ran a btdfu verify on it.

Then ran an btdfu upgrade filename

and it worked

However when it exited, it said "Error status could not read device"

typed

hcitool dev

Devices:

BLANK!!!! Back to square one. Was screwed.

Went back into virtualbox windows, now the USB device had a different number so i enabled the connection. It was looking for a driver. Re-ran the setup. This time it executed DFU.exe and it worked................................ UNTIL IT GOT TO THE END AND SAID FAILED!.

However, once i disconnected my VirtualBox USB device, the BLUETOOTH LIGHT POPPED ON!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

And now when I ran hcitool scan   i saw my cell phone!!!! Thanks for all the suggestions and help in this thread. Hope my thread helps some people.

BTW, FEISTY FAWN!!!!!!!!!!!!!!!!!!!!!!!!!! AWESOME!!! I love it. Vista ain't got nothing on this thing.

I got everything working!

---

### Post by slestak on 2007-06-22
what driver on our side would need to be changed to account for the new initialization change for this bluetooth card?  There is a bug at launchpad that I am trying to get some attn to this issue on, but it isnt moving.

---

### Post by 3SV on 2007-07-11
Many thanks to Topogigi for pointing me into the right direction. I have installed vista and that has broken my bluetooth in ubuntu. On this time there is a special download on the dell site specially for downgrading the firmware. I just run that exe in vista, en that was fixing the problem.

---

### Post by virtualj on 2007-08-20
I am having the same problem with my D820.
But I don't have a vista or XP partition anymore. I tried downgrading with XP running in VMWare but that didn't work, I get an erro message saying no device was found. With the Bart PE cd the installation doesn't even start.
Is there an other way or should I just install windows xp to do the downgrade?

---

### Post by aneas on 2007-08-20
> **virtualj said:**
> I am having the same problem with my D820.
But I don't have a vista or XP partition anymore. I tried downgrading with XP running in VMWare but that didn't work, I get an erro message saying no device was found. With the Bart PE cd the installation doesn't even start.
Is there an other way or should I just install windows xp to do the downgrade?

Thats what I ended up doing, its very stupid but it works. I should've done that from the beginning and would have saved a lot of time trying with bartpe etc..

---

### Post by virtualj on 2007-08-20
> **aneas said:**
> Thats what I ended up doing, its very stupid but it works. I should've done that from the beginning and would have saved a lot of time trying with bartpe etc..

I installed Windows XP and downgraded the bluetooth driver. Now my bluetooth works again.
Thanks for the help.

---

### Post by SarahKH on 2007-10-20
Just a bump and to say that, yes, downgrading the firmware worked a treat.  Had to pull the module and install it in another (XP) machine to do it, but it now works properly. 

God damn Vista.

---

### Post by Ralph L on 2008-01-19
I have a Dell Latitude D610 with the Dell 350 module for Bluetooth.  I can't make it work.  In particular I am trying to send the computer pictures from my cell phone.  This works fine under Windows XP.  I just start the send in the Nokia cell phone and XP brings up a window where I can specify where the image file is too be saved.  Please note that I have loaded the latest driver and firmware under XP.  Vista has never run on this computer so I don't think I have the problem of needing to drop back to an earlier firmware.

When I bring up Gutsy I get a Bluetooth icon in the panel (taskbar).  The blue light comes on solid.  If I left click the icon nothing happens.  If I right click the icon i get three choices:  Preferences, About, Browse Devices.  

There are 3 tabs under preferences:  ralph-laptop-0, Services, and General.  Under the ralph-laptop-0 tab I have "Visible and connectable for other devices" checked.  "Make adapter invisible after" is set to never.  The section on "Bonded devices" is grayed out so I can't do anything with it.  I don't even know what this is for.  Adapter name is "ralph-laptop-0.  Class of device is "Laptop computer.

Going to the Services tab I have all four services checked and running.

Going to the General tab I have checked "Automatically authorize incoming requests" and "Select class of device automatically"  In the Notification Area I have selected "Only display when adapter present".

Selecting "Browse Devices" (right clicking the Bluetooth icon in the taskbar panel) shows a device "Nokia 6102i".  That's my cell phone so Bluetooth has recognized my cell phone and picked up its identifier.  However, when I click connect for that device I get "obex://[00:18:c5:94:e2:f1]" is not a valid location.  I don't know what this means.  Also, I don't know that I even need to click Browse Devices.  

Any hints on what I should be doing would be greatly appreciated.  I am a newbie and am very lost.

Thanks in advance

Ralph

---

### Post by StewartG on 2008-03-03
/home partition shrunk, XP partition created, XP installed, Dell downgrade performed, Grub added back to MBR and Bluetooth now works! XP partition removed.

Bluetooth file sharing installed and working just fine.

What a complete waste of time, wish I had never wondered how Vista would run on my laptop. Thanks to all those that went before me to find this solution.

---

