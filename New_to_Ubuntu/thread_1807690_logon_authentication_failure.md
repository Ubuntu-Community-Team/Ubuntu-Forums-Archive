---
title: "logon authentication failure"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by luigibmth on 2011-07-19
i was getting peed off with having to enter my password every 5 minutes so i changed it (from system, password manager i think) to a shorter version, however, now i cannot login. 

neither my old or new password work?

how do i get back in? 

:(

---

### Post by androssofer on 2011-07-19
if you try alt-control-F1 can u log in on the command line?

---

### Post by raja.genupula on 2011-07-19
if you wanna try to reset your password , you can work out with this 

             [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by luigibmth on 2011-07-19
thx for your replies - i will try it tomorrow, what i cannot understand is, why am i locked out, the new password should work? 

any ideas please

---

### Post by luigibmth on 2011-07-20
> **androssofer said:**
> if you try alt-control-F1 can u log in on the command line?
where am i doing alt-ctr-F1?

---

### Post by luigibmth on 2011-07-20
> **raja.genupula said:**
> if you wanna try to reset your password , you can work out with this 

             [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)


tried this, still cant get in

---

### Post by androssofer on 2011-07-20
> **luigibmth said:**
> where am i doing alt-ctr-F1?

when u get to your login screen. then press that, the screen should go black, then bring up a command line interface saying "login:" (amongst other things)

then type your username, hit enter

then your new password, hit enter

if tht fails, try old password, and report back...

your new 1 should work, could an input issue tho, like caps lock on, or 1 tht i do all the time have num lock activated on my laptop, so any key right of H on my keyboard is a number... grr.

failing tht i'd go with raja.genupula's advice/his might b the best plan regardless....

---

### Post by raja.genupula on 2011-07-20
hmmm ....may be some unknown mistake , honestly i too dont know and i havent face any problem like that . leave it and enjoy the UBUNTU buddy .

---

### Post by luigibmth on 2011-07-20
> **androssofer said:**
> when u get to your login screen. then press that, the screen should go black, then bring up a command line interface saying "login:" (amongst other things)

then type your username, hit enter

then your new password, hit enter

if tht fails, try old password, and report back...

your new 1 should work, could an input issue tho, like caps lock on, or 1 tht i do all the time have num lock activated on my laptop, so any key right of H on my keyboard is a number... grr.

failing tht i'd go with raja.genupula's advice/his might b the best plan regardless....


i did this and now im at the terminal, how do i get back to normal ie desktop pls?

---

### Post by androssofer on 2011-07-20
> **luigibmth said:**
> i did this and now im at the terminal, how do i get back to normal ie desktop pls?

ctrl-alt-f7... i think

---

### Post by luigibmth on 2011-07-20
slowly going insane here, nothing suggested so far has worked, i tried the trick in the video changing the text in the shadow file, still no good

that was after spending ages using ubuntu 11.04 live cd with no mouse! trying to guess by hovering

finally got to access the shadow file with another live cd, changed the text but still cant login

all this because i used an application located in system preferences to change passwords

this is going to end up in a reinstall - or just go back to windows, but i so want to try something new

ps...i can login to the terminal but not into login panel on desktop using same password for said user

---

### Post by androssofer on 2011-07-20
know tht feeling my man! haha.

right log into the terminal, then type:

```
passwd
```

then you should be prompted for a new password.

then put in your old password

then reboot

```
reboot
```

and report back

---

### Post by luigibmth on 2011-07-21
> **androssofer said:**
> know tht feeling my man! haha.

right log into the terminal, then type:

```
passwd
```then you should be prompted for a new password.

then put in your old password

then reboot

```
reboot
```and report back


thx for your reply, i tried several times, no joy, i can access my account it seems in terminal mode from safe mode etc 

what about root account, how do i log in as a root user? then i can edit my account im thinking? will this work, like in windows one admin can change anything on other accounts?

---

### Post by androssofer on 2011-07-21
they r funny about talking about su and root on the forums... 

there is this on it:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

but dnt know if any1 is allowed to tell u how to do it.. (like i say they r funny about it) but what you can do with root u can do with ur own account using sudo via the terminal(might not be 100% correct) so wudnt advise using root.

best thing i can think of at this stage, as i dnt know the actual solution, would be to create a new user, copy ur /home directory into the new account, then log into it and it shud work like ur old account (as settings etc r stored in /home) and then delete the broken 1.

its a workaround i know, but i'd try it. unless sum1 else has any ideas?

---

### Post by westie457 on 2011-07-21
A less elegant way that I use most of the time is to reinstall straight over the top of the broken install. That is LiveCD > Install > Options for my location and keyboard > Install Options > Something Else. In the partitioning screen choose the correct partition > use as the same EXTn (n=2,3 or 4)> Leave the Format box blank > Use as /. If you have a separate /home partition make the selections for that as you did for / root. Click Apply and answer okay to other prompts. Install goes ahead resetting the system but leaving the contents of the Home folder as they are. Window appears asking for your name and name of the computer for the network and to create a password. Fill in the boxes as necessary and continue with the install. Accept default Grub settings and finally reboot. Logging in with your password, whether it is a new one or the old one. Just do not forget it or change it before the next major Upgrade/ Reinstall.

---

### Post by luigibmth on 2011-07-22
> **androssofer said:**
> they r funny about talking about su and root on the forums... 

there is this on it:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

but dnt know if any1 is allowed to tell u how to do it.. (like i say they r funny about it) but what you can do with root u can do with ur own account using sudo via the terminal(might not be 100% correct) so wudnt advise using root.

best thing i can think of at this stage, as i dnt know the actual solution, would be to create a new user, copy ur /home directory into the new account, then log into it and it shud work like ur old account (as settings etc r stored in /home) and then delete the broken 1.

its a workaround i know, but i'd try it. unless sum1 else has any ideas?

i did that, could still not login to the new created user on the gui login panel

---

### Post by luigibmth on 2011-07-22
> **westie457 said:**
> A less elegant way that I use most of the time is to reinstall straight over the top of the broken install. That is LiveCD > Install > Options for my location and keyboard > Install Options > Something Else. In the partitioning screen choose the correct partition > use as the same EXTn (n=2,3 or 4)> Leave the Format box blank > Use as /. If you have a separate /home partition make the selections for that as you did for / root. Click Apply and answer okay to other prompts. Install goes ahead resetting the system but leaving the contents of the Home folder as they are. Window appears asking for your name and name of the computer for the network and to create a password. Fill in the boxes as necessary and continue with the install. Accept default Grub settings and finally reboot. Logging in with your password, whether it is a new one or the old one. Just do not forget it or change it before the next major Upgrade/ Reinstall.


will give this a go before reinstalling, however if it doesnt work, gonna reinstall with 10.4 LTS

---

