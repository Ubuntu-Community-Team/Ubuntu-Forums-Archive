---
title: "Randomly hanging on start up and shut down"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-04-14
I am currently running Ubuntu 8.10 fully patched, randomly when booting up and shutting down it will hang and I have to cold shut it off. On shut down the freeze happens at a black screen after the splash screen goes off, at start up it happens part way through the splash screen with the progress bar (at different points each time typically) I am not sure if the issues are related or not so I am posting them as a single thread. Anyone have any idea what I can do to correct or even debug the issue?

~Jeff

---

### Post by jbrown96 on 2009-04-14
> **beastrace91 said:**
> I am currently running Ubuntu 8.10 fully patched, randomly when booting up and shutting down it will hang and I have to cold shut it off. On shut down the freeze happens at a black screen after the splash screen goes off, at start up it happens part way through the splash screen with the progress bar (at different points each time typically) I am not sure if the issues are related or not so I am posting them as a single thread. Anyone have any idea what I can do to correct or even debug the issue?

~Jeff

Try disabling the splash screen. You can edit your /boot/grub/menu.lst and add > single to the end of the kernel line for the newest kernel. You can also do this temporarily on boot. Press Esc at the grub loading screen, then press E and then E again on the second line. Type > single and the enter and b to boot. See if you can see anything

---

### Post by beastrace91 on 2009-04-16
I've disabled my splash screens, it has not frozen on boot up yet but here is where it stopped when the shut down was hanging (last 3 lines it displayed):

```
* Deactivating swap ... [ OK ]
* Unmounting local filesystems [ OK ]
* Will now halt
```

At that point it hangs till I press and hold the power button. This does not happen every time I shut down, just randomly, like the hanging at start up.

Anyone have any idea what the issue might be base on those lines?

~Jeff

---

### Post by cooldudeman01 on 2009-04-16
I'm having a problem shutting down my computer.  Dell D620 Laptop running Ubuntu 8.10.  Each time I shut down it will hang and I will have to do the manual holding of the power button.

When I disable the splash screens everything seems ok when shutting down, and the last message is "*All Processes killed within 2 seconds [OK]" or something to that effect.

In addition, if I do not login to Ubuntu, but rather shut down the computer from the login screen it will shut down correctly.

---

### Post by beastrace91 on 2009-04-22
Anyone have any idea how I can solve the shutdown hangs? It is happening more and more often now... sometimes if I am in a hurry I forget to check to see if it actually shut off before I put it away and then when I get home the battery is dead :(

As for the hanging at start up this happens far less often, it finally happened again since I disabled the splash screen here is where it hangs on boot up: ```
[   17.839479] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
[   17.878724] input: Syn PS/2 Synaptics Touchpad as /devices/platform/l8042/serio4/input/input8
        [ OK ]
```

Hope someone can help debunk this...

~Jeff

---

