---
title: "bluetooth midi adaptor connecting, but no midi port being created"
date: 2019-01-28
forum: Networking &amp; Wireless
---

### Post by alangh on 2019-01-28
This midi adaptor, as I can see from the logs, now connects to the linux box but there is no midi port being created on the linux box, as seen from executing amidi -l .
Any help with this would be appreciated.

For more detailed information: 
Bluetooth devices involved:
    Bluetooth midi adaptor - Yamaha MD-BT01    (which I believe supports Bluetooth LE 4.0 )
    USB bluetooth dongle - sold as Laird BT851 supporting Bluetooth LE 4.2
                            (internally this appears to be Cypress Semiconductor Corp. ID 04b4:f901 )

This is running on Ubuntu Studio 18.04 updated to 18.04.1

bluetoothctl --version
bluetoothctl: 5.48

hciconfig -a
hci0:    Type: Primary  Bus: USB
    BD Address: 00:16:A4:4A:3F:93  ACL MTU: 1021:8  SCO MTU: 64:1
    UP RUNNING PSCAN ISCAN 
    RX bytes:1209 acl:9 sco:0 events:92 errors:0
    TX bytes:5660 acl:9 sco:0 commands:76 errors:0
    Features: 0xbf 0xfe 0xcf 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: 'alan-SH67H3'
    Class: 0x1c0104
    Service Classes: Rendering, Capturing, Object Transfer
    Device Class: Computer, Desktop workstation
    HCI Version: 5.0 (0x9)  Revision: 0x10ca
    LMP Version: 5.0 (0x9)  Subversion: 0x220b
    Manufacturer: Cypress Semiconductor Corporation (305)

rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


From past expericence, because the midi adaptor was timing out, I did the following to increase the supervision timeout
sudo su
echo 2000 > /sys/kernel/debug/bluetooth/hci0/supervision_timeout

Then I ran the following commands to start logging:
sudo journalctl --unit=bluetooth -f | tee journalctl_log1.txt
sudo btmon --write hcitrace1.snoop | tee hcitrace1.txt
sudo dbus-monitor --system | tee dbusmon_log1.txt

