---
title: "Remote Ubuntu 12.04 desktop cannot display X on local laptop"
date: 2013-11-21
forum: Networking &amp; Wireless
---

### Post by john19 on 2013-11-21
I have an Ubuntu 13.04 laptop and an Ubuntu 12.04 desktop. I want to be able to open and see images, windows, and pdf files that are located on the desktop via remote access from my laptop. 

When I tried to follow instructions like those at "http://www.hungry.com/~jamie/xexport.html", I managed to sudo apt-get install telnetd, "xhost +", then access into my desktop, set and export the DISPLAY variable, and then open .png files using the "eog my_image.png" command, but the images would open up on the remote desktop's screen and NOT on my laptop's screen. I tried changing the DISPLAY variable to the ip address of my laptop, but I could only get images to display on the remote desktop. But I want to be able to see the remote desktop's windows on my laptop. 

In addition, when I tried to do it the other way around and to access my laptop from my desktop, I get a message " WARNING **: Could not open X display". If I don't have "DISPLAY" set, xterm terminal says "X11 initialization failed" 

Finally I tried to use SSH. First I generated a public and private key, then when I tried to connect using PuTTY with the IP address of the desktop and default settings. When I clicked "open," it said "PuTTY Fatal Error Connection refused: OK". When I tried the terminal command "ssh ###.###.##.###" (desktop ip), ssh said the same thing: "ssh: connect to host ###.###.##.### port 22: Connection refused".   

How do I get the pictures from my desktop to appear on my laptop? For my purposes, I don't care if someone can sniff my wifi and see every packet of data that goes th
rough because the data is just school coursework and pdf files. I just want there to be as little lag as possible and to be able to see the remote desktop. Thank you.

Also, what's with:
** (eog:10450): WARNING **: Command line `dbus-launch --autolaunch=6d91b5555c8bbff7573f20a500000002 --binary-syntax --close-stderr' exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.\n

---

### Post by steeldriver on 2013-11-21
**Provided both machines are inside a LAN (i.e. behind a NAT router with external ports closed)** the easiest way is 'Desktop Sharing', which uses Vino to provide a VNC service.

On the desktop machine, go to the dash and type 'Desktop Sharing' and when the dialog box pops up, check the box 'Allow other users to view your desktop'. Optionally uncheck the box 'Allow other users to control your desktop' if you want view-only access. Set the 'Security' preferences as you see fit.

On the laptop, open the 'Remmina Remote Desktop Client' and enter the IP address of the desktop.

Or if you want to forward individual applications, install openssh-server on the desktop and use ssh -X from a terminal - PuTTY is not necessary if the client is a Linux box. 

Personally I'd recommend uninstalling telnetd for security reasons. **VNC is not secure either so if you are not behind a NAT router post back and we can suggest some additional security measures using SSH tuneling.**

---

### Post by john19 on 2013-11-21
The Desktop Client is okay, but I also want multiple different users with multiple different accounts to all be able to get a graphical window view of pdf files in computer without each person directly interfering with the other person. With VNC, different users clash in the same screen.

Also, some problems:
ubuntu@ubuntu:~$ sudo apt-get openssh-server
E: Invalid operation openssh-server
ubuntu@ubuntu:~$ sudo apt-get ssh-server
E: Invalid operation ssh-server

(I installed sshd. )

Then:
ssh -X computername@HostIPaddress
Enter Password: *****
Welcome to ubuntu
eog image.png (No image displays)
DISPLAY = Local_IPaddress
export DISPLAY
eog image.png (No image displays)

Note:
SSH is too slow, VNC doesn't allow multiple users to view different  images, and telnet just won't re-route my image back to the local  machine.
Telnet only opens in the remote machine. 
See:
$ telnet Host_IP    
Trying Host_IP 
Connected to Host_IP 
:~$ DISPLAY=###.###.##.###:0.0 // DISPLAY=Local_IP 
:~$ export DISPLAY 
:~$ eog ./Facebook.png // DISPLAYS ON HOST'S SCREEN - Regardless of changes in DISPLAY

---

### Post by john19 on 2013-11-22
//Sorry, this is an accidental re-paste of what I just said.

So SSH it TOO SLOW. VNC does not allow multiple users to access the X-Window without interfering with one another (they all share a desktop space). Telnet only opens in the remote machine (not the local one) regardless of how I set the IP. See:

ubuntu@ubuntu:/home$ telnet ###.###.##.### //Host IP address
Trying ###.###.##.### //Host IP address
Connected to ###.###.##.### //Host IP address
Escape character is '^]'.
Ubuntu 12.04.3 LTS

johnmichaelreed@Ubuntu1204LTS:~$ DISPLAY=###.###.##.###:0.0 //Local IP
johnmichaelreed@Ubuntu1204LTS:~$ export DISPLAY
johnmichaelreed@Ubuntu1204LTS:~$ eog ./Facebook.png  //DISPLAYS ON HOST'S SCREEN.

---

### Post by steeldriver on 2013-11-22
If X forwarding over SSH is too slow then something is wrong with your setup or your LAN, I would think

If you want multiple concurrent user sessions over VNC, then you need to install a different kind of VNC server instead of using the default Vino 'Desktop Sharing' server. I use 'tightvncserver' but there is also 'vnc4server'. Then each user starts their own instance and connects to that via a dedicated port (the 'vncserver' script will choose a display number / port number, or you can ask it for a specific one on the command line). There are other solutions such as FreeNX that may work for you as well.

I have never tried to use X forwarding over telnet so I don't even know if it's supported

---

### Post by john19 on 2013-11-22
Well VNC (encryption disabled, low image quality by default) has much less lag than X11 forwarding (encrypted, handshake, higher image quality). Look it up and pick a random site: Ex. [http://arstechnica.com/civis/viewtopic.php?f=16&t=1155637](http://arstechnica.com/civis/viewtopic.php?f=16&t=1155637) . [COLOR=#000000]tightvncserver sounds like a good idea, though - I'll try that. I like VNC in that it can be used from Linux to Windows without Windows needing an X client. "[/COLOR]Insecure telnet" might be an option if it worked (I tried everything). Description of the process is here: [http://x.cygwin.com/docs/ug/using-remote-apps.html](http://x.cygwin.com/docs/ug/using-remote-apps.html) . Honestly, lag is my #1 concern atm.

---

