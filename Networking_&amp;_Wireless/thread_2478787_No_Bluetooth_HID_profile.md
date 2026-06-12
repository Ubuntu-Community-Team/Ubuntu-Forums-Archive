---
title: "No Bluetooth HID profile?"
date: 2022-09-05
forum: Networking &amp; Wireless
---

### Post by raichea on 2022-09-05
I've run Lubuntu on my small server since v16.04LTS and recently upgraded to 22.04LTS. It's always been rock solid and has performed well for about 6 years. A couple of years ago (while running 18.04 or 20.04), I started using a keyboard/mouse app on my Android phone to avoid having to physically connect devices to the machine. It worked perfectly on the few occasions I needed to directly access the machine (I usually SSH into it). Then some time ago (probably running 20.04, definitely not 22.04), the app on the phone refused to connect to the server. As I only need access infrequently, I just used a physical keyboard instead.

Following the upgrade to 22.04, it still doesn't work so I decided to debug. It seems the problem is that although the phone connects via Bluetooth, it does not establish a HID connection. Here's what is reported about the phone's connection:

00001105-0000-1000-8000-00805f9b34fb OBEX Object Push
              0000110a-0000-1000-8000-00805f9b34fb Audio Source
              0000110c-0000-1000-8000-00805f9b34fb Remote Control Target
              0000110e-0000-1000-8000-00805f9b34fb Remote Control
              00001112-0000-1000-8000-00805f9b34fb Headset Audio Gateway
              00001115-0000-1000-8000-00805f9b34fb PANU
              00001116-0000-1000-8000-00805f9b34fb Network Access Point
              0000111f-0000-1000-8000-00805f9b34fb Handsfree Audio              Gateway
              0000112d-0000-1000-8000-00805f9b34fb SIM Access (SAP)
              0000112f-0000-1000-8000-00805f9b34fb Phonebook Access              (PBAP) - PSE
              00001132-0000-1000-8000-00805f9b34fb Message Access Server
              00001200-0000-1000-8000-00805f9b34fb PnP Information
              00001800-0000-1000-8000-00805f9b34fb Generic Access
              00001801-0000-1000-8000-00805f9b34fb Generic Attribute

Using bluetoothctl, the server reports it has these profiles:

[FONT=monospace]        UUID: Message Notification Se..        (00001133-0000-1000-8000-00805f9b34fb)
                UUID: A/V Remote Control               (0000110e-0000-1000-8000-00805f9b34fb)
                UUID: OBEX Object Push                 (00001105-0000-1000-8000-00805f9b34fb)
                UUID: Message Access Server            (00001132-0000-1000-8000-00805f9b34fb)
                UUID: PnP Information                  (00001200-0000-1000-8000-00805f9b34fb)
                UUID: IrMC Sync                        (00001104-0000-1000-8000-00805f9b34fb)
                UUID: Vendor specific                  (00005005-0000-1000-8000-0002ee000001)
                UUID: Headset                          (00001108-0000-1000-8000-00805f9b34fb)
                UUID: A/V Remote Control Target        (0000110c-0000-1000-8000-00805f9b34fb)
                UUID: Generic Attribute Profile        (00001801-0000-1000-8000-00805f9b34fb)
                UUID: Phonebook Access Server          (0000112f-0000-1000-8000-00805f9b34fb)
                UUID: Audio Sink                       (0000110b-0000-1000-8000-00805f9b34fb)
                UUID: Device Information               (0000180a-0000-1000-8000-00805f9b34fb)
                UUID: Generic Access Profile           (00001800-0000-1000-8000-00805f9b34fb)
                UUID: Handsfree Audio Gateway          (0000111f-0000-1000-8000-00805f9b34fb)
                UUID: Audio Source                     (0000110a-0000-1000-8000-00805f9b34fb)
                UUID: OBEX File Transfer               (00001106-0000-1000-8000-00805f9b34fb)
                UUID: Handsfree                        (0000111e-0000-1000-8000-00805f9b34fb)

Neither shows an entry for HID, which the hardware obviously supports (as it worked previously) and Bluez 5.64 has HID support according to the documentation.

I've been unable to find anything describing how profiles can be individually controlled, so I have to assume HID should just work. Appreciate it if anyone can suggest what else I could try.

Thanks, Steve[/FONT]

---

### Post by raichea on 2022-09-05
I found a Bluetooth mouse and connected that to the computer without problem and it clearly shows the HID profile is in use, so I guess that's conclusive that the problem is not with Lubuntu.

---

### Post by nikaim811 on 2022-09-14
What was the actual problem?

---

