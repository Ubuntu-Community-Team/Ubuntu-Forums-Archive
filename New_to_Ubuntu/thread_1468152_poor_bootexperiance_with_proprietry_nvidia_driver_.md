---
title: "poor bootexperiance with proprietry nvidia driver (lucid)"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by hellomoto on 2010-05-01
Ok i've noticed a few threads with people having problems using the proprietary nvidia drivers and the following problems:

1, low resolution plymouth splash whilst booting (know problem)
2, issues after login in (GDM):
either long time to resolve the desktop, failing to initialize the nvidia graphics driver or gettin a blank screen for a long period before getting an active desktop.


I think a lot of these problems maybe interlinked so I have started this thread to invite anyone with the above problems to discuss possible solutions.

 Does anyone think installing the nvidia drivers manually will help: [http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")

Dino99 suggests the following: > **dino99 said:**
> on top panel, goto system --> admin --> synaptic and search for nvidia

you might have these packages installed:

- nvidia-current
- nvidia-common
- nvidia-current-modaliases

as lucid dont need xorg.conf by default, into console run:

sudo rm -f /etc/X11/xorg.conf

reboot

then goto system --> admin --> hardware driver, to see if nvidia-current is activated, you should have now your full resolution.

I followed instructions to fix the low resolution splash here:
[http://ubuntuforums.org/showthread.php?t=1451820]("http://ubuntuforums.org/showthread.php?t=1451820")

Further references to these problems can be found here:

[http://ubuntuforums.org/showthread.php?t=1466150&highlight=low+res+nvidia]("http://ubuntuforums.org/showthread.php?t=1466150&highlight=low+res+nvidia")
[http://ubuntuforums.org/showthread.php?t=1467837&highlight=lucid+nvidia]("http://ubuntuforums.org/showthread.php?t=1467837&highlight=lucid+nvidia")
[http://ubuntuforums.org/showthread.php?t=1467725&highlight=lucid+nvidia]("http://ubuntuforums.org/showthread.php?t=1467725&highlight=lucid+nvidia")
[http://ubuntuforums.org/showthread.php?t=1465793&highlight=low+res+nvidia]("http://ubuntuforums.org/showthread.php?t=1465793&highlight=low+res+nvidia")
[http://ubuntuforums.org/showthread.php?t=1463294&highlight=lucid+nvidia]("http://ubuntuforums.org/showthread.php?t=1463294&highlight=lucid+nvidia")
[http://ubuntuforums.org/showthread.php?t=1467379&highlight=lucid+nvidia]("http://ubuntuforums.org/showthread.php?t=1467379&highlight=lucid+nvidia")

Hope this helps and I invite anyone's possible solutions.

---

### Post by clhsharky on 2010-05-01
HI hellomoto

Good idea, hope it help many.

Sharky

---

### Post by ankit singh on 2010-05-01
what is solution for the issues after logging -long time it takes for the panel to appear on the surface.

---

### Post by sadaruwan12 on 2010-05-01
A very good Idea might help people at Canonical to find a better solution quickly.

---

### Post by hellomoto on 2010-05-01
> **ankit singh said:**
> what is solution for the issues after logging -long time it takes for the panel to appear on the surface.

I'm not sure, I've been through reams of system logs to no avail. 

I have tried manually install the latest nvidia driver - didn't solve the issue.

I have tried disabling all default start up programs - didn't solve the issue. 

I would be interested if anyone else gets the following error in there system.log as this seams were my box is taking loads of time to initialize the desktop. 

```

May 1 17:23:31 mark-desktop gdm-session-worker[1206]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

May  1 17:23:48 mark-desktop gdm-session-worker[1321]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory

May  1 17:23:48 mark-desktop gdm-session-worker[1321]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

```

As you can see my system messes around for 17 seconds here at start up at GDM login and I wonder if anyone else has the same problem.

---

### Post by ankit singh on 2010-05-01
> **hellomoto said:**
> I'm not sure, I've been through reams of system logs to no avail. 

I have tried manually install the latest nvidia driver - didn't solve the issue.

I have tried disabling all default start up programs - didn't solve the issue. 

I would be interested if anyone else gets the following error in there system.log as this seams were my box is taking loads of time to initialize the desktop. 

```

May 1 17:23:31 mark-desktop gdm-session-worker[1206]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

May  1 17:23:48 mark-desktop gdm-session-worker[1321]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory

May  1 17:23:48 mark-desktop gdm-session-worker[1321]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed

```As you can see my system messes around for 17 seconds here at start up at GDM login and I wonder if anyone else has the same problem.


yeah i also have the same problem

---

### Post by chemtut on 2010-05-01
+1 here

---

### Post by ankit singh on 2010-05-01
Its a bug which reappeared in lucid

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/500377](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/500377)

---

### Post by hellomoto on 2010-05-01
ok, can you all tell me what experiences you are getting with the above error. Has anyone looked to see if there is a bug for this on launchpad?

__________________________

Opps ^^^^^ to late, ok thank you.

---

### Post by ankit singh on 2010-05-01
Even my system messes for around 15-20 sec. Googling had different results.
Some said that its a bug in nvidia driver, some sites report as nvidia driver not compatible with x.org 7.5,i don't know ,lucid has sucked my mind. Within a span of hour i rebooted my pc 10 times. All experiments giving no results.

---

### Post by peterpan7191 on 2010-05-01
another prob.
compiz in my laptop is not starting at startup after the upgrade (4m 9.10)
need to do compiz --replace everytime ... :(    (cannot add into startup items due to other reasons)
ny wrk arounds or similar probs ???

---

### Post by ankit singh on 2010-05-01
Its looks like ubuntu in every release takes one step ahead and goes 5 step behind. I think they should concentrate for 1 new distribution per year. Will wait for this problems to get resolved for couple of days,otherwise i will again move to karmic.Bad release for nvidia users.Lucid sucked my brain,having a great headache now,28times different exp,28 times reboot, in just 2 hrs.

---

### Post by hellomoto on 2010-05-01
it hasn't been the best upgrade for me either.

all went flawlessly on my laptop with onboard graphics but my desktop with a nvidia graphics card, not so good.

I have however got lucid installed twice on the desktop now, 1 partition for testing. 1 for using day to day.

I will keep working at the above issue in my free time, anyone else please feel free to contribute any possible solutions.

---

### Post by jejones3141 on 2010-05-02
After upgrading from Karmic to Lucid, the proprietary nvidia driver fails to start up. From the xorg log:

[INDENT](EE) May 02 11:31:30 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) May 02 11:31:30 NVIDIA(0):     system's kernel log for additional error messages and
(EE) May 02 11:31:30 NVIDIA(0):     consult the NVIDIA README for details.[/INDENT]

and sure enough, the kernel log shows

[INDENT]API mismatch: the client has the version 195.36.15, but this kernel module has the version 190.53.
[/INDENT]

Looking in synaptic, the "current" nvidia driver is 195.36.15, but I don't see a "nvidia-current-kernel-source" or even a "nvidia-195-kernel-source" package. Without that, how can the 195.36.15 driver work?

Come to think of it, the version of libvdpau1 I see under synaptic (and installed, despite having upgraded to Lucid) is 0.4.2~karmic~nvidiavdpauppa4 (?!). Should I remove that?

UPDATE: Problem solved, somehow. I booted to a Live CD to compare repository contents and see just what got pulled in when installing nvidia-current. Took notes and then rebooted to my system as updated... and suddenly it all just worked! I wish it hadn't taken this long--I'd rebooted before, but to no avail--but I'm happy now.

---

### Post by ankit singh on 2010-05-02
yes u should remove that.Latest version is 0.4-3~lucid-...

talking about nvidia
Any one out there pls help

---

### Post by jejones3141 on 2010-05-02
(slaps forehead) Oh, yeah... that's from a repository the upgrade disabled. Thanks.

---

### Post by hellomoto on 2010-05-02
> **ankit singh said:**
> yes u should remove that.Latest version is 0.4-3~lucid-...

talking about nvidia
Any one out there pls help

still no more progress, sorry

---

### Post by ghost1k on 2010-05-02
Hello, guys. I'm using the latest driver from nvidia website (195.36.24).
Here is my solution: [http://lushchick.blogspot.com/2010/05/lucid-lynx-and-nvidia-video-cards.html](http://lushchick.blogspot.com/2010/05/lucid-lynx-and-nvidia-video-cards.html)
Good luck!

---

### Post by ankit singh on 2010-05-02
this is not the soln, no issues with nvidia,issues is with the system taking too much time to load desktop(after logging in)

---

### Post by Baltuki on 2010-05-03
Hi all,

I had the same problem, booting tooks about 20 sec. (after plymouth load) with a black screen and the mouse pointer.

I solved this disabling the floppy in the BIOS. I have no floppy but the system was looking for one.

Now it works flawlessly.

---

### Post by ankit singh on 2010-05-03
That solves mine,thanks.

---

### Post by hellomoto on 2010-05-03
> **Baltuki said:**
> Hi all,

I had the same problem, booting tooks about 20 sec. (after plymouth load) with a black screen and the mouse pointer.

I solved this disabling the floppy in the BIOS. I have no floppy but the system was looking for one.

Now it works flawlessly.

This has solved my issue too. Thank you so so much. For my own learning and others what did you check to find that the system was looking for a floppy disk? If it was a log please could you post the output for other people.

If this doesn't work for other people that are having problems with the nvidia driver, I do have another suggestion, try out fedora 13 that is soon out for release. This also uses plymouth but you may get an different boot experience? Fedora 13 will also be utilizing the Open 3D accelerated nvidia driver.

Although this thread will now be marked as solved I hope that it will still remain active for people suffering with a poor boot experiance.

Once again, thank you Baltuki for your solution.

---

### Post by lilbill on 2010-05-07
If you're having the slow boot problems because of floppy this refers to the following [bug]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/539515").

---

