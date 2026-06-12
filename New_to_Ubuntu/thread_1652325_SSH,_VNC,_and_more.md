---
title: "SSH, VNC, and more"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2010-12-24
Hey everyone, I'm working on my computers' setups to accomplish a few things:

1. Be able to connect to my computers at home in a pinch
2. Remotely control my computers securely.


Here's what I'm working with: 
1. Desktop with SSH installed (ubuntu)
2. Laptop (ubuntu)
3. Computers where ever (library, work, etc.) with XP or 7

My first issues:
1. In order to SSH into my desktop, I have to have already logged into my computer and locked the screen or what not. Is there a way to start my openssh server before I log in? For example, I want someone at my house to turn on my desktop without logging in, which would allow me to SSH into my desktop.
2. Since I've already got the SSH server up and running on my desktop, what is the most efficient and secure way to remotely control it with a GUI? Is tunneling VNC over SSH the best way or is that too slow?

Thanks :)

---

### Post by spiky001 on 2010-12-24
Hi I set my pc to login automatically so all I do is turn it on I can then ssh in also vnc, also if your bios allows you could set it up to wake on lan so you dont even have to turn it on

---

### Post by Lazy-buntu on 2010-12-24
I'd prefer not to have my computer login automatically, and I'm not too concerned about wake on LAN. Also, whether my computer is logged in or not doesn't fix the problem of having to click "allow" when I try to VNC connect to the computer.

Is there a way to add the SSH server to the startup to resolve the 1st issue? Edit: actually, I think it's Network Manager that isn't starting before I log in.

Edit 2: I'm a noob, there's a check box to fix the VNC issue.

---

### Post by spiky001 on 2010-12-24
Ok found this about starting ssh [http://ubuntuforums.org/showthread.php?t=1505653](http://ubuntuforums.org/showthread.php?t=1505653)
On the 2nd item if you open remote desktop there is an option to allow view desktop and control desktop make sure both are ticked, in the security section tick configure network to accept connections hope all this helps

---

### Post by Lazy-buntu on 2010-12-24
Found a solution: [http://forums.fedoraforum.org/archive/index.php/t-251584.html](http://forums.fedoraforum.org/archive/index.php/t-251584.html)

Simply check "available to all users" in Network Manager. It's simpler than the other approaches.

So now, what's a safe and efficient way to access my computers from outside of my LAN (assuming I want a GUI)?

---

### Post by spiky001 on 2010-12-24
You could tunnel vnc via ssh dont know how secure that is a good password of course, there is freenx not got mine setup yet.

---

### Post by Lazy-buntu on 2010-12-24
SSH should be fine from outside of my LAN, because I can pretty much run any program I know the name of.

The only thing I need to know now is how to mount drives through the terminal.

For example, if I SSH into either computer, none of my partitions are mounted by default (automatically). Therefore, if I SFTP into my computers, the MEDIA folder does not include the partitions I want to access. Any ideas as to how I would do that?

---

### Post by |Eric| on 2010-12-24
actualy using VNC is redundant (somewhat) 
remember linux is a multi user system 

one thing you can do from windows is this: 
get Xming ( a free X host to run from a usb key under windows) 

then get putty 
 start Xming then login into your remote machine with putty ( with the X tunneling enabled 

then start whatever apps you want to run on your machine . ( you should disable the auto matic login so you can spawn multiple X sessions ( each with its own user prompt

if you dont want to go tru all that assel install vnc server on your machine at home and run the client from where-ever note that vnc dosent ask for diffrent logins so you will be running on the session that is opened like RDP . 

you may also use dyn-dns or no-ip services ... makes life easyer .

---

### Post by |Eric| on 2010-12-24
you can add your partitions to mount in fstab and they should be mounted 
when you login remotely you may need to specify witch user has access to it  ( if you dont have access to the partition it will show as empty in most file-manager

you can also add mount commands to your .bashrc

---

### Post by spiky001 on 2010-12-24
```
sudo mount /dev/sdb? media
```unmount```
sudo umount /dev/sdb? media
```

---

### Post by sandyd on 2010-12-24
> **Lazy-buntu said:**
> Found a solution: [http://forums.fedoraforum.org/archive/index.php/t-251584.html](http://forums.fedoraforum.org/archive/index.php/t-251584.html)

Simply check "available to all users" in Network Manager. It's simpler than the other approaches.

So now, what's a safe and efficient way to access my computers from outside of my LAN (assuming I want a GUI)?
vpn into the network. then you can vnc into any computer you like.

---

