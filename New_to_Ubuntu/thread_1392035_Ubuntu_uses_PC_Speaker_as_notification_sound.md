---
title: "Ubuntu uses PC Speaker as notification sound"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by cpeake on 2010-01-27
Hi!

I'm slowly developing a warm relationship to Ubuntu, but every now and then small things get in the way.

Since the very beginning I've been distracted by Ubuntu occasionally using my PC Speaker to let me know about things happening in my system.

To be more precise, I get a Pc Speaker beep when:
- I receive new email(s) in Evolution.
- The system shuts down or boots
- Occasionalyl when error messages pop-up

This is a very small thing, but its breaking the immersion into this stylish and beautiful world that is Ubuntu. :)

I've been through System -> Preferences -> Sound, but I can't find where to disable it. I see sounds set as my "Alert sound" and "Error" sound, that I've never heard in Ubuntu! It's always with the creeekbeep from inside the PC.

---

### Post by J V on 2010-01-27
```
echo "blacklist pcspkr" | sudo tee -a /etc/modprobe.d/blacklist
```Enjoy :)

---

### Post by cpeake on 2010-01-27
> **J V said:**
> ```
echo "blacklist pcspkr" | sudo tee -a /etc/modprobe.d/blacklist
```Enjoy :)

Whoa you were quick to reply!

So this disables my PC Speaker entirely? I'll give it a shot.

---

### Post by J V on 2010-01-27
you can get replies in less than a minute of your post... it could also never get answered...

You just hope you have more of the former :)

---

### Post by cpeake on 2010-01-27
> **J V said:**
> you can get replies in less than a minute of your post... it could also never get answered...

You just hope you have more of the former :)

OK received e-mail notification of your reply and no beep!

But just for future reference, how do I undo this effect if I ever wanted to do so?

---

### Post by J V on 2010-01-27
I will dissect the command for you, that way you will understand what it does (always better ;) )

echo "blacklist pcspkr" is fairly simple, it creates text "blacklist pcspkr"

Usually it prints it to the terminal, but this time, we piped it | to the next command tee -a, which adds something to the end of a file, so it put the echo of "blacklist pcspkr" through the tee command into the /etc/modprobe.d/blacklist file, just remove it if you want it back (no-one does, pre-installed pcs usually get configurated to remove this and a few other things then image copied rather than installed :P)

---

### Post by MaindotC on 2010-01-27
> **J V said:**
> you can get replies in less than a minute of your post... it could also never get answered...

You just hope you have more of the former :)

Don't forget [Getting Help with Ubuntu](https://help.ubuntu.com/community/Signpost/Answers#help-use).

---

