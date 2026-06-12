---
title: "I can't scroll down with the mousewheel"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by quinnten83 on 2010-08-31
I must have done something really stoopid (yes with oo), because I'm unable to scroll down using my mousewheel.
Scrolling up seems to work, but scroling down doesn't, it will start to move, but after that first jump it stops and nothing happens.
I configured my compiz some, but didn't do anything out of the ordinary (I'm thinking maybe there is a plugin that is conflicting?).
I checked the mouse settings and the keyboard shortcuts, but couldn't find anything out of the ordinary.
Can you guys please give me a hand? Because this is really really annoying....

---

### Post by TNT1 on 2010-08-31
Is it the mouse? Try a different mouse or try your mouse in a different pc?

---

### Post by quinnten83 on 2010-08-31
*forehead slap*
it might be the mouse or the kvm switch I'm using.
I get the same thing in the other computer.

---

### Post by ilovelinux33467 on 2010-08-31
if you type xev in the terminal and try to scroll in the white box is there any output from terminal?

---

### Post by jtarin on 2010-08-31
> Some types of active KVM switches do not emit signals that exactly match the physical keyboard, monitor, and mouse, which can result in unwanted behavior of the controlled machine(s). For example, the user of a multimedia keyboard connected to a KVM switch may find that the keyboard's multimedia keys have no effect on the controlled computer(s). Likewise, a monitor connected in this way may be detected as an incorrect model, or not detected at all; this may cause issues for operating systems that rely heavily on boot-time "Plug n' Play" detection of this hardware, such as Ubuntu. [From the wiki]("http://en.wikipedia.org/wiki/KVM_switch")

---

### Post by quinnten83 on 2010-09-04
> **ilovelinux33467 said:**
> if you type xev in the terminal and try to scroll in the white box is there any output from terminal?

Sometimes, but not much.
But it's okay, as long as I know it's the KVM switch, I can live with this little inconvenience.

---

