---
title: "echo (sending text) to a file on another computer on LAN?"
date: 2013-12-07
forum: Networking &amp; Wireless
---

### Post by daniel.vustrovsky on 2013-12-07
I have a printer connected to one computer through USB without any drivers installed cause I have a program that prints directly to the "/dev/usb/lp0" file that the printer creates automatically. This also allows me to print through the terminal, eg *$ echo "test" > /dev/usb/lp0* as well

What I want to do is let other computers on the LAN access this file path in the same way. I've tried SSH, Samba and a USB redirector. With SSH the program won't be able to send text directly to /dev/usb/lp0 on the server because I have to be connected to the server through the terminal and I don't know what form I'd have to put the file path on the server into the program (when it's on the local computer, I just put /dev/usb/lp0). With samba I can't even echo to the file, the terminal says No such file or directory, the path I've used was *smb://computername/dev/usb/lp0*. And with the USB redirector, only 1 computer can be connected to the USB device, and I need at least 2. Any ideas? thank you :)

---

### Post by 7182818 on 2013-12-10
You could try using netcat.  For example, on the computer with the printer:

nc -u -l -k 0.0.0.0 9090 > /dev/usb/lp0 &

This will have netcat listen on port 9090 and send everything it gets to the printer

Then, the computers that you want to use the printer on, do the following:

mkfifo /tmp/lp0
tail -f /tmp/lp0 | nc -u <ip of computer with printer> 9090 &

You can then use /tmp/lp0 the same way you would use the printer file.  There's probably a cleaner way, but hopefully this will get you started with something!

---

