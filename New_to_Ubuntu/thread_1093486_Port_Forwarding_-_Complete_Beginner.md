---
title: "Port Forwarding - Complete Beginner"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by SumthingWicked5 on 2009-03-11
I used to use uTorrent when I ran XP. However, my friend got me hooked on Ubuntu for the security, and customization options. However, now that I'm here, I don't know how to do much! I'm trying to download stuff with Transmission, and it all works fine, just very slow. I check my port, and it says that the port is closed. With XP, it was pretty simple, I just did normal XP things to set my static IP and opened a port on my router, and I was fine. However, here, when I look up how to set a Static IP and stuff, I get intimidated. I was hoping someone could give me (and or send me to) an ABSOLUTE beginners guide to getting a port opened up for me. 

(I've never even used my text-editor, and I don't really know how to use the Terminal yet, so when I say Absolute beginner, I mean it)

---

### Post by Kareeser on 2009-03-11
Traditionally, setting a static IP should be done on the router level, not at the end-user system level.

If you have access to the web interface of your router, you can set port forwarding options there, and set a static ip for your Ubuntu box as well.

---

### Post by BDNiner on 2009-03-11
What application are you using to set your IP address. The default tool in ubuntu can be used to set a static ip address. I believe it is called gnome-network-manager and it is on the 3rd tab. If i remember correctly

---

### Post by kanikilu on 2009-03-11
I read there were some issues with setting a static IP in network-manager when Intrepid first came out, but I don't know if those have been fixed or not. You can try though, go to System > Preferences > Network Configuration and edit your wired ethernet connection to use a static IP.

As suggested earlier, if your router supports it, it might just be easier to assign that computer a static IP based on MAC address.

---

### Post by lovinglinux on 2009-03-11
> **kanikilu said:**
> I read there were some issues with setting a static IP in network-manager when Intrepid first came out, but I don't know if those have been fixed or not. You can try though, go to System > Preferences > Network Configuration and edit your wired ethernet connection to use a static IP.

It works. I have a notebook with Intrepid and the static IP was configured using the Network tool.

> **SumthingWicked5 said:**
> I'm trying to download stuff with Transmission...


I would recommend Deluge. Is better than uTorrent in my opinion, it's easy to configure, has all important features and a nice interface. Since you are not familiar using commands in terminal, I suggest you get the deb file from [http://www.getdeb.net/app/Deluge](http://www.getdeb.net/app/Deluge)

To install deb files is pretty easy. Just double click on it like you used to do with Windows executables.

EDIT: Deluge has UPnP support. Which means that if you enable this feature on your router, the port will be opened automatically. A lot of people will recommend not doing this for security reasons, but is up to you. If you do, would be nice to use a Firewall manager like UFW and [GUFW]("http://www.getdeb.net/app/Deluge") (GUFW is the graphical interface for UFW), which has a simple configuration for torrent ports.

---

### Post by SumthingWicked5 on 2009-03-11
Thank you guys so much for the help! I'm still having trouble though. I'm in my Network Connections, and I clicked edit on my wired network, but I can't find any option that has anything to do with a static IP to my understanding. Can you be a little more specific? Maybe I just don't know enough about it to be able to recognize it.

---

### Post by SumthingWicked5 on 2009-03-11
Nevermind! I got it all figured out! And thank you so much for the help. It's awesome to get a good trusted place for tips and stuff. You guys are awesome. 

And thanks for Deluge, LovingLinux. I like it a lot better!

---

### Post by lovinglinux on 2009-03-11
> **SumthingWicked5 said:**
> Nevermind! I got it all figured out! And thank you so much for the help. It's awesome to get a good trusted place for tips and stuff. You guys are awesome. 

And thanks for Deluge, LovingLinux. I like it a lot better!

You are welcome. Happy torrenting.

---

### Post by mkvnmtr on 2009-03-11
A tip on Deluge. My static address was set on the router. You would use the same method as in Windows or Mac. Google Port Fowarding and find how to log into your router. As far as opening ports on Ubuntu I don't. I click the option to use a random ports. I get my top speed allowed by my ISP in this manner. I also up the number of half open connections to about 50. It is only public torrents that are slow. If I am downloading a linux distro it will almost always be ant my top speed.

---

