---
title: "System locked up completely"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by moody_mark on 2009-02-25
I wonder if anyone can help. Ive been using Ubuntu for about 6 months now and I have been getting on ok. Now and then Ive seen this problem on two different PCs, but its happened more often on a new Dell E6400 PC I just received.

Im running 8.04 and got all the latest updates etc. Sometimes I'll be working and the gnome desktop will lock up, I have mouse action but no "click action" ie i cant select anything

I cant get into a shell with "CTRL+ALT+F1" and I cant restart gnome with the "CTRL+BACKSPACE". I can use the "SYSREQ" and REISUB but when I do I notice nothing in the logs that shows up as an error, i checked all the logs in /var/logs and i cant see anything that shows a process is taking up too much CPU etc.

The fan on the PC goes on and off as it does normally, but I dont know what to do. I know that the gnome desktop has bugs like any other desktop would but I would like to know if its something Ive done or in fact I could not use a particular application to avoid it. I do have a fair amount of processes running, I use the laptop for work and use vpnc, I use a couple of remote terminal desktops and terminal windows, I also use firefox and thurderbird. I checked yesterday and the PC wasnt using more than 25% on either core and the RAM useage as 1GB out of the total 2GB.

Currently the PC is "stuck" and I can tell as the gnome desktop clock is stuck on 11:03

Can anyone help?

I did post another thread here, but it was seen on resume after a screensaver it may or may not be relevant and was seen on a different PC

[http://ubuntuforums.org/showthread.php?t=1055055](http://ubuntuforums.org/showthread.php?t=1055055)

Ive left the machine in this current state at the moment as i want to try and find out the problem as its "live" (im using another machine to post this)

---

### Post by billgoldberg on 2009-02-25
> **moody_mark said:**
> I wonder if anyone can help. Ive been using Ubuntu for about 6 months now and I have been getting on ok. Now and then Ive seen this problem on two different PCs, but its happened more often on a new Dell E6400 PC I just received.

Im running 8.04 and got all the latest updates etc. Sometimes I'll be working and the gnome desktop will lock up, I have mouse action but no "click action" ie i cant select anything

I cant get into a shell with "CTRL+ALT+F1" and I cant restart gnome with the "CTRL+BACKSPACE". I can use the "SYSREQ" and REISUB but when I do I notice nothing in the logs that shows up as an error, i checked all the logs in /var/logs and i cant see anything that shows a process is taking up too much CPU etc.

The fan on the PC goes on and off as it does normally, but I dont know what to do. I know that the gnome desktop has bugs like any other desktop would but I would like to know if its something Ive done or in fact I could not use a particular application to avoid it. I do have a fair amount of processes running, I use the laptop for work and use vpnc, I use a couple of remote terminal desktops and terminal windows, I also use firefox and thurderbird. I checked yesterday and the PC wasnt using more than 25% on either core and the RAM useage as 1GB out of the total 2GB.

Currently the PC is "stuck" and I can tell as the gnome desktop clock is stuck on 11:03

Can anyone help?

I did post another thread here, but it was seen on resume after a screensaver it may or may not be relevant and was seen on a different PC

[http://ubuntuforums.org/showthread.php?t=1055055](http://ubuntuforums.org/showthread.php?t=1055055)

Ive left the machine in this current state at the moment as i want to try and find out the problem as its "live" (im using another machine to post this)

I have had that happing in Ubuntu 8.04 once or twice.

It seemed to happen when using Totem to stream videos over ssh.

I haven't had the same experience with Ubuntu 8.10.

It's most likely a bug.

I suggest you take a look at launchpad to see if a bug is filed (it most likely is already) and see if they have a dirty fix for it.

Or you could upgrade to the newest gnome version, which would mean you would need to upgrade to Ubuntu 8.10.

---

### Post by mkvnmtr on 2009-02-25
Running 8.10 doesn't seem to stop the problem for me. It is just sudden 100% cpu usage and I have to close the window. I have had htop running a few times and it does not seem to be an app I am running but a root process. I have lost the screen shot. It seems to happen a little more on 8.10 than 8.04. In the short time I was playing with 9.04 I don't remember the problem but that doesn't mean it is not going to be there. It really doesn't seem to be a big problem to me. I have had it happen on my Mac os many times but didn't have the tools to look for what was causing it.

---

### Post by moody_mark on 2009-02-25
Update on this: I was given some help my some of the guys in the #ubuntu-uk IRC today. Basically the problem occured when opening a .wav file in totem. If (as it is by default) the visualizations are left on then this seems to disagree with the video driver.

Interestingly enough it does not seem to hang the entire system, as I could ssh into the PC from another PC, BUT trying to kill gdm and X didnt actually make any difference my screen on the PC was "frozen" in time and I didnt get the login prompt back even though gdm was restarted.

I ended up having to reboot the PC. There didnt seem to be anything useful in the logs. :( Does anyone know of a bug of fix due for this? Its likely that this problem could occur with other applications that use video.

---

