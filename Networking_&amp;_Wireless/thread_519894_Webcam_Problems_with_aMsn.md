---
title: "Webcam Problems with aMsn"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by linuxmann on 2007-08-07
On amsn it says when i try to configure the webcam   Type "IP-Restrict-NAT
                                                                                                    Listening   false
                                                                                        You are firewalled or behind a router
-------------------------------------------------------------------------------------------------------------------------------
For one, i do not have a router and when i try to disable my firewall, the same thing happens. I have heard on the amsn wiki:

You are firewalled or behind a router

If you are unable to view a webcam in aMSN after a contact has send you an invite, or after you have issued the command to receive/send webcam, and you are behind a router, you may need to follow these steps:

If you receive: IP-Restrict-NAT and you receive false in webcam wizard, that means your connection is firewalled. (does not send the IP)

If this is the case, you will need to open some ports for the webcam to use because they are currently blocked.

To do this, open your router web-based configuration (check router manual for details on this). Once you have the web-based configuration open, browse for a setting called "port forwarding" or "port range forwarding" or something similar to that. (This might be found under the advanced features for your router).

Now that you have the port forwarding page open, you will want to set the port forwarding range so that aMSN will be able to accept and send the webcam stream.
Here's an example of how you will set up your port forwarding:

Application: aMSN
Start: 6890
End: 6900
Protocol: Both(TCP & UDP)
IP: xxx.xxx.x.xxx
Enabled: X (Yes/True)

Note: xxx.xxx.x.xxx is the IP of your machine that you are trying to send / receive webcam


If you have a web server open on your port 80, you can try to disable it too, sometimes it helps.
-------------------------------------------------------------------------------------------------------------------------------
Now what it says there does not make any sense. I tried calling the IP verizon and they blame it on linux. I was looking for "port forwarding" and also to try to open ports for the webcam to get out. Because i have heard the webcam needs some ports or something to send out the information or something. I tried going to the westell  modem page my IP had provided, and i saw nothing about opening ports or port forwarding or anything that can help me. Maybe i wasnt looking enough. I have a westell 6100 modem. This is very confusing and i hope some people can help me on this. I have 768k dsl from verizon. Feel free to ask any questions.

amsn says i have a flexcam 100 camera.

[http://www.amsn-project.net/forums/viewtopic.php?t=2954](http://www.amsn-project.net/forums/viewtopic.php?t=2954)

---

### Post by PudUK on 2007-10-31
I have exactly the same problem.

I've followed the port forwarding instructions on my router (Zyxel Prestige 660) to no avail.

I thought I was doing well persuading my wireless card to work...

---

