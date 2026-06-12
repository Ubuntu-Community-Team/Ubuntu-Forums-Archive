---
title: "On screen keyboard on login- HELP!!!"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by Mazehero55 on 2009-05-06
I've lost my keyboard and have been following this [guide]("http://www.mobilitytiger.com/health-articles/using-an-onscreen-keyboard-in-ubuntu/"). The thing is it says to change it to the plain login theme to get the on-screen keyboard to work. I can't do that without my keyboard to log in.
 
But I can use a live cd to edit a config file to change it to a plain theme. That process isn't in the guide, so I was wondering if anyone knew the file I have to edit to change it to the plain login theme? Or what I need toput in it.

my guess would be gdm.conf, but I don't know what to change in it???

Thank you so much for the help :D

---

### Post by mprince on 2009-05-07
I'm assuming you'll use an onscreen keyboard to edit these.


You may have a file called:

[INDENT]**/etc/gdm/gdm.conf-custom**[/INDENT]

You could edit it so that it will automatically log you in (you won't even be presented with the login screen).

Then you can simply change the login to the plain version with the login editor (under the Administration menu). You'll be able to use your mouse for that.

I tested the following and it worked and didn't cause problems.


Change username to your username.

```
[daemon]

AlwaysLoginCurrentSession=**[COLOR="Green"]false[/COLOR]**

AutomaticLogin=**[COLOR="Green"]username[/COLOR]**

[COLOR="Silver"]RebootCommand=/usr/bin/reboot;##############
HaltCommand=/usr/bin/poweroff;/sbin/poweroff;#############[/COLOR]

Greeter=/usr/lib/gdm/gdmlogin

AutomaticLoginEnable=**[COLOR="Green"]true[/COLOR]**
```



***** If you don't have gdm.conf-custom** then you could try editing your **gdm.conf** file which is located in the same directory. _I have not tested editing this though._

Change username to your username

```
[daemon]
# Automatic login, if true the first attached screen will automatically logged
# in as user as set with AutomaticLogin key.
AutomaticLoginEnable=**true**
AutomaticLogin=**username**
```

You may also need to find this and make sure it is set to false. It's further down the file. ```
AlwaysLoginCurrentSession=**false**
```

---

### Post by Mazehero55 on 2009-05-07
Thank you so much mprince!
This affectivly solved my problem in a way I hadn't even thought about. 
I cannot thank your hard work to answer my question enough.

---

### Post by mprince on 2009-05-07
You're welcome, Mazehero55. Actually, reading through the guide helped me a little. I didn't realize that I could simply type 'onboard' in terminal and bring up a decent little on-screen keyboard. This was something I had been looking for, but hadn't found yet.

---

