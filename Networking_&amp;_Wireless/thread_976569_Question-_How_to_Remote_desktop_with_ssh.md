---
title: "Question- How to Remote desktop with ssh"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by oneadvent on 2008-11-09
I would like to know how to setup remote desktop if I already have access to ssh?

Anotherwards I didn't set that up and I regret it.

Other note, the remote computer is Intrepid and the Local is XP Pro, so I want to use RDP.

Thanks for help!

---

### Post by kerpow on 2008-11-09
So you are using Windows as a clinet machine to connect to a Ubuntu machine, and you want to see the applications from the Ubuntu machine as though they are running on the Windows machine all via SSH?

Sure you can do that:

There is a project for X on Windows, its called Xming.  You can hook it up with Putty to achive the above.

[http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)

---

### Post by kerpow on 2008-11-09
OR if you prefer to use somthing like VNC over SSH, Google for 'SSH port forwarding'.  :)

---

### Post by oneadvent on 2008-11-09
Okay, the first wont work, because really I need to access a program that is on the computer to do something inside my network at home.

I know I can use VNC but I want to set it up through RDP. That option is in Ubuntu by default, but turned off, so how do I turn it on by command line, and then how do I connect to it through ssh?

Thanks for the help.

---

### Post by kerpow on 2008-11-09
> **oneadvent said:**
> Okay, the first wont work, because really I need to access a program that is on the computer to do something inside my network at home.

Not sure I follow. Is there a firewall in the way, is that your issue?

---

### Post by oneadvent on 2008-11-09
Well I was trying to get into a winded reason, but what i am trying to do is access my linksys router, by RDPing to my desktop then opening a browser to its internal gateway.

That would allow me to see if my netcam is talking to the router, because right now I am not seeing it, and I am not sure if that is an outside or inside problem.

---

### Post by kerpow on 2008-11-09
Well if your Desktop machine is Ubuntu with SSH server working, my first method will work just fine.

SSH into your Ubuntu machine with Xming setup and running on your Windows machine.  Then run a webbrowser via the SSH session, and you will see it shown on the Windows machine.

If for some reason you need to use VNC, you can still do that as long as Remote Desktop is setup on your Ubuntu machine, and your SSH server is setup to allow port forwarding.  

All in all I think the first method is easiest (and more fun).

---

### Post by oneadvent on 2008-11-09
As an alternative to what I was doing , yes that works great. I just wish I could see the desktop too.

I installed it and configured it and did what I needed, thanks.

---

