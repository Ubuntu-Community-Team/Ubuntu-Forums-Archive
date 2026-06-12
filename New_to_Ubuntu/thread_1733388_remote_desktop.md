---
title: "remote desktop"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by Sleven7 on 2011-04-19
I need to know how to set up my desktop at the house and be able to access it from another location.  I'm going out of town this Friday and would like to be able to log on.  Not sure of the particulars on how to do this.  I have another machine that is running Mint 9 at the house on a separate ISP so I thought I could work it out local before I have to leave.

I'm running Ubuntu 10.04 on the machine I need to access.

Can it be accessed from a Windows machine?
If not, would a live DVD of Ubuntu work?

---

### Post by Locke_99GS on 2011-04-19
You can use VNC.

**System -> Preference -> Remote Desktop**
Configure your settings here.

To do this from out of town, you might want to forward port 5900 in your router, though I would highly recommend tunneling over SSH when outside of your home-network. (port 22)

Yes, Windows can access a Linux VNC. You'll need the appropriate software. You might try TightVNC as it is the only thing that pops in my head, and I'm not entirely sure it works in Windows. I'm sure Google will let you know of VNC clients for Windows.

---

### Post by seawolf167 on 2011-04-19
> **Locke_99GS said:**
> You might try TightVNC as it is the only thing that pops in my head, and I'm not entirely sure it works in Windows.

My VNC viewer of choice on a Windows box is [UltraVNC]("http://www.uvnc.com/download/1082/"), the current viewer can be downloaded [here]("http://www.uvnc.com/download/1082/1082viewer.html")

You'll also need to know your WAN IP address, and since you most likely have a dynamic IP address, you should take a look at [NoIP]("http://www.no-ip.com/"). I use it on my various boxes so the IP is automatically updated to a DNS which is very easy to remember (versus a constantly changing IP address)

---

