---
title: "Conceptronic CBT200U2 bluetooth 2.0 usb adapter and Feisty"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by pgilmon on 2007-05-18
Hi, this is just to tell how to set up this adapter on Unbutu 7.04 (Feisty)

Plug the device into an USB port, and then install gnome-bluetooth:

```
sudo aptitude install gnome-bluetooth
```

After that, click on Applications -> Accessories -> Bluetooth File Sharing. A new icon appears next to the clock. Whenever you try to send a file from the phone to the computer, a window will ask you whether you want to accept it. The file is atomatically stored on the Desktop.

In order to send a file from the computer to the phone, just right-click on the file to send, then click on "Send to". Choose Bluetooth under "Send as" and select your phone under "Send to". Click on "Send" and you're done.

As you can see everything works out-of-the box (at least for me). I just wanted to post this in case anyone wanted to know about a device of this kind that works, since I've read about a lot of problems when trying to send files form the PC to the phone.

Thanks for your time and bye!

---

### Post by pgilmon on 2007-05-19
Here is how to pair with a mobile phone:


First, in order to know the your phone's address, type:

```
hcitool scan
```

Then run:

```
passkey-agent /usr/bin/bluez-pin [phone-mac-address]
```

Now try to pair to your computer from your mobile phone. It whould ask you for a password on both the phone and the computer. Just write the same on both.


If you have any questions, please ask.

---

