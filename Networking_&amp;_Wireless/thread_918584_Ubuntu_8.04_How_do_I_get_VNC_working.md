---
title: "Ubuntu 8.04 How do I get VNC working?"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by syborfical on 2008-09-13
With out posting a really angry thread.... 

I would like it if someone could help me or steer in the right direction. 

I want to set up VNC for unbuntu 8.04.. although I have been calling it another name of late ... :P

I want VNC setup So I don’t have to ssh into my Linux box. Its on a local network. if was that paranoid id be running Free BSD or Solaris. 

I use my linux box to down load torrents. 
I want to unhook the monitor and just have NIC and power cord plugged in.

I want be able to type in name of my linux box get to the desktop and start and stop torrents. I have spent 4 hours and the best result I have so far is a grey screen with a cursor. 

I can get VNC working flawlessly in 7.10. I reinstalled 7.10 just to make sure it wasn’t the machine or anything, within 12 minutes VNC was running how I wanted it.

I have followed numerous guides how to get VNC working guides each time I get a nice grey screen. Which doesn’t really help. 

I am 1 inch away from installing windows, at least VNC will work how I want it.

Could someone please help me? 
Thank you for reading

---

### Post by the_de5olate_0ne on 2008-09-13
If you're seeing a blank screen, then vncviewer isn't connecting to the target machine or the request isn't being acknowledged or granted. Check the settings for Remote Desktop on the target machine. Go to Settings -> Remote Desktop. Be sure to check the proper boxes to enable Remote Desktop. You want 'Allow other users to view your desktop' 'Allow other users to control your desktop' and nothing else checked. Then try running vncviewer again to connect.

---

### Post by superprash2003 on 2008-09-13
i believe vnc doesnt work when monitor isnt plugged in

---

### Post by syborfical on 2008-09-19
Yes you can un Ubuntu with out any monitor.

I have been doing it on a 7.10 box since it came out 
VNC works on 7.10 and i dont need to SHH or any of thise other ********.

Does anyone out there have a clue / know how to get VNC working so when i turn the power on. X loads and Vnc is loaded i just type the IP and and i can access my machine???

---

### Post by phreon on 2008-09-28
Hi,
Check out Vector Linux forum ...

[http://forum.vectorlinux.com/index.php?topic=7340.0](http://forum.vectorlinux.com/index.php?topic=7340.0)

I just went through this in VL and there could be some ideas here.

---

