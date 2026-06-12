---
title: "Add/Remove missing from Apps. 8.10 Intrepid"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by JoePublic9 on 2009-01-04
Hi all.
  First post from this noob.
I just noticed that my add/remove is missing from my applications.
I went to System > Pref > Main Menu and it does NOT have a check.
When I try to put one there it just removes it a second later.
 The reset button did not work as well.
I have no idea what I keep doing to screw my system up. I'm on my 3rd install so far. The last one lasted almost 2 weeks before I screwed it up.
I am always messing with it because I love having so much control over it.
  I love Ubuntu, esp. the community. 
 Thanks in advance for all your help.
            Joe

---

### Post by shifty_powers on 2009-01-04
[http://www.ubuntued.com/?p=8](http://www.ubuntued.com/?p=8)

will let you reset your gnome panel to it's defaults, and should bring back your add/remove entry.

it may well remove any other custom entries, so be warned...

---

### Post by JoePublic9 on 2009-01-04
Thank you Shifty for you quick reply, however, that didn't seem to work.
I copied that line in terminal and ran it and it said that file did not exist. I moved to that spot and did an ls and it didn't show up on the list.
I am not sure if it is hidden or anything. I tried running it with su but it gave my an "invalid augment r" message. or something, with that command.
  Any more ideas?  I would really like to avoid another installation as I just did it yesterday, lol. 
I am having fun though. I also noticed when I go to System > Admin > Users and groups to check the settings, (I added my nephew yesterday), I get an error message saying "unexpected error" when I try to unlock it. 
 Is it possible that these are related?  Seems like I dorked gnome up good.
Anyway, thanks again for the help but am still searching for answers.
           Joe

---

### Post by kwacka on 2009-01-04
In Ubuntu use 'sudo' rather than 'su'.

After trying to delete the file, did you restart XWindows, a new 'default' config file should have been created.

---

### Post by JoePublic9 on 2009-01-04
Ok,
 I used sudo and it asked for my password then it said I wasn't in the Sudoers file. I am not sure how that can be as it is the first account I created. I absolutely did not change anything in that account. However, I did create another account with admin privileges when I did the new install yesterday, just in case. I switched to that account and repeated the command. It asked for password and I gave it, it accepted it. Then I used the CONTR + Alt + BACKSPACE to close gnome, it immediately bumped me to log in screen. I logged in again and nothing is changed.
  I'm very sorry if I am just being stupid here but this is really started to get weird for me, lol.
  Anyway, thanks agian for your help. Still trying to avoid a new install.
                 Joe

---

### Post by namdung on 2009-01-04
> **JoePublic9 said:**
> Hi all.
  First post from this noob.
I just noticed that my add/remove is missing from my applications.
I went to System > Pref > Main Menu and it does NOT have a check.
When I try to put one there it just removes it a second later.
 The reset button did not work as well.
I have no idea what I keep doing to screw my system up. I'm on my 3rd install so far. The last one lasted almost 2 weeks before I screwed it up.
I am always messing with it because I love having so much control over it.
  I love Ubuntu, esp. the community. 
 Thanks in advance for all your help.
            Joe

This usually happens if the user is not an admin. In terminal, post output of
```
id
```
Check if *admin* is in the list.

Also post output of
```
sudo cat /etc/sudoers 
```

Which Ubuntu version? Was there any update/settings changes just before this issue?

---

### Post by JoePublic9 on 2009-01-04
Here are the results of id and the other command:

oe@joe:~$ id
uid=1000(joe) gid=1000(joe) groups=4(adm),20(dialout),21(fax),24(cdrom),26(tape),29(audio),30(dip),44(video),46(plugdev),104(scanner),106(fuse),108(lpadmin),114(netdev),124(sambashare),1000(joe),1005(main)
joe@joe:~$ sudo cat /etc/sudoers
[sudo] password for joe: 
joe is not in the sudoers file.  This incident will be reported.
joe@joe:~$ 

I hope that copied and pasted ok and helps. Thanks again.
             Joe

---

### Post by namdung on 2009-01-05
As expected, u r not an admin anymore, hence u cannot use *sudo*. 

If u want to be an admin again, log in as the other admin user u have created. In *System==>Admin==>Users & Groups==>Manage Groups==>admin*, select ur account (Joe). Remember to *Unlock* first.

Was Joe the first account u created while installing, which usually is the default admin user?

---

