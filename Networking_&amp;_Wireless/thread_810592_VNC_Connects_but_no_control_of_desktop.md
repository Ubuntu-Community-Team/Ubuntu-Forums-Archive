---
title: "VNC Connects but no control of desktop"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by RottenBananas on 2008-05-28
Hey guys,

I posted this in general help but no one knew, hoping this forum will

I've been messin around with vnc and ssh. Im goin from an ubuntu laptop to an ubuntu desktop.

I followed this guide:
[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

I can connect using the -via param in vncviewer. So all is good. I see my desktops screen and can access/run everything remotely.

I can also connect by forwarding X through ssh. CTRL+ALT+F1 to switch to console and then:
```
xinit -e ssh -XCT myuser@my.host gnome-session --:1
```

The connection part works...I see my desktop using either of the two methods.

The problem is that I cant control the desktop. If I open up firefox remotely it'll show up on my laptops screen but the desktop stays the same. If a user is on my desktop I cant see what they're doing. I've connected but I don't have control

I have 'Allow other users to control my desktop' checked through preferences>>remote desktop and the login window has 'same as local' for the remote tab but still no control

Any ideas?

---

### Post by RottenBananas on 2008-05-29
nobody knows??

---

### Post by dubois on 2008-05-29
What about VNC permissions on the PC you are connecting to, are they set to view only?

What OS is on the server PC? You might be able to find something that is blocking full access on the VNC server settings of the PC you are trying to remote into.

---

### Post by RottenBananas on 2008-05-30
Where do i change the vnc permissions on the server? its running ubuntu 8.04

Thanks for the reply

---

### Post by dubois on 2008-05-30
I'm not all that familiar with VNC going into a non Windows PC but one thing off the top of my head, is the account that you are using to remote in in the VNC users group on the target PC?

Also, here's another How To:

[https://help.ubuntu.com/community/VNC]("https://help.ubuntu.com/community/VNC")

---

### Post by RottenBananas on 2008-05-31
I checked users and groups on the server comp and there isnt even a vnc group listed. 

I think whats going on is that im not using vino. I have tightvnc, so I have to type vncserver :1 on the server comp first before it connects me.

When I try to connect with tightvnc off (using just vino) I get this error:```

 CConn:       connected to host localhost port 5599
channel 3: open failed: administratively prohibited: open failed
 main:        End of stream

```

it asks me for my password and after i hit enter that error shows up.
I googled it and found that tcpforwarding has to be set to yes in /etc/ssh/sshd_config...so i checked to see if it was, but i couldnt even find the command listed in the file. So i added it myself and restarted the server to try again but same error.

Any ideas?

---

### Post by bengoza on 2008-06-15
I followed that guide but I can't see my desktop. All I get is a grey window with a terminal prompt in it.

---

### Post by gavco98uk on 2009-08-01
first apologies for raising an old topic, but searching for help on this problem brings up this topic, and as I have just worked out how to solve it, I thought it worthwhile providing the answer for others with the same issue.

From the VNCclients document, troubleshooting section:
*If you connect to a VNC server, can see the initial desktop, can see the mouse moving around, but the rest of the screen doesn't update, then you probably need to disable desktop effects on the shared desktop. A [known bug]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126") means that desktop effects are currently incompatible with most VNC servers*

That solved it for me! Select System->Preferences->Appearance, Visual Effects tab, and disable effects, and you should now be able to control the desktop again.

Hope this helps someone!

---

### Post by djschwartz on 2009-08-01
That helped me - thanks for the tip!  I'll have to post in the thread I asked about the same issue in.

---

### Post by airjrdn on 2010-07-19
Worked for me in Linux Mint.  Stinks that I have to disable all effects, but at least I can remote in now.

---

### Post by Rope on 2010-07-24
Worked for me (all visual effects off) with ubuntu 9.10.
Shared desktop: ubuntu 9.10, 32 bit
Connnected with win7 64Bit Real VNC viewer

---

### Post by MobileTechGuy on 2010-10-04
I need to disable the visual effect in Ubuntu 10.04 LTS in order to use the Remote Desktop. Thanks for the tips. 

MobileTechGuy

---

### Post by aresrin on 2011-12-11
Thanks for the help! Disabling Visual Effects worked for me.
 
Viewing Ubuntu 10.04 LTS from Windows 7 64-bit using tightVNC

---

