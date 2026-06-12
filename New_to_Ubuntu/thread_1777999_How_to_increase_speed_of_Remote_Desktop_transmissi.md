---
title: "How to increase speed of Remote Desktop transmission?"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by swarup on 2011-06-08
I am using Ubuntu 9.04 (I know its outdated, but works great!), and my colleague is using Ubuntu 10.10. When we connect via Remote Desktop and he is seeing my screen, there is a longer-than-expected delay in his receiving screen updates i.e. when I am typing. Not only is there a delay, but he receives the new screen in a ripple effect i.e. the new screen starts appearing at the top of his monitor, and progressively takes over the previous screen like a wave coming in from the ocean. Are there any settings where we can make the transmission quicker or at least get rid of the ripple effect? He says the ripple effect has only started since we upgraded his Ubuntu from 10.04 to 10.10 around a week ago.

We are both connected via hard-wire ethernet, to a Cradlepoint mobile router which gets its outside signal via Sprint mobile broadband USB modem u720. The signal between the two computers is I'm pretty sure unrelated to the modem; our communication would be relayed directly from one computer to the other via the router.

---

### Post by crispy_420 on 2011-06-11
Are you connecting via the default "Remote Desktop Viewer" under Applications/Internet using the VNC protocol?

If so before the remote user connects don't just click the available host shown. Select "Connect" up top and a new window will open. Select VNC and near the bottom change the color depth "High Color (16 bits)". This will lessen the amount of data needed to be transmitted so it may improve the perceived lag time.

This would be a good start but there may also be other network related causes such as other users and their bandwidth utilization.

---

