---
title: "HELP I somehow managed to remove my root priveleges"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by Awfulwaffle on 2008-12-18
I was having trouble with fuseiso because of root permissions, and found a thread suggesting that I run 

sudo usermod -Gfuse `whoami`

and log off and back on.

When I logged back on, I had no root privileges! My add/remove programs option is missing from Applications now, as are a few things from my System>Administration menu!

Also, when I try to sudo into something, I get the following message after entering my password

awfulwaffle is not in the sudoers file.  This incident will be reported.


Hope I didn't screw things up too bad (really new to Linux), please help!

Thanks in advance

---

### Post by ichbinesderelch on 2008-12-18
seems like you deleted somehow yourself form the /etc/sudoers list, you need to add your user by logging in as root and running "visudo" than add some like 'username ALL=(ALL) ALL'

---

### Post by Awfulwaffle on 2008-12-18
Holy quick reply, batman! Sorry for the noob question, but it's seriously like my 3rd day using Linux haha. This is what I get after running visudo as root

  GNU nano 2.0.7            File: /etc/sudoers.tmp                              

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL




where do I go from here?

---

### Post by jerome1232 on 2008-12-18
This is actually a fairly easy fix.

Basically when the computer is booting up start hitting the 'esc' key it should bring up the grub menu.

Select the 1st option that has the word 'recovery' in it.

After a bit of text flying across the screen you should end up in a blue screen with a few options, select 'drop to a root shell'

now you should be at a prompt that looks like this root@computername:~#

Now we just need to add your user to the admin group and reboot the computer
```
adduser *usernamehere* admin
reboot
```

You should be good to go

edit: --- Actually I just missread his/her sudoers statment I'm tired lol ---

But adding yourself back to the admin group puts everything back to the way it previously was setup so I think it is still the perfered method.

---

### Post by ichbinesderelch on 2008-12-18
after root ALL=(ALL) ALL insert the line above with 'username ALL=(ALL) ALL', if i'm not wrong visudoe uses nano, just go to the correct line, type it in, press strg+o to write the file and strg+x to exit.
important is that you really do run it as root, so switch to vc1 with strg+alt+F1, login as root, edit the file, change back to vc7(strg+alt+F7) and relog there!

---

### Post by Awfulwaffle on 2008-12-18
Wow, thanks a lot for the turbo fast replies, both of you. Jerome1312, your fix worked, thanks a ton. I guess this is why I left Windows on my drive for the time being, so if I screw something up I still have a functioning computer haha.

---

