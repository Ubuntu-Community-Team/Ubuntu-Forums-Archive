---
title: "Connecting to Server"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by daniell59 on 2009-07-01
My Ubuntu 9.04 no longer automatically connects to the server when I boot up. How can I again connect to my wireless network?
It connects with Vista however.
Thanks

---

### Post by tarps87 on 2009-07-01
Do you meen a server or your wireless network?
If it is to your wireless network can Ubuntu still see it? Is the option to auto connect still enabled?
If it is a server we will need more details on it

---

### Post by daniell59 on 2009-07-01
> **tarps87 said:**
> Do you meen a server or your wireless network?
If it is to your wireless network can Ubuntu still see it? Is the option to auto connect still enabled?
If it is a server we will need more details on it

It is the wireless network.
Auto connect is not available.
Thanks, I am sorry that I was not clear. It merely reflects my lack of knowledge.

---

### Post by tarps87 on 2009-07-01
No problem, just need a bit more info.
Are you using the default network program? Right click the icon, then about. The default is called NetworkManager Applet
When you click on the icon can you see your network?
If you can not see you network can you post the output of
```
iwconfig
```
Thanks

---

### Post by daniell59 on 2009-07-01
> **tarps87 said:**
> No problem, just need a bit more info.
Are you using the default network program? Right click the icon, then about. The default is called NetworkManager Applet
When you click on the icon can you see your network?
If you can not see you network can you post the output of
```
iwconfig
```
Thanks

Thanks, but can you please elaborate some more. This is all new to me. I cannot try things out however until I reboot. At present I can only go online in Vista.

---

### Post by cariboo on 2009-07-01
You have to be running Ubuntu in order for us to help. In order to make things easier on you, and so you don't have to reboot into vista every time you run a command pipe the commands given to a text file, then copy them to your Vista partition. eg:

```
iwconfig > iwconfig.txt
```

To run the above command open an Applications-->Accessories-->Termianl.

In the same terminal could you type:

```
sudo lshw -C network > network.txt
```

Paste the output of the above two commands in your next post.

---

### Post by daniell59 on 2009-07-01
Here is a digital image. I hope this can clear things up.

---

### Post by tarps87 on 2009-07-01
I will try to explain things better, the main thing to establish is if you have the networking program.
The screenshot shows that your wireless card is working and enabled.
Do you have the network icon usally on the top right, it looks like two computers?
You said that it no longer auto connects, how did you set this up before?

---

### Post by daniell59 on 2009-07-01
> **tarps87 said:**
> I will try to explain things better, the main thing to establish is if you have the networking program.
The screenshot shows that your wireless card is working and enabled.
Do you have the network icon usally on the top right, it looks like two computers?
You said that it no longer auto connects, how did you set this up before?

I don't have the network icon any more. How can I get it back?

---

### Post by daniell59 on 2009-07-01
Can someone please tell me how to set this up.

Thanks

---

### Post by tarps87 on 2009-07-02
That dialogue is to set up a connection to a server, this will be where the confusion is coming form.

To get the network application up first right click on the panel at the top, now click add to panel. Add the notification area. The network icon should now appear. If it does not type this into a terminal
```
nm-applet
```

It sounds like you have just remove the notification area once you get it back you will be able to connect to your wireless network.[ATTACH]119724[/ATTACH][ATTACH]119725[/ATTACH][ATTACH]119726[/ATTACH]

---

