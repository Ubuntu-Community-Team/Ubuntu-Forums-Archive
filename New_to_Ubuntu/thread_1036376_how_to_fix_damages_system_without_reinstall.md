---
title: "how to fix damages system without reinstall ?"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Wilbur Kelly on 2009-01-10
I had an 8.10 that I installed about 2 weeks ago and it was working well. I removed some packages and have seriously damaged it. I was trying to fix the fact that my NVIDIA wasn't working but that is not my focus now. I want to "goback" to my predamaged system.

Before this I installed remastersys and made a "backup" LiveCD of the working system. That liveCD boots my previouus system so it has the files to do so. I don't know what those files would be but my thought is that I could copy them off the liveCD once it is booted up onto a USB drive and then bootup my damaged system and cp them onto my damaged system.

The system I have now was booting into runlevel 3 and somehow (from a book) I managed to get to the graphic screen. I am concerned that when I reboot I may be back to where I was, and even if I get to the graphic screen (Gnome) it is still very damaged. I have lost system=>administration=>hardware drivers. I have lost my speaker at the top of the screen because the file it points to, gsomehting, isn't there. So IF I could restore the previous files I could resurrect the system.

Can it be done?

Thanks,
Wilbur Kelly
Wilbur Kelly is online now Report Post   	Edit/Delete Message

---

### Post by BGFG on 2009-01-10
It sounds like you may have removed some Gnome-desktop components. If you can get into the desktop session you can try:
```

sudo apt-get install ubuntu-desktop

```
but if not, you can try the same command in the failsafe session. When you get the login screen, at the bottom left select session options and select the failsafe.

---

### Post by Wilbur Kelly on 2009-01-10
> **BGFG said:**
> It sounds like you may have removed some Gnome-desktop components. If you can get into the desktop session you can try:
```

sudo apt-get install ubuntu-desktop

```
but if not, you can try the same command in the failsafe session. When you get the login screen, at the bottom left select session options and select the failsafe.

I did "sudo apt-get install ubuntu-desktop" and it came back that that package could not be located.  So, using synaptics, I installed ubuntu-desktop and now the speaker is working again.  I still don't have hardware drivers under system=>administrator=>hardware drivers...

I appreciate your help and am glad to have the speaker working again.  I have been using synaptics to reinstall things trying to get NVIDIA working and I am sure uninstalled more things than I should have.  Since there should be a working setup in remastersys would that be the quickest way to get back to where I was before I got carried away with synaptic uninstalls...?

---

### Post by Papa-san on 2009-01-10
> **Wilbur Kelly said:**
> I did "sudo apt-get install ubuntu-desktop" and it came back that that package could not be located.  So, using synaptics, I installed ubuntu-desktop and now the speaker is working again.  I still don't have hardware drivers under system=>administrator=>hardware drivers...

I appreciate your help and am glad to have the speaker working again.  I have been using synaptics to reinstall things trying to get NVIDIA working and I am sure uninstalled more things than I should have.  Since there should be a working setup in remastersys would that be the quickest way to get back to where I was before I got carried away with synaptic uninstalls...?
You will only get something there if you need proprietary drivers. Did you have any in use before? I don't think I needed any Nvidea drivers, and I know I use their vid card.

---

### Post by Wilbur Kelly on 2009-01-10
I have tried with both the proprietary and various changes via synaptics (some of which, made in haste got me into this problem) to try to get NVIDIA working (GeForce 6150 le) which I did not succede in.  That is not the problem I am working on now, but remains a prolem I want to solve.  Interesting thing is that just after installing, the first time, I went to some web page titled something like: 12 things to do after installing 8.10 and following the instrucitons was able to use the card to go to applications=>visual effects=>extra and get a high resolution and the "extra effects" but something I undoubtedly changed left me at a low resolution and I have not been able to get it working again despite a lot of trial and error.  That is one problem I intend to work on later, but I don't want to change the question yet, of how to restore my system to it's former state.  Thanks.

---

