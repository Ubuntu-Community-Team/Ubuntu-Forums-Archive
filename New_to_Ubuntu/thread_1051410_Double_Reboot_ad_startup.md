---
title: "Double Reboot ad startup"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by SilverF0x on 2009-01-26
Hi to all. 
I'm a absolute beginner in ubuntu, i did install the 8.10 and update everything.
I start playing with grub configurator with the tool that i download from install/remove software, and notice that when i start windows xp, or ubuntu, my bios reboot two times.

Example

i start computer and select windows xp, it load one second, and BOOM, reboot, then i select again windows xp (he tell me how to boot because last boot was failure) and everything start ok.

The same when i select ubuntu, it reboot, and then when i select for the second time.

How to solve that?
Thanks.

---

### Post by schmildo on 2009-01-31
I'm not very good at grub; so when I used to have problems with booting I'd run away and cry; 
Then i discovered: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
You can download this as an ISO and burn it to a CD, or put it onto a usb;
Either way, if you boot from it, you should get a menu that will help out; i think it had advanced stuff; but from memory there was an option that said something like; "I don't know what to do; just fix grub"

and it has worked for me twice so far.

Let me know how you go.

:)

---

### Post by lokar on 2009-08-07
A friend of mine experienced the same problem on a Samsung R510H. Did you manage to solve the problem?

---

### Post by pavel_n on 2009-09-01
> **lokar said:**
> A friend of mine experienced the same problem on a Samsung R510H. Did you manage to solve the problem?

I have experienced the problem of double reboot at startup with Samsung NP-R508 + Windows XP + Ubuntu 9.04.

It was solved by changin BIOS settings:
**AHCI **option set to **Manual **from **Auto **and the suboption  set to **Disable**

---

### Post by LewRockwell on 2009-09-01
> **pavel_n said:**
> I have experienced the problem of double reboot at startup with Samsung NP-R508 + Windows XP + Ubuntu 9.04.

It was solved by changin BIOS settings:
**AHCI **option set to **Manual **from **Auto **and the suboption  set to **Disable**

thank you for posting a possible solution for others!

.

---

