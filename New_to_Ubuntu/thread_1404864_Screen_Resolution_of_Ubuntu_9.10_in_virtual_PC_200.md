---
title: "Screen Resolution of Ubuntu 9.10 in virtual PC 2007"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by mebuntwo on 2010-02-11
Well, I used to use linux heavily, but it's been a few years.  I just installed Ubuntu 9.10 in a Virtual PC 2007 box on my Windows Vista PC.

In ubuntu, I cannot get a screen resolution higher than 800x600.  My video card is NVIDIA GeForece G210 that comes with my HP P6180T desktop.  I have a 27" LCD HP monitor.

How can I get a higher resolution for my Ubuntu?  I searched and tried this:

[http://helpdeskgeek.com/virtualization/fixing-screen-size-resolution-in-virtual-pc-running-ubuntu/](http://helpdeskgeek.com/virtualization/fixing-screen-size-resolution-in-virtual-pc-running-ubuntu/)

But, after I created that xorg.conf file under /etc/X11, I can no longer boot to the prompt, I only get a Login: prompt on the top left corner.

I did Ctrl-Alt-F7, to no avail, I did Ctrl-Alt-F1 through F6, to no avail, and had to reinstall Ubuntu in my VPC.

Do any of you have an idea how I can increase the resolution of my ubuntu which is installed in VPC 2007?  Thank you!

---

### Post by QIII on 2010-02-12
If your virtualization software is anything like many others, you will have to consult the documentation for that software first.

Many of them have settings such as allowing variable resolution in the virtualization software itself before you can change it in the machine.  You will have to be sure that resizing is allowed there.

---

### Post by bronquel on 2010-02-12
i use virtual box to run ubuntu... i tried changing the resolution from ubuntu, and that would not work.  only recently did i realize to resize you just drag the window bigger or smaller.  usually a key sequence will give you full screen.  though for this to work you'll have to install the extras(guest additions) your virtualization software provides.

---

### Post by mebuntwo on 2010-02-12
> **bronquel said:**
> i use virtual box to run ubuntu... i tried changing the resolution from ubuntu, and that would not work.  only recently did i realize to resize you just drag the window bigger or smaller.  usually a key sequence will give you full screen.  though for this to work you'll have to install the extras(guest additions) your virtualization software provides.

Are you talking about the SP1 of VPC 2007?  I have installed it.  The VPC window is not draggable.  

It's hard to work with a resolution of only 800 x 600.  Any other ideas to share, people? Thanks.

---

### Post by mebuntwo on 2010-02-12
> **mebuntwo said:**
> Well, I used to use linux heavily, but it's been a few years.  I just installed Ubuntu 9.10 in a Virtual PC 2007 box on my Windows Vista PC.

In ubuntu, I cannot get a screen resolution higher than 800x600.  My video card is NVIDIA GeForece G210 that comes with my HP P6180T desktop.  I have a 27" LCD HP monitor.

How can I get a higher resolution for my Ubuntu?  I searched and tried this:

[http://helpdeskgeek.com/virtualization/fixing-screen-size-resolution-in-virtual-pc-running-ubuntu/](http://helpdeskgeek.com/virtualization/fixing-screen-size-resolution-in-virtual-pc-running-ubuntu/)

But, after I created that xorg.conf file under /etc/X11, I can no longer boot to the prompt, I only get a Login: prompt on the top left corner.

I did Ctrl-Alt-F7, to no avail, I did Ctrl-Alt-F1 through F6, to no avail, and had to reinstall Ubuntu in my VPC.

Do any of you have an idea how I can increase the resolution of my ubuntu which is installed in VPC 2007?  Thank you!

To make it clearer: Ubuntu does not boot to the GUI interface after I created the xorg.conf file following that link above.  It only shows me a Login prompt at the top left corner.  After I attempted to login with my user name and password, it seems to hang there, bcz the screen has a strip of greenish color horiontally across the screen, and thus I cannot read the output.  It seems to hang there and does nothing.

---

### Post by QIII on 2010-02-12
In the GRUB2 menu, do you have an option to boot into recovery mode?

---

### Post by mebuntwo on 2010-02-12
> **QIII said:**
> In the GRUB2 menu, do you have an option to boot into recovery mode?

Yes, if I do Ctrl-Alt-F1, but it still boots to the Login: prompt and wants me to repeat the same old, bad story.

---

### Post by QIII on 2010-02-12
You mean that you select recovery and then root, you are not dropped to a shell?

---

### Post by QIII on 2010-02-12
BTW -- before I forget to mention it -- your VM software probably has its own virtual video driver, so your physical video card's driver may not actually be used in the VM.

---

### Post by QIII on 2010-02-12
Sorry for the repeat messages...

I also went back to look at the URL.

Did you do a simple C&P of the text?

It looks like there are non-printable formatting characters (at least in my browser).

If you C&Ped, you may have some wacky stuff in xorg.conf

---

### Post by mebuntwo on 2010-02-12
> **QIII said:**
> You mean that you select recovery and then root, you are not dropped to a shell?

You are correct.

---

### Post by mebuntwo on 2010-02-12
> **QIII said:**
> BTW -- before I forget to mention it -- your VM software probably has its own virtual video driver, so your physical video card's driver may not actually be used in the VM.

I think you are correct, the VM has its own implementation of a virtual video card, but the sp1 of vpc 2007 claimed to have fixed the problem, in other words, with sp1 of vpc 2007, we should be able to have higher resolution, as far as i know.

---

### Post by mebuntwo on 2010-02-12
> **QIII said:**
> Sorry for the repeat messages...

I also went back to look at the URL.

Did you do a simple C&P of the text?

It looks like there are non-printable formatting characters (at least in my browser).

If you C&Ped, you may have some wacky stuff in xorg.conf

Yes, I was aware of those unprintable characters. But I took care to have cleared those. Any remnant garbage after my cleanup, maybe, I am not sure if this is the cause of the whole problem.

---

### Post by QIII on 2010-02-12
Do you get the blue screen with the gray box and the red highlighted choices when you get into recovery mode?

---

### Post by mebuntwo on 2010-02-12
> **QIII said:**
> Do you get the blue screen with the gray box and the red highlighted choices when you get into recovery mode?

Yes, I did after Ctrl-Alt-F1, I selected to boot in recovery mode, but it still brings me the same old Login: prompt and wants me to repeat the same old story.

---

### Post by QIII on 2010-02-12
I have to go back and earn my daily loaf of bread.

If you are able to get to the shell...

xorg.conf is not used by default in Karmic.  Other processes figure out what to do.  If you did not create an xorg.conf to try this, you can revert to the default mode.

I wouldn't get completely rid of what you have done at this point, since you may want to review what you have for some simple oversight.

If you can get to the shell, issue

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

That'll effectively return you to a state where you don't have an xorg.conf, you'll get the default behavior on startup and then you can look at the xorg.conf (now .bak) at your leisure.

I'll try to check in after work (as long as my wife's honey-do list isn't too long!)

---

### Post by QIII on 2010-02-12
Did you arrow down to root or webroot?

---

### Post by mebuntwo on 2010-02-12
> **QIII said:**
> I have to go back and earn my daily loaf of bread.

If you are able to get to the shell...

xorg.conf is not used by default in Karmic.  Other processes figure out what to do.  If you did not create an xorg.conf to try this, you can revert to the default mode.

I wouldn't get completely rid of what you have done at this point, since you may want to review what you have for some simple oversight.

If you can get to the shell, issue

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```That'll effectively return you to a state where you don't have an xorg.conf, you'll get the default behavior on startup and then you can look at the xorg.conf (now .bak) at your leisure.

I'll try to check in after work (as long as my wife's honey-do list isn't too long!)

Thank you. But, the problem is precisely that I can NOT get to the shell, no matter what I try.  If I can get to the shell, I am sure things will be a lot easier, because then I can play with the system.  But, the thing is, I am completely shut outside of the system.

---

### Post by mebuntwo on 2010-02-12
> **QIII said:**
> Did you arrow down to root or webroot?

Nope.  But anyway, I have re-installed Ubuntu, now the question is: How can I possibly get a resolution higher than 800 x 600, within the VPC host?  Thanks.

---

### Post by Scunizi on 2010-02-12
It's a conspiracy.. VirtualPC is a MS product and doesn't like Linux........ All kidding aside, if you're not married to VirtualPC switch to VirtualBox.. much easier and it "just works".  To get better resolution as someone mentioned, you have to intsall the vbox-guest additions.. This has to be done from cli.

---

### Post by QIII on 2010-02-12
For future reference, root or webroot would have gotten you there.

I ran across this ...  It seems the normal VM additions don't work with Linux.  It may be that when you install something like this, you will be able to get what you need.

I know that even in VirtualBox, you need to add Guest Additions to get the screen resolution you want (as well as seamless integration and such).



[http://www.microsoft.com/downloads/details.aspx?familyid=bf12642f-77dc-4d45-ae4e-e1b05e0a2674&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=bf12642f-77dc-4d45-ae4e-e1b05e0a2674&displaylang=en)

---

### Post by QIII on 2010-02-12
> **Scunizi said:**
> It's a conspiracy.. VirtualPC is a MS product and doesn't like Linux........ All kidding aside, if you're not married to VirtualPC switch to VirtualBox.. much easier and it "just works".  To get better resolution as someone mentioned, you have to intsall the vbox-guest additions.. This has to be done from cli.

I don't think the Guest Additions have to be installed from the terminal.  I haven't had to do that with any other flavors of Linux or with OpenSolaris.  (Unless the Windows version of VirtualBox works differently...)

+1 on VirtualBox.  

Just be sure that you install the full version, not VirtualBox OSE, or you will not be able to set up USB support.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by mebuntwo on 2010-02-12
> **QIII said:**
> For future reference, root or webroot would have gotten you there.

I ran across this ...  It seems the normal VM additions don't work with Linux.  It may be that when you install something like this, you will be able to get what you need.

I know that even in VirtualBox, you need to add Guest Additions to get the screen resolution you want (as well as seamless integration and such).



[http://www.microsoft.com/downloads/details.aspx?familyid=bf12642f-77dc-4d45-ae4e-e1b05e0a2674&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=bf12642f-77dc-4d45-ae4e-e1b05e0a2674&displaylang=en)

I'll definitely try out VirtualBox. Thanks for the note. I was looking into VMware, but it costs something and I gather it is not worthwhile to purchase it for just playing.

Looks like VirtualBox is Open Source, so, definitely gonna give it a shot.  

The Guest Addition is something that might need to be installed INSIDE the linux or INSIDE my Windows box?

---

### Post by QIII on 2010-02-12
> **mebuntwo said:**
> I'll definitely try out VirtualBox. Thanks for the note. I was looking into VMware, but it costs something and I gather it is not worthwhile to purchase it for just playing.

Looks like VirtualBox is Open Source, so, definitely gonna give it a shot.  

The Guest Addition is something that might need to be installed INSIDE the linux or INSIDE my Windows box?

The Guest Additions (an .iso file) have to be downloaded to your Windows machine (there should be instructions), and while you are running your VM that .iso is referenced in the VM software and you click install.  You don't need to "install" anything in Windows -- you install it through VirtualBox.

That's confusing.  You don't install it in Windows, nor in Ubuntu inside the VM.  You install it using the top menu in VirtualBox while you are pointed at the Ubuntu VM.

Ack.  Sorry.  There are instructions.

I'm old.  I forget stuff.

What was the question?  :)

---

