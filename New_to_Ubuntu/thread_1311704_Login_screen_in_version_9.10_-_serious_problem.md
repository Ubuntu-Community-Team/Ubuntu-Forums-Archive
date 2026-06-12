---
title: "Login screen in version 9.10 - serious problem"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by chrisKr on 2009-11-02
I have just upgraded to version 9.10. Following the upgrade i made one change. In the user login menu i checked a box so that every time i start the computer ubuntu asks me to type in my username and password (before it used to be set to log in automatically without prompting me.) And here lies the problem. Either the upgrade was not properly done or v9.10 has a serious problem.
 
When i swithch the computer on, the system boots as normal. But when it gets to the login prompt which normally asks for username and password the system blocks up. I cannot select neither the username nor the password, the login prompt then reboots itself indefinately and i cannot log in. It just gets stuck there and nothing logs in.
 
The only thing i am able to do with my limited knowoledge of ubuntu was to login using the recovery console. I run fsck and no problems were found. I then typed exit and it took me to the virtual console. 
 
I know that using this virtual console i can tell ubuntu to log in automatically like it used to do before and the problem would be solved. The problem is i dont know how to do this as i dont know how to use bash.
 
Can you help? If possible the exact code would be helpful as i am a beginner and this problem is keeping me up at night.

---

### Post by lavinog on 2009-11-03
> **chrisKr said:**
> I have just upgraded to version 9.10. Following the upgrade i made one change. In the user login menu i checked a box so that every time i start the computer ubuntu asks me to type in my username and password 
There shouldn't be an option to require typing in a username.  There is a dropdown user list now.

Did the configuration app look like the attached screenshot?

---

### Post by chrisKr on 2009-11-03
That was the screen i used to make the change.  I selected the top option and rebooted.  Since then i am unable to log back in as the thing crashes and loops and does not allow me to log in.  Basically the log in screen appears, stays there for 3 seconds and reboots itself.  Nothing can be selected or typed in.  This repeats indefinately until it brakes all together and all i can see is a black screen going on and off.

---

### Post by lavinog on 2009-11-03
see if /etc/gdm/custom.conf exists and if it contains anything of interest.
I am not at my home machine to test, but I recall that file holds some of the configuration for the autologin.

---

### Post by ulfj on 2009-11-03
same problem here,I am doing a clean install instead of the upgrade.this is the first upgrade which hasn't worked flawlessly.but when I could get it to boot it ran great.

---

### Post by lavinog on 2009-11-03
/etc/gdm/custom.conf on my home computer has this:
```

[daemon]

TimedLoginEnable=false
AutomaticLoginEnable=false
TimedLogin=greg
AutomaticLogin=greg
TimedLoginDelay=30

[security]

```

---

### Post by kansasnoob on 2009-11-03
> **lavinog said:**
> /etc/gdm/custom.conf on my home computer has this:
```

[daemon]

TimedLoginEnable=false
AutomaticLoginEnable=false
TimedLogin=greg
AutomaticLogin=greg
TimedLoginDelay=30

[security]

```

Using auto-login mine looks like this:

> [daemon]
AutomaticLoginEnable=true
AutomaticLogin=lance
TimedLoginEnable=false
TimedLogin=lance
TimedLoginDelay=10

Of course you're not lance.

So you could edit by running:

```
gksudo gedit /etc/gdm/custom.conf
```

That should at least get you booting then we could try to figure out the rest.

---

### Post by lavinog on 2009-11-04
> **kansasnoob said:**
> 
```
gksudo gedit /etc/gdm/custom.conf
```



from the command line you would edit it with:
```

sudo nano /etc/gdm/custom.conf
```
then use ctrl-x to save and exit.

---

