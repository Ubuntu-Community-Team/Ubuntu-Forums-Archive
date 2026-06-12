---
title: "Login Failure"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by tlcmd on 2010-01-28
Me again, sorry.
Ubuntu 9.10; 1.4 GHz Althon, 320 G Hard drive.
Have Windows XP and installed ubuntu on partitioned hard drive with option to open either operating system on boot.

1)Set up with automatic login. Worked fine!!
Then I
2)Have removed all the games; did have to authenticate when removing "Mines".
3) Added Musescore (prerelease version 9.6)
4) Added Swiftfox
5) Added Avast (antivirus)
6) Added music files (12k MP#, ogg vorbis, etc) to Rhythmbox.
7) Added 3 .xml files to Musescore

Now automatic login has been disabled and I cannot login using my password. 

This has happened 3x before and I finally had to re-install Ubuntu each time. 

I need  "Mickey Mouse" instructions to correct this problem, please. I'm reasonably coherent in Windows XP and do have an MD degree. But this Ubuntu 9.10 OS is beginning to really frustrate me. Can I re-install without a login and password???

Thanks.

Assistance please.

Thanks.

---

### Post by warfacegod on 2010-01-28
When Grub loads select "recovery mode" for the highest number kernel. When the menu appears (might take a bit) select Drop to shell. Then:

```
passwd username
```

Replace username with your username. This will allow you to change your password, so enter a new one, verify it. Then type reboot and then login using your same username with your new password.

---

### Post by Dorrax on 2010-01-30
will that fix the automatic login problem? If he set it to automatic, he shouldn't need to enter a password on the login, so the password shouldn't be incorrect and shouldn't need to be changed.

---

### Post by warfacegod on 2010-01-30
It may or may not fix the Auto login problem but it should, at least, get him into his system so he can fix it. I had this happen to me in 8.04 because it decided that my password wasn't correct.

---

### Post by A&#11375;A on 2010-01-30
I shouldn't criticise someone's computer usage habit, but automatic logins are ill advised on all systems. I don't allow any of my clients to get away with this for any reason, i liken it to having no locks on your car or house.

But to each his own.

Once you reset the password as mentioned above you should be able to re-enable auto-login.

One trick I teach my clients is to use a phrase such as "thecowjumpedoverthemoon" while containing dictionary words this type of password is very difficult to brute force and will suffice for basic logins. It's also easy to remember.

---

### Post by Dorrax on 2010-02-03
It depends on your needs. I use my computer to run my TV. But the scripts needed to make it turn on the TV display are only run on start up, I can't see the login screen to log in, so I have to use automatic.

---

### Post by warfacegod on 2010-02-03
> **Dorrax said:**
> It depends on your needs. I use my computer to run my TV. But the scripts needed to make it turn on the TV display are only run on start up, I can't see the login screen to log in, so I have to use automatic.

If you are the only user the pointer should already be over your username. Left click> type password> hit Enter.

---

