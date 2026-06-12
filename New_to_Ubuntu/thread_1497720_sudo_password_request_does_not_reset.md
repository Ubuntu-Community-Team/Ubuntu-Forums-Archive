---
title: "sudo password request does not reset"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by trikster_x on 2010-05-30
I just installed 10.04 and I was playing with my terminal and noticed that sudo no longer resets on terminal window close or user logout.  If I use sudo in multiple windows, I must open 1 more than the number of windows I was previously using to get a password request when using the sudo command.

Is this the new default behavior for sudo password requests?  Or did something get messed up on my install?  I have not done anything to my terminal settings yet, so everything is exactly as it should be on a fresh install.

If this is the default behavior, how do I change it to reset when the terminal window is closed or I log out of my user account?  This seems like a potential security problem for me since I do a lot of sudoing on a daily basis, and I don't generally like to log out when I walk away from my computer since it is a family computer and I keep the password to the only user account secure from anyone else.

---

### Post by marshmallow1304 on 2010-05-31
I know it doesn't reset on closing a terminal window, but I thought it should reset when logging out.  In any case, if you're worried about security, you can edit the settings in /etc/sudoers:

```
sudo visudo
```
Change
> Defaults        env_reset
to
> Defaults        env_reset,timestamp_timeout=0

to make sudo timeout immediately.  I believe the default is 15 minutes.


Alternately, you can run
```
sudo -K
```
to immediately "timeout" sudo whenever you step away.

---

### Post by trikster_x on 2010-05-31
Thanks for the info, I'll definitely use the reset command.  I double checked whether or not the reset happens on logout and it doesn't, so I still need to know how to get that behavior straightened out.

---

