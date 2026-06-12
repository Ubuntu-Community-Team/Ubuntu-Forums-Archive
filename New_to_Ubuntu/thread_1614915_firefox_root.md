---
title: "firefox root"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by dzon65 on 2010-11-06
After a reinstall there's no mozilla folder in /root,it used to be there on my previous setups. I need to know my root profile for a cleanup script I run. How come ,this is the third install btw with this prob, firefox doesn't show in /root?

---

### Post by tajiknomi on 2010-11-06
[SIZE=2]I think it is in **/etc**.....[/SIZE]

---

### Post by yeats on 2010-11-06
By default there would be no such folder.  When a user runs Firefox for the first time, Firefox creates a profile folder in the user's home directory called ".mozilla" - which means that you probably ran Firefox while logged in as root in a previous installation.  Running Firefox as root is not good practice and logging in as root is not supported on these forums.  Is there a particular reason you need to have root be a Firefox user?

There may be a better way for your cleanup script to work.

---

### Post by uRock on 2010-11-06
The folder should be created if you actually log into root and open firefox. Being that the root account isn't set up to be logged into from the Log in screen, there is no reason for it to have a .mozilla folder or any other settings folder like that. They'd be a waste of space.

Edit: I just tried running sudo firefox and it still made no .mozilla folder. I still see no reason for having one, unless you plan on logging into the root account and running it, which wouldn't be wise.

---

### Post by dzon65 on 2010-11-06
Like I said,had it in my previous setups.To fully run that cleanup script (this part being the firefox' cache cleanup part) I add my default and root profile to the script. I'm not planning to run Firefox in root whatsoever.It's merely a part of that script.
like:rm -rf $homepath.mozilla/firefox/$userprofile.default/Cache/*
sudo sh -c "rm -rf /root/.mozilla/firefox/$rootprofile.default/Cache/*"

---

### Post by uRock on 2010-11-06
A few releases ago they stopped adding profile folders such as .mozilla to the root account. You'll have to create it manually or alter your script.

To make it, either log into the terminal as root and create it with the **mkdir** command or open nautilus with **gksudo nautilus** and create the folder.

---

### Post by lovinglinux on 2010-11-06
> **dzon65 said:**
> Like I said,had it in my previous setups.To fully run that cleanup script (this part being the firefox' cache cleanup part) I add my default and root profile to the script. I'm not planning to run Firefox in root whatsoever.It's merely a part of that script.
like:rm -rf $homepath.mozilla/firefox/$userprofile.default/Cache/*
sudo sh -c "rm -rf /root/.mozilla/firefox/$rootprofile.default/Cache/*"

You don't need a Firefox profile in root. The script will ignore the missing folder, because it has -rf in the command. The -r means is recursive and the -f means "force". It will try to remove the folder and won't throw any errors if it doesn't exist.

You could also remove the root part from the script, since it is unnecessary.

---

### Post by dzon65 on 2010-11-06
> **lovinglinux said:**
> You don't need a Firefox profile in root. The script will ignore the missing folder, because it has -rf in the command. The -r means is recursive and the -f means "force". It will try to remove the folder and won't throw any errors if it doesn't exist.

You could also remove the root part from the script, since it is unnecessary.
Yeah,just did that.Works indeed without throwing errors.Thanks for the replies.
Kind regards,J.

---

