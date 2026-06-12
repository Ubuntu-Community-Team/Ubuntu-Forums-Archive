---
title: "X2go over ssh - Power Off"
date: 2020-11-08
forum: Networking &amp; Wireless
---

### Post by Quarkrad on 2020-11-08
Using a kvm virtual 20.04 machine and my 20.04 host (both ubuntu mate) I've set up a x2go connection including ssh keys.  All appears well - I can do everything I've attempted so far in terms of making changes on the remote (kvm) machine.  However, I cannot power down the remote, either using the gui or initiating terminal commands on the remote desktop via the x2go window.  The only way I can shut down the remote machine is to close the x2go session, and via a **shh username@ip address** command in my host terminal initiate a **sudo poweroff **command.  This is the first time I have set  up ssh, x2go (and kvm) so I'm an absolute newbie - is this the method of closing down the remote machine or should I be able to do it via the x2go window session on my host?  (My scenario is setting up a remote connection to friends/neighbours machines to do some work - hence when I've finished I want to power down the remote.  Unlike a remote server where you would leave it running).

---

### Post by TheFu on 2020-11-08
I've never tried shutting down a VM over x2go.  Hang on a minute.

I
[LIST=1]
[*]used x2go to connect to a 20.04 VM (also KVM) running fvwm.
[*]Open a terminal, I'm an xterm guy.
[*]sudo shutdown now
[*]Then close the x2go session (upper left corner, close) and 
[*]open a terminal on the KVM host machine and run **virsh list**. The machine I told to shutdown had. It didn't tell x2go to close any windows, but it was definitely off.
[/LIST]
If I didn't use **sudo shutdown now** and just used **sudo shutdown**, there is a 1 minute delay before the OS shuts down. This is part of the shutdown command.

Are you seeing something different?

BTW, if you are on the same LAN with the KVM hostOS, I'd really encourage you to check out SPICE.  As great as x2go is, spice feels 10x faster, but it isn't secure enough for internet connections without a full VPN, IMHO. I've posted my spice connection script in these forums a few times the last 2+ months. For over the internet, GUI connections, x2go is still the best tool that I've found.

---

### Post by Quarkrad on 2020-11-08
Thank you for your response. Strangely it is all working now and the remote is switching off so I'm seeing the same as you.   Although I have all the VMs on the same machine/LAN for this test,  I will be connecting to friends/neighbours over the internet so I will take your advice and go with x2go.  I'm considering ditching my Virtualbox testing environment as x2go is a lot faster; so now looking forward to your your suggestion of using Spice for my internal VMs and x2go for external remote connections.  My last issue is connecting to a windows 10 VM from my 20.04 host environment - I'll keep trying.  Appreciate your help here and in other peoples posts.

---

### Post by TheFu on 2020-11-08
Win10 in a kvm/VM can use spice. Just install the qxl video driver into Windows and choose that driver in the VM settings along with spice. Redhat makes the driver, last time I checked.

---