And then turned on the midi adaptor, and used the "Settings Manager -> Bluetooth Manager to pair the midi adaptor.
The journalctl log is at pastebin: [https://pastebin.com/PBmXdeQp](https://pastebin.com/PBmXdeQp)
The btmon log is at pastebin: [https://pastebin.com/jGf1n0sG](https://pastebin.com/jGf1n0sG)
The dbus log was voluminous, so I didn't attach it.  But if its wanted I can do so.

And some additional info from command line:
 sudo bluetoothctl
[NEW] Controller 00:16:A4:4A:3F:93 alan-SH67H3 [default]
[NEW] Device DC:EA:50:2A:52:E7 MD-BT01
[NEW] Primary Service
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service0019
    03b80e5a-ede8-4b33-a751-6ce34ec4c700
    Vendor specific
[NEW] Characteristic
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service0019/char001a
    7772e5db-3868-4112-a1a9-f2669d106bf3
    Vendor specific
[NEW] Descriptor
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service0019/char001a/desc001c
    00002902-0000-1000-8000-00805f9b34fb
    Client Characteristic Configuration
[NEW] Primary Service
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service000c
    0000180a-0000-1000-8000-00805f9b34fb
    Device Information
[NEW] Characteristic
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service000c/char0017
    00002a28-0000-1000-8000-00805f9b34fb
    Software Revision String
[NEW] Characteristic
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service000c/char0015
    00002a26-0000-1000-8000-00805f9b34fb
    Firmware Revision String
[NEW] Characteristic
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service000c/char0013
    00002a27-0000-1000-8000-00805f9b34fb
    Hardware Revision String
[NEW] Characteristic
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service000c/char0011
    00002a25-0000-1000-8000-00805f9b34fb
    Serial Number String
[NEW] Characteristic
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service000c/char000f
    00002a24-0000-1000-8000-00805f9b34fb
    Model Number String
[NEW] Characteristic
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service000c/char000d
    00002a29-0000-1000-8000-00805f9b34fb
    Manufacturer Name String
[NEW] Primary Service
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service0008
    00001801-0000-1000-8000-00805f9b34fb
    Generic Attribute Profile
[NEW] Characteristic
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service0008/char0009
    00002a05-0000-1000-8000-00805f9b34fb
    Service Changed
[NEW] Descriptor
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service0008/char0009/desc000b
    00002902-0000-1000-8000-00805f9b34fb
    Client Characteristic Configuration
Agent registered
[MD-BT01]# show
Controller 00:16:A4:4A:3F:93 (public)
    Name: alan-SH67H3
    Alias: alan-SH67H3
    Class: 0x001c0104
    Powered: yes
    Discoverable: yes
    Pairable: yes
    UUID: Headset AG                (00001112-0000-1000-8000-00805f9b34fb)
    UUID: Generic Attribute Profile (00001801-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
    UUID: OBEX File Transfer        (00001106-0000-1000-8000-00805f9b34fb)
    UUID: Generic Access Profile    (00001800-0000-1000-8000-00805f9b34fb)
    UUID: OBEX Object Push          (00001105-0000-1000-8000-00805f9b34fb)
    UUID: PnP Information           (00001200-0000-1000-8000-00805f9b34fb)
    UUID: IrMC Sync                 (00001104-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
    UUID: Audio Source              (0000110a-0000-1000-8000-00805f9b34fb)
    UUID: Audio Sink                (0000110b-0000-1000-8000-00805f9b34fb)
    UUID: Vendor specific           (00005005-0000-1000-8000-0002ee000001)
    UUID: Message Notification Se.. (00001133-0000-1000-8000-00805f9b34fb)
    UUID: Phonebook Access Server   (0000112f-0000-1000-8000-00805f9b34fb)
    UUID: Message Access Server     (00001132-0000-1000-8000-00805f9b34fb)
    UUID: Headset                   (00001108-0000-1000-8000-00805f9b34fb)
    Modalias: usb:v1D6Bp0246d0530
    Discovering: no
[MD-BT01]# devices
Device DC:EA:50:2A:52:E7 MD-BT01
[MD-BT01]# info DC:EA:50:2A:52:E7
Device DC:EA:50:2A:52:E7 (random)
    Name: MD-BT01
    Alias: MD-BT01
    Paired: yes
    Trusted: yes
    Blocked: no
    Connected: yes
    LegacyPairing: no
    UUID: Generic Access Profile    (00001800-0000-1000-8000-00805f9b34fb)
    UUID: Generic Attribute Profile (00001801-0000-1000-8000-00805f9b34fb)
    UUID: Device Information        (0000180a-0000-1000-8000-00805f9b34fb)
    UUID: Vendor specific           (03b80e5a-ede8-4b33-a751-6ce34ec4c700)
[MD-BT01]# 
[MD-BT01]# quit
Agent unregistered
[DEL] Controller 00:16:A4:4A:3F:93 alan-SH67H3 [default]
[DEL] Primary Service
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service0019
    03b80e5a-ede8-4b33-a751-6ce34ec4c700
    Vendor specific
[DEL] Characteristic
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service0019/char001a
    7772e5db-3868-4112-a1a9-f2669d106bf3
    Vendor specific
[DEL] Descriptor
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service0019/char001a/desc001c
    00002902-0000-1000-8000-00805f9b34fb
    Client Characteristic Configuration
[DEL] Primary Service
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service000c
    0000180a-0000-1000-8000-00805f9b34fb
    Device Information
[DEL] Characteristic
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service000c/char0017
    00002a28-0000-1000-8000-00805f9b34fb
    Software Revision String
[DEL] Characteristic
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service000c/char0015
    00002a26-0000-1000-8000-00805f9b34fb
    Firmware Revision String
[DEL] Characteristic
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service000c/char0013
    00002a27-0000-1000-8000-00805f9b34fb
    Hardware Revision String
[DEL] Characteristic
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service000c/char0011
    00002a25-0000-1000-8000-00805f9b34fb
    Serial Number String
[DEL] Characteristic
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service000c/char000f
    00002a24-0000-1000-8000-00805f9b34fb
    Model Number String
[DEL] Characteristic
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service000c/char000d
    00002a29-0000-1000-8000-00805f9b34fb
    Manufacturer Name String
[DEL] Primary Service
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service0008
    00001801-0000-1000-8000-00805f9b34fb
    Generic Attribute Profile
[DEL] Characteristic
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service0008/char0009
    00002a05-0000-1000-8000-00805f9b34fb
    Service Changed
[DEL] Descriptor
    /org/bluez/hci0/dev_DC_EA_50_2A_52_E7/service0008/char0009/desc000b
    00002902-0000-1000-8000-00805f9b34fb
    Client Characteristic Configuration

 amidi -l
Dir Device    Name

---

### Post by alangh on 2019-02-27
I have found one solution to the problem.

So the setup is a Kawai K1 synthesizer keyboard (cira 1990) with Yamaha MD-BT01 Midi Bluetooth LE 4.0 adaptor plugged in. On a linux box (with no built in bluetooth) running Ubuntu Studio 18.04.1 with a USB bluetooth adaptor (Laird BT851 supporting Bluetooth LE 4.2) plugged in.

The problem I had was how to load sysex files onto the keyboard. The sysex librarian programs like [edisyn]("https://github.com/eclab/edisyn") and [Qsynth]("http://www.ucapps.de/jsynthlib.html") do not show the Kawai or Yamaha.

On the linux box run:

```
sudo modprobe snd_virmidi
```
    
This lasts until the next reboot. Note that Ubuntu Studio has the module snd_seq already loaded by default.

Bring up the Bluetooth Manager in the Settings Manager and make sure MD-BT01 appears and is paired.
Bring up the application QjackCtl and press the Start button to start jack. Then press the Connect button to bring up the Connections window.

Under its ALSA tab, there will be MD_BT01 clients for both output and input. For a test that the keyboard is sending midi events to the linux box, one can bring up a synthesizer like Qsynth so it also shows in Connections. Then connect MD-BT01 output port to Qsynth input port in the ALSA tab, and in the Audio tab, Qsynth output port to System input. Pressing keys on the keyboard should sound on the linux box.
 
 Now how to send sysex to the keyboard?
 
 I evenually discovered one needs a rawmidi virtual port. A program I found that constructs one is amidi, provided with the alsa-utils 1.1.3 package ( [https://packages.ubuntu.com/bionic/sound/alsa-utils](https://packages.ubuntu.com/bionic/sound/alsa-utils) ). The sysex librarian programs like JSynthLib appear to only use hardware ports. One wants to create a rawmidi virtual port, connect it to the MD-BT01 ALSA input port, and then read the file in.
 
 The procedure I used to do this is by examining the source code for amidi and identifying where it does the create and where it does the write to the input port. Then run amidi in gdb in a terminal:
 
 ```
gdb amidi
 (gdb) break 595    # break after snd_rawmidi_open(...) but before snd_rawmidi_write(...).
 (gdb) run -p virtual -s ~/Documents/K1/A101.SYX
 Breakpoint 1, main (argc=<optimized out>, argv=<optimized out>) at amidi.c:595
595            if ((err = snd_rawmidi_nonblock(output, 0)) < 0) {
(gdb) 

```
Now looking in the Connections windows at the ALSA tab, one can see that a new client has appeared with a virtual rawmidi port. Connect it to the MD-BT01 input port. Then go back into gdb:

```
(gdb) continue

```
And the sysex file is written to the keyboard (assuming the correct switches on the keyboard are set to allow it).

Note that an issue that 1990's hardware will not be fast enough to handle the sysex input (raised here [https://kawaik1.wordpress.com/2016/04/03/how-to-send-sysex-data-to-the-kawai-k1/](https://kawaik1.wordpress.com/2016/04/03/how-to-send-sysex-data-to-the-kawai-k1/) ) does not appear to be a concern because Bluetooth LE connections have automatic flow control.

It would be nice to have a way of doing this without the broken field running.

---

