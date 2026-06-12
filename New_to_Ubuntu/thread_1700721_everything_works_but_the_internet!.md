---
title: "everything works but the internet!"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by mwilkinson71 on 2011-03-05
Hello, I have a Dell Insperon Mini 10 that I stripped of windows 7 and installed ubuntu netbook remix Nepherius on. This computer has no CD drive, so the install was done and completed thru the USB. the new OS seems to be working fine, (programs run, desktop works, Etc.) all except connecting to the internet. when I plug a cat5 cable in, and ask NetworkManager to connect, it can find the Auto-etho, but cannot connect to anything. I cant connect wirelessy because the NetworkManager says, "device not ready (firmware missing)"

---

### Post by arochester on 2011-03-05
First, try the easy way. Look in your Menu for an item called "Hardware Drivers" or "Additional Drivers". Open that. Does the driver for your wireless card appear in there? If it does, temporarily, connect your computer by wire and click the Enable button. It takes a little while. It should download, install and enable the driver. REBOOT. Job done.

---

### Post by Crazedpsyc on 2011-03-05
You may have to connect wiredly before it can find any wireless drivers!

---

### Post by mwilkinson71 on 2011-03-05
Thanks for the replys, when i click Additional Drivers an error comes up that says "Downloading package indexes failed, please check your network status.Most drivers will be available." I click close and it searches for available drivers.and finds nothing.

---

### Post by wojox on 2011-03-05
Keep your cat cable plugged in, open network manager, go to wired and click auto-etho > edit.

Make sure connect automatically is checked and avaliable to all users and reboot.

---

### Post by fabricator4 on 2011-03-05
Plug the cat 5 cable in before you boot the machine.  There's a chance that this will jump start the ethernet connection.

Once you've loaded the required drivers you should be able to plug in at any time, and use the wireless network.

Chris

---

### Post by mwilkinson71 on 2011-03-06
I tried both those but its still not connecting to the internet via the cat5. I looked online to find what drivers i need and used a USB stick to put them on my Ubuntu computer, is there a way to install them manually?

---

### Post by PRC09 on 2011-03-06
A couple of links for Dell Mini,might be of help......


[http://www.mydellmini.com/](http://www.mydellmini.com/)

[http://www.ubuntumini.com/](http://www.ubuntumini.com/)

---

