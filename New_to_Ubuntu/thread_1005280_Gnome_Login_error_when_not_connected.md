---
title: "Gnome Login error when not connected"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by csblouhoender on 2008-12-08
Hi,

I recently installed Ubuntu 8.04 on my laptop(Hp 7400). At the office I am connected to the internet and running dual monitors.

I have found that the "There was an error starting the gnome settings daemon" (see attached image) error occurs whenever I am booting from home or wherever I don't have my network cable plugged in. 

I have tried all the posted solutions. But with no result.

I'm sure there's just some tiny adjustment required, but being  the super noob that I am I have run out of options\resources.

Please help.

I also just realized that it has to do with whether I was connected during the previous session. So maybe something it does when logging off rather than in?

---

### Post by prshah on 2008-12-08
> **csblouhoender said:**
>  So maybe something it does when logging off rather than in?

With the network connection disconnected, open System-Preferences-Sessions-Options-[indent]
UNCHECK "Automatically remember .." and then click the "Remember currently running applications" button.

Now it will no longer autolaunch programs that were active when you last logged out. 

Hope it helps.

---

### Post by csblouhoender on 2008-12-08
Thanks for the response,

Although I should probably mention that the "Automatically remember .." part is already un-ticked...for what that's worth.

---

### Post by csblouhoender on 2008-12-09
No...doing the click "Remember currently running applications" button thing doesn't change what it does either. :confused:

---

### Post by prshah on 2008-12-09
> **csblouhoender said:**
> No...doing the click "Remember currently running applications" button thing doesn't change what it does either. :confused:

There is also a known problem (in Intrepid) if you have entries for eth0 in the /etc/network/interfaces file; can you post the contents of the file here?

However, the issue is a hang when booting without network plugged in, not exactly what you are experiencing, but maybe related?

---

### Post by csblouhoender on 2008-12-09
Here it is...

auto lo
iface lo inet loopback


iface wlan0 inet dhcp
wireless-essid NETGEAR

auto wlan0


iface eth0 inet dhcp

auto eth0

---

### Post by prshah on 2008-12-09
> **csblouhoender said:**
> 
iface eth0 inet dhcp
auto eth0

From Intrepid onwards, eth0 need not be specifically defined in the /etc/network/interfaces file; try commenting out the above two entries. To comment out the entries, open the file, place a "#" (hash) in from of each eth0 entry, save and quit. Changes will not take place until a reboot. To edit the file, press Alt+F2, and give the command ```
gksudo gedit /etc/network/interfaces
```


You may lose the network adapter altogether with this change; in this case, reopen the file, and remove the "#" character.

Post back with your results.

---

### Post by csblouhoender on 2008-12-10
Thanks for your help so far prshah,

but..

Ok, my bad... I just realized that Intrepid is Ubuntu 8.10. 

How Noob am I?!

I have 8.04 (Hardy) 

Don't know if that changes anything. Let me know if its safe or neccesary to still try your suggestion.

---

### Post by prshah on 2008-12-10
> **csblouhoender said:**
> 
Don't know if that changes anything. Let me know if its safe or neccesary to still try your suggestion.

Nope, the suggestion has no value for 8.04; maybe someone else can help? Try bumping the thread after waiting an additional day...

---

### Post by csblouhoender on 2008-12-10
Thanks anyway dude...

---

### Post by csblouhoender on 2008-12-15
Ok,

I'm tring again...

I get the error when I log-in and I'm not connected to the internet. My computer still runs normally and I haven't experienced any difference other than, I'm not connected. 

But it still is annoying and one can't help to think that it does something? 

Does it do something? 

I had the big huge font at login problem as well (solved now) if that means anything. Don't know if the two go together. 

Anyway, if anyone can help me with that it'll be cool. If not- Oh well, I'm a pretty quick learner so pretty soon Ubuntu will be under my skin, I might just figure it out and then I'll solve it on my own. And then take over the world. But not before posting a solution.  

Thanks. \\:D/

---

