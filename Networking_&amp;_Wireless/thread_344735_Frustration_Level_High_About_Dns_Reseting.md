---
title: "Frustration Level High About Dns Reseting"
date: 2007-01-23
forum: Networking &amp; Wireless
---

### Post by TIMMYB199 on 2007-01-23
Hi,
well i have loaded ubuntu on my older computer and i have to admit for a 400mhz computer the internet ect work great, until i reboot and the computer adds 192.168.0.1 in network settings under dns. below it is 205.171.3.65. which happens to be the one i need so everytime i reboot i need to delete the top one. i have tried the dhclient thing through terminal but i have no dhclient.conf file. just dhclient-script which when i open there is nothing on the gedit screen. i am frusterated because i started with linspire and it would not recognize my wireless internet card. so i tried ubuntu which i got to work but the reboot thing is ticking me off. why doesnt someone provide a update for people that would install on its own? well anyway if someone could please help guide me to an answer , i am building the computer for my dad and there i dread explaining delete'ing the wong dns. anyway 

please help me

tim
i don't want to reinstall windows 2000 pro

---

### Post by TIMMYB199 on 2007-01-23
ok now i tried sudo  gedit/etc/resolvconf/resolv.conf.d/base 

everytime i try it says there is no file

do i need to get to my root directory , not the one with

phil@philscomputer:~$



??????

---

### Post by TIMMYB199 on 2007-01-23
got into the resolv.conf but it has the dns number i need already, and someone said it would reset itself on reboot anyway

---

### Post by Threbus5 on 2007-01-23
Hi,

Does the "automatic" 192.168.0.1 occur if you use fixed network addresses?

Let me see if I can duplicate your issue.

See you in a couple minutes.

OK, bad news and good news. (using an old 333 Mhz Gateway)

I deleted my normal 192.168.0.1 DNS and replaced it with a 205.171.x.y IP and then restarted/rebooted.

Bad news is that I could not duplicate the problem. But then, my machines use Dapper.

Good news is that with Ubuntu 6.0.6 Dapper, there does not seem to be either any type of (a) automatic insertion of DNS 192.168.0.1 or (b) addition of that IP for a DNS after a reboot/restart. 

Take care.

---

### Post by TIMMYB199 on 2007-01-23
what is dapper? should i load that instead??

i have found out that the 192 bla bla address is the same address you use to access the setting for my router.

all the solutions everyone gives my i dont have the files in etc.

anyone else for help??

---

### Post by TIMMYB199 on 2007-01-23
how to i know what ubuntu i have

---

### Post by TIMMYB199 on 2007-01-23
now i got into my dhclient.conf through clicking and edited it and it says i don't have permission to save the file. this is crap, i have never had to type a password so many times and then have it tell me i don't have permission, how do i not have permission i installed the thing. is there a way i dont have to type a password evry five minutes


anyone

i am growing weary

---

