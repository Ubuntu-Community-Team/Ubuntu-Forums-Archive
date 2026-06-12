---
title: "How to apply a Simple Password..? (ubuntu says it is too SHORT) I WANT SHORT.."
date: 2010-04-30
forum: New to Ubuntu
---

### Post by rsroxxx on 2010-04-30
I have been using Ubuntu from a Week..!
I used a STRONG password(12 characters) before. But now, i want to change it to a simpler one, about 5-6 characters..!
   But when i try changing it, ubuntu says, "your new password is too short", and simply discards it :(
   I understand that for security reasons, i should get a bigger complex password..! BUT I WANT A SMALL SIMPLE PASSWORD, so that my 5 yr old daughter can remember it easily..! Now. How can i do that...?

---

### Post by madjr on 2010-04-30
the 4 top passwords

Love
God
Sex

and

dang forgot... *go undusts hackers*

so i can see that since yours is 3 chars long is either Sex or God


btw, my 5 year old son, knows a 6 char password hehe

---

### Post by swoll1980 on 2010-04-30
> **rsroxxx said:**
> I have been using Ubuntu from a Week..!
I used a STRONG password(12 characters) before. But now, i want to change it to a simpler one, about 5-6 characters..!
   But when i try changing it, ubuntu says, "your new password is too short", and simply discards it :(
   I understand that for security reasons, i should get a bigger complex password..! BUT I WANT A SMALL SIMPLE PASSWORD, so that my 5 yr old daughter can remember it easily..! Now. How can i do that...?

You can set it manually in the config file. Might be /etc/passwd Google it. You can also change the limit too.

---

### Post by clive littlewood on 2010-04-30
Hi

Sorry but I think the minimum is 6 characters.

To change that will be a config issue (above my head)

Clive

---

### Post by mikewhatever on 2010-04-30
Why does you 5 year old daughter need to enter a password? Is she supposed to install programs or administer the system?

---

### Post by JamezQ on 2010-04-30
> **rsroxxx said:**
> I have been using Ubuntu from a Week..!
I used a STRONG password(12 characters) before. But now, i want to change it to a simpler one, about 5-6 characters..!
   But when i try changing it, ubuntu says, "your new password is too short", and simply discards it :(
   I understand that for security reasons, i should get a bigger complex password..! BUT I WANT A SMALL SIMPLE PASSWORD, so that my 5 yr old daughter can remember it easily..! Now. How can i do that...?

Why not just make it a simple word. Like, Skipping.

---

### Post by P4man on 2010-04-30
Open a terminal and type
```
sudo passwd
```

Lets you change your pw and it can be as long or short as you want.

But I agree that your daughter shouldnt have to enter one to log in (you can disable that) and not be allowed to use it for administrative purposes,

---

### Post by swoll1980 on 2010-04-30
> **jamezq said:**
> why not just make it a simple word. Like, skipping.

123456

---

### Post by swoll1980 on 2010-04-30
> **mikewhatever said:**
> Why does you 5 year old daughter need to enter a password? Is she supposed to install programs or administer the system?

so she can log in?

---

### Post by madjr on 2010-04-30
> **swoll1980 said:**
> 123456

exactly

or just auto-logon

---

### Post by P4man on 2010-04-30
> **swoll1980 said:**
> 123456

So then you have  a 6 character password that is even less secure than almost any 3 character pw. Might as well make it a 2 or 3 character pw then.

---

### Post by swoll1980 on 2010-04-30
> **P4man said:**
> So then you have  a 6 character password that is even less secure than almost any 3 character pw. Might as well make it a 2 or 3 character pw then.

He doesn't want a password it's for his 5 year old kid.

---

### Post by rsroxxx on 2010-04-30
Well, u cant use a simple (5-6 character or less) password.
Ubuntu wont accept a small password..!
I've tried all the above solutions, they simply wont work..!

I cant find any config file either, which i can manipulate(to decrease the password string length :( )

The best option would be to simply to set a password with her nick name and put her b'date in succession...!

---

### Post by rsroxxx on 2010-04-30
[SIZE=1]> **P4man said:**
> Open a terminal and type
```
sudo passwd
```Lets you change your pw and it can be as long or short as you want.

But I agree that your daughter shouldnt have to enter one to log in (you can disable that) and not be allowed to use it for administrative purposes,

[/SIZE]  
[SIZE=2]It doesnt works. terminal says -  [/SIZE]"Sorry Try Again."
and after 3 tries, it asks u, to repeat everythin again..

---

### Post by P4man on 2010-04-30
> **rsroxxx said:**
> Well, u cant use a simple (5-6 character or less) password.
Ubuntu wont accept a small password..!
I've tried all the above solutions, they simply wont work..!

You must have overlooked my post, because it does work. Create the user, set a long password, open a terminal and type

sudo passwd username_of_your_daughter

enter your current password (of the user that is logged in), then the new one for your daughter. done. It even accepts a one letter password

---

### Post by mikewhatever on 2010-04-30
> **swoll1980 said:**
> so she can log in?

Autologin, what's wrong with that?

---

### Post by P4man on 2010-04-30
> **mikewhatever said:**
> Autologin, what's wrong with that?

I do suppose his 5 year old is not the only user of that pc, so having a login screen is useful :) But you can disable asking a password on login, at least for previous versions, I assume its the same on lucid, and I agree that would be better. Have a regular password for the daughter, just skip asking it in the login screen.

---

### Post by rsroxxx on 2010-04-30
> **P4man said:**
> You must have overlooked my post, because it does work. Create the user, set a long password, open a terminal and type

sudo passwd username_of_your_daughter

enter your current password (of the user that is logged in), then the new one for your daughter. done. It even accepts a one letter password



i created a new user (username = nat)
set a long password, say 123456789
everything is fine.

now, i tried in terminal, "sudo passwd nat" 
it asks for a pass... Cool, ha..?
n THEN, when i type any password ranging from 123456, or as u say, a single letter N.
it simply says, TRY AGAIN..!
n after 3 tries, u end up where u begun.

So, it DOESNT works. i can send u screenshots, or put my pc on remote support for u if u want..! but trust me, it wont work :(

---

### Post by Kenny_Larsen on 2010-04-30
Have you considered the above suggestion of setting a usual password (yours will do) for your daughters account and then just not requiring it at login? It's probably safer anyway as a failsafe against accidents!

---

### Post by P4man on 2010-04-30
> **rsroxxx said:**
> i created a new user (username = nat)
set a long password, say 123456789
everything is fine.

now, i tried in terminal, "sudo passwd nat" 
it asks for a pass... Cool, ha..?

please read carefully. It asks for YOUR password first. Because the operation you are about to do (change someone elses password) requires you to become root (sudo). So just enter your password first. then it will ask the new password for nat, which can as short as you want.

here, my login is bob, I created a new user called nat.
```

**bob**@bob-desktop:~$ sudo passwd nat
[sudo] password for **bob**: [COLOR="Red"]( I enter my super secure password)[/COLOR]
Enter new UNIX password: [COLOR="Red"](i enter x)[/COLOR]
Retype new UNIX password: [COLOR="Red"](i enter x again)[/COLOR]
passwd: password updated successfully
```

user nat now has x as password.

Agreed with everyone suggesting no password on login though, but really it can be changed to a short one as well.

---

### Post by rsroxxx on 2010-04-30
> **P4man said:**
> please read carefully. It asks for YOUR password first. Because the operation you are about to do (change someone elses password) requires you to become root (sudo). So just enter your password first. then it will ask the new password for nat, which can as short as you want.

here, my login is bob, I created a new user called nat.
```

**bob**@bob-desktop:~$ sudo passwd nat
[sudo] password for **bob**: [COLOR=Red]( I enter my super secure password)[/COLOR]
Enter new UNIX password: [COLOR=Red](i enter x)[/COLOR]
Retype new UNIX password: [COLOR=Red](i enter x again)[/COLOR]
passwd: password updated successfully
```user nat now has x as password.

Agreed with everyone suggesting no password on login though, but really it can be changed to a short one as well.

hey thanks..!
n u were ryt, i overlooked it..it Works :)

---

### Post by P4man on 2010-04-30
> **rsroxxx said:**
> hey thanks..!
n u were ryt, i overlooked it..it Works :)

Good, but not the best solution for your problem.

Does anyone know how to enable a specific user to login without password on lucid?

---

### Post by imbjr on 2010-04-30
> **P4man said:**
> Good, but not the best solution for your problem.

Does anyone know how to enable a specific user to login without password on lucid?

Yes, there is a way. I do this for my parent's machine - but the admin account still has a password.

Basically, it involves very careful editing of the /etc/shadow file such that the encrypted password for a given user is the same as that you will find for a the Ubuntu user on the Live CD. After that they just have to select their user id and press enter - no password entered, tho I suspect internally the password is something like "", i.e. an empty string.

---

### Post by sisco311 on 2010-04-30
> **P4man said:**
> Good, but not the best solution for your problem.

Does anyone know how to enable a specific user to login without password on lucid?

System -> Administration -> Login Screen

---

### Post by P4man on 2010-04-30
> **sisco311 said:**
> System -> Administration -> Login Screen

I dont want autologin. i want to be able to select my user, but some users I want to log in without entering their password. My nephew is growing up quickly but I dont think he's good at touch typing yet, nor remembering passwords for PC he uses for gcompris a few times per month.

---

### Post by sisco311 on 2010-04-30
> **P4man said:**
> I dont want autologin. i want to be able to select my user, but some users I want to log in without entering their password. My nephew is growing up quickly but I dont think he's good at touch typing yet, nor remembering passwords for PC he uses for gcompris a few times per month.

Add the user to the nopasswdlogin group.

---

### Post by P4man on 2010-04-30
> **sisco311 said:**
> Add the user to the nopasswdlogin group.

Oh nice! They certainly made that easier, so easy I couldnt find it for my life lol. thanks!

---

### Post by sisco311 on 2010-04-30
> **P4man said:**
> Oh nice! They certainly made that easier, so easy I couldnt find it for my life lol. thanks!

You're welcome!

Yep, my first guess was to write a [pam]("http://en.wikipedia.org/wiki/Pluggable_Authentication_Modules") policy, but they beat me to it. :)  


Just in case someone is wondering, it's in the /etc/pam.d/gdm file:
```
...
auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
...

```

---

### Post by AlexanderDGreat on 2010-07-21
Thank you it worked for me. But what's the difference between:

sudo passwd (username) VS

sudo passwd **$**username ? Anyone?

I saw it in a 2006 thread here: [http://ubuntuforums.org/showthread.php?t=145255]("http://ubuntuforums.org/showthread.php?t=145255")

---

### Post by sisco311 on 2010-07-21
$username is the value of the username variable:
```
username=AlexanderDGreat
echo $username    #or
passwd $username
```

In this case both username and $username are just placeholders like [foobar]("http://en.wikipedia.org/wiki/Foobar"), you have to replace them with your login name:
```
passwd AlexanderDGreat
```

---

### Post by AlexanderDGreat on 2010-07-21
Thank you! So that's it.

---

### Post by theproles on 2012-10-22
> **P4man said:**
> Open a terminal and type
```
sudo passwd
```

Lets you change your pw and it can be as long or short as you want.



P4man is right. You simply enter your password using the code above, press Return/Enter, then enter your new password twice. Easy peasy.

---

### Post by coffeecat on 2012-10-22
Old thread - closed.

---

