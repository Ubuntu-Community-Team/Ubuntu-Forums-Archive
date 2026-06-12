---
title: "Getting My Wireless Card To Run On Startup"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by bitninja on 2006-11-18
I successfully got my Belkin Wireless Pre-N (Airgo chip) card to work on my Ubuntu laptop. Yay! My only issue is that I can't figure out for the life of me how to get it to connect to my network on startup. It seems to automatically "modprobe ndiswrapper" by itself. So the card itself is on, but I have to manually run "iwconfig wlan0 essid blah key restricted blah" and then "dhclient wlan0" to get it to actually connect. My /etc/network/interfaces has my ESSID and my WEP key, and it's correct. I've made a script so I don't have to manually type everything in every time, but I can't seem to figure out how to get it to run at boot time. I've tried the crontab way, I've tried the GNOME session manager way (which doesn't save, so as soon as I close the session manager everything I did is discarded), I've tried the rc.local way...nothing. ](*,) Does anyone know of a way I can fix this? :confused: 

Thanks in advance,
Cody

---

### Post by stupidkid on 2006-11-18
Edit the /etc/network/interfaces file. (Not sure about the exact file path or what you need to edit, but there should be a example file).

---

### Post by eggdeng on 2006-11-18
A really easy way to do this is just save your script to the /etc/init.d directory, then sudo chmod +x your_script Good luck with it.

---

### Post by FrodoB on 2006-11-19
Publish the section in interfaces for your device. Whatever you are doing manually can be added there and it will likely work. 

Adding scripts at startup is fine, but if you can do it the offical way and document it, more people will be helped.

---

### Post by bitninja on 2006-11-19
Well here's my /etc/network/interfaces...

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp
wireless-essid <my essid>
wireless-key <my key>

auto wlan0


It's been like that since I got my card working...but it doesn't work. I'll try dropping my script in init.d.
EDIT: Dropping it in init.d didn't work either...I think it's because I'm using ndiswrapper, and ndis doesn't run til after all of the init stuff happens...that could be a problem.

---

### Post by trubblemaker on 2006-11-19
FYI sometimes the driver is slow to boot up. you can run the script at boot with a post-up:

```

iface wlan0 inet dhcp
     post-up /path/to/script

```

Some people find that this really slows down there boot time.  others don't.  I read somewhere that init.d will run at each stage of boot so you might also not want it to be run multiple times.  You probably want to run it on login, so added it to your session either with rc.local or System>Preferences>Sessions>Startup Programs.
 
In my experience the startup programs runs quick and lets you boot faster.  Also FYI if you clean up your /etc/network/interfaces file you will also boot faster.  I don't think that you actually use all those interfaces on an everyday basis.  Your machine searches for all of them when there in your interfaces file.  Commenting the 'auto ...' will make for a faster boot, but you will have to manually bring them up later if you want to use them. (ifup ifdown ect.)

Hope this helps

---

### Post by bitninja on 2006-11-19
Thanks! I'll try that next. I'll let you know how it goes.

---

### Post by bitninja on 2006-11-19
Well I still have the problem of my startup programs not saving after I exit the session manager...could that be due to the fact that I have a blank session list? I did clean up my /etc/network/interfaces and added the post-up to it, now all I need to do is reboot and test it out.

---

### Post by trubblemaker on 2006-11-19
Great hope it works for you!

---

### Post by bitninja on 2006-11-20
Well, the post-up works! The only drawback is that it takes about 30-45 seconds after you see the Gnome desktop that it actually activates. It runs after login like I want, but not right on login. Oh well. It's better than nothing I guess.

Thanks for the help!
Cody

---

### Post by trubblemaker on 2006-11-20
yeah I noticed that and I've made some improvements.  on your menus go into Admin?>Preferences>Sessions>Startup Programs (Sorry not on my linux box write now.) and run the script from there. (you might need to and "sudo dhclient wlan0" to the end of it but its way faster boot and it still does the trick.  I blame ndiswrapper for the slow boot.  you can make it a root script and remove the sudo's  by 
```
 chown root /path/to/file 
```  I also advice changing the file at that time so only user can write so no one can takeover the script.


Hope this works better for you it really sped up my boot time.

---

### Post by bitninja on 2006-11-21
I don't know why, but anything I enter into the Startup Programs doesn't save. I haven't been able to track down the problem, so I can't do that solution. The post-up works just fine anyways.

---

### Post by trubblemaker on 2006-11-21
look into rc.local it might be another solution for you to run on login

---

### Post by bitninja on 2006-11-21
Will do, thanks.

---

### Post by Verily on 2007-03-25
Possibly a stupid question, but I'm having this problem, too, (same card-- Belkin Pre-N Wireless, running on Ubuntu Edgy) and don't really know how to set up a fix.  Partly because I'm a linux noob, so I'm not even sure how to go about writing a script to run so I've been typing in the statements at startup each time.

Could anyone help me with that and/or have any other ideas how to get this card running at startup?

---

