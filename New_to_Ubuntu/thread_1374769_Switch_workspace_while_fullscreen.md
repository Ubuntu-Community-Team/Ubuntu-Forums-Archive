---
title: "Switch workspace while fullscreen"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by okey666 on 2010-01-07
If I am using an application full screen, I cannot use ctrl-atl-left arrow etc. to switch workspace. Is there some way to do this?

For example, when I am using virtual box full screen, I would like to leave it full screen on one workspace, while I switch to another to do quickly do something else. The same goes for using alt-tab. I am using compiz.

Can anyone help?

---

### Post by theDaveTheRave on 2010-01-07
Okey666,

I don't have a problem using the keyboard shortcut you mention when I have a window on full scree....

However check out that you have the keyboard shortcuts correctly in

I also have shortcuts to jump to any any of my 6 desktops (I choose 6 as otherwise things begin to complicated, and I can't remember where certain windows are!). Maybee that will solve your problem also?

Also if you like working in fullscreen mode, you may be interested in a 'tiling window manager'. which automatically fills your screen with all your open windows, and allows you to alter their configuration on screen, on the fly - none of that altering the size of stuff nonsense.

David

---

### Post by arubislander on 2010-01-07
The problem has been misdiagnosed by the OP. The behavior mentioned is only exhibited when using Virtualbox in full-screen mode. The solution is however simple. Just press the Host key and the keyboard will be un-captured and all key presses will revert to the host system. Try pressing CTRL-ALT-RIGHT ARROW / LEFT ARROW and you should be able to switch desktops.

---

### Post by okey666 on 2010-01-07
Thanks, I didn't think of un-capturing the mouse before switching. Its a little annoying but works well.

---

### Post by VastOne on 2010-01-07
> **okey666 said:**
> If I am using an application full screen, I cannot use ctrl-atl-left arrow etc. to switch workspace. Is there some way to do this?

For example, when I am using virtual box full screen, I would like to leave it full screen on one workspace, while I switch to another to do quickly do something else. The same goes for using alt-tab. I am using compiz.

Can anyone help?

Do you have Guest additions installed on your Virtualbox?  This allows you to do away with the host key and makes it all seamless

---

### Post by arubislander on 2010-01-08
> **VastOne said:**
> Do you have Guest additions installed on your Virtualbox?  This allows you to do away with the host key and makes it all seamless

You'd think it would... It makes capturing and un-capturing the mouse seamless.. but not the keyboard... You still have to un-capture it first (or just click anywhere outside of the guest os window, but of course, that's not possible in full screen mode)

---

