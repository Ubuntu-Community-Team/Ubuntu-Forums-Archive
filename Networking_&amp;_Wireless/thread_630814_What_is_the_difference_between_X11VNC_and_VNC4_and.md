---
title: "What is the difference between X11VNC and VNC4 and Vino?"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by xp_newbie on 2007-12-03
The scene of VNC here is incredibly confusing. :(

In my quest for a VNC solution that would work for login screen as well (what comes with Ubuntu Dapper 6.06, Vino, works only after the system has been logged ini), I found:

Posters that swear by vnc4 (vs. Vino: "Vino is slow and limited, etc.")

Poster that swear by x11vnc (vs. vnc4 : "vnc4 simply doesn't work in Gutsy").

As for myself, non of the HowTos that I found so far, provide a complete solution for my needs (logging in remotely from a Windows XP machine, running the free RealVNC 4).

I actually wasted quite a lot of time on implementing a HowTo that is based on Installing vnc4server and xinetd. The result was flaky and confusing remote operation (it would actually disconnect the client from network completely). So in my search for a different solution I came across other postings that confused me even more. Thus I have the following questions:

[LIST=1]
[*]Why does vnc4server need to be installed when there is already a VPN server running in the system (Vino)?
[*]Why isn't **System > Administration > Login Window >  Click on [Remote] Tab > Change style to "Same as Local" enough for remote login**? (it's not enough, I tried it).
[*]Is X11VNC newer or older than VNC4? Does 'X11' in its name imply that it ignores GNOME settings?
[/LIST]

These are my questons for now. I would appreciate any answer that could help me understand the subject (including a link to a good article).

Thanks,
Alex

---

### Post by xp_newbie on 2007-12-04
No one knows how to answer these questions? :confused:

---

### Post by krunge on 2007-12-04
Here is a general way to have x11vnc work for a login screen (i.e. nobody logged in yet):

[http://www.karlrunge.com/x11vnc/#faq-display-manager]("http://www.karlrunge.com/x11vnc/#faq-display-manager")

The location of the X setup script that you add the x11vnc line to depends alot on what distro and display manager (gdm, etc) you run (and can change from version to version).  The link gives some common names and locations. 

x11vnc doesn't know what "GNOME" or "KDE" are.   It just exports via VNC whatever is on the screen.  AFAIK, no distro or desktop has ever integrated x11vnc into one of their menus, etc.

---

### Post by reidkaufmann on 2008-03-05
> **xp_newbie said:**
> Why isn't **System > Administration > Login Window >  Click on [Remote] Tab > Change style to "Same as Local" enough for remote login**? (it's not enough, I tried it).

Enabling remote login with GDM doesn't refer to the VNC protocol.  It allows remote login using XDMCP protocol which I believe is an extension of the X protocol or closely related.  If you want to use this use to connect to your linux server/pc, use Xephyr from linux clients or Xming on Windows clients.

> **xp_newbie said:**
> Is X11VNC newer or older than VNC4? Does 'X11' in its name imply that it ignores GNOME settings?

I'm curious too.  I've used X11VNC before and it seemed pretty good, but I was only using on a low resolution (1024x768) display.  I've been using vino lately because it's conveniently integrated, but I've found that it makes the redraw from scrolling in gvim really slow when I've got a coworker sharing the desktop.  I don't know if that's because it's less efficient or because I'm running a higher resolution or because I'm using an old PCI graphics card for dual display...  In other words I'd like to know which is most efficient (in terms of client side refresh AND server side resource utilization), but I haven't done an apples to apples comparison.

---

