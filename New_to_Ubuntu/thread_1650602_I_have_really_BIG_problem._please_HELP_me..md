---
title: "I have really BIG problem. please HELP me."
date: 2010-12-21
forum: New to Ubuntu
---

### Post by jijiisme on 2010-12-21
I used Xubuntu 10.10. 
My computer is P4 1.6, DDR1 512M, VGA 32M on board. I changed resolution from 1280x1024 to lower one.
the computer logout my account. So I log in again but I can't log in because of logout again.

the really problem is I login the computer still logout. help.

now i used recovery mode and call the firefox and call for help. :confused:

thank you for reading.

---

### Post by NightwishFan on 2010-12-21
Question: Is your Avatar a Jiji Toy?

Also, this might be easily solved by running a safe graphics mode session and choosing the "reconfigure graphics" option when prompted. Though it might help us to have a copy of your /var/log/syslog, and /var/log/Xorg.0.log

Also what is the model of your graphics card, ATI?

---

### Post by jijiisme on 2010-12-21
Answer : Yes.

save graphic mode = xfce ?

gigabite 8vm533m-RZ, this is my motherboard name. the VGA is on board.

can you give me solution with CLI base. can you?

---

### Post by NightwishFan on 2010-12-21
Wow I am slow, your name is Jijisme.... :popcorn: (Kiki is an awesome movie).

Well, you can try removing a Xorg.conf if you have one:
```
sudo mv /etc/X11/xorg.conf /etx/X11/xorg.conf.backup
```

That should reset your Xorg config. Notice the X is capitalised.

---

### Post by jijiisme on 2010-12-21
right I am a really black cat :)

there is no file like that name in that directory.

now I override the root password and login with root account.
but i want my account back.

---

### Post by NightwishFan on 2010-12-21
I am sorry, how did you override your account? Ubuntu uses sudo by default, it should not have any problems with overwriting accounts. What happened?

---

### Post by jijiisme on 2010-12-21
type in terminal : sudo passwd
                           first your password type
                           another password for root
                           another same password for root

I used root account, because I have only one computer. so I used my account with recovery console. I run terminal and type "firefox" and quit. and work with CLI and leave CLI and go browser and go CLI. I only do one job in time. so I did.

---

