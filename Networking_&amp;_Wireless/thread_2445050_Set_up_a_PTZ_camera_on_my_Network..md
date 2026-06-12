---
title: "Set up a PTZ camera on my Network."
date: 2020-06-08
forum: Networking &amp; Wireless
---

### Post by irv on 2020-06-08
I hope this is the place to ask this question? I purchased a PTZ camera and want to have it on my network. I was able to get the setting off the camera. The IP address is 192.168.100.84. My network router is 192.168.1.1. I need to change the IP on the camera to 192.168.1.84.
My question is in a couple of parts. First, do I need to connect the camera directly to the laptop using a cross-over-cable?  If I connect it to my router I can not see it.
Next, if I use a cross-over-cable how can I change the IP address? Do I do it in a browser window or at the command prompt? And how do I do it?
There have Windows and Mac software to do this, but nothing for Linux.
This is the camera I am trying to set up. [https://www.bhphotovideo.com/c/product/1237029-REG/ptzoptics_pt20x_usb_wh_g2_20x_usb_gen2_video_conferencing.html]("https://www.bhphotovideo.com/c/product/1237029-REG/ptzoptics_pt20x_usb_wh_g2_20x_usb_gen2_video_conferencing.html")

---

### Post by chili555 on 2020-06-08
I know very little about this subject, however, your question has been posted for some time now with few views and no comments. I will simply ask a few questions that may help others that are more informed formulate an answer. > 
want to have it on my network.Do you mean that everyone in your network, that is, everyone connected to your 192.168.1.1 router can see the video output? Or do you mean that the video should be available by some mechanism to the world, that is, on the internet?> 
The IP address is 192.168.100.84. Where does this appear? > If I connect it to my router I can not see it.When you go into the administration pages of the router and check the connected clients, is there any sign of the camera; did the router assign a 192.168.1.xx address by any chance?

---

### Post by irv on 2020-06-09
Okay, let's take your questions in order.
When I say I want to have it on my network. If it is seen as a device on my network, I will be able to use it in OBS to record or live stream.
Where did I get the IP address 192.168.100.84, The camera has an HDIM port and a remote to control the camera. By selecting *,#,4 it will display the network setting for the camera on the monitor, but there is no way to change them. There is a program for Windows and Mac to do this, but nothing for Linux. Another vendor not supporting Linux.
And your last question about not seeing the router. If the IP address is not in my range, 192.198.1.? it will not see it. There will be no sign of it until I can change it to 192.168.1.84. The 84 is just a number that is not assigned to any device on my network

---

### Post by The Cog on 2020-06-09
That's a nice looking camera.
It is possible that 192.168.100.84 is a factory default address. You could add a nearby address to your Linux box and then talk to it. Connect it to the network using its ethernet connector. Then replace eth0 with the interface name of your network device in this command:
```
sudo ip addr add 192.168.100.1/24 dev eth0
```
Then you should be able to talk directly to it from your computer. I would hope it has a web interface that you can access with your browser - otherwise I would not know what to do.
P.S.
I found some docs on the camara's VISCA-over-IP. You either need to spend time doing some network programming, or find an app that is designed to control these cameras.
Apparently, the camera listens on UDP port 52381 and custom byte sequences go on top ot that. Commands must be sequence-numbered.
[https://ap.community.sony.com/s/question/0D50B00004d6fsLSAQ/visca-over-ip-third-party-control-for-the-srg300-camera?language=en_US](https://ap.community.sony.com/s/question/0D50B00004d6fsLSAQ/visca-over-ip-third-party-control-for-the-srg300-camera?language=en_US)
[https://ptzoptics.com/wp-content/uploads/2014/09/PTZOptics-VISCA-over-IP-Commands-Rev1_0-5-18.pdf](https://ptzoptics.com/wp-content/uploads/2014/09/PTZOptics-VISCA-over-IP-Commands-Rev1_0-5-18.pdf)

---

### Post by irv on 2020-06-11
This is really a nice camera but when it comes to supporting Linux it sucks. 
Here is how I solved my problem. The camera comes with a remote for controlling the camera, but it also has some shortcuts to setting up the Network. As I said in another post, that the * # 4 displayed the default IP of the Camera. But by plugging in the Network cable and connecting it to my router and pressing the # * 4 it set the IP to my Network. I did the * # 4 again to get the new IP which was 192.168.1.208. I then opened a browser and type in the new IP in the address bar and then logged into the camera. I had to enter the login name and password. admin, admin. I then change the DHCP to fixed IP selected the apply button and restarted the camera by powering it off and then back on again. It was just that simple.
I will mark this thread solved.

---

### Post by chili555 on 2020-06-11
Thank you so much for posting the detailed solution. I am confident that more than a few searchers will find and appreciate it.

---

### Post by The Cog on 2020-06-12
Does that mean that you can fully control the camera from a web browser - don't need one of those custom controller apps at all? That would make a huge difference to how attractive the camera is to me.

---

### Post by irv on 2020-06-12
Once you get into the camera via a browser you can control the camera, the tilt, pan, and zoom. Here is a great howto with a screenshot of the browser interface that will show the controls on the left side of the window. Once you have the camera on your network you can do a lot. I haven't tried it yet, but you can also give others control of the camera remotely while in Zoom. I don't need this feature but it is nice to know you can do this.
check it out: [https://www.youtube.com/watch?v=_Zz5UuBtIEM]("https://www.youtube.com/watch?v=_Zz5UuBtIEM")

---

### Post by The Cog on 2020-06-13
Thanks. And oh yes, that is a really nice looking camera. We wants one.

---

