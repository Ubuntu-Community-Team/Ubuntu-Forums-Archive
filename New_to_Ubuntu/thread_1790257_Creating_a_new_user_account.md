---
title: "Creating a new user account"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by anyutka2009 on 2011-06-24
How do I create a new user account in addition to mine?
I created one before, but deleted it, now can't figure it out.
Tried the command line sudo adduser... it doesnt work
Please Help!!

---

### Post by Rex Bouwense on 2011-06-24
Just go to Administration->Users and Groups.  Add a user.  You are there.

---

### Post by -kg- on 2011-06-24
There are many guides on the 'net, as well as on the Ubuntu site.  I don't know how much it varies, but the version you're using would be helpful.

In fact, I encourage you to go to the "User CP" above and include the version of Ubuntu/Kubuntu/Whatever-buntu you're using.  That way, someone who is able to help you will at least know which of the 'buntus you're using without having to ask.

---

### Post by haqking on 2011-06-24
> **anyutka2009 said:**
> How do I create a new user account in addition to mine?
I created one before, but deleted it, now can't figure it out.
Tried the command line sudo adduser... it doesnt work
Please Help!!

Wiki knows all ;-)

[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

---

### Post by nothingspecial on 2011-06-24
> **anyutka2009 said:**
> 
Tried the command line sudo adduser... it doesnt work


That may be a symptom of greater problems, because it should work.

What did you try?

---

### Post by anyutka2009 on 2011-06-24
> **nothingspecial said:**
> That may be a symptom of greater problems, because it should work.

What did you try?

command line : sudo adduser <username>

this is what i get:

bash: syntax error near unexpected token `newline'

---

### Post by haqking on 2011-06-24
> **anyutka2009 said:**
> command line : sudo adduser <username>

this is what i get:

bash: syntax error near unexpected token `newline'

stupid question but you are replacing the <username>with a username right ?

or that will happen the <> and contents is a placheolder

example sudo adduser bob

---

### Post by anyutka2009 on 2011-06-24
> **haqking said:**
> stupid question but you are replacing the <username>with a username right ?

or that will happen the <> and contents is a placheolder

example sudo adduser bob

yea.. i did...

---

### Post by haqking on 2011-06-24
> **anyutka2009 said:**
> yea.. i did...

ok so type exaclty what you are typing or show a prnt screen of your terminal output ?

---

### Post by anyutka2009 on 2011-06-24
> **haqking said:**
> ok so type exaclty what you are typing or show a prnt screen of your terminal output ?

OK! it worked! but this is what it says next:

adduser: Please enter a username matching the regular expression configured
via the NAME_REGEX[_SYSTEM} configuration variable.  Use the `--force-badname'
option to relax this check or reconfigure NAME_REGEX.

---

### Post by anyutka2009 on 2011-06-24
and... i need it without a password...

---

### Post by haqking on 2011-06-24
> **anyutka2009 said:**
> OK! it worked! but this is what it says next:

adduser: Please enter a username matching the regular expression configured
via the NAME_REGEX[_SYSTEM} configuration variable.  Use the `--force-badname'
option to relax this check or reconfigure NAME_REGEX.

it works now ? so you were typing the <username> ? ;-)

were you using numbers ?

it wouold be easier if you show is an image of your output so we can see anything you might be doing wrong

---

### Post by dFlyer on 2011-06-24
You not using any caps in your user name are you. Caps are not allowed.

---

### Post by nzjethro on 2011-06-24
Good-oh. If possible, do you want to post what you were doing  wrong so that others know what to do if they have the same problem? By the looks of it, you're using illegal characters in your username. Luckily, it's telling what to do in the error message! IF it's capitals, remove them, a username can't contain capitals. If it's all numbers, try:

```
sudo adduser --force-badname <username>
```

As for the password, it's probably easier to add a password to your account, and then remove it when the account is established. I'm not even sure if you can make a password-free account, so put in an easy-to-remember password, and then we'll shaw you how to remove it when it's set up.

---

### Post by anyutka2009 on 2011-06-24
> **haqking said:**
> it works now ? so you were typing the <username> ? ;-)

were you using numbers ?

it wouold be easier if you show is an image of your output so we can see anything you might be doing wrong

I created the account now... i just had these <> in....
but how can i have NO passwd?

---

### Post by haqking on 2011-06-24
> **anyutka2009 said:**
> and... i need it without a password...

use man adduser

it will show you your options

one is disable password

i am referring you to man instead of typing option to encourage the use of man

---

### Post by haqking on 2011-06-24
> **anyutka2009 said:**
> I created the account now... i just had these <> in....
but how can i have NO passwd?

yeah the <> are only placeholders

see above post for man on adduser for disabling password (not recommended)

it is not an admin user you are creating is it ?

however remember there is a minimum password enforcement in ubuntu which i think is 4 by default.

read here for more information

[https://help.ubuntu.com/8.04/serverguide/C/user-management.html](https://help.ubuntu.com/8.04/serverguide/C/user-management.html)

---

### Post by anyutka2009 on 2011-06-24
> **haqking said:**
> yeah the <> are only placeholders

see above post for man on adduser for disabling password (not recommended)

it is not an admin user you are creating is it ?

however remember there is a minimum password enforcement in ubuntu which i think is 4 by default.

read here for more information

[https://help.ubuntu.com/8.04/serverguide/C/user-management.html](https://help.ubuntu.com/8.04/serverguide/C/user-management.html)

no its not.... just a guest account.... i see the options.. but dont see the command line for it ;

 adduser  [options]  [--home  DIR]  [--shell  SHELL]  [--no-create-home]
       [--uid ID] [--firstuid ID] [--lastuid ID] [--ingroup GROUP | --gid  ID]
       [--disabled-password]      [--disabled-login]      [--gecos      GECOS]
       [--add_extra_groups] [--encrypt-home] user

---

### Post by haqking on 2011-06-24
> **anyutka2009 said:**
> no its not.... just a guest account.... i see the options.. but dont see the command line for it ;

 adduser  [options]  [--home  DIR]  [--shell  SHELL]  [--no-create-home]
       [--uid ID] [--firstuid ID] [--lastuid ID] [--ingroup GROUP | --gid  ID]
       [--disabled-password]      [--disabled-login]      [--gecos      GECOS]
       [--add_extra_groups] [--encrypt-home] user

well it is getting late for me and im typing crap ;-) and doing your searching with weary eyes.

because of default password enforcement i think you will need to edit the shadow file and rplace some of the encrypted characters which i cant remember right now.

but someone will post it or you could search for it ;-)

and remember a guest account with a blank password is a classic backdoor in...not recommended

---

### Post by haqking on 2011-06-24
I am feeling helpful
[http://www.jfriendly.net/index.php?option=com_content&view=category&layout=blog&id=43&Itemid=69](http://www.jfriendly.net/index.php?option=com_content&view=category&layout=blog&id=43&Itemid=69)

right hand side there is a small snippet and link to .pdf

do it at your own risk and beware of blank passwords.  it is not recommended

---

