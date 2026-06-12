---
title: "Simdock can't find icon images"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by cyclone5uk on 2009-02-03
I just installed simdock, but when I run it I get this error:

Can't load image from file '/usr/share/firefox/icons/mozicon128.png': file does not exist.

I'm using Intrepid.

---

### Post by kestrel1 on 2009-02-03
Never tried Simdock, but I use Cairo-Dock.
I have found this to be very nice to use & if you want to try it go [HERE]("https://help.ubuntu.com/community/CairoDock")
Let us know if you are likely to use Cairo-dock or if you really want to get SimDock to work.

---

### Post by x12796 on 2009-02-04
I get this same error in both Ubuntu 8.04 and 8.10.  I'll point the dock to the proper image, and then add additional launchers.  When I close simdock and restart the application it reverts back to the state it was in the first time that I launched Simdock.  Any ideas?

---

### Post by kestrel1 on 2009-02-05
Did you think about trying Cairo-Dock? It is better supported than SimDock in Ubuntu.

---

### Post by cyclone5uk on 2009-02-25
I ended up trying a few different docks but went with AWN - which I love. Works great, even on my netbook!

---

### Post by gandaran on 2009-02-25
simdock never worked properly on any ubuntu version!

---

### Post by kestrel1 on 2009-02-25
Yes, AWn is good as well. I need to try it again, as the version I used a while ago was not as good as Cairo-Dock at the time.

---

### Post by kukibird1 on 2009-02-25
This worked for me using the terminal.

sudo mkdir /usr/share/firefox/icons
sudo ln -s /usr/lib/firefox-3.0.6/icons/mozicon128.png /usr/share/firefox/icons

When you restart Simdock the error should be gone .

---

### Post by trainerjonathan on 2009-04-19
> **kukibird1 said:**
> This worked for me using the terminal.

sudo mkdir /usr/share/firefox/icons
sudo ln -s /usr/lib/firefox-3.0.6/icons/mozicon128.png /usr/share/firefox/icons

When you restart Simdock the error should be gone .

this didn't work for me...
what did work was editing the .xml file in the .SimDock folder with the correct path

---

### Post by kukibird1 on 2009-04-19
> **trainerjonathan said:**
> this didn't work for me...
what did work was editing the .xml file in the .SimDock folder with the correct path

This is much better thanks.

---

