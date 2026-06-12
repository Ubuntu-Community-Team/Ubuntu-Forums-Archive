---
title: "Log Out confused: Missing shutdown, hibernate, etc on one account"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-07-19
I've installed Xubuntu on an old machine, and it works fine.

On my account, the menu has Log Out with a little green running man as a picture [IMG]http://ubuntuforums.org/attachment.php?attachmentid=121639&stc=1&d=1248013260[/IMG].

When I press it, it immediately logs me out and takes me to the login screen.

On the other hand, on my daughter's account, the menu has Log Out with a grey door and red arrow [IMG]http://ubuntuforums.org/attachment.php?attachmentid=121638&stc=1&d=1248013260[/IMG].

When I press it, it asks whether I want to Log Out, Restart, Shut Down, Suspend or Hibernate.

How can I get my account to use the more flexible door instead of the green running man?

---

### Post by Paddy Landau on 2009-07-21
bump?

---

### Post by mhurst102282 on 2009-07-21
Can we see a screenshot of the menu?

---

### Post by adam_kimber on 2009-07-21
You could try Applications > Settings > Menu Editor to see if it is unchecked and re-check it!

---

### Post by Paddy Landau on 2009-07-21
> **mhurst102282 said:**
> Can we see a screenshot of the menu?
Sorry, the Print Screen button doesn't work when the menu is up.

> **adam_kimber said:**
> You could try Applications > Settings > Menu Editor to see if it is unchecked and re-check it!
Well, it's Main Menu, not Menu Editor.

But...

I found it!

The reason that mine is a different icon has nothing to do with its action. I've obviously changed the icons through Applications > Settings > Appearance > Icons.

The reason that it didn't prompt me was that, somehow, I must have accidentally changed the "Prompt on Logout" flag:

Applications > Settings > Settings Editor > xfce4-session > general > PromptOnLogout.

Don't ask me how!

Thanks for your suggestions, as they led to me to the solution.

---

