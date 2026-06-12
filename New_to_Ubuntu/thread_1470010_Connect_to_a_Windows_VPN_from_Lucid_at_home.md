---
title: "Connect to a Windows VPN from Lucid at home"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by drillerccg on 2010-05-02
Trying to help my sister migrate from Windows to Ubuntu. We are both novices at this. She has everything she needs with Ubuntu but does need a connection to her office (doctor's office using windows) that has a VPN setup. I have no idea how to help her. The searches I have done, do not cover the very basics (what we need, what settings, etc). Is there a How To for this or can you help me please?

We have located the Remote Desktop Viewer and Terminal Server Client but we don't know how to use them. She has given me an IP and a password, that's all. Do I need more info from her work? TIA

---

### Post by gordintoronto on 2010-05-02
Here's some information:
[https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN)

Go to the section for the version of Ubuntu you are using. When they say "install such-and-such" you can use Administration/Synaptic to install it.

A VPN provides access to files. It's like having a file server which is far away instead of being in the next room. Remote Desktop and Terminal Server have nothing to do with VPN. You need an IP address and a password to set up a VPN client.

---

### Post by drillerccg on 2010-05-02
Thank you for the help. It appears that Lucid has the Microsoft VPN kind installed already. Is the Gateway the same thing as the IP you had mentioned? I now need the correct passwor to connect. My sister seems clueless about the exact user names` and passwords.

Also, I now understand that the VPN is a more secure connection. But what would the Remote Desktop Viewer and Terminal Server Client be used for?

---

### Post by alphacrucis2 on 2010-05-02
> **drillerccg said:**
> Thank you for the help. It appears that Lucid has the Microsoft VPN kind installed already. Is the Gateway the same thing as the IP you had mentioned? I now need the correct passwor to connect. My sister seems clueless about the exact user names` and passwords.

Also, I now understand that the VPN is a more secure connection. But what would the Remote Desktop Viewer and Terminal Server Client be used for?

They allow console (GUI) access to a remote machine. IIRC Remote Desktop Viewer is part of VNC which allows remote control of a Windows machine and seeing what the local operator is doing. Useful for tech support. Terminal Server client is similar but runs a console under a different session to the one logged in locally.

---

### Post by drillerccg on 2010-05-02
Thank you for your response. So if I get my sisters use rname and password with an IP address I can connect to her VPN, correct? Once I am connected to her Windows VPN, can I run programs and access files on her machine at work? Is that done by connecting to the VPN or once connected I have to run another program to see her desktop? TIA

---

### Post by Tank Jr on 2010-05-03
When you connect to the VPN server it will authorize you to access the network it is part of. Then you can use stuff like remote desktop or ssh to connect to machines that are part of that network.
Think in this way: the VPN access is like getting into a building, you use your key to unlock the door and gain access to the building. Once inside  you can go to any room you want, but you still need to have the keys for that room.

---

### Post by drillerccg on 2010-05-03
> **Tank Jr said:**
> When you connect to the VPN server it will authorize you to access the network it is part of. Then you can use stuff like remote desktop or ssh to connect to machines that are part of that network.
Think in this way: the VPN access is like getting into a building, you use your key to unlock the door and gain access to the building. Once inside  you can go to any room you want, but you still need to have the keys for that room.

Thank you for your response. Lets assume I am able to establish a VPN connection by clicking the connection menu in the upper panel of Ubuntu (have not been able to yet but am hoping it's due to not knowing the correct user name). What next?

 My sister likes to run her Windows programs from home on her new Ubuntu machine. I'm guessing, once I make a VPN connection, I should use Remote Desktop Viewer to access and operate her computer at work?

Can I also use the Terminal Server Client? Which is better/ more secure or does it make a difference in VPN?

TIA

---

### Post by drillerccg on 2010-05-03
any help?

---

### Post by itisachilles on 2010-05-04
go to your sisters work (or have her do it) and install a VNC client i recommend tight VNC but its really up to you from there you can set whatever pass word and settings you want (like the remote desktop settings on ubuntu) this will allow you to access her machine remotely at your home machine open "remote desktop viewer" and hit connect in the upper left hand corner change the protocol setting from SSH to VNC and type in your sister's IP as "host" then make sure that the "view only" box is unchecked then hit connect then it will either ask you for the password you set or just go straight to her screen and then pat your self on the back for you have complete access to every thing you can do with a mouse and a keyboard.just so you know that does not rely on VPN as far as my experience leads me to believe and if you really want to share files go to [www.dopbox.com](www.dopbox.com) and follow the instructions you find there. 
hoped it helped.
achilles.

---

### Post by drillerccg on 2010-05-04
> **itisachilles said:**
> go to your sisters work (or have her do it) and install a VNC client i recommend tight VNC but its really up to you from there you can set whatever pass word and settings you want (like the remote desktop settings on ubuntu) this will allow you to access her machine remotely at your home machine open "remote desktop viewer" and hit connect in the upper left hand corner change the protocol setting from SSH to VNC and type in your sister's IP as "host" then make sure that the "view only" box is unchecked then hit connect then it will either ask you for the password you set or just go straight to her screen and then pat your self on the back for you have complete access to every thing you can do with a mouse and a keyboard.just so you know that does not rely on VPN as far as my experience leads me to believe and if you really want to share files go to [www.dopbox.com]("http://www.dopbox.com") and follow the instructions you find there. 
hoped it helped.
achilles.

Thank you for your response. I think she has something like that already setup. She is able to access her VPN from home and access/read/write with her Windows XP and Vista machine. I'm just wondering what I need on an Ubuntu machine to accomplish the same for her? Any help would be appreciated.

She says that she has an icon on her desktop that the IT person placed and all she does is click on it and she is in her work's computer at home.

---

### Post by itisachilles on 2010-05-04
hmmmm well without actually being there to help i no very little about this icon of yours but sounds very close to what i describe in th other post and i would advise right-clicking selecting "properties" and reading what you find there very thoroughly  before proceeding beacause i have herd of some IT speacilists installing some non-free software that basicly only work with proprietary Vnc clients. if so your screwed.
sorry to be the bringer of bad news:(
achilles.

---

### Post by drillerccg on 2010-05-04
Problem solved. It appears that they had a site to site VPN set up (whatever that means) and I could not connect remotely to their VPN. On top of it, my sister had given me the wrong IP address. She'd given me the router's IP address instead of the VPN's IP address. Their IT person help me set it up.

All I had to do was to fire up  Applications/Internet/Terminal Server Client, under the general tab put the IP address where it said computer, used RDP protocol since it was XP ( I guess you have to use the RDPv5 for Vista and 7), fill in the username and password and click connect. I was right on her desk top. I left everything else as it was and did not change anything.

The Remote Desktop Viewer did not work at all and closed the connection. All this was possible because her work machine actually had this function enabled. Thanks for everyone that helped.

---

