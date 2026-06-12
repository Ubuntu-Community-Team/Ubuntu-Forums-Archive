---
title: "Connect to Desktop (mythtv) from anywhere?"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by JBot on 2007-10-27
Good afternoon ubuntu community...

I have been running ubuntu for a while, always content with just having a basic home computer set up. However, recently i picked up a laptop, and have more or less converted my desktop into a media server.
This option works great when i am at home connected to the same network with my laptop and desktop. However, when i go to school, i am wanting to procrastinate but i dont have all the tools (ie. my movies on my desktop at home) to do so.
Also, i recently set up Mythtv backend on my desktop, and have the frontend client on my laptop, which again works great when i am at home, but i am wondering if i can connect to that via a different network. More importantly, i am wondering if there is a way i can watch tv from anywhere. (sometimes im stuck at school and a hockey games on or something...)

I am running a macbook, (dont criticize, it looks good!....), but i dont think thatll make a difference.

 If anyone knows of a good tutorial that will help me set up my home machine to be accessable from anywhere, that would be perfect. 

THANK YOU!!
and please, dont reply "search the forums before posting" and not provide a link. I have searched, and havent been able to find this help. 

:guitar:

---

### Post by JBot on 2007-10-27
forget to mention. i am running 7.10

---

### Post by kebes on 2007-10-27
You can use SSH to log into your media server remotely, and use it to "port forward" the port needed for MythTV frontend/backend connection. I can give you details on this, but the problem is that the Internet is too slow to send the amount of data fast enough. The video quality will be very bad.

Similarly you can use VNC to log into the desktop of a remote machine, but it will be too slow for video applications.

I think the only solution would be to use SSH or SFTP to copy the file you want from the remote server to your laptop (wherever you happen to be), and then play the file locally (using mplayer or VLC, or whatever you prefer). If you want to get more complicated, you could set up scripts on your MythTV that automatically exports a compressed version of the video, so that the file sizes are smaller for the transfer. (I believe MythTV supports auto-encoding of content, actually...)


Hope that helps.

---

### Post by JBot on 2007-10-27
i was thinking of logging onto my desktop via ssh and just change the path on the frontend to read from that dir., but than that wouldnt solve the problem of watching tv.
I have vnc set up to watch movies, but i like having the interface of mythtv, and i havent really enjoyed streaming through vnc since you have to set up a network stream every time you want to watch videos. The only way i know how to do this remotely is connecting through a rdc/vlc and set it up that way. not very efficient. 

So let me rephrase my main question:
Is there a way to connect to my backend server to watch tv from anywhere?

thank you kebes for your help. Do you think you could provide your details on using ssh to log in remotely?

---

### Post by kebes on 2007-10-27
To do it via SSH, you just need to know the port that your MythTV backend runs on (whatever port number you're using to get your frontend on the laptop to connect to the backend on the media server). I think the default is 6543.

Then you login via SSH into the media server (so obviously you need the media server to be running an SSH server/daemon, like OpenSSH; and you need port 22 unblocked on your firewall and router):
```
ssh user@xxx.xxx.xxx.xxx -L 6543:localhost:6543
```
Where "user" is your username on the media server, and "xxx.xxx.xxx.xxx" is the IP address of the media server. The -L switch links a port on your local machine to a port on the remote machine. So it will be as if the two computers are on the same LAN.

This, in principle, will allow full MythTV interaction (watching recordings and streaming live TV), but as I said it's probably going to be too slow and choppy.


It looks like this add-on does what you want:
[http://www.mythtv.org/wiki/index.php/MythStreamTV](http://www.mythtv.org/wiki/index.php/MythStreamTV)

I've never used it, but it claims to compress the MythTV stream so that you can access it from the MythWeb interface. Worth a try.

---

