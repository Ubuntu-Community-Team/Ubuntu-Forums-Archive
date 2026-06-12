---
title: "Virtualbox and a tablet pc?"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-10-15
got virtual box working, i only use windows any more for a few art programs and i hate having to reset.... wait boot into windows.... use program then reboot and use ubuntu for the 70% of stuff i do.
 
So my question is.. how do i get my windows VM to flip screen like it does in normal windows?
As far as i can tell most everything els is the same
thanks!

---

### Post by dvlchd3 on 2009-10-16
What do you mean by "flip screen"?

---

### Post by scorp123 on 2009-10-16
> **dvlchd3 said:**
> What do you mean by "flip screen"? You never used a tablet PC? Think of it like a big version of an iPhone. You hold it sideways in a "landscape" fashion and the screen should adjust. You rotate it 90° so the tablet is now in "portrait" mode and the screen should again adjust.

The problem here as I see it is that the virtual machine inside VirtualBox can't have any knowledge of what's happening to the tablet screen.

Probably the best option would be to tell VirtualBox to re-adjust the guest screen after each rotation?

---

### Post by HarrisonNapper on 2009-10-16
I'm not sure on this one, but you might try either capturing the keyboard entirely except the host screen or making an insert for Ctrl-Alt-Left/Right

---

### Post by R3fr4cti0n on 2009-10-16
> **scorp123 said:**
> Probably the best option would be to tell VirtualBox to re-adjust the guest screen after each rotation?

how would i go about doing this? i downloaded the drivers for the flip buttons, hoping that they would work but they're not compatable

---

### Post by scorp123 on 2009-10-16
> **R3fr4cti0n said:**
> how would i go about doing this?

Machine > Adjust Window Size (Host+A)

---

