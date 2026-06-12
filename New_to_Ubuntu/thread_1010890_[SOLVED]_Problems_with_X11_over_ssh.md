---
title: "[SOLVED] Problems with X11 over ssh"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by anandamide on 2008-12-14
Hey guys
Really hope someone here can help me out, I'm sure I'm making an elementary mistake somewhere but don't know enough about Linux to spot it!

I'm wanting to run a specific program (a very obscure one) over ssh, with the display output routed to my monitor. I have a .ssh/config file which reads as 

> ForwardX11 yes

I have no trouble logging into the remote computer, opening up all sorts of X stuff (including the gui for the software I want to use); however, one output window refuses to open. No error message pops onto the terminal (tried running ssh -v but then the whole gui got a bit unstable). The cli command to call up a similar output window to the one I want is a bit more useful, displaying the following:

> 
_X11TransSocketINETConnect: Can't get address for localhost
Can't connect to xDisplay!
Segmentation fault

Any help would be greatly appreciated.

Phil

---

### Post by anandamide on 2008-12-15
It turns out this was a problem with Fedora and the software on the remote computer (unfortunately not fixable in the foreseeable).

---

