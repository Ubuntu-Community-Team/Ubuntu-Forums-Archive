---
title: "Auto update manager for Recommended &amp; Other updates"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by Paddy Landau on 2010-08-13
I've set my Update Manager to install updates automatically (Settings > Updates > Install security updates without confirmation).

However, this updates only the "Important security updates" automatically. It doesn't install the Recommended and other updates.

I have *always* installed all available updates, including Recommended and other, and always will continue to do so unless something happens to change my mind.

So...

Is there a way to get Update Manager to install all the other updates automatically, without my having to open Update Manager on a regular basis? Maybe with a command line that I can place in cron? (I don't want to upgrade the distribution automatically, though; I wish to stay with LTS.)

---

### Post by Calcipher on 2010-08-13
The idea to allow the updater to work like this has been suggested ([http://brainstorm.ubuntu.com/idea/11084/](http://brainstorm.ubuntu.com/idea/11084/)), personally I find it odd that it doesn't already have this option.  That being said, there is a complicated way to do what you want, though it might not be the best idea for someone new to this.  
The general idea is that you'd want to make a small script that contains the following commands:
```

apt-get update
apt-get upgrade

```
It is a little more dangerous, but you could change the 'upgrade' to 'dist-upgrade'.  
After you made this script, you'd want to add it to root's CRON file (crontab) and set the thing to run on some regular frequency (daily?).  
The reason I'm not giving instructions on how to do this is that I think it is a bit of a bad idea.  If you are still interested in doing this, let us know and maybe someone else can fill in the details, just be careful.

---

### Post by Paddy Landau on 2010-08-13
> **Calcipher said:**
> The idea to allow the updater to work like this has been suggested ([http://brainstorm.ubuntu.com/idea/11084/](http://brainstorm.ubuntu.com/idea/11084/))
Thanks, I've added my vote.

Thanks for the script lines. I should have been able to work that one out myself! :rolleyes:

> **Calcipher said:**
> The reason I'm not giving instructions on how to do this is that I think it is a bit of a bad idea.
I know how to use cron, thanks.

But I'm curious as to what makes it a bad idea. Isn't that the equivalent of running update-manager and clicking Check then Install Updates (which is what I do anyway)?

---

