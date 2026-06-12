---
title: "Network Manager help"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by travmanx on 2009-11-08
I used to have WICD Manager installed, but I didn't like it. I went back to Network Manager, but all configs is gone. 
I open it up and it says under wired 'ifupdown (eth 0)'. I clicked the add button and everything is blank. I am unsure what to place in under MAC address. Is it the MAC address of the router? If so where do I find it.

Is there a way to auto config this, like it does when you install Ubuntu?

---

### Post by williejones on 2009-11-08
Are you connceting to cable or wireless?

---

### Post by williejones on 2009-11-08
After reading your post agin, I see it is a wired connection.  Try shutting down to see if anything is recognized.
You may need to click on network manager to find your connection.  If this works set network manager to automitcally connect.

---

### Post by lswb on 2009-11-08
It's common when wicd is installed to use /etc/network/interfaces for configuring the wired connection, but that doesn't work so well with Network Manager. Take a look at your /etc/network/interfaces file.

```

auto lo
iface lo inet loopback

```

If there are any other lines besides these, delete or comment them out. (Must be edited as root, you can use "gksudo gedit /etc/network/interfaces" or whatever editor you're familiar with.

---

### Post by travmanx on 2009-11-08
> **williejones said:**
> After reading your post agin, I see it is a wired connection.  Try shutting down to see if anything is recognized.
You may need to click on network manager to find your connection.  If this works set network manager to automitcally connect.

Like the only icon I get is the one that looks like a wireless signal strength. I right click... only option I get is VPN Connections and "Wired Networks - device not managed"

---

### Post by williejones on 2009-11-08
Have you tried what lswb suggested above?

---

### Post by travmanx on 2009-11-08
> **lswb said:**
> It's common when wicd is installed to use /etc/network/interfaces for configuring the wired connection, but that doesn't work so well with Network Manager. Take a look at your /etc/network/interfaces file.

```

auto lo
iface lo inet loopback

```

If there are any other lines besides these, delete or comment them out. (Must be edited as root, you can use "gksudo gedit /etc/network/interfaces" or whatever editor you're familiar with.



[B][U]
Edit: Fixed! Thanks guys for helping![/U][/B]

---

### Post by williejones on 2009-11-08
Good job lswb

---

