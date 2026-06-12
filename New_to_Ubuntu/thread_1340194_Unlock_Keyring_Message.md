---
title: "Unlock Keyring Message"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by Grendel336 on 2009-11-28
How do I stop that window from opening every time I log in? 

It asks for password. But I can also simply click cancel to get it to go away. 

How can I just stop it from appearing at all? 

Thanks for the help. 

I did not have this issue with older Ubuntu versions. 
It's only been with the newest release.

---

### Post by brij on 2009-11-29
hi 

delete the folder $home/.gnome2/keyrings which holds the keyring info. once you do that it wont ask again.

---

### Post by Marais on 2010-06-04
On Linux Lucid this known bug where the password prompt shows up everytime Evolution is launched is driving me NUTZ!

After the upgrade for Lucid Linux yesterday the problem has returned.

Before the upgrade a simple matter of disabling the gui in the startup manager.
Now all is disabled but Evolution keeps prompting for passwords.
I'm set up as an automatically signed in user.

I deleted the files in /home/juser/.gnome2/keyrings

I also deleted the folder itself  /home/juser/.gnome2/keyrings

I also deleted the file in

/home/user/.gnome2_private

all to no avail!

I uninstalled and reinstalled ubuntu-desktop (to reinstall gnome-keyrin. I did the same for seahorse.

Any suggestions? Mr. Google has run out of ideas:(:confused:

---

