---
title: "Linux Served"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by troymius on 2011-02-20
Please excuse my question if it is too amateur.

I work for a large company and do a lot of CAE work. We use Windows desktops and a  high performance computing (HPC) Linux cluster. Recently our IT folks installed an application (RGS?) that allows us to remotely connect to the Linux system and see a Linux desktop in a window on our XP machines. I love it because I can do a lot of work in that Linux window while the rest of my XP machine is occasionally consumed by its internal psychological issues.

Another thing I like about it is that no matter where I connect from, I get the same environment, files, settings etc. The connection is reasonably fast and one can trade the interface image quality for speed. I really hope this is the future of all corporate desktops ;-)

Now at home I have 3 computers, they all have dual boots (Ubuntu/Win). Even if I do a NFS, Ubuntu One or stuff like that, I still struggle to keep track of what file is where, what update needs to be done to what machine, why wifi stopped working here and why the system there won't shut down after my 2-year old son pounded on the keyboard for 10 minutes.

**So it came to my mind that what I would really like most for home is have somebody run a remote server with my (virtual or real) Linux system and let me connect to it (via browser, RGS, remote desktop, or whatever) from whatever system I am sitting at. I would be willing to pay $20 or so per month and would not need to worry about backups, updates, etc. I would not even need a fast PC. And when I buy a new PC, I would not have to install or configure anything except for a tiny client. **

So my question is: **is there such service available?** If not, why? Is it that the internet connections are not usually fast enough for a full desktop to be served? I am thinking that is the main reason. Or is there not enough demand for such thing?

I know there are project that dance around such setup (Jolicloud, Ulteo) but they do not seem to be exactly what I am looking for (but again, I don't know enough about them). 

Any thoughts? (I would call it LaaS - Linux as a Service :) )

---

### Post by jerenept on 2011-02-20
```
ssh -x
```

Is this what you're looking for?
There is also VNC.

---

### Post by troymius on 2011-02-20
Hi jerenept. No that was not my question. My question is: is there a company that runs a whole bunch of linux machines that I could connect to (for a fee) and have linux desktop served (via VPN, ssh, RGS... ) rather than running it on my home comp?

---

### Post by Ocxic on 2011-02-20
you can get a VPS (Virtual Private Server) but I'm unsure about a GUI

---

### Post by jerenept on 2011-02-20
> **Ocxic said:**
> you can get a VPS (Virtual Private Server) but I'm unsure about a GUI

I suppose if you installed an X Server and OpenSSH server..... Come to think of it, this is a pretty great way to test-drive Linux! use puTTY to connect to a linux server!

---

### Post by troymius on 2011-02-20
VPS... yes, for example the web hosting service I am using is a virtual server I can connect to but I can not start xserver there of course. There is no need for it on a web hosting server. 

What I am looking for is a "desktop hosting" :) A server where I can run X and send it my way. So I figure there is no such service commonly available.

---

### Post by troymius on 2011-02-20
These guys mention "remote desktop" on a VPS: [http://www.jspzone.net/vps.htm](http://www.jspzone.net/vps.htm) 

So maybe it is not unusual after all? Does anybody have an experience whether the remote access is typically fast enough to write code, surf web (no  video) etc?

Plus, if I used ssh -x would it be secure enough to do on-line banking and such?

---

### Post by troymius on 2011-02-21
Nobody talks to me :cry:

---

### Post by IWantFroyo on 2011-02-21
Just a warning: you might not want to try VNC, because it automatically opens ports and a hacker will eventually find it. 
Good luck, and sorry I can't help you more!

---

### Post by aeiah on 2011-02-21
whilst this is possible, you may find that your internet connection will make the experience very frustrating. 

you'll probably find it better if you create a server at home. you could just buy a NAS and have it serve an NFS share with your files on it, or you could turn a more powerful machine into a full desktop, and connect to it with vnc or freenx like you want to. since it'll be on your internal network, things will be a lot quicker (and cheaper).

in the corporate environment, some businesses have a large terminal server and connect employees to it with thin clients. these tend to be small machines who's sole purpose in life is to connect to the network, and launch VNC or windows remote desktop. thin clients tend to be pretty cheap so if it suits you, you could turn one of your computers into a server and buy a thin client to replace it.


i know you wanted something that doesnt involve much work, but a private server (virtual or otherwise) will probable involve a lot of money, and a lot of configuration. i dont think there's a market for the sort of thing you want because its both expensive and, due to average internet speed, mostly quite slow.

---

### Post by troymius on 2011-02-21
Thanks aeiah and *froyo. I wonder if the setup we have at work now will ever become common among public. I guess time will tell. Thanks again very much.

---

