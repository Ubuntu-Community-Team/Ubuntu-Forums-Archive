---
title: "[SOLVED] Bluetooth mouse has to be paired again if idle for a while"
date: 2015-05-25
forum: Networking &amp; Wireless
---

### Post by zhangweiwu on 2015-05-25
There seems to be two major bluetooth reconnection problems in Ubuntu. One is caused by upowerd, and can be solved by killing upowerd before enabling bluetooth. The other would require user to click "Connect" in Bluetooth's paired device list to re-connect devices, that is, reconnecting has to be done from the PC end, and can be solved by setting AutoConnectTimeout to 0 in /etc/bluetooth/main.conf

My problem is none of these two, but due to prevailing cases where people suffer from the two problems, hours of Google search can't find my problem. Of course I tried the two remedies and saw no difference.

My problem is that devices has to be deleted, paired again, if the mouse is idle for a while. The same behaviour is seen on both 14.04 and 15.04. If I click "Connect" in the paired-bluetooth-devices list, it goes disconnected in a few seconds, then, once in a few seconds, the UI control toggle button "flashes" to enabled position once in a while, for a few milliseconds, then flashes back to "disabled" position. It seems as if the connection is established, but dropped quickly every time.

I also tried other suggestions, like manually setting PIN (when OS already default to 0000) and writing my device's manufacturer ID into /usr/share/gnome-bluetooth/pin-code-database.xml

In a typical case, the bluetooth is paired with computer and working first time since boot, at 163rd second, and idle for a while, and has to be paired again, at 2348th second:
```

[  163.676833] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[  163.676866] Bluetooth: HIDP socket layer initialized
[  166.692914] hid-generic 0005:045E:077C.0004: unknown main item tag 0x0
[  166.693370] input: Microsoft Sculpt Touch Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/bluetooth/hci0/hci0:21/input13
[  166.697449] hid-generic 0005:045E:077C.0004: input,hidraw3: BLUETOOTH HID v1.20 Mouse [Microsoft Sculpt Touch Mouse] on 74:f0:6d:81:bd:72
[  863.736609] perf samples too long (5002 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
[ 2348.704414] hid-generic 0005:045E:077C.0005: unknown main item tag 0x0
[ 2348.706471] input: Microsoft Sculpt Touch Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/bluetooth/hci0/hci0:21/input14
[ 2348.707452] hid-generic 0005:045E:077C.0005: input,hidraw3: BLUETOOTH HID v1.20 Mouse [Microsoft Sculpt Touch Mouse] on 74:f0:6d:81:bd:72

```

None of lspci or lsusb gives a bluetooth adaptor. I guess that my WeTab clone (bModo 12) has "Qualcomm Atheros AR9285 Wireless Network Adapter" doubling as a bluetooth adaptor. The mouse being examed is Microsoft Sculpt Touch, although I had another brandless mouse with the same problem. In fact I haven't seen a bluetooth mouse working with Linux yet.

I hasitate to get my hands dirty to write a script to ping my mouse or automatically decouple and pair again following a shortcut-key 'reminder'.

Thanks!

---

### Post by zhangweiwu on 2015-05-27
The solution is two fold. 1) add the following to 
```

<device oui="28:18:78" type="moouse" name="Microsoft Sculpt Touch Mouse" pin="0000"/>

```

2. When it doesn't reconnect, don't first rework on computer, remove battery from the mouse and put it back in a few seconds, it start to work right away - and keep working for 2 days already.

---

### Post by frogotronic on 2016-03-14
Where do I add the code?  To which file?

---

### Post by juntjoo2 on 2016-12-15
so what is the resolution for this?

---

### Post by zhangweiwu on 2016-12-15
> **cement_head said:**
> Where do I add the code?  To which file?
The file is  /usr/share/gnome-bluetooth/pin-code-database.xml - I mentioned it in the original post but forgot to do so again in the solution.

---

### Post by juntjoo2 on 2016-12-15
> **zhangweiwu said:**
> The file is  /usr/share/gnome-bluetooth/pin-code-database.xml - I mentioned it in the original post but forgot to do so again in the solution.

Sorry, I'm confused. Do I put that just anywhere in the file? Also, do I put that exact device output number or am I supposed to look that up somehow, and what about the "name" field? Does that matter? I don't have a MS mouse. Mine's Logitech. Thanks

I should point out that I believe we have the same problem as mine also disconnects after idle and to reconnect I have to manually disconnect in settings and then reconnect. And no, setting the other file timeout to 0 didn't help me either.

oh you know, I just looked into that file and that entry is already in there.  So that must just be a reference for a popular device.  So do I need to as such an entry for my Logitech mouse in there? Where did you get advice on this solution?  And that entry wasn't in your file originally?  Maybe they added that for the latest Ubuntu...

---

### Post by zhangweiwu on 2016-12-16
I can't answer both - in the year, I moved to Ubuntu 16.10 and lost my Microsoft mouse.  I also couldn't recall how I associate this behaviour with the missing default PIN.

---

### Post by juntjoo2 on 2016-12-16
Np, thanks. I just grabbed me an RF mouse. Bam, problem solved

---

