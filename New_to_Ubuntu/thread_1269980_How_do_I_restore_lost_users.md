---
title: "How do I restore lost users?"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by cat2005 on 2009-09-18
I reinstalled a custom made ubuntu.  I did not format /home because I wanted to retain the multiple accounts I previously created.

After successful install I looked in /home and found the multiple accounts, just as I expected.  However, I was not able to re-create those users.  

For example:  I went to the user / group area and clicked "add new user".  I typed everything in correctly (making sure of spelling, etc) but got the message "Home Directory Already Exists - Please enter a different path".

Well, of course it already exists.  I can clearly see it.  

I need to recreate the user accounts.  Their "home" was preserved but not the accounts themselves.  The only account I now have is my default admin account.

Suggestions would be appreciated.

Thanks.

---

### Post by Paqman on 2009-09-19
You'll have to use the command line:
```
sudo adduser --no-create-home username
```

You might still strike permissions problems in which case you need to do one of:

[LIST]
[*]Specify the correct uid for each user when you create them
[*]OR set them up in the exact same order you did the first time
[*]OR run a quick "sudo chown -R username:username /home/username" on each home folder
[/LIST]

---

### Post by cat2005 on 2009-09-19
> **Paqman said:**
> You'll have to use the command line:
```
sudo adduser --no-create-home username
```You might still strike permissions problems in which case you need to do one of:

[LIST]
[*]Specify the correct uid for each user when you create them
[*]OR set them up in the exact same order you did the first time
[*]OR run a quick "sudo chown -R username:username /home/username" on each home folder
[/LIST]



Paqman,

You stated:  ". . .username:username. . ."

Did you mean ". . .username:groupname. . ." or not?

Forgive my ignorance.

Relatedly, what if I wanted to both:  a) make every subfolder and file inherit the permissions given to the "parent" folder and b) make every newly created subfolder and file inherit those same permissions?

That would be a big help!

---

### Post by Paqman on 2009-09-19
> **cat2005 said:**
> Paqman,

You stated:  ". . .username:username. . ."

Did you mean ". . .username:groupname. . ." or not?


Actually you're right, but so am I :)

Each user is a member of a group with the same name as their username. 

> 
Relatedly, what if I wanted to both:  a) make every subfolder and file inherit the permissions given to the "parent" folder and b) make every newly created subfolder and file inherit those same permissions?

That would be a big help!

That's exactly what the -R flag in the chown command I gave does. It stands for "recursive", which is geek speak for a command that burrows down through the directory structure, applying itself to everything.

---

