---
title: "Gnome-RDP - Windows server 2003"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by simulated1 on 2007-07-04
Hello i have a bit of an annoying problem. 

Ive just installed Ubuntu on my laptop after testing it out on a virtual machine. Im mainly a windows person as my job role depends upon it so in short, a newbie to linux. 

Ive basically got a network with Server 2003 running which is logged in 24/7, 2 xp machines and my laptop with ubuntu installed. Since my server is the network slave providing streaming media services to xbox media center as well a domain controller, i need to remote in to it frequently. Before i decided to use linux i used MSTS client to connect to it. Ive just found Gnome rdp, and downloaded it and installed. The idea was i could remote in to all my boxes on my laptop from the comfort of my front room sofa ;) . So to bring this epic explanation to a point, every time i connect to my 2k3 server it creates a separate log in session under the same user account. This is a problem since i have apps running on the server that i need to use. When another session is created under the same account, the apps load a second time and then obviously moan that its ports are already in use. 

This doest happen when im using xp's ts client, i just log in as normal under the same single session. 

I tried krdc and TSC and got the same thing. Ive been through the options but there is nothing there relating to sessions. Could somebody explain to me why this is happening and whether or not its something i need to configure on my server ( still learing 2k3 at the minute ) or if ive missed a setting somewhere. 

Thanks :)

---

### Post by Synflux on 2007-07-06
When you used the Windows RDP client were you connecting to the console of the server? This can be done by adding /console onto the mstsc command line.

Otherwise, there's a config option in 2k3 that allows/disallows multiple logins from the same user. Check in Terminal Services config-> Server settings-> Restrict each user to one session.

This can also be set by group policy though so if you might have to check those as well.

I haven't actually used gnome-rdp so couldn't help you with the exact settings for that. The standard terminal services client that comes with Ubuntu has an option under 'performance' to connect to the console

Hope that helps you,

---

### Post by pisuke on 2007-10-10
In tsclient (Terminal Server Client) gui, go to preferences tab.

There you will find the option: Attach to console

Check it and when connected it will open existing session.

Don't know how to do it with krdc, someone?

---

### Post by photonearth on 2007-10-11
Gnome-RDP is just a frontend for rdesktop, you can specify -0 to connect to the console (man rdesktop). 

Since there is no place to specify this in Gnome-RDP, a dirty trick is to append " -0" after the hostname in the Computer field.

---

