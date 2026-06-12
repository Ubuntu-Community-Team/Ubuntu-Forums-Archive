---
title: "how do i keep my fingerprint reader working?"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by voster on 2009-09-17
greetings all, i'm a long-time windows user turned linux newb and i need to know the best way to go about something: i have a simple project written in PHP and mySQL that has a UareU.4000B as part of the system.

I would like to go from windows to linux, but there are no drivers for the UrU right now. My initial idea was to run the UrU driver in winE, along with wamp and firefox but it's not working out so great.

Is there an easier way of getting the result that I want? (run my php/sql project, keep the fingerprint reader working)

thanks

---

### Post by yknivag on 2009-09-23
I'm not sure about your specific problem but [libfprint](http://reactivated.net/fprint/wiki/Main_Page) has drivers for several devices and a way of integrating them.

EDIT: The UareU4000B is supported by libfprint so hopefully you'll find something there to help you.

---

### Post by diablo75 on 2009-09-23
Not sure if this would help, but here's how I got my fingerprint sensor to work in Ubuntu:

[http://davestechsupport.com/blog/2009/05/20/how-to-setup-a-fingerprint-sensor-in-ubuntu/](http://davestechsupport.com/blog/2009/05/20/how-to-setup-a-fingerprint-sensor-in-ubuntu/)

Although I should add that there are a couple quirks I've noticed.  The most noticeable quirk of them all is the fact that I'm never given an on-screen, clear-text prompt that says "Swipe your finger to continue...", with a few exceptions.  It DOES tell me to swipe my finger when:

-I'm trying to unlock my computer from a "blank" screen-saver
-I'm running a program in the terminal with sudo

It doesn't seem to prompt me for a finger swipe when I:

-Login to my account
-Run GUI programs that require admin rights to be granted (like Synaptic/Update Manager or just about anything in the System>Administration menu).  I'll notice a "Starting Administrative Application" with a spinning cursor but no processor overhead working on anything; it's actually waiting for me to swipe my finger without prompting me.

So there is some support with this feature that need to be implemented.  One of the things I wish it would do is, on a failed swipe, allow you to swipe a second time or even third time before asking for a password.

---

