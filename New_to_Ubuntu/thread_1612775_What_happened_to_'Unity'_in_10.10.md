---
title: "What happened to 'Unity' in 10.10????"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-11-03
Hello:

Previously, I downloaded and installed ubuntu netbook 10.04 in VirtualBox.

It had this great desktop, as I later found out, called 'Unity'.

When I did the same for ubuntu netbook 10.10, 'Unity' is gone and the standard desktop has taken its place.

How do I get 'Unity'?

Thanks,

---

### Post by cariboo on 2010-11-03
Log out and go to the sessions menu and select the netbook session.

---

### Post by Robert.Thompson on 2010-11-04
> **cariboo907 said:**
> Log out and go to the sessions menu and select the netbook session.

Nope, tried that before.

Re-downloaded & re-installed in VirtualBox and got this error msg at startup:

   "No required driver detected for Unity"

Shouldn't the Unity driver be included in the netbook download?

Where do I get this elusive driver and how do I install it?

If this happens to 'new users' they will never even know about the Unity desktop - what a shame...

---

### Post by Zzl1xndd on 2010-11-04
If I remember correctly 10.04 NBR didn't use Unity. I believe Unity was introduced with 10.10. 

That being said Unity requires Compiz and I don't believe that Virtual Box has support for 3d Acceleration so that maybe the issue.

---

### Post by Merk42 on 2010-11-04
> **tweakedenigma said:**
> If I remember correctly 10.04 NBR didn't use Unity. I believe Unity was introduced with 10.10. 

That being said Unity requires Compiz and I don't believe that Virtual Box has support for 3d Acceleration so that maybe the issue.
This but a little different

Unity didn't come until 10.10, that is true, but it requires MUTTER (not compiz) which isn't compatible with Virtualbox.
The desktop version of 11.04 that uses compiz should be with Virtualbox Additions installed.

---

### Post by Robert.Thompson on 2010-11-04
> **tweakedenigma said:**
> If I remember correctly 10.04 NBR didn't use Unity. I believe Unity was introduced with 10.10. 

That being said Unity requires Compiz and I don't believe that Virtual Box has support for 3d Acceleration so that maybe the issue.

What desktop was used in 10.04 NBR?

I just loved it. It worked perfectly in Virtual Box.

Where can I get 10.04 NBR?

Thanks for any help,

---

### Post by Zzl1xndd on 2010-11-04
> **Merk42 said:**
> This but a little different

Unity didn't come until 10.10, that is true, but it requires MUTTER (not compiz) which isn't compatible with Virtualbox.
The desktop version of 11.04 that uses compiz should be with Virtualbox Additions installed.

Thanks for the Clarification. Didn't realize that the 10.10 version was using Mutter (had just seen 11.04 would be using Compiz).

---

### Post by CharlesA on 2010-11-04
> **Robert.Thompson said:**
> What desktop was used in 10.04 NBR?

I just loved it. It worked perfectly in Virtual Box.

Where can I get 10.04 NBR?

Thanks for any help,

It was just called "netbook launcher" or something like that.

You can find the ISOs here: [http://releases.ubuntu.com/10.04/](http://releases.ubuntu.com/10.04/)

---

### Post by Robert.Thompson on 2010-11-04
> **CharlesA said:**
> It was just called "netbook launcher" or something like that.

You can find the ISOs here: [http://releases.ubuntu.com/10.04/](http://releases.ubuntu.com/10.04/)

Thank you! 10.04 NBR is now living happily in a Virtual Box on my laptop.:)

Just two questions:

If the install for 10.10 NBR says that I am missing the Unity driver, is everyone?

If the Unity desktop doesn't install, why is it included in the Live CD installation?

---

### Post by Zzl1xndd on 2010-11-04
> **Robert.Thompson said:**
> 

If the install for 10.10 NBR says that I am missing the Unity driver, is everyone?

If the Unity desktop doesn't install, why is it included in the Live CD installation?

I believe that its VirutalBoxes video driver that doesn't support it. 

Unity works fine when I install it on my desktop.

---

### Post by CharlesA on 2010-11-04
> **tweakedenigma said:**
> I believe that its VirutalBoxes video driver that doesn't support it. 

Unity works fine when I install it on my desktop.

^ That's why. Same reason why Aero in Win Vista/7 doesn't work in VBox.

---

### Post by Robert.Thompson on 2010-11-04
> **tweakedenigma said:**
> I believe that its VirutalBoxes video driver that doesn't support it. 

Unity works fine when I install it on my desktop.

Got it!

I apologize for my confusion. (concerning the Virtual Box aspect)

---

