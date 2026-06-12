---
title: "Nvidia update problem"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by pistelli on 2009-01-30
I just intstalled 8.10 on a Dell XPS M1710.  I went to turn on the visual effects and it told me i had to enable my Nvidia Graphics Accelerater card.  After i enabled it, it said i had to restart so i did.  When it boots up it gets past the screen with the loading bar and then just goes blank.  I tried restarting a couple times and i have the same problem.

How can i fix this.

...I think i read a post on this a few days ago but i couldn't find it, it might be easier to point me in that direction.

---

### Post by Hospadar on 2009-01-30
when the screen goes blank, try Ctrl-Alt-F1 to get to a terminal.  This might give you some helpful output.  You can also try restarting your x server from there with ```
 sudo /etc/init.d/gdm restart
``` and see if it gives you any helpful errors (it'll probably try to jump you back to your graphical interface when you do that, ctrl-alt-F1 back to your virtual terminal)

---

### Post by pistelli on 2009-01-30
Before you responded tried booting in recovery mode.  I chose the option that repairs broken packages and then did a file system check.  Then i dropped into the shell prompt and tried "sudo dpkg-reconfigure x -phigh xserver-xorg" exited and resumed boot.  

I got back to the gui logged in and updated the nvidia drivers from the synaptic package manager and it seemed to work good.  I then enabled it and it said it would be enabled after restart, so restarted.  

I again have the same problem as before, after the loading bar completes  a black screen comes up. Ctrl-Alt-F1  does nothing.  So I tried restarting in recovery mode again and tried "sudo /etc/init.d/gdm restart" and nothing happens. I then tried the steps i did previously and nothing happens.

I was reading a similar post yesterday and they had the OP enter some nvidia-settings command in something and save before boot-up so it would remember which card to use.  Could that be the problem?

---

### Post by smothpocket on 2009-01-30
If you install the drivers from nvidia's site it configures the xorg.conf for you. This might not solve your problem, but I would try to remove the ones from the repo and use the ones from nvidia's site.

you have to install build-essential
```
sudo apt-get install build-essential
```

then press ctrl-alt-F1

```
sudo /etc/init.d/gdm stop
```
```
./~/Desktop/nvidiafile
```

then it will ask if you want it to configure your xorg.conf for you and say yes... if you happen to say no or want to try again then you can use this script

```
sudo /usr/bin/nvidia-xorg
``` or... something like that...

---

### Post by pistelli on 2009-01-30
I can only type commands in with recovery mode.  It says it can't fetch [http://somewebsite.com](http://somewebsite.com) and I am assuming that's because its not connected to the internet in recovery mode.  The Ctrl-Alt-F1 does work at all at my black screen.  The splash screen loads and the a black screen comes up.

---

