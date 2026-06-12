---
title: "Problem launching JACK"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by limjix on 2010-07-29
Srry but I am new at this.

I opened Jack control, and i clicked start. However i get a error message

This is what was in the log:

22:35:14.996 Patchbay deactivated.
22:35:15.379 Statistics reset.
22:35:15.403 ALSA connection graph change.
22:35:15.763 ALSA connection change.
22:35:18.643 Startup script...
22:35:18.644 artsshell -q terminate
sh: artsshell: not found
22:35:19.046 Startup script terminated with exit status=32512.
22:35:19.046 JACK is starting...
22:35:19.047 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
22:35:19.088 JACK was started with PID=3395.
22:35:19.089 JACK was stopped with exit status=255.
22:35:19.090 Post-shutdown script...
22:35:19.091 killall jackd
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
encounter xruns. Please apply all the above mentioned changes and start jack again!
jackd: no process found
22:35:19.499 Post-shutdown script terminated with exit status=256.
22:35:21.147 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.


Any idea on what to do?

Thanks!

---

### Post by themusicalduck on 2010-07-29
Are you using a real-time kernel or the generic kernel? If you are just using normal Ubuntu and haven't installed any different kernels then it should just be the generic.

Try clicking on Setup and make sure Realtime is unchecked.

---

### Post by limjix on 2010-07-30
Thx alot this solved the problem! But is till cant seem to launch Ardour because they say they could not start Jack.

---

### Post by themusicalduck on 2010-07-30
Firstly, make sure that no other applications using sound are running before starting Jack.

Also, always start Jack before starting Ardour if you aren't already.

It might just be that a rogue application is doing something weird with the sound, so a restart might even just fix it.

If it still won't work, run Ardour from the terminal (applications > accessories > terminal) with ```
ardour2
``` and see if there are any errors.

---

### Post by limjix on 2010-07-31
thx so much dude! that solved it! :D

*thumbs up*

---

