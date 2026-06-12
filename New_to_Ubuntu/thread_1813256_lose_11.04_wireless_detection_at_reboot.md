---
title: "lose 11.04 wireless detection at reboot"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by jplyons on 2011-07-27
Re: Ubuntu 11.04 install wireless detect problem

Hi,
I am still concerned about my broadcom bcm4311 802.11b/g wlan driver not
detecting my wireless router.

I have success when I do the following:

Remove these (below) using synaptic package manager.
b43-fwcutter
bcmwl-kernal-source
firmware-b43-installer

I then reboot.
I then re-install...
b43-fwcutter
bcmwl-kernal-source
firmware-b43-installer

I reboot again and wireless networks are detected. I just connect.
It works!

Then I shut down. When I reboot wireless networks are gone!
If I do the above steps all over again, wireless comes back.

I lose it every time I re-boot after a successful install.
What is happening? Is there a login script I need to modify?

Where is the 11.04 login script.

Thank you for any help. I cannot close this issue yet.
Joe

---

### Post by mikewhatever on 2011-07-27
The question has been answered two days ago in the original thread.
[http://ubuntuforums.org/showthread.php?t=1808815&page=2](http://ubuntuforums.org/showthread.php?t=1808815&page=2)

PS: What's the fascination with login scripts?

---

### Post by jplyons on 2011-07-28
Hi,

I'll try removing the STA thing.
Login script facination: I want to set environment path for
java, android sdk's as per instructions in an android book.
Don't know where to do it.

Thank you.
Joe

---

### Post by jplyons on 2011-07-28
Hi again,
All I have that is STA and seems relevant is 
broadcom-sta-common and brodcom-sta-source. Both of
these are in the list when I filter for BCM. However,
both uninstalled so there is nothing to remove.
Once again, thanks for your help.
Joe

---

