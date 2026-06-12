---
title: "Howto: Verizon UM175 USB EVDO under Hardy"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by jcostom on 2008-09-02
Before starting, have your updates done.  At the time I'm writing this, 2.6.24-19-generic is the current stable -generic kernel.  Everything here also works fine on the 2.6.24-21-eeepc kernel on my eeePC 1000, running Hardy.  Also install gnome-ppp before you get started.  You'll need to know your UM175's phone number as well.  For this guide, I'll assume it's 212-555-1212.

**Step 1.** Plug the device in.  Ok, you’re done Step 1.

**Step 2.** Launch gnome-ppp, configure settings, other than the defaults:
[LIST]
[*]Modem Tab
[LIST]
[*]Device: /dev/ttyACM0
[*]Type: USB Modem
[*]Speed: 460800
[*]Phone Line: Tone
[*]Volume: Off
[/LIST]
[/LIST]

[LIST]
[*]Options Tab
[LIST]
[*]Minimize: checked
[*]Dock in Notification Area: checked
[/LIST]
[/LIST]

Click Close.  Fill in the fields in the main Gnome PPP window:

[LIST]
[*]Username: [email]2125551212@vzw3g.com[/email]
[*]Password: vzw
[*]Phone Number: #777
[/LIST]

**Step 3.** Click Connect

**Step 4.** There is no step 4.  You’re connected.

Congratulations, you’re online, EVDO style.

---

### Post by yonacab on 2008-12-18
How do you get this usm175 usb verizon install into ubuntu? I have a mini 9 inspiron with only this os program.

---

