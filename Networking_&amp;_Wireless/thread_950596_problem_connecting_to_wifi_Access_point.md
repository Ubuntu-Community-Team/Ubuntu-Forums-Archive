---
title: "problem connecting to wifi Access point"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by mortel_elec on 2008-10-17
i'm new in Ubuntu, trying to connect to my home wifi, i'm using netgear 802.11b, my ubuntu laptop recognize the access point, but i cannot connect to it. can you please help me.

---

### Post by icanfly0307 on 2008-10-17
Hi, 
      When you mean that you cannot connect to the access point, what exactly is happening? Could be more specific on what you're trying to do and the error that is occurring? (Maybe post a few screenshots.) :)

---

### Post by pytheas22 on 2008-10-17
First, try installing wicd.  You can download an installer for it [here]("http://downloads.sourceforge.net/wicd/wicd_1.5.3_all.deb?modtime=1222631284&big_mirror=0"); save it to your desktop and double-click the icon to install.  After it's installed, you can launch it from your Applications>Internet menu.  You may have better luck connecting with wicd.

If not, try restarting your router (by unplugging it, waiting a minute, then plugging it back in).  This may help.  If that still doesn't change things, do you have better luck if you disable security on your network?

If none of the above helps, please post the output of:
```

lshw -C Network
lspci -nn
lsusb
sudo iwlist scan
uname -m
```

---

### Post by mortel_elec on 2008-10-17
> **icanfly0307 said:**
> Hi, 
      When you mean that you cannot connect to the access point, what exactly is happening? Could be more specific on what you're trying to do and the error that is occurring? (Maybe post a few screenshots.) :)

After i detected the Access Point, i tried to connect, it as for key since i'm using a hex encryption.  then i click connect.  actually nothing happens it just did not connect.

---

### Post by pytheas22 on 2008-10-18
> After i detected the Access Point, i tried to connect, it as for key since i'm using a hex encryption. then i click connect. actually nothing happens it just did not connect.

Did you have a chance to try the suggestions from my post?  There's a good chance that switching to wicd, in particular, would solve the problem.  It sounds like the problem is that you can't manage to get an IP address, which is sometimes Network Manager's fault.

---

### Post by icanfly0307 on 2008-10-18
It looks like Network Manager's fault. Sometimes it does that. It used to happen to me in Fedora, but that was because i used WPA as my security. Did you enter the ***hex key*** when it was actually asking for the **_passphrase_**? Double check because that would cause you to not be able to connect.

 Also, did you set the sharing mode option correctly ie. "Open System" "Shared Key"? You can usually figure this setting out by logging in to your router. How many bits is your key? ie 64, 128?

---

