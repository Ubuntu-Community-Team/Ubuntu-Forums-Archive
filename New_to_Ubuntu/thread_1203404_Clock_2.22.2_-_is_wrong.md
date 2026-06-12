---
title: "Clock 2.22.2 - is wrong?"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by RickFAA on 2009-07-03
I like a clock for me desktop.
I have 'Clock 2.22.2'.
I put my timezone to 'US-NY' and 3 Internet sync places on.
But if I see my PC is on, the day is OK, the month is OK,
but the time is not.

I see my cell at 10:00am, and my PC is 2:00pm?
I can't found the right answers. Thanks!

RickFAA

---

### Post by ubudog on 2009-07-03
Open a terminal and type ntpdate clock.redhat.com.  Make sure to set your timezone to New York.

---

### Post by liamnixon on 2009-07-03
Is it resetting your time zone?

It would appear [someone else was having your same issue]("https://bugs.launchpad.net/ubuntu/+bug/226216"), and it was fixed with an update to 2.4.1.

If neither solution works, you could check [this page]("https://help.ubuntu.com/community/UbuntuTime") if you haven't already.

---

### Post by RickFAA on 2009-07-07
Sorry,
I used the terminal and type 'ntpdate clock.redhat.com'
but I get 'bind() fails: permission denied'

So I trys to reboot and did it over. And.... fails.

Do I need to get 2.4.1?  Where do I get a update?
What do I need to fix it?

All I need is a 'time' or 'clock' on my desktop.
My 'timezone' is 'America/NY'.
Went I see my cell (GPS) - the time is correct. (8:11PM)
But my desktop time is 4 hours later. (12:12AM)???

Thanks!

---

### Post by wojox on 2009-07-07
Open synaptic and look for Clock 2.24.1

---

### Post by ubudog on 2009-07-07
> **RickFAA said:**
> Sorry,
I used the terminal and type 'ntpdate clock.redhat.com'
but I get 'bind() fails: permission denied'

So I trys to reboot and did it over. And.... fails.

Do I need to get 2.4.1?  Where do I get a update?
What do I need to fix it?

All I need is a 'time' or 'clock' on my desktop.
My 'timezone' is 'America/NY'.
Went I see my cell (GPS) - the time is correct. (8:11PM)
But my desktop time is 4 hours later. (12:12AM)???

Thanks!

You have to put sudo in front of it.  Then enter your password.

---

### Post by QIII on 2009-07-07
Did you read either of the links liamnixon gave?

This is particularly important if you have a dual boot configuration, but one of his links has a bit about setting UTC=no.  You are on the east coast, which is 4 hours (I believe) after GMT.  So 10:00 am in NY would be 2:00 pm GMT.

Look for the heading 
**Make Linux use 'Local' time**

---

### Post by ubudog on 2009-07-07
Open a terminal and type sudo ntpdate clock.redhat.com and enter your password.  See if that works.

PS:Make sure to set your timezone first.

---

