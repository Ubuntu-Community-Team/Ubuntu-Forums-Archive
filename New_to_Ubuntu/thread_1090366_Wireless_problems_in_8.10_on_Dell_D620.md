---
title: "Wireless problems in 8.10 on Dell D620"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by katriona on 2009-03-08
I have a dual-booting Dell Latitude D6200 laptop and recently switched my Linux side from Fedora to Ubuntu.  Some friends in the Texas Tech Linux User Group helped me install 8.04 from a liveCD, then I upgraded to 8.10 through the update manager.  When I first installed 8.04, I was able to connect to the wireless network at my apartment but had trouble connecting to the wireless on campus (apparently a common problem for Linux and Mac users at my school due to the way the wireless is set up).

However, starting yesterday my wireless stopped working on my Ubuntu side and I have no idea why my computer no longer detects any networks whatsoever (not even any of the ones it could detect before).  I doubt it's due to broken hardware since the wireless still works just fine on my Windows side.  I've heard that hardware for Dell Latitude laptops can be tough to work with in Linux, so maybe I'm having a driver problem?

My wireless card is an Intel Pro Wireless 3945 ABG.  Do I need to download and install drivers to make it work properly in Ubuntu, and if so where can I get them?  Any help would be greatly appreciated.  Thank you.

---

### Post by fly-by-night on 2009-03-13
I have a IWL3945 too.  I occasionally have to Disable and then re-Enable Networking for it to connect again.
Sometimes it automatically connect or I have to left click the Network icon (on taskbar) and Connect to Hidden Wireless Network.  Change "new" to your network name (should be on the dropdown (mine is manually configured)).
Also to connect to Net I had to manually specify openDNS (or your choice) servers manually by right clicking Network icon and specify it in Edit Connections (wireless).

My laptop is a Compaq V6000 (V6560EA) and worked from a fresh install. 
I currently (touch wood) have no problems what so ever.  But then again I leave all themes etc at defaults to avoid messups.

Once you installed it again and got wireless working, back-up your system with Clonezilla and you never have to re-install again - hopefully.

---

