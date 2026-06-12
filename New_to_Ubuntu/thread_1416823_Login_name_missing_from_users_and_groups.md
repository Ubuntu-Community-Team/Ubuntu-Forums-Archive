---
title: "Login name missing from users and groups"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by Michaelg14 on 2010-02-26
My login name, the one I installed 9.10 with is not showing up in users and groups.  When I try to add it I get a user name already exists error

I can't use USB devices in Virtualbox without enabling my user name in users and groups.

Thoughts?

---

### Post by CharlesA on 2010-02-26
Are you an administrator or restricted user?

---

### Post by Michaelg14 on 2010-02-26
I am the user that installed Ubuntu.  It asks for a name and password during the install process.  That name is not showing up.  Root is shown but that is the only name listed.  My login name "greybeard" is not.

Mike

---

### Post by Michaelg14 on 2010-02-26
I assume from the deafening silence that I am the only one having this problem.  This is also a shameless bump message.

Mike

---

### Post by Post Monkeh on 2010-02-26
> **Michaelg14 said:**
> I assume from the deafening silence that I am the only one having this problem.  This is also a shameless bump message.

Mike

what account are you using to log in? greybeard?

---

### Post by Joeb454 on 2010-02-26
> **Michaelg14 said:**
> I assume from the deafening silence that I am the only one having this problem.  This is also a shameless bump message.

Mike

3 hours is neither a deafening silence, nor a long enough time to bump ;) 24 hours on the other hand....

Can you actually login AS greybeard?

---

### Post by Michaelg14 on 2010-02-26
I am logging in as greybeard but doing it automaticly.  All other functions work as advertised and my log-in password works fine.  I need to use Virtualbox and need to enable greybeard in the virtualbox group.  greybeard is not showing up.  The only user showing up anywhere is root.  When I try to add greybeard from the gui or in a terminal I get a message saying the user already exists.  

Thanks.

I just logged out and back in manually and nothing changed.

Mike

---

### Post by Post Monkeh on 2010-02-27
[http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/](http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/)
that page explains how to add a user to a group from the command line.

my virtualbox group is called "vboxusers", just make sure you're trying to add yourself to the right group.

that doesn't explain why your name doesn't appear in the users and groups list, but it may solve your immediate problem

---

### Post by Michaelg14 on 2010-02-28
No matter how I try to add a user I get the same message "greybeard already exists".  It just doesn't show up in my group list.  Virtualbox will not use USB devices without it.

Mike

---

### Post by Post Monkeh on 2010-02-28
> **Michaelg14 said:**
> No matter how I try to add a user I get the same message "greybeard already exists".  It just doesn't show up in my group list.  Virtualbox will not use USB devices without it.

Mike

don't try to add a user, try to add your user to the right group.


if your name is greybeard, and your virtualbox setup is like mine (the group is called vboxusers)

```
usermod -a -G vboxusers greybeard
```

then that command in a terminal should work. just make sure that your virtualbox group is called vboxusers (you should be able to check this in your users & groups of the administration menu)
it may still not work, there's obviously something funny going on when your user has disappeared from the main users list.

---

### Post by Michaelg14 on 2010-02-28
Thanks but it didn't work.  I have, since this started, reinstalled 9.10 for another reason, and it is still not putting greybeard in my user list.

The group ID for vboxusers is 0 It is usually 123 I think.

mike

---

### Post by Post Monkeh on 2010-02-28
it's 121 on mine. 0 should be the root group, it seems your groups have been screwed up.

i don't know why that wouldn't have sorted itself with a reinstall though. did you reformat when you reinstalled? sorry i can't be of more help

---

### Post by Michaelg14 on 2010-02-28
I did reformat but I have a separate home partition that I didn't format.  Maybe I will back it up and try reformatting it.

Mike

---

### Post by Post Monkeh on 2010-02-28
hmm. i'm no expert, but i think the files controlling your users and group settings are in the usr folder, so i don't understand why they wouldn't sort themselves after

---

### Post by Michaelg14 on 2010-02-28
Whatever the problem was it cleared up when I formatted the home partition.  It also cleared up a couple other minor issues.  I guess a good house cleaning is in order once in a while.

Thanks for all the responses, I appreciate the help.

Mike

---

