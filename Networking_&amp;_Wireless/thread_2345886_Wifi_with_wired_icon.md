---
title: "Wifi with wired icon"
date: 2016-12-08
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2016-12-08
Hi all,

Seems identical to [the problem here]("http://askubuntu.com/questions/789843/wired-connection-icon-is-displayed-instead-of-wifi-icon-ubuntu-16-04"). All good until I close the laptop lid then open. When I open, the wireless icon has changed to a wired icon.

Usually it is still connected wirelessly regardless of the wrong icon. Sometimes it is not connected at all. Sometimes it will connect after:

```
sudo service network-manager start
```

Other times it won't and the only thing for it is a restart after which it works normally, online wirelessly and with a wireless icon. 

The following command suggested on the previous link works to get the wireless icon back:

```
systemctl restart NetworkManager.service
```

Then everything works as it should. This needs to be issued every time I open the lid, though. An unacceptable and clumsy workaround.

My question: how do I prevent the wireless icon changing to a wired one when I open the laptop lid and, more importantly, how do I get it to connect consistently (like every time I open the lid)? Frankly, I don't care what the icon is but I do care that it is a roll of the dice as to whether the wireless is going to be working at all when I open the lid. [Here's the vital statistics]("http://pastebin.com/ac6t5ws7").

Further info, just ask.

---

### Post by #&amp;thj^% on 2016-12-08
If this command works,
```
systemctl restart NetworkManager.service
```

 you could create a script to automate it.

Open a terminal and type the following:

```
sudo nano /etc/systemd/system/wifi-resume.service 
```
Now paste the script in there with a right click. Exit with CTRL + X and  press Y to save. Now to activate it:
 ```
sudo systemctl enable  wifi-resume.service
```
Script:

```
#/etc/systemd/system/wifi-resume.service
#sudo systemctl enable wifi-resume.service
[Unit]
Description=Restart networkmanager at resume
After=suspend.target
After=hibernate.target
After=hybrid-sleep.target

[Service]
Type=oneshot
ExecStart=/bin/systemctl restart network-manager.service

[Install]
WantedBy=suspend.target
WantedBy=hibernate.target
WantedBy=hybrid-sleep.target
```

Hope this helps

---

### Post by Bucky Ball on 2016-12-12
Thanks for that 1fallen. I have been busy doing other things so will fiddle about with this later. Or should I say, next time it happens. Lo and behold, it hasn't since I started this thread. Ain't that the way ... :|

---

### Post by #&amp;thj^% on 2016-12-12
> **Bucky Ball said:**
> Thanks for that 1fallen. I have been busy doing other things so will fiddle about with this later. Or should I say, next time it happens. Lo and behold, it hasn't since I started this thread. Ain't that the way ... :|
No Thanks needed..;)
But thats Good you haven't needed to use it.:)  Had a friend with a wifi card close but Older than yours and it seems to do the job for him...although he reports at times (Rarely Though) he gets two nm-applets at times when resuming from a suspend.
Best Regards

---

### Post by Bucky Ball on 2016-12-24
Well, wireless has been hopeless in 16.04 for me on three machines and always has been since it was released. Haven't been able to fix any of them and wasted too much time attempting to. 14.04 LTS is faultless so have reverted to that on one machine and will probably do so on the others so let's consider this closed.

Will request staff close this thread. Thanks for the input once more, 1fallen. ;)

---

