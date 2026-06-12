---
title: "I've broken something big, help please"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by Duffking on 2009-03-29
Help! I accidentally removed the panel at the top of the screen and couldn't get it to come back looking the way it was when I installed linux (8.04 TLD, it's the eee pc version of linux). So I created a new user account, logged into it and now no matter what account I log into, the interface is flickering everywhere. Any windows I open just disappear immediately and cannot be selected. Can anyone lend a hand?

---

### Post by mistypotato on 2009-03-29
Sounds like a key on the keyboard is stuck or somethings mashing it to me :confused:

---

### Post by linuxisevolution on 2009-03-29
Can you boot into recovery mode?

Turn on the computer, and quickly hit escape when you see the grub loader. Then choose recovery. Next choose "drop to a root shell" and type 
```

apt-get install icewm icewm-themes xfce4 

```

Then restart and click sessions and xfce4 or icewm before logging in.

---

### Post by Duffking on 2009-03-29
I can but it says 'Give Root password for maintenance.'

---

### Post by hyper_ch on 2009-03-29
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...
 
 A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)
 
 And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.
 
 Or in short terms: Help others to help you ;)
 
 See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)
 
 Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Duffking on 2009-03-29
Sorry, I've just changed the title. Just logged into GNOME failsafe in the login options and everything is fine... I'm a total newbie with Linux, any ideas what's wrong when not in the failsafe?

EDIT: Failsafe still isn't quite fine, when I scroll the main menu, it also flickers...

---

### Post by linuxisevolution on 2009-03-29
> **Duffking said:**
> I can but it says 'Give Root password for maintenance.'

You have to type your password....

Follow the directions that I gave you and do it again..:)

---

### Post by linuxisevolution on 2009-03-29
> **Duffking said:**
> Sorry, I've just changed the title. Just logged into GNOME failsafe in the login options and everything is fine... I'm a total newbie with Linux, any ideas what's wrong when not in the failsafe?

EDIT: Failsafe still isn't quite fine, when I scroll the main menu, it also flickers...

I KNOW WHAT YOUR PROBLEM IS!!! w00t...

I have the same problem, and it just didn't register in my mind...

Login to gnome failsafe, Click System >> Admisteration >> hardware (or restricted) drivers.

Disable any drivers you see listed.

---

