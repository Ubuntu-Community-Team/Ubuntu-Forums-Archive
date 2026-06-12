---
title: "Help with permission."
date: 2009-08-28
forum: New to Ubuntu
---

### Post by Nukester on 2009-08-28
I am using this manual to install my WUSB54GSC driver for my Wireless adapter:



[b]Greetings to all!

I've been fixing a computer for a friend, and by fixing I mean blowing away Windows and replacing it with a much better alternative - Ubuntu 8.04.1.

My friend bought a Linksys Compact Wireless-G (WUSB54GSC) network USB card. I thought, hey, plugging it in should work... right?!!? After going through every 4 letter word in the dictionary and making up a lot of new ones, I finally got it working. So, I would like to pass my experience on to my fellow Linux users.


Here's how I did it (I hope it works for you!)

1. Turn on your computer (if it's off, or not broken from you getting upset by this problem)

2. Make sure your wireless card is unplugged from the USB port.

3. Take a break, this was a lot of work, have a beer.

4. Okay, after the beer, you're going to need a Windows machine.

5. Install the USB drive on the Windows machine using the installation disk. If you dont have one, say a few 4 letter words, then come back and download them from here: [http://www.linksys.com/servlet/Satel...#versiondetail](http://www.linksys.com/servlet/Satel...#versiondetail)

6. Copy two files from your Windows machine to your Ubuntu machine...

C:\WINDOWS\System32\Drivers\rndismp.sys
C:\WINDOWS\System32\Drivers\usb8023.sys


7. Now you need two more files, and you can get them from a lot of places. I would get them from the link you downloaded or the CD you have. They are...

WUSB54GSC.cat
WUSB54GSC.inf

On the CD or zip file, they should be under the Drivers directory... I hope.



8. Go back to Ubuntu (thank god!!!)

9. Open a terminal window

10. Input the following

Code:
sudo ndiswrapper -e wusb54gsc
sudo ndiswrapper -i /home/eric/linksysDriver/WUSB54GSC.inf
sudo cp /home/eric/linksysDriver/*.sys /etc/ndiswrapper/wusb54gsc
sudo modprobe ndiswrapper
ndiswrapper -l

NOTE: This is from my computer, I created a directory linksysDriver under my home directory. Don't copy me unless your name is eric!



Hopefully at the end, you'll get:
Code:
wusb54gsc : driver installed
	device (13B1:0026) present

11. If you get that, drink another beer!!!! If not, drink one anyway.... you'll probably need it soon :-(

12. Plug in your Wireless USB card.

13. Type lsusb in a terminal window to make sure all is well.

14. RESTART UBUNTU!! This took me a while to figure out

15. Pray that it doesn't lock up

16. Do what you do to connect to your wireless network, it may be iwconfig with some other settings or simply go into System->Administration->Network



I hope this helped a little. I know this can be a pain to install, but it was worth it. Heck, I'm using it now to write this message!

Good luck to all![/b]





I need help with step 7, as I tried to look for the WUSB54GSC.inf and .cat file in my Driver file on the Linksys CD, but all I see are ndiswdm.inf and some other irrelevant files, can anyone tell me where i can find em, or download em?

---

### Post by Iowan on 2009-08-28
Did the [download link]("http://www.linksysbycisco.com/US/en/support/WUSB54GSC/download") in the article you referenced have the files you needed?

---

