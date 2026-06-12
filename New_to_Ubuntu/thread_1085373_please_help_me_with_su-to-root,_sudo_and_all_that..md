---
title: "please help me with su-to-root, sudo and all that.. something just changed..."
date: 2009-03-03
forum: New to Ubuntu
---

### Post by cb34 on 2009-03-03
hello everyone. i need some help which im sure can be done, i just can't remember how i did it.

this is the problem.. i had my system setup perfect where i want it, but after updating it changed some things..

i always have it setup with the root account disabled, and i dont ever plan to enable it.

for programs like Synaptic package manager, i had it set so it would ask me for my pass, not the root pass, but my pass(i am the only one that uses this computer and I sudo when i need to do something admin related, or I sudo -i, i never want a root account enabled.) now after the upgrade, it is doing su-to-root and asking me for the root pass, when there is none enabled, i want it how it was before.. i changed the option in gconf-editor to make gksu use gksudo... checked the sudoers file, /etc/group etc. etc.... i cant figure out how i had it before...

please help me so that when i open a program like Synaptic, it doesn't ask for the root pass, but my pass, which i am admin for my machine.

i can always change the link to Synaptic so instead of su-to-root, change it to gksudo, but there's gotta be another way, as i would have to change a whole bunch of links for every admin program.. i had it set how i like before, please help me out..

basically i had it where anything that would ask for the root pass, would ask for my pass instead.. because there is no root pass enabled.. just me.

Thank you so very much.. this is annoying. :D

EDIT-> just an example... 'gksu gnome-system-log' is asking me for the root pass, when it never did before... how did i have this thing set up before?? grrrr.... am i stuck with having to change all the links to gksudo?

---

### Post by Truefire on 2009-03-03
If you ARE the user with root powers, that would be no different than having a root account with SUDO. 

Sudo just runs a command as another user, in Ubuntu's case, "root".

The seperation between user accounts is what makes Linux safe, among other things.

---

### Post by cb34 on 2009-03-03
it is asking me for ther root password. i dont have one enabled.
i never have. i enabled the root pass just to check if it would let me run a certain su-to-root command, and it did.. so i re-disab;ed the root account.

i had it set before where anything that would ask for the root account, asks for my account pass.

it is my computer, there is no other users on this computer.

---

### Post by cb34 on 2009-03-03
example: in my gnome panel. the link to view gnome system log is:
gksu gnome-system-log and it asks for the ROOT password.(there is none. it's disabled)
if i change it to 'gksudo gnome-system-log' it works fine.

i had it before where it is gksu, and it would ask for my user pass, and work fine, not EVER ask for the ROOT pass.

how do i get it to be like that again is what im askin?

Thank you very much for any help.

---

### Post by cb34 on 2009-03-03
Re: gksu vs gksudo
Even though gksudo appears to be a symbolic link to gksu, meaning that they should behave in the same way, I have seen evidence to the contrary a few times on these forums. Someone has some problem with gksu synaptic, but gksudo synaptic will work... or vice versa.

Oddly enough, most forum users (including me) will advise using gksudo, but if you look at the commands for administrative applications in the Gnome menu in Ubuntu, they are usually gksu (gksu users-admin, for example--not gksudo users-admin).
-----
just read this in another thread on here....

so is the only way, to change all gksu and su-to-root links to gksudo?? i thought there must be another way??? i don't remember changing all the links before.

i dont understand why the last update would do this???

---

