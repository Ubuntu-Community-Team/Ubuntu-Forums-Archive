---
title: "New to Ubuntu, Can't get wirelss after updates"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by Quantum Fabric on 2008-08-17
Hey guys any help would be awesome here, 

I had my ubuntu all set up and working great, but when I performed some 270+ updates I for some reason have lost sight of my wireless card. When I go into my backup I kernel I can see my wireless options but it is unable to connect to my wireless network. I have from what I understand a very new version of Ubuntu, and I'm not really sure where to go from here. I am currently using my windows to write this so I still have a computer, but it's windows

When I go into my wireless options it says I have ethernet connection and dial up connection capabilities but the wireless doesn't even show up, the only difference was that I did my updates and I lost my wireless card. I see there is a restore mode, is it possible to restore to my original settings? (I've only had ubuntu for about 2 weeks so I wouldn't be losing much)

I asked a friend who is quite familiar with Ubuntu and told me to do something along the lines of "ndiswrapper" but that had something in front of it.

Any ideas???

---

### Post by Ayuthia on 2008-08-17
> **Quantum Fabric said:**
> Hey guys any help would be awesome here, 

I had my ubuntu all set up and working great, but when I performed some 270+ updates I for some reason have lost sight of my wireless card. When I go into my backup I kernel I can see my wireless options but it is unable to connect to my wireless network. I have from what I understand a very new version of Ubuntu, and I'm not really sure where to go from here. I am currently using my windows to write this so I still have a computer, but it's windows

When I go into my wireless options it says I have ethernet connection and dial up connection capabilities but the wireless doesn't even show up, the only difference was that I did my updates and I lost my wireless card. I see there is a restore mode, is it possible to restore to my original settings? (I've only had ubuntu for about 2 weeks so I wouldn't be losing much)

I asked a friend who is quite familiar with Ubuntu and told me to do something along the lines of "ndiswrapper" but that had something in front of it.

Any ideas???

Can you help provide some information about your card?  Please provide the results of the following from the Terminal:
```
lspci
lshw -C network
uname -a
```

It might be possible to get your card working before using ndiswrapper.  If it is an update issue, usually a fix comes out fairly quick.  If you need to use the wireless card, you can always go back to the previous kernel until the next kernel update.

---

