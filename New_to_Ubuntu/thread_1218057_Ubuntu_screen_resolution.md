---
title: "Ubuntu screen resolution"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by Plebton on 2009-07-20
:)Hi there People, I've just joined this Forum. I've been using Ubuntu for a couple of weeks now and I'm still trying to get my head round some of the simple tasks. I don't know what the screen resolution was when I first installed Ubuntu but it always booted up with that resolution. Then a friend called and he changed the resolution so that the letters were larger and easier to read. It was great until I came to turn the computer off. When I turned it on again a day later it wouldn't boot up to the home page, It's just a mass of lines and the mouse is froze. Is there any way out of this without having to re-install Ubuntu?
                            Hope someone can help,
                                  Plebton.:(

---

### Post by komputes on 2009-07-20
Boot into recovery mode using these instructions: [https://wiki.ubuntu.com/RecoveryMode...toRecoveryMode]("https://wiki.ubuntu.com/RecoveryMode?action=show&redirect=BootingIntoRecoveryMode")

and then select the xfix script to reconfigure the video. You can then resume to normal mode.

---

### Post by Plebton on 2009-07-20
[SIZE=4]Hi there Komputes, thnx for the info on recovery. I'm stuck at the prompt. root@Cobweb:~#
What command do I put in at the cursor?
                     Plebton.
[/SIZE]

---

### Post by /usr/sbin on 2009-07-20
> **komputes said:**
> Boot into recovery mode using these instructions: [https://wiki.ubuntu.com/RecoveryMode...toRecoveryMode]("https://wiki.ubuntu.com/RecoveryMode?action=show&redirect=BootingIntoRecoveryMode")

and then select the xfix script to reconfigure the video. You can then resume to normal mode.

Have you done everything that komputes has told you to do so?

---

### Post by Plebton on 2009-07-20
**[SIZE=3][COLOR=Black]Hi /usr/sbin,[/COLOR][/SIZE]** [SIZE=3]**yep, I've done what he said. I've now got a black screen with the cursor flashing, waiting for me to input a command, but I don't know what to put in.**[/SIZE]

---

### Post by zerhacke on 2009-07-20
> **komputes said:**
> 
and then select the xfix script to reconfigure the video. You can then resume to normal mode.

Seems you forgot this part.

---

### Post by komputes on 2009-07-20
You should get a blue recovery menu and not a root # prompt, unless you are using an older version of Ubuntu. Be sure you are not selecting "Root prompt" or "netroot" scripts. What version are you running?

If you type in /usr/share/recovery-mode/recovery-menu and then press enter at the root prompt, do you get this blue menu?

If none of this helps, try pressing ctrl-d at the root prompt and describe what happens afterwards.

---

