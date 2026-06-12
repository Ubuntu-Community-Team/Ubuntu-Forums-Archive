---
title: "how to get inside my tower"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by adult swim on 2008-08-31
i was at  my parents house over the weekend and they had an extra computer laying around so i thought i would bring it home and turn it into a server.  i didnt bring a monitor, or keyboard with it.  i did however set it up to automatic login and use vnc to gain access to it with my laptop when i had a keyboard and monitor to work with.  i had it up and running to where i could control it.  
now im back at my house and when i try to access it via vncviewer, i get the error   vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
anyone have ideas of how i can gain access to this computer?

---

### Post by djm-uk on 2008-08-31
Is it possible you have changed IP network (eg from 192.168.1.x to 192.168.0.x)? The usual default on VNC is to allow all networks (+ in the list), but if it only allowed the local network when it was installed and the local IP range changes...

Also did you boot it up without the keyboard attached to make sure you didn't get a 'keyboard error press F1 to continue" message on boot

Although a 'refused' message suggests an explicit TCP RST on the connection - firewall settings on the server??

David

---

### Post by lisati on 2008-08-31
One thing I'm a bit hazy on: is the machine you're accessing with VNCViewer on your local network or is it in another location?

---

### Post by adult swim on 2008-08-31
the tower is hardwired to my router and im wireless on my laptop.  i have viewed the router via firefox to deterimine the ip assigned to the tower.  i didnt know about keyboard error.  i have a wireless mouse i can attatch to the tower and click aimlessly and try to log on again.

---

### Post by adult swim on 2008-08-31
if it helps, i can ping the tower address and see activity on the router leds.

---

### Post by dmizer on 2008-08-31
Shouldn't take too much to solve this, we just need to get into the box, but we'll need to plug in a keyboard.

then hit:
<ctrl>+<alt>+<f2>

Type in your username (don't make any mistakes), and hit <enter>
Type in your password, and hit <enter>

Now you should have command line access even though you can't see anything. Now we can install software which will give you CLI viewability.

Type this command and hit <enter> (if you make a mistake, hit <ctrl>+c, and start over):
```
sudo aptitude install openssh-server
```

Type your password, and hit <enter>

Now, there should be a lot of hard drive activity.  If not, you may need to reboot the server.

Once you have openssh-server installed, from your laptop you should be able to access your headless server by typing the command:
```
ssh server-username@server.ip.address
```
where "server-username" is the actual username you created on the server box.

Once you have cli access, you can take a look at the logs in /var/log and see what might have caused your vlc connection to fail.

---

### Post by adult swim on 2008-08-31
this sounds like it will sure everything up.  all i have to do now is find myself a keyboard to borrow.  thanks all!

---

