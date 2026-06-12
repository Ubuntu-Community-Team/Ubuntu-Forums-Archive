---
title: "Ubuntu server 9.10 - with Xubuntu- Desktop how to stop gdm"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by gottijr on 2010-03-10
-linux newbie-

  i installed xubuntu on my ubuntu server 9.10

  trying to stop the gdm and get back to shell

  i tried <code>gdm stop</code> doesn't work 

  also <code>/etc/init.d/gdm stop</code> doesn't work

  anybody has a suggestion?

---

### Post by NT4usB on 2010-03-10
9.10 introduces some different ways to stop stuff.
First, you did use 'sudo' with those commands, didn't you?
iirc, when I did I received some info back in the terminal on the 'new' way to stop... something simple like:```
sudo stop gdm
``` or some such.
Maybe there's a new man page on stop?

---

### Post by gottijr on 2010-03-10
it doesn't work

  yes i used sudo

  gdm stop or stop gdm  or /etc/init.d/gdm stop 
  
  does not work

  other suggestion?

---

### Post by NT4usB on 2010-03-11
Well, I know it was something simplified. man page tell you anything? If I was in front of my Ubuntu box, I'd have the answer in a minute. Bet I can google it in a minute... lets see.
Found your other posts.
Found service gdm stop.
Did you try service xdm stop (or some such?)
iirc, for the few minutes I had Xubuntu installed on a laptop it was using a different display manager...

---

