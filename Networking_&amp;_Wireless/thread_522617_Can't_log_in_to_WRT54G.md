---
title: "Can't log in to WRT54G"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by Judo on 2007-08-10
I find this very strange.  I'm still connected to my router and I haven't had any trouble with my connection, but I can't seem to log in.  I put 192.168.1.1 into Firefox, put in the username and password, but the login box just pops up again.

I know what usernames and passwords I use and I tried them all.  Still, nothing.  I went onto the computer it's connected to but I was unable to set up or edit an account.  In the past, I've been able to create a new account, but not this time.  (is "account" even the correct word for this?)

I tried to due a hard reset, more than once, but no luck there.  I suppose I will keep trying that, but I really don't think it's going to work.  (I know they're stubborn, but really, I've tried a lot)

However, I do have the WPA key, since I set up the connection manually (/etc/network/interfaces), and I'm pretty sure I know the username.  Is there anything I can do with that?  If not, what can I do?

It's not like I've lost my connection.  I'm just trying to set up Apache, but I would really like to find out what's wrong.  Especially if something else comes up in the future.

---

### Post by noob12 on 2007-08-10
Generally the user manual will have a way to reset the router to factory settings and at factory settings the user manual will tell you the default password.  You can download user manuals from the Linksys site from their support section.  For linksys WRT54G series routers, this type of resetting is usually done by holding the reset button down for 10 seconds.  Then the default login is no username and password **admin**.  Note that if you do this it will completely reset the router to its initial factory settings. You will lose any settings you had set on it, including your key etc.   I'm not sure if wireless is enabled initially.  You may have to connect by a hard ethernet cable to reconfigure it after that.

---

