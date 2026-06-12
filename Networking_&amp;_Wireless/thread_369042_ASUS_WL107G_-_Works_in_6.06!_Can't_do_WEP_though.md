---
title: "ASUS WL107G - Works in 6.06! Can't do WEP though?"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by Naubra on 2007-02-24
After struggling with a linksys card forever, i went and bought an [SIZE="3"]ASUS wl107g[/SIZE] at the advice of someone on this forum.

Couldn't get it to work in 6.10, so i booted up the 6.06 cd and it worked like a charm. 
My only problem is that when i tried to enable WEP, i get no dhcp offers on ifup.

I recall reading something about **WEP keys needing dashes**, or needing to be either ascii or hex (I tried both to no avail), but i can't find the thread i read that in.

So close to actually staying with linux this time after trying every couple years, please help! 

Thanks in advance.

---

### Post by Naubra on 2007-02-24
tap tap

---

### Post by beanworks on 2007-02-24
Hi,

I am not using 6.10 (using 6.06), but I have a Dlink card on one machine, and a linksys usb adapter on another, both working, with WEP.

My wireless router generated a WEP key for me (you wouldn't need to have the router do it, but that's usually an option), which I then copied and typed into the configuration wizard on the ubuntu machines.  If the router generates a hex key (as mine did, but displayed it in regular letters and numbers), that's what you have to choose on the ubuntu wireless configuration.  On mine machines, the entry box looks like it's not big enough for the entire key, but it does fit.  Also, the key doesn't display as you type (like a password), so type carefully! (or I suppose you could copy and paste it into a text doc, transfer it to the other machine and paste it into the wizard - but that would be too easy...)

AFAIK, WEP does not use dashes, but I suppose you could create one with dashes if you really wanted to.

Although you didn't ask, I'll offer a little more advice:  my connections didn't work until I assigned an IP address from the client machines (pick anything that's not already in use, for example, if your router is 192.168.1.0, you could "grab" 192.168.1.185 for the wireless machine), and DNS servers (which I looked up on the internet, to get my ISP's numbers for my area), and the gateway, which is the router's IP address.  (The subnet mask, of course, is 255.255.255.0)

Hope this helps. :)

---

### Post by dbott67 on 2007-02-24
I'm not using the ASUS card, but after fumbling around a bit trying to get mine working (see this thread: [http://www.ubuntuforums.org/showthread.php?t=274915)](http://www.ubuntuforums.org/showthread.php?t=274915)), I ended up installing network-manager-gnome and everything works properly.

```
sudo apt-get install network-manager-gnome
```

---

### Post by Skidpad on 2007-02-24
Hmmm.  I had no trouble with my ASUS card, although when I installed it, I had removed all encryption from my router to ensure that the card would work properly.  Once I verified that, I added WEP (no dashes, just an obscure ASCII phrase with no spaces between the words).  

Have you tried removing all security on your router, and then building back into encryption?

---

