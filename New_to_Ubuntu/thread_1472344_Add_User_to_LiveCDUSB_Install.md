---
title: "Add User to LiveCD/USB Install"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by librecharly on 2010-05-04
Hi! 

I created a bootable USB installation of Ubuntu 10.04. Boots up fine as "Live session user." I want to go in and:


[LIST=1]
[*]Create my own user account
[*]Set it up to have sudo rights
[/LIST]
I go to the user and groups tool, click "add", and it indicates that I need to authenticate to modify the system configuration, and prompts for a password for root. I have tried "ubuntu," "Ubuntu," and just a blank password.

If I try sudo in terminal, I get "unknown uid: 999"

Any idea what I need to be doing?

thanks,
Charles

---

### Post by madjr on 2010-05-04
well you need to actually install it

or what exactly are you trying to do with it?

---

### Post by garvinrick4 on 2010-05-04
login=ubuntu
password is nothing at all.

With a Live CD you have no persistence (will not hold changes) so adding a user is
futile, making any change is futile.

Live USB you have to make one with persistence and changes will hold up to 4 gig.
Using Start-up disk creator in ubuntu.

Some LIVE USB installs do not hold persistence.

---

