---
title: "Can't get my bluetooth mouse to work in ubuntu 8.10"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by switch10 on 2009-06-10
I have a MoGo bluetooth mouse.  It works perfectly in fedora 11.  I set it up in ubuntu 8.10 and it says the pairing was successful, and my computer shows the mouse in the device area.  But the mouse does not work.  

Would it be possible to upgrade the bluetooth program to the one that is on fedora 11?

Thank's 

Dave

---

### Post by switch10 on 2009-06-10
I installed blueman and it wont even pair with the mouse.  when I reinstalled the default bluetooth app, the mouse worked for a second, but stopped right away.  Whats going on here?  it works fine in other OS's

---

### Post by switch10 on 2009-06-11
bump.  anyone know what's going on here?

---

### Post by eMJayy on 2009-06-11
Hi. I don't have any experience troubleshooting bluetooth mice, but I found a previous thread that should give you some good ideas. I'd suggest that you read through from the beginning of the thread to the end before trying any of the suggestions - that way you will be able to see what might be more relevant to your issue. Near the end of the thread, someone with your brand of mouse was able to fix their issue so you'd definitely want to take a look at that. 

[http://ubuntuforums.org/showthread.php?t=87919](http://ubuntuforums.org/showthread.php?t=87919)

---

### Post by switch10 on 2009-06-13
Thanks for the link, but I've already tried all that.  My problem is not configuring the mouse.  bluez and blueman (the two i've tried) both see the mouse and configure everything fine, but the mouse does not work.  It must be some kind of conflict on my system, because if I put in a fedora 11 live cd, the configuration is the same, but the mouse works great!! 

I just don't get it.  I have the same version of bluez that fedora 11 uses.  It should work right?

---

### Post by joonate on 2009-08-01
Hi All,

I used to use hidd however it doesn't come up with 8.10 on default installation. I tried blueman as most of my googling pointed-out. It certainly looks much better than Gnome's standard applet. Though It recognized my bluetooth mouse ( BTM-5963 ) but I did not manage to get it working.

Then it dawned on me what if hidd is still available as a package however I do know that it is old and opensuse my previous distro choice is not including it any more.

_[COLOR=black]So a quick search on Synaptic Package Manager gave me bluez-compat package which includes hidd.[/COLOR]_ Then running  ' sudo hidd --search ' VOILA my mouse is working. 

Hope this helps,

---

### Post by switch10 on 2009-08-01
thank you for the help but im getting:

"Connecting to device 00:02:76:01:39:10
Can't get device information: Connection timed out"

I ditched the 64 bit install for the 32 bit, and I had my mouse working, but when I rebooted it stopped working, and i was never able to pair it again.  I'm about ready to just give up with this I have know idea what is going on.

---

### Post by mgmiller on 2009-08-01
There are a couple of things you can try.  Just for giggles, try an Ubuntu 9.04 live CD.  There have been a lot of changes in the bluetooth stack and there were even more after the release of 9.04 which won't show up on the live CD.

On your existing 8.10 install try doing the following:

```
gksu gedit /etc/default/bluetooth
```

Look at the line that says:
```
HID2HCI_ENABLED=1
```

And change it to:
```
HID2HCI_ENABLED=0
```

Save the file and close everything and reboot.

You may have to re-pair the keyboard and mouse by pressing the buttons on the dongle and mouse one time after rebooting.

It will not show up in bluez when done this way, so don't try to pair them that way.

This is the only way I can get my Logitech Dinovo Edge  bluetooth mouse/keyboard to work reliably.

---

### Post by joonate on 2009-08-06
> **switch10 said:**
> thank you for the help but im getting:

"Connecting to device 00:02:76:01:39:10
Can't get device information: Connection timed out"

I ditched the 64 bit install for the 32 bit, and I had my mouse working, but when I rebooted it stopped working, and i was never able to pair it again.  I'm about ready to just give up with this I have know idea what is going on.

That happened to me a few times too. After re-trying couple of times it eventually connected. Here is how I do it step by step:

1. Run "sudo hidd --search"
2. Turn on mouse.
3. Hit the connect button.
4. Searching ...
    Connecting to device ******
5. After mouse is functioning I run  "sudo hidd -t 5" This makes the connection last 5 minutes.

---

