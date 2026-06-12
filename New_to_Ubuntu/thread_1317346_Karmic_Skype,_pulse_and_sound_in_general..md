---
title: "Karmic: Skype, pulse and sound in general."
date: 2009-11-06
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-11-06
Just upgraded to Karmic an hour ago.

Mostly things are fine, but I find everything related to "sound" a mess.

Firstly, skype works but is slow and after making a call for about 30s my CPU usage goes up to 100%. The culprit is pulse as   also goes up quite high. I had this problem in jaunty as well. I removed pulse completely and installed alsa to solve the issue. However, I don't think thats feasible any longer since pulse has been completely integrated.

Secondly, the way you can control individual sounds is a bit problematic (for me at least). All apps start off with their sounds at full blast and ideally I'd like them at the medium level. Is it possible to set that? (i.e. preempt all the apps launching at a really loud volume).

My speakers are still hissing when I turn my volume up (a problem not there when I plug my speakers into my iPod).

The most pressing issue is Skype. If that can't be fixed I may have to downgrade.

Thanks!

---

### Post by abhiroopb on 2009-11-10
The problem with skype I have sort of solved as I now updated to the latest version of skype (2.1.0.7) that seems to support pulse.

I say "seems to" as it still has a number of problems.

1. It connects the call fine and I can talk without high CPU usage. However, after the first call finishes and I want to make a second call I won't be able to hear anything and the person I will be talking with won't be able to hear anything.

2. Exiting skype becomes a problem and I need to kill the process.

3. Now if I want to check my sound settings and I right click on the volume icon and click "sound preferences", I get the following error: "Waiting for sound devices".

The only way to "solve" this is basically to wait for about 2-3 minutes and then restart skype (obviously not ideal).

Any help?

---

### Post by camaron1 on 2009-11-11
[PHP]I don't think thats feasible any longer since pulse has been completely integrated[/PHP]
I removed pulseaudio with no issues and sound works fine for me. If you do this, you can install gnome alsa mixer to control volume.

---

### Post by Primefalcon on 2009-11-11
> **camaron1 said:**
> [PHP]I don't think thats feasible any longer since pulse has been completely integrated[/PHP]
I removed pulseaudio with no issues and sound works fine for me. If you do this, you can install gnome alsa mixer to control volume.
I solved the issue myself I uninstalled skype from ubuntu, went here

[http://packages.medibuntu.org/jaunty/index.html](http://packages.medibuntu.org/jaunty/index.html)

download and install in this order skype-common, then skype

go into synaptic and lock them by right clicking and then electing lock from the menu, that stop them from being upgraded.

yes it's a jaunty package but it works fine in karmic, just make sure you remove both skype and skype common before you do this as well as any other skype packages you may find

---

### Post by abhiroopb on 2009-11-11
> **Primefalcon said:**
> I solved the issue myself I uninstalled skype from ubuntu, went here

[http://packages.medibuntu.org/jaunty/index.html](http://packages.medibuntu.org/jaunty/index.html)

download and install in this order skype-common, then skype

go into synaptic and lock them by right clicking and then electing lock from the menu, that stop them from being upgraded.

yes it's a jaunty package but it works fine in karmic, just make sure you remove both skype and skype common before you do this as well as any other skype packages you may find


Did you do this with Pulse or did you remove pulse and use alsa and then do this?

The jaunty packages for skype (i.e. 2.0.0.74) don't support pulse and are one of the reasons that skype's CPU usage reaches a 100%. Using the old package with skype does not work at all. The newer package (also from medibuntu repository) allows you to use pulse, however, the problems I mentioned above still occur.

---

### Post by abhiroopb on 2009-12-03
Although I have gotten skype working, my sound still snaps, crackles and pops (and occasionally hisses as well).

I would like to try getting rid of pulse or at least disabling it.

The latest skype works well enough but my CPU usage still spikes. 

I also have a decent speakers which work fine with my iPod but sound terrible when connected to my computer (all .mp3 files are >192kbps).

---

