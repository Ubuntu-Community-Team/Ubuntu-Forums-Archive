---
title: "VirtualBox Guest Additions Screw up my ability to take Screenshots HELP!"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by CuXe on 2010-07-09
So I am running Ubuntu 10.04 from a virtual machine using VirtualBox.  The problem I am having is that I can't take screenshots because all I get is a black image.

I upgraded all of my software through Synaptic thinking that the screenshot problem might have had something to do with outdated  files.

After the upgrade finished it seems like the Guest Addtions from Virtualbox got overwritten because after restarting I could no longer enter full screen mode.

I decided to take a screenshot (Prt SC) and voila! there was my screenshot.  Now when I re-installed the guest additions so that I could go fullscreen I am back in the hole once again! I can't take screenshots because all I get is one black image.

Any ideas? Any1?

---

### Post by cong06 on 2010-07-09
I'm a bit confused.
You have two computers, a host, and a virtual machine (vm). (the vm inside the host).

When you refer to taking screenshots, what are you taking screenshots of?
1) The host only? (ie: the vm isn't visible at all)
2) The host with the vm screen inside? (ie, you're using the vm, but use the host program to take a picture of it)
3) the vm only? (ie: you're using the vm and use vm programs to take the screenshot)

I should also mention that there's other programs that don't allow these kinds of screenshots (#2). If you're watching a movie with vlc (iirc) you get a blue screen when you take a screenshot.

---

### Post by CuXe on 2010-07-09
Hi, thanks for replying. This is my setup:

I have windows XP as a host and Ubuntu 10.04 is running inside of a virtual machine.

When I go fullscreen on my ubuntu virtual machine i want to be able to take a screenshot of the desktop however when I try to take a screenshot from ubuntu's Accessories > Take screenshot .. all I get is a black image, no screenshot was taken at all.

If i try to take a screenshot of the ubuntu virtual machine with virtualbox I also get the same result, just one black image.

The thing is that without virtualbox's guest additions I am able to take screenshots using ubuntu's Accessories > Take screenshot but when I install the guest additions (to take my ubuntu virtual machine fullscreen) I lose the ability to take screenshots within ubuntu.

I am not trying to take a screenshot from the host into ubuntus virtual machine, just a regular desktop screenshot using ubuntu. I hope that wasn't confusing :(

---

### Post by cong06 on 2010-07-09
> **CuXe said:**
> 
I am not trying to take a screenshot from the host into ubuntus virtual machine, just a regular desktop screenshot using ubuntu. I hope that wasn't confusing :(

Ok. That makes sense.

What if in Ubuntu you open up a terminal and type: "gnome-screenshot" Then click save.
mine looked like this:
```

isaac@server:~$ gnome-screenshot 
isaac@server:~$ 

```
Did you get any output between "gnome-screenshot" and the next "prompt" (ie: '$' sign)?

---

### Post by CuXe on 2010-07-09
When I type that in the terminal and press enter, the "Save Screenshot" window opens but the preview only shows a black image which is the same that has been happening until now :(

If I save that screenshot and go to the folder where I saved the image the result is the same, a black image, no screenshot.

---

### Post by cong06 on 2010-07-12
I'm not sure what to tell you.

What I'd suggest is you check out the virtualbox forum. The fact that you don't have problems with the guest additions uninstalled makes me think that it's going to be a virtualbox problem instead of an ubuntu problem.
That's not to say that someone else here knows the answer.
Virtualbox Forums: [http://forums.virtualbox.org/](http://forums.virtualbox.org/)

In anycase, if you find the answer, let us know. Someone else with your problem might stumble upon this thread...

---

### Post by CuXe on 2010-07-12
> **cong06 said:**
> I'm not sure what to tell you.

What I'd suggest is you check out the virtualbox forum. The fact that you don't have problems with the guest additions uninstalled makes me think that it's going to be a virtualbox problem instead of an ubuntu problem.
That's not to say that someone else here knows the answer.
Virtualbox Forums: [http://forums.virtualbox.org/](http://forums.virtualbox.org/)

In anycase, if you find the answer, let us know. Someone else with your problem might stumble upon this thread...

I sure will! Thanks for helping me out :)

---

### Post by diablo75 on 2010-07-12
Taking a screenshot in the VM with the Additions installed produced a black screenshot, but without, it works fine.  But you also mentioned trying to take one "With Virtualbox" and that produced the same results.  Have you tried taking a screenshot with Windows itself?  If your cursor is outside the VM, releasing control to the host, you should be able to take a screenshot in Windows by hitting the Printscreen button and then open an instance of mspaint and click Edit>Paste.  You might have already tried this but wanted to mention in case you hadn't.

Still, it looks like you've found a glitch with Vbox.

---

### Post by CuXe on 2010-07-12
It certainly sounds like some sort of bug or glitch or something, I just started a thread in Vbox's forum about it...

BTW That post about the 10 things to do after installing Ubuntu ROCKS! ... highly useful for noobs like myself :)

---

### Post by CuXe on 2010-07-12
OK.... Just got an answer from an admin at Vbox's forum and I quote:

> **Problem here is the 3D effects**. Once these are enabled, the screenshots _**will**_ be black. Disable Compiz (desktop effects) and you should be back in business. Disabling 3D in the VM settings is essentially the same.

I don't know how to disable compiz as a whole (without uninstalling the thing) so I went an disabled 3D acceleration from the virtual machine display tab and VOILA! I got my screenshot!  .. So as long as 3D is enabled on a virtual machine screenshots are a no-go.

---

