---
title: "Unable to update / change password for wireless network connection"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by jal301 on 2009-01-04
When I initially set up my wireless connection, I used an old password for the router.  When I would load Ubuntu, I was always prompted for this admin password in order to connect to this wireless network.  Now, I would like to change the admin password to my router (which I have done) however, Ubuntu keeps requesting that I enter the old password and won't accept the new password (will freeze trying to connect to the router unless I change the admin password back to the original).  I have tried deleting this connection and adding as new but it automatically shows and will only accept the original password.

So I suppose I have two questions.  How do I finally get this password changed on my router (which I know how to do) but so that Ubuntu accepts it.  And, is there any way to eliminate the need to enter a password for the wireless network each time Ubuntu boots?

---

### Post by jimmy the saint on 2009-01-04
Right-click on the nework icon in the task bar and select "edit networks."
If you remove your network, it should just forget about it and the next time you connect it shoudl be as if you are for the first time.  It should then ask you for the password and remember that one just like it did the old one.

---

### Post by jal301 on 2009-01-04
I have tried this numerous times and it just doesn't seem to work.  Each time it defaults back to the original password and won't even allow me to enter the new password because it is shorter and won't allow me to click "OK" since it is greyed out until the old, original password is entered.  This is so baffling.

---

### Post by jal301 on 2009-01-04
I have noticed that each time I delete this wireless connection and then it is added again, it is always shown as the default connection.

I guess the changing of the passwords really isn't an issue - I can surely keep my old password if it is possible to eliminate the need to enter the password each time Ubuntu is booted.  Do you know how to eliminate that need?

---

### Post by Wheeeze on 2009-01-04
Hi there,

Please excuse this beginners 'poke and hope' suggestion based on nothing technical at all.

Have you tried powering down and re-starting the computer after deleting the old password?  It may then be ready to accept the new one.

Best wishes,

Wheeeze

---

### Post by jal301 on 2009-01-04
Yes, I had tried a re-boot as well.  But I believe that I have found my answer to at least eliminating the request for password at every boot.  Seems to be an issue for auto-login users.  See the following:

[http://ubuntuforums.org/showthread.php?t=991228](http://ubuntuforums.org/showthread.php?t=991228)

---

