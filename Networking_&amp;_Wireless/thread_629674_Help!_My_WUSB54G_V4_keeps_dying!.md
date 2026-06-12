---
title: "Help! My WUSB54G V4 keeps dying!"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by drengi on 2007-12-02
I followed this guide and got my wusb54g v4 working in gutsy:

[http://ubuntuforums.org/showthread.php?t=588045](http://ubuntuforums.org/showthread.php?t=588045)

...except it only works for about 20 minutes. After that the lights die. Unplugging and plugging it back in doesn't help; the lights flash for a split second and go out again. Resetting the PC is the only way to restore functionality.

To make matters even worse, iwconfig and wicd still think the adapter is working. iwconfig gives me a signal strength and wicd still thinks I'm connected. It's obvious the adapter died since the lights are out and I can't access anything on the network.

I installed feisty thinking it might solve it. Nope. Exact same problem. Stupid thing keeps dying.

Could it be a power issue? Black magic? I'm a linux newb so I have no idea what's causing this frustrating problem :(

---

### Post by drengi on 2007-12-02
bump...this wireless problem is the only thing holding me back from completely switching to linux

---

### Post by tak1150 on 2007-12-03
Could you see if the network restores after you issue this command?

```
sudo /etc/init.d/networking restart
```

---

### Post by drengi on 2007-12-03
> **tak1150 said:**
> Could you see if the network restores after you issue this command?

```
sudo /etc/init.d/networking restart
```

Thanks for the reply, I'll be sure to try that out next time it dies (which soon be soon...)

I've looked into the problem a bit more and I believe it has to do with the USB ports. When the wusb54g fails this appears in the system log:

"usb 4-5: USB disconnect, address 3"

After this, all USB ports become unresponsive.

I made another thread which specifically targets the USB problem here: [http://ubuntuforums.org/showthread.php?t=630559](http://ubuntuforums.org/showthread.php?t=630559)

---

### Post by tak1150 on 2007-12-03
does this USB card work in Windows without the same problem?
I had the card that controls USB go bad once on my desktop and I had to get a new motherboard (which was under warranty :)).

---

