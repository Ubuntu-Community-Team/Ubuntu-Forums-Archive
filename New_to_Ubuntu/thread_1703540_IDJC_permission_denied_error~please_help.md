---
title: "IDJC permission denied error~please help"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by Iamfennec on 2011-03-09
Hi all as you might guess I'm 100% new to the Linux OS language and concepts so I'm asking for your help... I'm trying to configure the Internet DJ Console as per [http://idjc.sourceforge.net/install_first_run.html](http://idjc.sourceforge.net/install_first_run.html)  Tells me to do... I have opened the terminal and been able to get the info as instructed but when it comes to adding the lines of code that are missing I'm getting a permission denied error both in terminal and through the window interface. Here's what it looks like:

[FONT=Verdana]$ jackd -d alsa
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
Please check your /etc/security/limits.conf for the following lines
and correct/add them:

  @audio          -       rtprio          100
  @audio          -       nice            -10

After applying these changes, please re-login in order for them to take effect.

You don't appear to have a sane system configuration. It is very likely that you
encounter xruns. Please apply all the above mentioned changes and start jack again![/FONT]audiofennec@audiofennec-desktop:~$ sudo echo "@audio   -   rtprio   100" >> /etc/security/limits.conf
bash: /etc/security/limits.conf: Permission denied
audiofennec@audiofennec-desktop:~$ sudo echo "@audio   -   nice     -10" >> /etc/security/limits.conf
bash: /etc/security/limits.conf: Permission denied
audiofennec@audiofennec-desktop:~$ 


So what am i doing wrong and why am i getting a permission denied error?  please help

---

### Post by cariboo on 2011-03-09
@ dnotes that the file is symlinked to somewhere else, what if you use the full path to the symlinked file?

if you open a terminal and type ls -l in the directory @audio is located you should see something similar to this:

```
000-default -> ../sites-available/default
```

---

### Post by StephenF on 2011-03-11
> **cariboo907 said:**
> @ dnotes that the file is symlinked to somewhere else
@ denotes a group rather than a user. Context matters.

The problem appears to be with sudo not working for some reason.

---

### Post by dimas869 on 2011-06-27
> **Iamfennec said:**
> Hi all as you might guess I'm 100% new to the Linux OS language and concepts so I'm asking for your help... I'm trying to configure the Internet DJ Console as per [http://idjc.sourceforge.net/install_first_run.html](http://idjc.sourceforge.net/install_first_run.html)  Tells me to do... I have opened the terminal and been able to get the info as instructed but when it comes to adding the lines of code that are missing I'm getting a permission denied error both in terminal and through the window interface. Here's what it looks like:

[FONT=Verdana]$ jackd -d alsa
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
Please check your /etc/security/limits.conf for the following lines
and correct/add them:

  @audio          -       rtprio          100
  @audio          -       nice            -10

After applying these changes, please re-login in order for them to take effect.

You don't appear to have a sane system configuration. It is very likely that you
encounter xruns. Please apply all the above mentioned changes and start jack again![/FONT]audiofennec@audiofennec-desktop:~$ sudo echo "@audio   -   rtprio   100" >> /etc/security/limits.conf
bash: /etc/security/limits.conf: Permission denied
audiofennec@audiofennec-desktop:~$ sudo echo "@audio   -   nice     -10" >> /etc/security/limits.conf
bash: /etc/security/limits.conf: Permission denied
audiofennec@audiofennec-desktop:~$ 


So what am i doing wrong and why am i getting a permission denied error?  please help



that is because you sistem configurations are wrong
do this:

$ sudo echo "@audio   -   rtprio   100" >> /etc/security/limits.conf
$ sudo echo "@audio   -   nice     -10" >> /etc/security/limits.conf

or $sudo nano /etc/security/limits.conf

and add the two lines manually


and if you want to read more go to:
[http://idjc.sourceforge.net/install_first_run.html](http://idjc.sourceforge.net/install_first_run.html)

anyway...i havent be able to get IDJC to work as every time i tryed it messes my audio server

---

