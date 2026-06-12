---
title: "Change username"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by emiliano67 on 2009-09-07
Hi,
I would like to use the method suggested by bodhi.zazen to change username:

sudo -i
usermod -d /home/new -m old
sed -i -e 's_old_new_g' /etc/passwd
sed -i -e 's_old_new_g' /etc/group
sed -i -e 's_old_new_g' /etc/shadow

What I don't understand are the bits 's_old_new_g'. What would be in a real situation where old user is *em (password: old_pass)* and new user is *one (password: new_pass)*? On tinivole example is usermod -d /home/opra -m opra but in bodhi.zazen is usermod -d /home/new -m old. Which one is correct? Thanks

---

### Post by kyle6513 on 2009-09-07
im guessing that it would work like this
say my current user is hardy and i wanted to change it to jaunty
it would work like this

sudo -i
usermod -d /home/jaunty -m hardy
sed -i -e 's_hardy_jaunty_g' /etc/passwd
sed -i -e 's_hardy_jaunty_g' /etc/group
sed -i -e 's_hardy_jaunty_g' /etc/shadow

of course i haven't tested this
use at your own risk!

---

### Post by emiliano67 on 2009-09-07
What I don't understand is what does s_hardy_jaunty_g means? Old and new password? That's the way to write it? What it stands for in each instance?

---

### Post by uchari on 2009-11-13
> **kyle6513 said:**
> im guessing that it would work like this
say my current user is hardy and i wanted to change it to jaunty
it would work like this

sudo -i
usermod -d /home/jaunty -m hardy
sed -i -e 's_hardy_jaunty_g' /etc/passwd
sed -i -e 's_hardy_jaunty_g' /etc/group
sed -i -e 's_hardy_jaunty_g' /etc/shadow

of course i haven't tested this
use at your own risk!

doesnt work for me in karmic... is there a new command for that?

---

