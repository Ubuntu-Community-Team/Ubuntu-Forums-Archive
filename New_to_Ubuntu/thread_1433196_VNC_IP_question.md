---
title: "VNC IP question"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by hman1169 on 2010-03-18
When I try to configure VNC / Remote Desktop Settings, I get the attached image. It says,

"Your desktop is only reachable over the local network. _Others can access your computer using the address 192.168.1.103 or hman-desktop.local_." and my question is a basic one.

How does someone enter the IP of my Linksys for someone not in my network to connect to me? What is the format?

I am guessing it is going to be something like this... ??://**24.###.33.##:hman-desktop.local**

More simply what does someone have to type into the connect window in remote desktop viewer to connect to my computer? Both of us are using Ubuntu...

Any input is greatly appreciated.

Thanks

Chris

---

### Post by gradinaruvasile on 2010-03-18
Only IP:port is required for VNC. 
The solution here is port forwarding - you have to tell your Linksys to open a port (higher than 30-40000 is recommended to avoid scanning as possible) - and that port will be forwarded to your computer's 5900 port (standard VNC). Complex password is mandatory if you want protection.

Note that this is highly unsecure because VNC is itself not a secure protocol and hackers know it!! Your computer basically will be reacheable from anywhere from the internet.

---

### Post by hman1169 on 2010-03-18
[gradinaruvasile]("http://ubuntuforums.org/member.php?u=589640") Thank you so much for your reply... I get it. It works the same way my old FTP did many moons ago... I just port forwarded from my linksys... I really needed the refresher... I suppose I could also DMZ Host it too right? if only for a few minutes...

I have a friend who is even newer to Ubuntu than I am... (installing it tomorrow) and he will definitely need some assistance just looking around at how much different from Windoze XP... I have to set up his email and import some old windows stuffs he needs...

Again, Thanks you for your quick reply!

---

### Post by Jeff Anthony on 2010-03-19
There is a simple way to secure the VNC connection using SSL. I'm not sure the specific instructions to do it in Ubuntu but I'm sure we have the technology!

---

