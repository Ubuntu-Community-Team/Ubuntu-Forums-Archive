---
title: "Moving Files off Blacked-Out Desktop in Jaunty"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Enicko on 2009-04-28
My beloved laptop Jackalope1 is down. I run Jaunty 64 on a w500 thinkpad. I have an external monitor that I run VirtualBox on and leave the laptop monitor on Ubuntu.  I'm still on ext3 for what it's worth.

After a long day of working in VirtualBox, I noticed the window controls (minimize / maximize, close) were gone from my windows in ubuntu.  I had just finished a sales flyer for tomorrow and moved it to the ubuntu side - without saving a copy to the network or emailing it to where it needed to go - (insert self defeating term here). 

Jaunty has been pretty stable lately, other than the ATI issues, so I didn't think anything of it.  I ran an update, closed Vbox, and restarted.  Oh snap.  Black screen.

Here is what I have:  Login / start up is fine.  Ubuntu start screen with username / password is normal. After that, everything but the mouse is black.

Oddly enough, Gkrellm is running although in a different font.

Now, I could wait it out until tomorrow for the rest of the machine to work, praying that my linux support guy at work is back from a personal emergency - which also sucks - but I need that flyer off the desktop pronto or my az will have bigger problems.

I am able to select the options menu at the start up screen and go into the terminal, which positions itself at the lower right hand side of the screen.  Unfortunately I know little about working in terminal, other than "apt-get" and "top".

So, while I obviously have bigger issues, does anyone know how to get at files on the desktop, when you can't see the desktop?  If I could move it to a USB drive I'd be in business...:confused:

---

### Post by llamabr on 2009-04-28
```
cd Desktop
ls
```

Notice that Deskstop starts with a capital D

---

### Post by ibuclaw on 2009-04-28
ssh is your friend :D

Can you boot into "**recovery mode**" on your desktop and go into "**Root with Networking**" and connect to your network (ethernet connect would be the key to this)?

If so, install the ssh server:
```
sudo apt-get install openssh-server
```
Then type in
```
ifconfig | grep "inet "
```
To show the IP address of your desktop. ie:
> 
          inet addr:169.254.5.127  Bcast:169.254.255.255  Mask:255.255.0.0
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet addr:**192.168.1.10**  Bcast:192.168.1.255  Mask:255.255.255.0


Then switch to your laptop, and open a nautilus. Click **File->Connect to Server**, and enter in the following information:

Server: **192.168.1.10**
Port: 22
Folder: /home
Username: **your_name**

Replace the "Server" IP with the IP of the desktop, and the "Username" with your account name on the desktop computer.

Click **Connect**, then you will be prompted to enter in the user's password.

Upon successful authentication, nautilus will show a new mounted drive, showing your /home folder on your Desktop, to which you can safely copy over the files to your laptop.

Regards
Iain

---

### Post by Enicko on 2009-04-29
Got it, I can see the documents name and file type.  I have a USB drive inserted.  How do I move or copy the file to it?

 - I should clarify - I'm in the terminal via the cd Desktop / ls command from above.  The ssh was already installed, but I can't get another machine to find this one on the network.  Would have tried this last night but I needed to be back in the office on their network to get at it.

---

### Post by sim-value on 2009-04-29
with the cp command like

```
cp file /media/disk/file
```

To know the name of your USB stick execute
```
ls /media/
```

---

### Post by Enicko on 2009-04-29
I ran the ls /media/ - it only shows 
cdrom cdrom0

I pulled the usb out, same results, moved it to another port, same results. Restarted with the usb in the port, same results.

---

