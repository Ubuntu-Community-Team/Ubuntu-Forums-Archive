---
title: "How to get started using my local network? How to access local computers?"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by sofasurfer on 2008-05-05
I have a Belkin router with 2 computers (Windows with Trendnet adapter and Ubuntu with Linksys usb adapter) wirelessly connected to the internet. 

I have accessed my router setup by going to 192.168.2.1 and learned that my Windows address is 192.168.2.2 and my Ubuntu address is 192.168.2.3.

Now, how do I use my network to access one computer with the other? I think this would be called accessing my LAN? Is there a step by step tutorial that I have not been able to find?

---

### Post by meg23 on 2008-05-05
Are you referring to accessing files or being able to view and manipulate the desktop or both?

---

### Post by sofasurfer on 2008-05-05
I guess both. I want to share files and I want access to the other computer. I guess the correct answer at this point is that I want to do whatever you can help me with.

When I go to my router setup page the "DHCP client list" shows:

IP Address  	Host Name  	  MAC Address
192.168.2.2     daryl-0a73614f5   00:18:e7:0b:30:94
192.168.2.3     unknown           00:1a:70:36:c3:ea

I think this is showing my 2 computers.

When I go to "network interfaces" in my "other" applications I see:

lo    127.0.0.1     255.0.0.0      Loopback  up   00:00:00:00:00:00
wlan0 192.168.2.3   255.255.255.0  Broadcast up   00:1a:70:36:c3:ea
	
I think this is showing only 1 computer (wlan0)

Ok. This is the only info I can find that means anything to me. Does it help at all?

Thanks for replying.

---

### Post by meg23 on 2008-05-05
The addresses that are important are the 192.168.2.2 and 192. 168.2.3. These are the &#618;P addresses of the computers on your local network. In order to use remote desktop on ubuntu, you need to go to system>preferences>remote desktop and enable desktop sharing (which is the vnc server) with a password and make sure the prompt for permission setting is disabled. Now that you have enabled desktop sharing, you need to download a VNC client/server for windows XP, I recommend tight vnc. You can download it from here: 

[http://www.tightvnc.com/download.html](http://www.tightvnc.com/download.html)

I cannot tell you too much about how to configure tight vnc because I haven't used windows in 5 plus years but I do know that it is a fine piece of software. In order to get on to your Ubuntu box from tightvnc on the windows box, you need to enter the ubuntu boxes local IP into the client and it will prompt you for a password and then you will connect to the machines desktop. To get on to the windows machine remotely, enable the VNC server, determine the local IP of the windows machine, and go to your Ubuntu box and open a terminal. Type in the following:

vncviewer localipofwindowsmachine:0

Once again, you will be prompted to login and the vnc screen will open. 

About filesharing, you have a few options. The first option is to use samba filesharing. 

Samba is very easy to configure, see this youtube video for a simple how to:

[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

Samba does not need to use local IP addresses. 

Another option is to use a file syncing program like Unison. I find that samba is not always reliable so I prefer to use Unison to sync files between computers. Unison will need to use local ip addresses. You can install unison by opening a terminal and typing:

sudo apt-get install unison

Try some these things and reply back if you need help configuring anything.

PS: To find your local IP in ubuntu, open a terminal and enter:

ifconfig

Bare in mind that IP addresses change on occasion.

---

### Post by Iowan on 2008-05-05
> **sofasurfer said:**
> When I go to my router setup page the "DHCP client list" shows:

IP Address  	Host Name  	  MAC Address
192.168.2.2     daryl-0a73614f5   00:18:e7:0b:30:94
192.168.2.3     unknown           00:1a:70:36:c3:ea
The dhclient configuration file (dhcpcd.conf???) can be modified to report hostname to DHCP server.

Samba is the best way to share files between Windows and Linux - Setup *can* be a bit involved. [Here]("http://ubuntuforums.org/showthread.php?t=202605") is a good starting point.

---

### Post by howlingmadhowie on 2008-05-05
> **sofasurfer said:**
> I guess both. I want to share files and I want access to the other computer. I guess the correct answer at this point is that I want to do whatever you can help me with.

you sound a little confused as to how networking works. a computer can allow programs called services (or servers) to listen and react if another computer in the network wants something. consider for example http. a http process on a computer waits (usually on port 80) for a request to come in other the network. it then does something and sends a text file back. 

sometimes these servers make services available through which you can do a lot more. a telnet server of an ssh server on a unix machine will allow a request coming in over a network connection to control a shell on the server. 

in the same manner it is quite simple on computers with an x-server (as the name suggests) to send the graphical interface of a program over the network. 

just for your information :)

---

