---
title: "Help with USB"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by louis0591 on 2009-02-13
Hey, like everyone else here i'm reletivley new to ubuntu. everything has been going great for the exception of two things.  ubuntu recognizes both my usb external hd and my usb mouse. i have a memory card reader and its it recognized under the "computer" option but when i insert a memory card into the reader and double click on the location nothing pops up.

i also have a prob with the system sound.  i only get sound from the startup and from music/video/and online flash files. i get no other sounds in the system. 

can anyone help me fix this?

---

### Post by sydbat on 2009-02-13
For the memory reader, try putting the memory card into it, *then* plug the reader into your USB.

What other sounds are you looking for? There are no sounds set by default for system events (in Windows, they have theme sounds set up by default).

If you mean media players, games, etc are not generating sound, go to System > Sound > Devices and change the settings from Autodetect to ALSA or PulseAudio or OSS. There is a test button next to each option to allow you to make sure the one you choose is working. Then open your media player, game, etc and test it is real life. Play with each option until you get sound.

---

### Post by orange72_camaro on 2009-02-13
I am having the same problem.  when I double click on the SD card I get this error

Unable to mount location

Cannot invoke CheckForMedia on HAL: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I tried what sydbat said and it does nothing to help.


ok an update for me.  if I put in a 2gb SD it works fine.  my 4 and 8 dont work and give me that error.  any ideas on why it wont support a 4 or 8?  the card reader works with the 4 and 8 on my wifes eeepc with windows xp so I dont think its the reader.

---

### Post by louis0591 on 2009-02-14
orange72_camaro, thnx 4 the reply, glad to c im not the only 1 w/ ths prob. but ur farther along then me. my reader doesnt even get recognized in media. my external hd shows up but thats it.

---

### Post by jcats on 2009-02-14
For both Orange Camaro and louis;
Where the devices you are trying to mount ever run in Windows? If they were, did you use the "safely remove" when you were done with them? If you just pulled them out of the USB ports, it won't mount in Ubuntu. Try reinstalling in a Windows machine and properly unmount them.
Once that is done, and they still won't mount-
Plug in your USB in Ubuntu and look in "Places" for the name of your USB
In the terminal, type:

> sudo mkdir /media/"device name"

with "device name" being the name of your USB(don't use the quotation marks)
Then type in terminal

> sudo mount /dev/sdb1 /media/"device name"

That should mount your device. 
When your ready to unmount it, type in terminal:

> sudo umount /media/"device name"

Hope this helps
jcats

---

