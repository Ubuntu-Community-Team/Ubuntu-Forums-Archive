---
title: "Terminal code for scheduled shutdown"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by BrokeMahPC on 2009-12-09
Hi all - 1st post!
I have not been using Ubuntu long and I am starting to use the Terminal more and more.
I was wondering if there was a code to schedule a shutdown for the following situation:

Kaffeine has been left to record some TV and I would like to switch the PC off after I have gone to bed and Kaffeine has finished what it has to do.

I came up with:
code: sudo shutdown -h -P 23:30
This does seem to work but I am shutting the PC down with Kaffeine and a Terminal running and wondered if that would upset things in some way. When I tried it the PC seemed to take a few extra seconds on the next boot?

Any ideas? - thank you in advance.
Karmic Koala9.10 Desktop i686

---

### Post by jimmy the saint on 2009-12-09
You should be fine.

---

### Post by tom.swartz07 on 2009-12-09
> **BrokeMahPC said:**
> Hi all - 1st post!
I have not been using Ubuntu long and I am starting to use the Terminal more and more.
I was wondering if there was a code to schedule a shutdown for the following situation:

Kaffeine has been left to record some TV and I would like to switch the PC off after I have gone to bed and Kaffeine has finished what it has to do.

I came up with:
code: sudo shutdown -h -P 23:30
This does seem to work but I am shutting the PC down with Kaffeine and a Terminal running and wondered if that would upset things in some way. When I tried it the PC seemed to take a few extra seconds on the next boot?

Any ideas? - thank you in advance.
Karmic Koala9.10 Desktop i686

I dont see any problems with that. with a scheduled shutdown command, you dont necessarily need to worry about harming something- the system knows it will be shut off at that time and close programs accordingly. If you had the command to kill all processes and then immediately log off, you might run into some trouble- but thats not the case here.

---

### Post by musarraf172 on 2009-12-10
> **BrokeMahPC said:**
> Hi all - 1st post!
I have not been using Ubuntu long and I am starting to use the Terminal more and more.
I was wondering if there was a code to schedule a shutdown for the following situation:

Kaffeine has been left to record some TV and I would like to switch the PC off after I have gone to bed and Kaffeine has finished what it has to do.

I came up with:
code: sudo shutdown -h -P 23:30
This does seem to work but I am shutting the PC down with Kaffeine and a Terminal running and wondered if that would upset things in some way. When I tried it the PC seemed to take a few extra seconds on the next boot?

Any ideas? - thank you in advance.
Karmic Koala9.10 Desktop i686



Try " sudo shutdown -P 23:30" it works for me!

---

