---
title: "when booting is it normal for it to show text??"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by JamesParnell on 2009-11-16
examples of what i mean are:

[LIST]
[*]fsck from util-linux (numbers)
[*]/dev/sda1: clean (more info)
[*]music: clean (more info)
[*]**music: recovering journal**
[*]**linux - unreadahed-other main process (545) teminated with status 4**
[*]setting proliminary keymaps
[/LIST]and when i turn off i get all the shutdown messages such as:

[LIST]
[*]**init: usplash main process (2026) terminated with status 3**
[*]disabling lapatop mode
[*]blah
[*]blah
[*]etc
[*]system will now halt
[/LIST]
 
are all these common ,and ones that are not, what do they mean and how to i solve them.
 
also, before all these i get **vga=786 is Depreciated. use set gfx (then it goes and i dont have time to tpye the rest:P)**

---

### Post by nitstorm on 2009-11-16
i get some jabber wen i boot before the login screen, but it disappears before i can even read it....

---

### Post by garvinrick4 on 2009-11-16
Believe there is a setting for show text in Start-Up Manager in 9.10.

---

### Post by JamesParnell on 2009-11-16
The ones im most concerned about are the ones i have (am about to) highlight

---

### Post by skymera on 2009-11-16
I've had similar to that show on every Linux distro i've used.
The splash screen usually covers it.

When you boot next, remove splash from the GRUB line and you'll see all the text for boot. 

My ubuntu takes about 2.3 seconds to shutdown, so i never see it as a worry.

---

### Post by t0p on 2009-11-16
> **JamesParnell said:**
> The ones im most concerned about are the ones i have (am about to) highlight

There's no real reason to be concerned.  If there's nothing wrong with your system, they're utterly unimportant.  If there *is* something wrong with your system, searching through the boot messages might reveal a clue as to the issue.  But searching these forums with google is often more effective.

If you want to see a log of your boot messages, type into a terminal:

```
dmesg
```

---

### Post by JamesParnell on 2009-11-16
ok then thanks, i will start searching now, thanks.

---

### Post by JamesParnell on 2009-11-16
nothing on google, just a load of forgeign sites -_-

---

### Post by t0p on 2009-11-16
> **JamesParnell said:**
> nothing on google, just a load of forgeign sites -_-

"Foreign"?  *"Foreign"?*  The internet is the whiole world, buddy.  Not just where *you* are.  You're American, aren't you?  Think you own the internet or something...

Anyway, I said search google *if you have a problem with your computer*.  Not search it if you can see boot messages!  If you *don't* have any problems, the boot messages mean nothing.  Forget about them.  Change your grub line if you don't wanna see them.

I also said *search these forums with google*.  Not just "search google".  So you shouldn't have got any "foreign" sites.  Unless American/British sites are foreign to you.  What the heck does "foreign" mean on the internet anyway?

If you want to look through your boot messages for some reason, use the 'dmesg' command.

---

### Post by JamesParnell on 2009-11-16
no actually "buddy", im english. and i mentioned the foriegn sites because i searched for english sites only, which lets be honest, is what i need, as i dont speak chinese. so maybe you should get the stick out your ***, leave me to make my typos, without offending anyone, other than yourself, obviously. As for the "search these forums with google" i must of misread, i apologise.
Now, i thank you for your advice, it was very helpful, i have found a few helpful pages in here and it will make for some good reading.
 
Thanks Nitsormm, Garvinrick4, Skymera and t0p for all of your input and help.
Solved.

---

