---
title: "help!"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by jdeluca5 on 2009-05-28
I was having trouble with vbox recently and i'm not sure what i did, but whenever i run a sudo command in the terminal, i get this line spit back at me:sudo: must be setuid root  I don't know what happened but i can't run any commands(that i know) really and can't open synaptic... please help!!

---

### Post by clonne4crw on 2009-05-28
vbox as in what? VirtualBox?

---

### Post by jdeluca5 on 2009-05-28
yes virtual box... i've been trying to boot into the recovery console but so far i can't even manage to do that. I'm struggling to say the least.

---

### Post by ssanders4917 on 2009-05-28
you have to be root. do you have more than one login?

---

### Post by clonne4crw on 2009-05-28
To fix the sudo issue:
# chown root:root /usr/bin/sudo
# chmod 4111 /usr/bin/sudo

---

### Post by jdeluca5 on 2009-05-28
@clonne   I tried the lines you suggested, i got no output, and i then entered ls -l /usr/bin/sudo to check and see if the ownerships changed but i came away with: -rwsr-xr-x 2 jeff root 115136 2009-02-16 22:17 /usr/bin/sudo  I am currently trying to get into the recovery console to make some changes, but i put in my live cd and i get no option for recovery console in any of the menus. any advice?   thanks for the help

---

