---
title: "Where to install the drivers?"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by Nemain on 2009-12-29
Don't know if this should be in the Network section, but this feels absolute beginner talkish, so I'll try here :)

I've been trying to get my wireless card working, it's a Broadcom thing which I've had problems with in Vista, Fedora, Win7 and now Ubuntu. I've found the drivers, and now I wonder, where should I untar them?

Following these instructions [http://www.broadcom.com/docs/linux_sta/README.txt]("http://http//www.broadcom.com/docs/linux_sta/README.txt")
I do know how to do it, but not where...

---

### Post by 3rdalbum on 2009-12-29
For Broadcom, the first thing to do is connect to your router using an Ethernet cable, so you have an internet connection. Now go to System > Administration > Synaptic Package Manager and click the Reload button.

Once that's all finished, close Synaptic and go to System > Administration > Hardware Drivers. If there is an appropriate driver available from the Ubuntu repositories, it will be offered to you. Activate it and once it's all downloaded and installed, you can reboot (preferably shut down all the way and then start up again) and access your wireless network.

This sounds a lot easier than following those overly-complex instructions.

If you have to install this driver, then you can extract it anywhere, just as long as you can navigate your terminal to the directory. Hint: In the terminal, type the word "cd" and press the space bar, and then drag the directory onto the terminal to complete the command. This navigates the terminal to the correct directory for you to run those commands in.

---

### Post by Nemain on 2009-12-29
There's two drivers, I can activate one and the other just don't activates itself when I ask it to. I tried to reload, but it was all the same.
So I have to stick to the manual way... Wow, the tip about dragging the directory into the terminal, cool! :)
Thank you for your help (though I'm not there yet :))

---

