---
title: "Terminal Says Password is too simple??"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by raziiq on 2009-05-19
I am trying to change the password of my account but when i type this command

**sudo /etc/passwd**

it asks me for my password and then asks me to enter a new password and when i m trying to enter my new password, it says, it is too simple.

How to Force it use the password i m passing??

---

### Post by rajeev1204 on 2009-05-19
> **raziiq said:**
> I am trying to change the password of my account but when i type this command

**sudo /etc/passwd**

Change passwords with this command sudo passwd <username>

Give whatever you like

regards
rajeev

---

### Post by darsie on 2009-05-19
> **raziiq said:**
> I am trying to change the password of my account but when i type this command

**sudo /etc/passwd**



If you are changing the password for your account you do not need to sudo. Just type:

```
passwd
```

If it says the password is to weak, then use a stronger password! Add some numbers, punctuation or caps.

---

### Post by rajeev1204 on 2009-05-19
> **darsie said:**
> If you are changing the password for your account you do not need to sudo. Just type:

```
passwd
```

If it says the password is to weak, then use a stronger password! Add some numbers, punctuation or caps.


You dont understand his question.He needs to use whatever password he likes , not what the system tells him

```
sudo passwd <username>
```

The above code does it without acting like your parents. :)

---

### Post by raziiq on 2009-05-19
> **rajeev1204 said:**
> You dont understand his question.He needs to use whatever password he likes , not what the system tells him

```
sudo passwd <username>
```

The above code does it without acting like your parents. :)

Hey thanks Man, it worked for me, your post was of great help.

One more question though, as root is disabled by default in uBuntu, i think using this command will also enable root right??

**sudo passwd root**

---

### Post by davetv on 2009-05-19
post removed due to forum rules

---

### Post by _Purple_ on 2009-05-19
Please read this
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by davetv on 2009-05-19
very sorry - didnt know

---

### Post by davetv on 2009-05-19
while I'm here ... let me tell you about why I removed my post (rules) and why those rules are good by me.

About 4 months ago or so ... I installed a quake client in /usr/local/share/games .... then I changed my mind about the client I wanted.

DO NOT DO THIS.

I logged in as root, and typed rm -rf /usr/local/share/games/quake/ * ... note the space between the / and the * 

It deleted EVERYTHING off my laptop .... operating system and all .... I was lucky that all was backed up.

It's probably a lesson for all users .. noob or otherwise.

The forum rules are ok.

---

### Post by rajeev1204 on 2009-05-19
> **raziiq said:**
> Hey thanks Man, it worked for me, your post was of great help.

One more question though, as root is disabled by default in uBuntu, i think using this command will also enable root right??

**sudo passwd root**

Forum rules discourage 'enable root user' questions.Also, i dont know or dont need root user acess so i cant answer your question.

Recovery mode also logs you in as root .Without a password.

But its easy to figure out how to enable it.Google it for answers.

Cheers !;)

regards
rajeev

---

### Post by rajeev1204 on 2009-05-19
> **davetv said:**
> while I'm here ... let me tell you about why I removed my post (rules) and why those rules are good by me.

About 4 months ago or so ... I installed a quake client in /usr/local/share/games .... then I changed my mind about the client I wanted.

DO NOT DO THIS.

I logged in as root, and typed rm -rf /usr/local/share/games/quake/ * ... note the space between the / and the * 

It deleted EVERYTHING off my laptop .... operating system and all .... I was lucky that all was backed up.

It's probably a lesson for all users .. noob or otherwise.

The forum rules are ok.

I believe that step is possible even with sudo and a rm -rf.

---

### Post by sisco311 on 2009-05-19
> **raziiq said:**
> 
One more question though, as root is disabled by default in uBuntu, 


No, the root account is not disabled, the root account password is locked. The /etc/shadow file contains encrypted password as well as other information such as account or password expiration values, etc.
i.e.
```

sudo cat /etc/shadow 
...
root:**!**:14383::::::                                #locked root account
sisco:**!$1$Qi97C0h3$F00ldPm21**:14314:0:99999:7:::   #locked account
...
sisco311:**$1$Qi97XdPR11**:14314:0:99999:7:::  #enabled account with a password 

```
 
[noparse]
The "!" entry (eg. :!: or :!$1$Qi97C0h3$F00ldPR1337KcWuT:) indicates the account password has been locked.[/noparse]

Since the root account exists it is still possible to run commands with root-level privileges. 
sudo allows users belonging to the admin group to run certain programs as root without having to know the root password.

[uhelp]community/RootSudo[/uhelp] 
[http://www.cyberciti.biz/faq/understanding-etcshadow-file/]("http://www.cyberciti.biz/faq/understanding-etcshadow-file/")

---

### Post by davetv on 2009-05-19
no doubt a sudo command woulda done it rajeev ... I was in "/" at the time .... was it the space? or was it dumb ... or both .. I still laugh ... it made me upgrade from feisty to hardy ... so all's not bad.

---

