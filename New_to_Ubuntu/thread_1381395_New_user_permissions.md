---
title: "New user permissions"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by Chrisco66 on 2010-01-14
I have an installation of 9.10 that is just the way I want it.  I would like to let my kids use the computer, but I dont want them to be able to do any damage.  Here are my questions:

1.  If I set up a new user, what permissions should I allow?  For example, if I want them to be able to use Synaptic, do I have to enable the "administer the system" checkbox in "users and groups"?  Do I need to remove the new user from any groups to protect my installation?  

2.  Is there a list of all the groups, and what they do?  I am still confused about the relationship between user privileges and group membership.  If I add a user to a group, does that user get the privileges of the all other members of that group?  I understand the owner, group, and other concept when it comes to files, and the user, group thing seems to be similar.  

3.  Ubuntu automatically adds a new group with the name of the user when created.  If I add a user "me", there will be a group named "me". There is also a groups called "user".  What is the significance of this?  If I use "users and groups" and remove the new user from its own group, what will happen?  The new user is still a member of other groups. As you can see, I'm a little lost.  

I have looked all over for a simple explanation of how the group membership is related to the "privileges" in the users and groups settings.  I read the free guide provided by Keir Thomas.  It helps, but still doesn't answer my question.  I also read the article by psychocats (did I spell that right), and it helps too, but Im still not seeing the relationship to groups and privileges.  Any help would be appreciated.

Thanks in advance..

---

### Post by yeats on 2010-01-14
Hi,

I have a similar situation.  I let my young son have a log in and that works really well for both of us.

> 1. If I set up a new user, what permissions should I allow? For example, if I want them to be able to use Synaptic, do I have to enable the "administer the system" checkbox in "users and groups"? Do I need to remove the new user from any groups to protect my installation?

Probably "desktop user" would be fine.  This does not allow software installation, but it does let them customize their desktop and shut down the computer.  The desktop user would not be added to any administrative groups that you'd need to worry about IMHO.

> 
2. Is there a list of all the groups, and what they do? I am still confused about the relationship between user privileges and group membership. If I add a user to a group, does that user get the privileges of the all other members of that group? I understand the owner, group, and other category when it comes to files, and the user, group thing seems to be similar.

The System -> Administration -> Users and Groups has a list if you click Manage Groups, but it does not explain what each group does.  Most groups are named for the program that has permission levels, though, so Google will help.  If you add a user to a group, yes, that user would inherit those permission levels.

> 3. Ubuntu automatically adds a new group with the name of the user when created. If I add a user "me", there will be a group named "me". There is also a groups called "user". What is the significance of this? If I use "users and groups" and remove the new user from its own group, what will happen? The new user is still a member of other groups. As you can see, I'm a little lost

Each user has a group, and if you added a user to "your" group, that user would have permissions on all your files.  If you only wanted to share one file at a time, you would have to grant permissions - read, write, and execute - one at a time per file. 

> I have looked all over for a simple explanation of how the group membership is related to the "privileges" in the users and groups settings. I read the free guide provided by Keir Thomas. It helps, but still doesn't answer my question. I also read the article by psychocats (did I spell that right), and it helps too, but Im still not seeing the relationship to groups and privileges. Any help would be appreciated.

Keep looking - this information is out there.  I have actually found books helpful.  Users, groups, and permissions are *ancient* computer-wise and any Linux/Unix book from the past 10 years would cover that level of concepts well.

---

### Post by llamabr on 2010-01-14
I think you're overthinking it.  Linux will understand what you mean when you create a new user and want that user to be 'just a user'.  There's no reason for someone like that to use synaptic.  If you trust them with that responsibility, then you might as well open everything up, and give them sudo access.

On the other hand, if they need something installed, they can ask you.  Just add a user.

You're now a system administrator with users.  Welcome to the nightmare.

---

### Post by yeats on 2010-01-14
> You're now a system administrator with users. Welcome to the nightmare.

That's true too!  You'll probably want to implement some sort of Helpdesk ticketing system before long!:D

---

### Post by Chrisco66 on 2010-01-15
Thank you both for your replies.  I tried to reply a few hours ago at work but the computer I was using kept locking up.  Its running win 7--lol.

I guess the kids really don't need to use Synaptic.  I see what you mean by welcome to the nightmare.  I can see the kids coming at me one at a time with software requests.  Maybe Ill start pulling my hair out now to get a head start?  

I experimented a little on another computer.  I think I have it figured out..CDL

---

