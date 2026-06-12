---
title: "samsung mobile"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by RobikShrestha on 2011-04-01
I installed samsung pc studio 3 but I cannot transfer data with USB cable. What should I do? Also how do I make the bluetooth of my laptop work with mobile?

---

### Post by GaryTheCat on 2011-04-01
What sort of mobile?

Can you mount it as a usb drive?

A bit more info might help us to help you :D

---

### Post by RobikShrestha on 2011-04-01
It is samsung z170 mobile phone. I could read/write multimedia to it in windows 7 by installing samsung pc studio. But here I installed PC studio. It tries to detect USB cable, but takes forever. It does not issue any message that USB can't be mounted or USB not detected, but rather tries to detect cable but does not detect it. Also, how do i connect my PC and mobile with bluetooth? Both have in-built bluetooth devices. on system->preferences->bluetooth, it says, Your computer does not have any bluetooth adapters plugged in. What is an adapter?

---

### Post by GaryTheCat on 2011-04-02
I have a Samsung Galaxy S (I was hoping you'd say it was an android phone).

Do other USB devices work on your machine? (Memory Sticks etc)

I don't know the specifics of your phone but I'd put money on there being an option in the menu to turn on "mass storage mode" - Although after a quick google search, it seems like your handset might not support "mass storage".  I'd think about using Samsung software in windows to update your firmware and try again in ubuntu.

If that doesn't work, it might just be 'one of those things you still need windows for' - us Linux-philes hate that phrase but as an example, I only use my Windows partition to update my tomtom - I've spent hours trying to get it to work with ubuntu (which is remarkable because it's built on linux),  figured the occasional boot into my windows partition was less hassle than more tinkering with Ubuntu.

Apart from that, I'm out of ideas - but it's a safe bet someone here will have the answer.

Good Luck!

G

---

### Post by GaryTheCat on 2011-04-02
Sorry

As for the bluetooth issue - look in system --> Administration --> Additional drivers to see if there's a bluetooth driver in there

G

---

### Post by 3rdalbum on 2011-04-02
> **RobikShrestha said:**
> I installed samsung pc studio 3 but I cannot transfer data with USB cable.

WINE doesn't work with USB devices, because it requires communication at too low a level.

If your mobile doesn't work as "USB mass storage" and let you transfer data just using the desktop, then you'll need to use the software on Windows - or live without it.

---

