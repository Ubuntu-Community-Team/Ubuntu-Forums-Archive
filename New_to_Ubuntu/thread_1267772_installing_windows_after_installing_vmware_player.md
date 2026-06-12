---
title: "installing windows after installing vmware player"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by canam101 on 2009-09-16
I posted the question below in the how-to section but got no response. I have had good luck here and thought I would try again.

Re: HOWTO: VMWare Player / Windows XP / Ubuntu Repositories 
Thanks for an excellent tutorial. I have the player installed, but have not yet installed windows xp. You say:

Run VMWare Player and Install your OS
Code:
vmplayer ~/vmware/WindowsXPPro.vmx


I can run the player, but how do I install windows xp?

If I put the windows xp disk in my cd drive and click on setup.exe, will that somehow create WindowsXP.vmdk, because that seems to be what vmplayer wants?

Or do I have vmplayer browse to the CD, and do something?

Or what?

I know this is probably so obvious that it didn't seem necessary to spell it out, but some of us don't get it unless it is spelt out.

Thanks

---

### Post by Mike_IronFist on 2009-09-16
> **canam101 said:**
> I posted the question below in the how-to section but got no response. I have had good luck here and thought I would try again.

Re: HOWTO: VMWare Player / Windows XP / Ubuntu Repositories 
Thanks for an excellent tutorial. I have the player installed, but have not yet installed windows xp. You say:

Run VMWare Player and Install your OS
Code:
vmplayer ~/vmware/WindowsXPPro.vmx


I can run the player, but how do I install windows xp?

If I put the windows xp disk in my cd drive and click on setup.exe, will that somehow create WindowsXP.vmdk, because that seems to be what vmplayer wants?

Or do I have vmplayer browse to the CD, and do something?

Or what?

I know this is probably so obvious that it didn't seem necessary to spell it out, but some of us don't get it unless it is spelt out.

Thanks

Hi. VMware Player is supposed to be able to "Mount the host CD drive" (that is your real computer's CD drive), which would allow it to detect the CD and install Windows XP. However, I don't think VMware player allows full installation of OSes. It's only made for using virtual harddrive images that have already been created, hence "player".

Instead, I recommend installing and using Virtualbox. You can get it from Add/Remove, and it works splendidly. It's also way more user friendly than any VMware product.

---

### Post by canam101 on 2009-09-16
Thanks very much for that tip. I removed vmware and pretty easily installed virtualbox - very nice gui.

I now have windows installed within linux. The only problem so far is that I do not see any usb support. I found a note somewhere that it only exists with the 'closed source' version.

Is that right, or did I overlook something in setting it up? Nothing about usb when I do a 'virtualbox usb' search of the repository.

It isn't much use without the usb since there are a couple of windows applications that use the usb connection that I would like to run using virtualbox.

---

### Post by canam101 on 2009-09-16
Ah, I see. I got off my duff and did a search for 'virtualbox usb' and found a post which mentions that you have to download the version from virtualbox.org. I'm doing that now and will report when I get it running.

Thanks again for your help.

---

### Post by Mike_IronFist on 2009-09-17
> **canam101 said:**
> Ah, I see. I got off my duff and did a search for 'virtualbox usb' and found a post which mentions that you have to download the version from virtualbox.org. I'm doing that now and will report when I get it running.

Thanks again for your help.

No problem. Just remember, Virtualization isn't flawless, so expect the possibility of issues with USB devices on virtual machines.

---

