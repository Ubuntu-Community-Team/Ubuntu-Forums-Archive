---
title: "Support via Remote Desktop Control"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by brucewagner on 2010-02-26
Researching. What's the very best remote desktop viewer for Ubuntu? Commercial or otherwise? Not impressed with built-in one so far.... unless I'm doing something wrong.

---

### Post by kwacka on 2010-02-26
Just for viewing/accessing files one of the VNC (e.g. tightvnc).

For control Nomachine's NX system - see Freenx.

If you search here you'll find plenty of information on both.

---

### Post by bodhi.zazen on 2010-02-26
What is it you do not like ? That will help us advise you further.

---

### Post by brucewagner on 2010-02-26
Sorry.  I should have specified what problems we're having...

We are just starting a tech support business to help provide support for the "total novice" Ubuntu users....   (even more novice than ourselves, if you can believe that... ;) )

We are attempting to use the "Remote Desktop Viewer" and "Remote Desktop" which are built-in to Ubuntu 9.10 --- which appear to be, vinagre and vino-preferences   We're planning on supporting many users with this tool, and we don't want to pay some proprietary third-party company annual or monthly license fees to such an application.

We're having two issues with vinagre though:

(1)     Is there a simple simple solution to the NAT router / Port Forwarding issue...    One that would bypass the need to do custom port-forwarding on the user's router.   For example, I see this "Nat-to-Nat Connector add-on for uVNC"  (here [http://www.uvnc.com/addons/nat2nat.html](http://www.uvnc.com/addons/nat2nat.html) )    Is there something like this that would work with Vinagre which would automatically work through routers?

(2)     We notice that the viewer's screen is not updated when the remote desktop minimizes or moves a window.   Is there some compatibility issue(s) with running Desktop Effects and/or Compiz...?  If so, What exactly should we disable.... in order to make Vinagre work properly....?

(3)     Are "tightvnc" and "Nomachine's NX system (Freenx)" other, different, applications...?   

Which application is better at remote control... for remote support, remote training, etc.  Which is better at access through NAT routers?   Are Compiz or other "desktop effects" an issue at all?

Thanks SO much!

---

### Post by CharlesA on 2010-02-26
tightvnc is in the repos, but I believe you need to install FreeNX from the debs on their site.

As for configuring port forwarding, I know that VINO can do it as long as the router has UPnP functionality. Unfortunately, there are loads of security issues if you expose VNC to the internet.

I think the issue of the screen not updating is due to desktop effects being enabled. Could be wrong, but I seem to recall having similar problems when desktop effects were enabled.

---

### Post by doas777 on 2010-02-26
it sounds like you want to run it over the public internet, so no, without signifigant modification, the ubuntu vino implementation is not safe for this purpose.
I really like FreeNX but it does not allow you to share the same desktop session as the interactive user (so you can'[t move the mouse while they follow along.)

---

### Post by CharlesA on 2010-02-26
Same deal with TightVNC and the other VNC servers.

---

### Post by doas777 on 2010-02-26
> **CharlesA said:**
> 

I think the issue of the screen not updating is due to desktop effects being enabled. Could be wrong, but I seem to recall having similar problems when desktop effects were enabled.

this is likely the case. use teh -nodamage switch on vncviewer, or disable desktop effects to fix the screen updating. unfourtunatly --nodamage consumes much more bandwidth, since the entire screen is retransmitted with each motion.

---

### Post by brucewagner on 2010-02-27
Ok....  I got the built-in server ( vino-preferences ) and the built-in client ( vinagre ) to work over the public internet...

All I had to do was have my user plug their ethernet cable directly into the cable-modem... bypassing the router altogether.   This, and setting the server ( vino-preferences ) to "configure network automatically to accept connections"... and then closing that box.  Then, opening it again... to get the IP address from the user... allowed me to connect. 

And it worked even with the fancy animations and compiz stuff ON...  I could SEE the windows become wiggly when moved... and I could see them minimize with the animation, like a genie and a bottle...

Very cool.

---

