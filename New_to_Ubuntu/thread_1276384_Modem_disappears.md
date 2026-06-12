---
title: "Modem disappears?"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by Randomwolf42 on 2009-09-27
[FONT=Courier New][SIZE=2]I'm currently dual-booting Ubuntu (I can't remember the version number, and it just says 'generic' for the type) and Windows XP. I find Ubuntu a lot more practical in many ways, and mostly I prefer it to XP, but I find I don't use it as often as I would because I have an unusual problem. 

When I first got Ubuntu set up on my computer, a friend who knows a lot more about computers than me [/SIZE][/FONT][FONT=Courier New][SIZE=2]set up the internet.[/SIZE][/FONT][FONT=Courier New][SIZE=2] He downloaded a modem driver from the Linmodems website that matched my modem somewhat (I'm not sure how exact it was, but it worked. Apparently it's an Agere Winmodem) and for a while it worked. 

However, the internet stops working at random times, and it will not reconnect for some reason. When I check the system files, it appears that the modem literally isn't there[/SIZE][/FONT][SIZE=2][FONT=Courier New]. :confused: I have to restart the computer, sometimes twice, to get it to find the modem again.

By the way, I don't know if this helps any, but I use gnomePPP to connect (which I think is a frontend for either PPPD or WVDial, I'm not sure which, or how it works, really.)

Any help would be greatly appreciated, thanks in advance. :) (And yes, I know Dial-up isn't very good, but it's all I can get right now.)
[/FONT][/SIZE]

---

### Post by lkraemer on 2009-09-27
I'd suggest starting with this link:
[http://ubuntuforums.org/showthread.php?t=1100310&highlight=wvdial](http://ubuntuforums.org/showthread.php?t=1100310&highlight=wvdial)
posting #4 at the sentence:
"These work wonderful with wvdial, etc."

You might just want to start with:
```

sudo wvdialconf /etc/wvdial.conf

```

If wvdial works then you should be able to get Gnome-ppp working.

If you open a terminal and type:
```

history > myhis.txt

```
and then post the text file we probably can figure out what was done
to install the modem driver.

A better option is to just buy an External Hardware Serial US Robotics
modem, and be up and running in 30 minutes or less.  wvdial will find
it, and once you configure the wvdial.conf file it works.

When you run wvdial in a Terminal window, you MUST leave that Window open (you can
minimumize it) until you are finished with your ONLINE session.  Then reopen the
wvdial window use CNTL C to terminate wvdial, then close the Terminal Window..

Once you are connected, you may have to uncheck the box for Firefox OFFLINE to be able to surf.

lk

---

### Post by Randomwolf42 on 2009-09-28
[SIZE=3][FONT=Courier New]Hmm, I'll have to look into that external modem... But for now, I'm stuck with what I've got. (the really weird thing is that I checked all over the box when I bought my modem and it gave no indication that it was a 'winmodem' and not a 'real' modem. 

I'm attaching a copy of the connection log, but I still can't figure it out. It says the modem is hanging up, but it won't let me reconnect, because the computer doesn't see the modem. I thought maybe it might have been the drivers, but the person who set it up for me used the latest drivers they had, and told me not to get the kernel updates when I'm updating the computer, apparently it will make it incompatible. Perhaps I accidentally downloaded one anyway...
[/FONT][/SIZE]

---

### Post by lkraemer on 2009-09-29
OK, It appears to be working, you just need to get the authentication
correct.  What did you set when you ran sudo pppconfig?  CHAP or PAP?
If you haven't followed the previously posted setup file, DO IT NOW!
Don't try to guess your way through.  Start with PAP, then setup your
wvdial.conf file also with your login and password.  If PAP doesn't
work then try CHAP by running sudo pppconfig again, but delete the 
first configuration from the menu before setting up CHAP. (PAP will
most likely work.)

Make sure you have the wvdial.conf file correct:
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem    ###MIGHT BE DIFFERENT
Baud = 48800
New PPPD = yes            ###TRY THIS
Stupid mode = yes         ###TRY THIS
;carrier check = no 
Modem = /dev/ttyACM0      ###THIS MIGHT CHANGE
ISDN = 0
Phone = 4460568           ###THIS CHANGES
Password = yourpassword   ###THIS CHANGES
Username = yourusername@yourisp.net  ###THIS CHANGES

```
You will also need to do:
```

sudo chmod a+x /usr/sbin/pppd

```

If wvdial dials out and the other computer's modem answers, your loginname, password, or authentication is incorrect.

REMEMBER after wvdial dials, you can pick up a handset and monitor the
activity by listening to what is going on with the communications.
If your config file is correct you should authenticate and then control
will be passed to ppp. You will see several strings of HEX (funny characters)
and then you should stay connected. (you will use CNTL C to
terminate the session when you are done, but for this session you MUST
leave the Terminal window OPEN...) You may have to uncheck the box
marked OFFLINE when you open your browser to make it online. Surf,
then terminate the open session with CNTL C in the open terminal window
where you initiated wvdial.

Keep trying after VERIFYING you PAP, CHAP and wvdial configuration.

lk

---

