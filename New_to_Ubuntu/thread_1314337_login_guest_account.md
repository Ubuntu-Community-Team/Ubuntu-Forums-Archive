---
title: "login guest account"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by Rahabib on 2009-11-04
ok this has been covered but I found a sort of work around that almost works.  I was wondering if there was someone who can help me out here.

First off, this isnt necessarily done for security reasons, its mainly to keep the system clean for many users to use.

So in order to create a guest account at login, I created an account "Anybody" (cant use "guest" due to a bug).  I set it to unprivileged as well.

Next, I created a script with my very limited knowledge of scripting.
[php]#!/bin/bash
/usr/share/gdm/guest-session/guest-session-launch&[/php]Then I set it to load automatically during login using the "System > Preferences > Startup Applications"

Test it out, and it works!.. kinda.  it automatically sets up a guest account but when you go to logout it dumps you to the main "anybody" account I set up, which isnt good.

If I run teh script manually, it works just fine.  it goes to a guest account and when you logout it takes you back to the login screen.  So, apparently, its an issue with running it at startup.

Any suggestions?

---

### Post by Rahabib on 2009-11-04
oops didnt realize this forum was no longer being used.

---

### Post by cariboo on 2009-11-04
Why not just limit what the users can do in the guest account, About the only thing a guest would need to do is access the internet. They don't need permissions to do anything else.

---

### Post by Sef on 2009-11-04
> Why not just limit what the users can do in the guest account, About the only thing a guest would need to do is access the internet. They don't need permissions to do anything else.

+1.  Is there a reason that you wrote a script and not just unclicked the permissions that you did not want them to have?

---

### Post by vreemde eend on 2009-11-06
I'm looking for the same thing. The point is: I want the home directory of the guest-user to be cleaned we he logs out. That's exactly what happens with a guest session. The only problem is you can't select a guest session until a regular user has logged in.

kind regards,

pieter

---

