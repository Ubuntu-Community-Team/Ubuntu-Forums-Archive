---
title: "Install Problems with wubi"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by Dshock73 on 2009-12-27
I'm trying to install UNR using WUBI and I keep getting an error.  It says : An error occured:
Cannot download the metalink and therefore the ISO
For more information see the log file.........
 
Can anyone help me with this?

---

### Post by lisati on 2009-12-27
Wubi places its log file in the %temp% directory. You can view the folder by clicking on Start->Run and then typing the **%temp%** in the box, and pressing Enter.

Don't be surprised if there's a load of other stuff there, most of which can probably be safely delete.

---

### Post by Dshock73 on 2009-12-27
Well I kept uninstalling and installing it and after about 10 times it just started to work hopefully all else goes well.  This is my first go at a linux based system

---

### Post by Dshock73 on 2009-12-28
well I just realized I accidently tried installing UBUNTU and not UBUNTU NETBOOK REMIX.  so I canceled that and now i'm trying to install UNR and its still not working?? ? ? ? ?

---

### Post by Dshock73 on 2009-12-28
I found the log and i'm just really confused as to what all was in there?

---

### Post by plusnplus on 2009-12-28
Hi Dshock73,
Why not you try download iso file from ubuntu.com and install it directly from the cd? (boot from cd-rom)
my opinion, it is more easy then install from wubi.

---

### Post by Dshock73 on 2009-12-28
I have no optical drive. trying to install on my netbook.  I'm currentyl downloading the iso so can boot from usb but its taking forever figured i'd try wubi while I waited.

---

### Post by billyjmc on 2010-01-03
I've outlined a procedure to use wubi with UNR in this post:
[http://www.uluga.ubuntuforums.org/showthread.php?p=8600249#post8600249](http://www.uluga.ubuntuforums.org/showthread.php?p=8600249#post8600249)

Anyhow, the overview idea is to just download the UNR ISO, mount it using Microsoft's Virtual CD Control Panel, and then run the wubi included on the ISO. The version of wubi included on the ISO is set up to run without a network connection, so this avoids the whole issue.

Hope this helps!

---

### Post by amrish on 2010-01-31
The UNR install via USB thing doesn't seem to work for my situation at all. I've gotten Windows 7 installed via my flash drive with 0% issues.
Also the WUBI seems cool, but it keeps erroring out with metalink download issue.

I tried: on my netbook windows 7 32-bit

- Using WUBI off the netbook CD mounted on my netbook
- Downloading a fresh WUBI and putting it in a folder with the .iso of netbook Ubuntu

Noticed

- On my desktop it works fine and it's using windows 7 64-bit

---

