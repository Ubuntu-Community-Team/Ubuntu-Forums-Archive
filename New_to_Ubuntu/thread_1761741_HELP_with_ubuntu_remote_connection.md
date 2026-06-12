---
title: "HELP with ubuntu remote connection"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by hookitup on 2011-05-18
So i have read a few threads in regards to this topic but i cant seem to get a clean cut explanation on what to do. i am trying to remote into my ubuntu 11.04 machine form my Windoes 7 laptop , **_not on the same network._**  i want to be able to go places and bring my laptop but work on my ubuntu box. 

a step by step explanation would be great, with some links as to where i can download stuff if neede , i dont know much about VNC or SSH or whatever else there is out there but im willing to learn. i know Teamviewer sucks so i dont want to go that rout.  

Please help
Thanks in advance

---

### Post by hookitup on 2011-05-20
No help :confused: ,..

. would this be something to use on the windows side ? [http://en.softonic.com/s/vnc-viewer-windows-7](http://en.softonic.com/s/vnc-viewer-windows-7)


and then like in the software centre use the _x11VNCserver_ or the _ssl/ssh vnc viewer_ for my ubuntu machine


which one will be compatible if both then which do you think i should use and how do i set it up in rearguards to the information in the picture

---or any other better suggestions on how to achieve remote desktop not on same network---

Please help 
Thanks

---

### Post by jemofthewest on 2011-05-20
I use ssh to get access to my Ubuntu server when I'm away.  It won't  give you remote desktop functionality per se, it only gives you the  command line, but that should be enough depending on what you want to  do.  The two things you need to get SSH to work is to allow it through  your firewall and forward the port from your router.  The first site  below is a tutorial on setting up iptables, and I believe the example  firewall given allows port 22 to be open (the port SSH works on).  The  second website is a general website used to look up your router and find  out how to forward ports if you don't already.

[http://ubuntuforums.org/showthread.php?t=281539](http://ubuntuforums.org/showthread.php?t=281539)
[http://portforward.com/](http://portforward.com/)

Then, you gotta find your external IP address with the following website:

[http://www.whatsmyip.org/](http://www.whatsmyip.org/)

Finally, just type ssh [email]username@ext.ern.al.ip[/email] into a shell or putty if  you're using windows and voila.  You can make it easier on yourself by  looking up setting up a hostname with dyndns ([http://www.dyndns.com/](http://www.dyndns.com/))  and if I remember correctly during the process of that it'll set up  dynamic dns automatically... otherwise look that up in the community  documentation.  See the following link:

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

Luckily, thats free of charge :-)

Best of luck!

---

### Post by crispy_420 on 2011-05-21
Dynamic DNS service as mentioned.

Remote desktop: [NX Server]("http://www.nomachine.com/select-package.php?os=linux&id=1")

---

### Post by hookitup on 2011-05-24
thanks but i was looking for something not based in the terminal, im still a nubbie i don't have any server software, its just ubuntu 11.04 and windows 7 laptop, id like to be able to view the desktop and so on so forth . ...any easy yet reliable means of doing this ?

---

