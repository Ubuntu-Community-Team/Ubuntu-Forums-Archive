---
title: "rdesktop vnc .... remote desktop control without locking"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by jeanlucmalet on 2010-03-04
Hi!
that's some times now that I seek for a tools that could help me show to some remote user (my mom) what she have to do when having this or that issue.
for this I tried first to use VNC so that I can control the remote laptop and see what she is doing.... the problem is that she has a slow band network connection and then remote control is simply unusable....
the Remote is on windows, I'm on linux
I tried with netmeeting, using a window laptop and it was usable.... I tried to remote control the linux with a local X11 server on the windows.... it was usable...
I tried with rdesktop it was also usable and I could login, but this cause the remote to get locked and then I can't say "look in such case you do like this and like that"....
ekiga don't support desktop sharing.... 
how can I fulfill my goal? it's lame that we can more easely take control of a remote linux using a window host than the reverse....
thanks in advance
JLM

---

### Post by Sef on 2010-03-04
Moved to ABT.

---

### Post by jeanlucmalet on 2010-03-04
Abt?

---

### Post by linuxman94 on 2010-03-04
**A**bosolute **B**eginner **T**alk

---

### Post by velle frak on 2010-03-04
Absolute Beginner Talk ;).

:edit: Linuxman, you beat me to it ;) .

Rdesktop uses the rdp protocol, and is in fact, like you said, a remote desktop tools (you log remote to a computer, so it gets locked to other users) and not a remote assistance tool, which is what you need.

In your case, I think VNC, or the remote desktop viewer using the VNC protocol is your best bet.

Try to reduce bandwidth use by reducing video quality.

Hope this helps.

---

### Post by jeanlucmalet on 2010-03-04
well... first time that I get a post moved into Absolute Beginner Talk after 5 years of use of linux and lot of SA stuff ;). 
I would like to know if there is a remote control application that use video like encoding (mpeg4 or h264) vnc use jpeg encoding and then is really inefficient in encoding changement (the bandwith is rather high compared to same resolution mpeg4 encoding)... so my idea is to use a codec like h264 to encode efficiently.... 
thanks and regards
JLM

---

### Post by bodhi.zazen on 2010-03-04
You can look at freeNX, although I do not know how they do the encoding.

---

### Post by 2hot6ft2 on 2010-03-04
> **bodhi.zazen said:**
> You can look at freeNX, although I do not know how they do the encoding.
I was about to say FreeNX. I was looking thru the node.conf file and I think what you want is shadowing. There are a lot of options and it's designed for slow connections.
[http://www.nomachine.com/products.php](http://www.nomachine.com/products.php)

And here's for more on their encoding (compression)
[http://en.wikipedia.org/wiki/NX_technology](http://en.wikipedia.org/wiki/NX_technology)

> #ENABLE_DESKTOP_SHARING=1

#
# General shadowing / mirroring notes:
#
# By default shadowing is only allowed for the same user.
#
# If nxserver finds nxshadowacl binary, it asks it, for which users 
# the permission is granted.
# 
# nxshadowacl <user>
# 
# Exit code:
#
# 0 -> Save cookie in session file for other users
# 1 -> Do not save cookie
#
# Check if user is allowed to be shadowed by admin user.
#
# nxshadowacl <user> <admin>
# 
# Exit code:
#
# 0 -> Yes, allow shadowing and add to list
# 1 -> No, don't allow shadowing
# 

#
# When using NX 3.0 shadowing, this enables asking the user whether
# he authorizes another user to shadow his session
#
# 0: No authorization request will be presented,
#    and the session will be shadowed as if the user had approved.
# 1: (default) Ask for authorization
#
#ENABLE_SESSION_SHADOWING_AUTHORIZATION=1

# Allow session shadowing in interactive mode:
#
# 1: The shadowing user can interact with the shadowed session.
#
# 0: The shadowed session is view-only. No interaction with the
#    shadowed session is possible.
#
#ENABLE_INTERACTIVE_SESSION_SHADOWING=1

I know I like it but I'm not working with a windows machine.

---

### Post by Paddy Landau on 2010-03-04
I don't know if you'd like [Yuuguu](http://www.yuuguu.com/).

---

### Post by 2hot6ft2 on 2010-03-04
Here you can look at a lot of the various remote desktop application  features.
[Comparison of remote desktop software]("http://en.wikipedia.org/wiki/Comparison_of_remote_desktop_software")

---

### Post by breley on 2010-03-05
> **bodhi.zazen said:**
> You can look at freeNX, although I do not know how they do the encoding.+1 for FreeNX.  Worked like a treat between my clients and  servers, even overly lowly PPTP VPN connections.

---

### Post by HermanAB on 2010-03-05
Your mom is running windows?  Configure rdesktop to use 16 colours and no background image.

---

### Post by asmoore82 on 2010-03-05
Use ultravnc server on the windows end and tightvnc/tigervnc on your end.
Tune it for low bandwith like this:
```
vncviewer -bgr233 -compresslevel 9 <your mama>
```

---

