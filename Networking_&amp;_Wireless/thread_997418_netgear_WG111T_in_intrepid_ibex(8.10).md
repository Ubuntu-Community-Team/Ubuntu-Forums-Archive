---
title: "netgear WG111T in intrepid ibex(8.10)"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by ryan! on 2008-11-29
is there a different install process than hardy?

---

### Post by ryan! on 2008-11-29
please help me

---

### Post by Ihsahn on 2009-01-06
I'm also having the same problem. However. I got the internet working immediately by copying the folders 'network and networkmanager' or something like that from I think it was etc on my 7.10 partition and installed the regular stuff. Ndiswrapper and ndisgtk. I then installed the wg111t drivers and it worked fine.

That was yesterday. I get on today. It doesn't work and I have no idea why. I haven't changed anything as far as I'm aware.

Sorry for the vagueness of stuff. I'm still a n00b :)

---

### Post by teh.chicken on 2009-01-22
I have been having the same problem too, but have seemed to have  found a fix.
I followed the tutorial posted here:[https://help.ubuntu.com/community/Wi.../Device/WG111T](https://help.ubuntu.com/community/Wi.../Device/WG111T) until step 5, however instead of installing netwg111t.inf, I used netw**11**t.inf (this is the one on my cd and off the netgear website, I don't know what's  different)  and the athfmwdl.inf (also on cd). I then uninstalled the network-manger applet with synaptic and installed wicid from here: [http://wicd.sourceforge.net/download.phpv](http://wicd.sourceforge.net/download.phpv), using wicd to connect I had no problems. 

Hope it helps

---

### Post by gumbald on 2009-01-28
I can't seem to find those files, all I can download from the Netgear site is an .exe, which isn't much use to me. Any chance you could send them to me? :)

Aha: [http://kbserver.netgear.com/release_notes/d102626.asp](http://kbserver.netgear.com/release_notes/d102626.asp)

Still doesn't work, that archive doesn't contain netw11t.inf, can't find that still...

---

### Post by teh.chicken on 2009-02-01
Yes sure...
[http://www.mediafire.com/?sharekey=786e76de7366e83891b20cc0d07ba4d2a4e5743ccc](http://www.mediafire.com/?sharekey=786e76de7366e83891b20cc0d07ba4d2a4e5743ccc)
I've uploaded them on media fire, hope they work!
:) 

ABOVE LINK IS BROKEN PLEASE LOOK BELOW

---

### Post by teh.chicken on 2009-02-01
Sorry that link doesn't seem to work try these instead-
[http://www.mediafire.com/?aijdymdotzz](http://www.mediafire.com/?aijdymdotzz)
[http://www.mediafire.com/?qdy4zdwnq4m](http://www.mediafire.com/?qdy4zdwnq4m)

---

### Post by teh.chicken on 2009-02-01
Here is yet another link, this one to the netgear website where you can download a folder containing all of the drivers you need..
[http://kb.netgear.com/app/answers/detail/a_id/723]("http://kb.netgear.com/app/answers/detail/a_id/723")

---

### Post by svpersteve on 2009-02-02
I followed all of these steps, but when I open Wicd manager, it cannot find any wireless networks, even though a macbook is connected to the internet by wireless, I've got my ubuntu pc connected to the internet through it. 

I installed both the .inf files before uninstalling Network Manager completely in Synaptic Package manager. 

I'm running 8.10 and I've just installed  it as a dual boot with XP by mounting the downloaded image file and installing it from within XP. 

Hope somebody can help me... thanks :O)

---

### Post by teh.chicken on 2009-02-02
Try installing from the ndis5 folder (/WG111T_re1.2_rc1/ndis5/...), in  there you'll find all the drivers (.inf) and the other files they need (.sys...) . If you havn't got that folder, it should be on the cd that came with the dongle or you can download it from the netgear site ([http://kb.netgear.com/app/answers/detail/a_id/723](http://kb.netgear.com/app/answers/detail/a_id/723)). Then, uninstall all of your drivers and re-install ndisgtk with synaptic and insatll the drivers found in the ndiss5 folder. Then, under prefrences in WICD set the "WPA Supplicant Driver" to "ndiswrapper".
Hope that helps :S 
Good luck!

---

### Post by stepen on 2009-03-24
I have some issue with wg111t usb dongle adapter in 8.10. I installed ndiswrapper, then I get the athfmwdl - driver's present
netwg11t - driver's present, is this what we should expected or not?

I can see available wireless network list by network-manager or WICD, but failed to connect to the network by WPA/WPA2, I also try to use network-manager to connect to unsecure network, still not working, is this driver issue?

Thanks in advance

---

