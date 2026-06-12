---
title: "Intel Pro/Wireless 3945 (IPW3945)"
date: 2007-12-23
forum: Networking &amp; Wireless
---

### Post by Havoc7592 on 2007-12-23
So I know that this is one of the more popular topics on the forums, but even after reading through everything and trying a bunch of stuff, I can't get my wireless working.

I am using 7.10 on my Toshiba Satellite U205-S5057.  It uses the Intel Pro/Wireless 3945 card.  It can detect networks, but when I try to connect to mine (with WEP and broadcast disabled), it fails.  I'm aware of Bug #158045, but I'm not sure if that's really the problem.  The computer works when I'm plugged in, but I'd really rather not have to do that every time.

Thanks for your help,
Bryan

---

### Post by ubutufan on 2007-12-23
What exactly is the problem you are dealing with?
Not sure I understood. Is wired working but wireless not?
Clarify and possibly give more info. Also edit the file /etc/network/interfaces and post it here

---

### Post by stephenjbarr on 2007-12-23
I am seeing the same problem with intel 3945ABG. After applying the latest updates, I am no longer able to use wireless. If I boot into an old kernel, it works fine. But, my newest kernel (stock Gutsy 32-bit) is no longer able to use the wireless. It was working fine until just a few days ago, and the only thing I can think of that changed is the new updates.

---

### Post by ubutufan on 2007-12-23
having no information/details does not help.
Therefore based on symptoms described by you people, I suggest the following
Edit the file /etc/network/interfaces and make sure it has the following ONLY. NOTHING ELSE.

auto lo
iface lo inet loopback


Save the file & reboot.
Let us know if you can connect now

---

### Post by Havoc7592 on 2007-12-23
Sorry, I'm not sure what other details you're looking for.  I'm using Gutsy Gibbon and my Intel Pro/Wireless 3945 cannot connect to networks even though it can detect them.

If there is something else that would help to know, please let me know and I will do my best to answer it.

I checked the file, and it says exactly what you told me to enter.

Thanks for all the help.

Bryan

---

### Post by ubutufan on 2007-12-23
Thanks Bryan for responding.
If you are sure that the interfaces file contains nothing else other than those two lines (this is like virginizing the connections) then the problem may be the network manager.
I am also using this card and dealt with same issues in the past.
I switched over to another program for my connections, called Wicd. You may use it for wired and or wireless.
Information and download installation instructions you may find at
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

The feedback from my experience is that this soft would connect to all sorts of wireless networks regardless of encryption methods used.
If you decide to install it, you should know that it will automatically UNINSTALL the Network Manager and take over. Once installed you find it under Applications>Internet
Let me know

---

### Post by Havoc7592 on 2007-12-23
Sweet, thats something I haven't tried yet.  I'll give it a shot tomorrow and post how it goes.  Thanks for helping...this whole thing has been a headache.

Best Wishes,
Bryan

---

### Post by Edho on 2007-12-23
Just for your info...

Installed my router Netgear WRG614 two weeks ago.
Wireless + 4 wired-ports.

My wifi card is also Intel 3945. (in Asus notebook)

I configured the router :
-, Broadcaosting yes  (network visible)
-, WEP security.
-, no Mac-adress filtering.

On the pc-side i choosed "roaming mode".

So, i use the original networkmanager , installed by Gutsy.

Works fine.

During last two weeks i did all the updates, included new Kernel  ,... according updatemanager.

The wireless still works verry good.

---

### Post by real_optimus_prime on 2007-12-23
Even after installing Wicd Network manager, I was not able to connect. However, after trying for 15 minutes i got connected. After disconnecting  I was not able to connect, behavior is some how unpredictable. I saw the same problem with gnome network manager. I guess the problem is with the restricted linux driver package from intel. 

I guess time to get back to Ndiswrapper then :(.

---

### Post by aspie on 2007-12-24
I'm not sure if this is related.  But are you suspending/hiberating the laptop, or booting up from scratch?

I also have this card in my (ASUS) laptop.  It works fine, but if I hibernate and then resume it doesn't work.  I don´t believe this is a problem with the driver, as there are many reports of the hibernate issue in Gutsy.

---

### Post by SpacePilot on 2007-12-24
I have trouble with the kernel module itself. After a few hours it crashes randomly and I am not able to unload it from the kernel. Have to do a reboot to get it up and going again. This is very annoying and it's a problem that came with one of the updates.

---

### Post by Havoc7592 on 2007-12-25
So, I enabled broadcast...and everything works perfectly now.  So, I guess for all of you that are having problems...start there.  Thanks for all of the help everybody.

---

### Post by HIGHLIFE on 2007-12-25
> **SpacePilot said:**
> I have trouble with the kernel module itself. After a few hours it crashes randomly and I am not able to unload it from the kernel. Have to do a reboot to get it up and going again. This is very annoying and it's a problem that came with one of the updates.

Space Pilot I'm having the same problem.  It's terribly annoying.. Does anyone know how to fix this?

---

### Post by aspie on 2007-12-26
Well, mine is really playing up now. I'm sure it wasn't this bad when I first built the system.  So I guess it's possible that mine issues are down to the module too.  

Maybe I can just rollback some updates if I can work out how to do it.  I'll  try it and report back.

---

### Post by geonerd on 2007-12-27
> **ubutufan said:**
> Thanks Bryan for responding.
If you are sure that the interfaces file contains nothing else other than those two lines (this is like virginizing the connections) then the problem may be the network manager.
I am also using this card and dealt with same issues in the past.
I switched over to another program for my connections, called Wicd. You may use it for wired and or wireless.
Information and download installation instructions you may find at
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

The feedback from my experience is that this soft would connect to all sorts of wireless networks regardless of encryption methods used.
If you decide to install it, you should know that it will automatically UNINSTALL the Network Manager and take over. Once installed you find it under Applications>Internet
Let me know
Thank you for this post.  I have the same laptop as OP and the wicd works great.

---

### Post by real_optimus_prime on 2007-12-27
I uninstalled Wicd and reinstalled gnome-network-manager. Since, then wireless is behaving pretty fine. I have chosen roaming mode both for wired and wireless or u should have the following two lines in /etc/network/interfaces : 

auto lo
iface lo inet loopback

No I was not hibernating my laptop. I don't know where the problem lied but now I'm satisfied with the roaming mode. I see manual mode takes helluva time to obtain IP.

---

### Post by HIGHLIFE on 2008-01-01
I just wanted to let you guys know that I've been using wicd on my Dell 1520 with an intel 3945 for the past day and it seems to work much better then the network manager in terms of keeping my connection going (especially reconnection speed). I'll keep you guys posted, but right now it seems to be working much better than network manager.

---

