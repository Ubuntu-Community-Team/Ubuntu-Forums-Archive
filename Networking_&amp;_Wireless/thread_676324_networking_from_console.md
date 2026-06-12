---
title: "networking from console"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by DillyP on 2008-01-23
I was working on setting up the bridge interfaces to configure VirtualBox.  The instructions tell you to make a bridge interface by doing a sudo tunctl -t tap1 -u username

I do this, and it doesnt come back with errors, but even after a networking restart or a complete reboot, the changes don't seem to be reflected in the /etc/network/interfaces file.

This happens with any of the other commands too, such as a sudo brctl addbr br0.

I ended up configuring the networking by editing the interfaces file in gedit, but I am wondering what I did wrong or why those commands didn't take hold.

Tried this on several other gutsy computers too... must be newb operator error.

Can someone please enlighten me?

---

### Post by lloyd_b on 2008-01-23
> **DillyP said:**
> I was working on setting up the bridge interfaces to configure VirtualBox.  The instructions tell you to make a bridge interface by doing a sudo tunctl -t tap1 -u username

I do this, and it doesnt come back with errors, but even after a networking restart or a complete reboot, the changes don't seem to be reflected in the /etc/network/interfaces file.

This happens with any of the other commands too, such as a sudo brctl addbr br0.

I ended up configuring the networking by editing the interfaces file in gedit, but I am wondering what I did wrong or why those commands didn't take hold.

Tried this on several other gutsy computers too... must be newb operator error.

Can someone please enlighten me?

I'm not all that familiar with the tunctl command, but what I suspect is happening is that that particular command only *creates* the interface,  but does not even attempt to activate it.  So your solution of editing the interfaces file would in fact be the "correct" way of getting the interface activated at each reboot.  

Remember, you are dealing with some basic Linux commands, which generally do one thing, and *only* one thing. 

You may be able to activate it manually with a "sudo ifup tun1", but if you want it brought up at each restart, then stick with editing the interfaces file...

Lloyd B.

---

### Post by DillyP on 2008-01-23
Issuing the commands I did, and then doing an ifconfig -a I could see all the interfaces I created, but when I rebooted they would be gone.... just wondering if there was an option I had to specify to make them persistent, etc or if it was somehow a privilege issue (even though I used sudo).

The instructions I was following are posted here: [https://help.ubuntu.com/community/VirtualBox]("https://help.ubuntu.com/community/VirtualBox")

---

### Post by karyonix on 2008-01-24
tunctl, brctl, ifconfig commands you use affect current session only, they do not not save settings for next boot.  
You can modify /etc/network/interfaces file to set up TUN/TAP and network bridge for use with VirtualBox after reboot.  Settings in /etc/network/interfaces file will tell the computer to run tunctl, brctl, and other commands automatically, so you do not have to run them manually after reboot.  

See an example of what to put in /etc/network/interfaces here -- [http://ubuntuforums.org/showthread.php?p=4191629](http://ubuntuforums.org/showthread.php?p=4191629)

To apply the settings in modified /etc/network/interfaces file without reboot, use this command.
```
sudo /etc/init.d/networking restart
```

---

### Post by DillyP on 2008-01-24
Yeah, thats what I had to do to get it working... guess I was just puzzled as to why ubuntu.com would instruct to use those commands if they are session effective only.  Thanks for that post though- your post with your interface file is the one I used to get mine running!

---

