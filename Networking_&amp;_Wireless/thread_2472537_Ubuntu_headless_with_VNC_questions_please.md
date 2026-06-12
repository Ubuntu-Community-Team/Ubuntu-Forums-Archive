---
title: "Ubuntu headless with VNC questions please?"
date: 2022-03-02
forum: Networking &amp; Wireless
---

### Post by lord-basil on 2022-03-02
Newbie  running Ubuntu 20.04 minimal installation on a small form factor PC solely to  run some specialist amateur radio software. It's been set up with a  conventional monitor and a  wireless mouse and keyboard. 



I  have SSH working. I now what to run it headless 24 hours seven days a  week, but also want to be able to log into it in GUI mode on the wired  network it resides on, using VNC on  Windows 7 64 bit Pro PC's, the same  machines as I use Real VNC viewer on to log into various headless  Raspberry Pi's


What  flavour of VNC server should I install on the Ubunto PC in order to run  the Ubunto from my Windows 7 PC's running VNC please? 



What  do I need to do to run the Ubuntu PC headless, and ensure it stays up  24 / 7 with NOTHING going to sleep or into some sort of energy saving  mode please?


Thanks.

---

### Post by TheFu on 2022-03-02
You shouldn't use VNC.  VNC should have died long ago. There are much better options.

Sleep is an ACPI setting. There are many ways to setup that. I don't remember it ever being automatic. If you don't turn sleep/standby mode on, then it shouldn't ever happen unless you install some software that does that. 

There are many different ways to have a remote GUI from Windows into a Linux system.  99% of the time, you should use ssh, but sometimes, a GUI is handy. Sadly, MSFT doesn't include an X/Server, so you won't be using the best option, normal X/Windows. This is how Unix people do remote GUI programs for the last 30+ yrs.

Rather than VNC, use **x2go**. It is faster, more efficient, and much more secure, since it uses ssh tunnels from clients into the server.  The Windows client is very stable. I used it daily for months without any issues.  Install the x2go-server on the remote Ubuntu system, then install the x2go-client on Windows.   On Windows, you'll also want the font-package. That isn't needed for OSX or Linux x2go clients.

You do realize that Win7 lost support, so many things won't work ... or aren't guaranteed to work ... since nobody tests on Win7 for the last 2 yrs.

x2go is 2-3 times faster than RDP or VNC AND 100,000x more secure than both, since authentication uses ssh.  ssh is part of the NX protocol, which x2go is based on.  Trust me.  VNC is like night.  x2go is like daytime.
[https://wiki.x2go.org/doku.php/doc:installation:start](https://wiki.x2go.org/doku.php/doc:installation:start) has all the links and instructions.  Just add the PPA on Ubuntu. For Windows, you'll download 2 setup.exe files (client and the fonts).  Takes less than 5 minutes to setup if ssh is already working. 2 min on the remote "server" and, maybe, 3 minutes on the client-side.

Forget VNC.

When you finally move to a Linux workstation (rather than Windows), you can use X/Windows, which fully integrates local and remote GUI programs. You can't tell the difference.  BTW, running a remote X-client program also uses an ssh-tunnel, but it is more verbose on the network and doesn't work so great over the internet.  x2go is secure enough for use over the internet.

All of this is F/LOSS, so don't be concerned about "free" vs F/LOSS.  It's F/LOSS and that's a good thing.

---

### Post by him610 on 2022-03-02
++x2go

---

### Post by lord-basil on 2022-03-04
Thanks for the replies, I am afraid I have been unable to get x2go working. Why is it so complex? On Windows installing Real VNC is a two minute job, and foolproof, once run with default settings it just, err, works :) I am not concerned about the level of security, the PC will only be on my home network. The Raspberry PI OS makes using VNC simple, you just tick a box to enable it, and I don't want to install a different VNC on my Windows PC's just to talk to one headless one. Forgetting any security levels, can I install the same VNC as is integrated into the Rsspberry Pi Buster OS on this Ubuntu PC please? Thanks.

---

### Post by TheFu on 2022-03-04
> **lord-basil said:**
> Thanks for the replies, I am afraid I have been unable to get x2go working. Why is it so complex? 

VNC is harder. At least it was the last time I used it. It requires a server startup file with settings that are dependent on the DE.  The great thing about Linux is how flexible it is.  The bad thing about linux is that flexibility requires the ability to customize.  That's what is happening here, I believe.

x2go is easy, faster, and works on your platforms, _provided you don't use Gnome3 as the DE._  Gnome3 really wants direct GPU access and no remote desktops allow that. Performance will be terrible. Use **any** other DE, and x2go works great.

I've pointed a horse at the water hole, but only the horse can choose to drink. Good luck.  

If you'd like more help with x2go, provide more details than *it doesn't work.* There are 20+ different GUIs for Unix-like OSes, including Linux. Each of those have strengths and weaknesses.  Remote desktops don't know which DE/GUI you've installed, so they don't come with setups for each.  VNC is being used less and less and has some limitations that other methods don't have.  

Google found this related to VNC: [https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)  I don't know anything about that link, except that Ubuntu Community people created it and it hasn't been updated in 1.5 yrs.

---

### Post by lord-basil on 2022-03-04
Thanks, in the end I found this link,albeit for an earlier version of Ubuntu. It worked straight away and was easy to install following the clear instructions. All left at default settings gave a full screen capture. in the past when I had to use Linux attempts at a VNC set up usually resulted in "funny" screen sizes and fonts. I thought I'd see how Ubuntu handled adding an elderly laser printer, something else that was a nightmare when I last used Linux. It handled it with aplomb, although for this set up it isn't needed, but fair is fair, it seemed to go very smoothly with no messing about. Thanks again. 

This is the link I used to give a painless installation of RealVNC server, and my RealVNC viewers on various windows 7 64 bit PC's all connect fine. 

[https://www.zealfortechnology.com/2018/08/install-and-configure-realvnc-in-linux.html](https://www.zealfortechnology.com/2018/08/install-and-configure-realvnc-in-linux.html)

---

