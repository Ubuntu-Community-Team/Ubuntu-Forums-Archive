---
title: "Help with tcsh/.cshrc"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by bhargava470 on 2009-07-18
Hi all,

I'av been using bash shell for a while now ... now I am interested to try tcsh I installed tcsh and changed the shell entry in the /etc/passwd to /bin/tcsh. now I want to add to the PATH but I'm not able to find .cshrc file in  ~. can someone tell me which settings is the tcsh following now ( there has to be some configuration file for it right:confused:  correct me if I'm wrong) 

How can I configure the environment for TCSH.... can I have a sample tcshrc file anywhere.

Any help in this regard is apreciated.

Thanks

---

### Post by The Tronyx on 2009-07-18
Hello,

Have you actually logged back in since changing your shell in /etc/passwd?  Once the changes take effect, after the edit to /etc/passwd and you log in, you should automatically be using tcsh and have the profile created for you automagically.

You can verify what your current shell is by using echo $SHELL as seen below.

> 
tronyx@wrekx:~$ echo $SHELL
/bin/bash


---

### Post by shodai100 on 2009-07-18
Hey,

Ubuntu does not install with tcsh, but you can get it by doing the following:

Go to the terminal.

put in the following code:

"sudo su"
"apt-get update"
"apt-get install tcsh"

done.

---

### Post by bhargava470 on 2009-07-18
> **The Tronyx said:**
> Hello,

Have you actually logged back in since changing your shell in /etc/passwd?  Once the changes take effect, after the edit to /etc/passwd and you log in, you should automatically be using tcsh and have the profile created for you automagically.

You can verify what your current shell is by using echo $SHELL as seen below.

yes I did logout and logged in back ...but only to find that there was no config file ... however the default shell now is tcsh  > echo $SHELL  /bin/tcsh 
but I dont see any .cshrc (or anything like .tcshrc) 
```
ls -a | grep rc
.bashrc
.dmrc
.screenrc
```Thanks

---

### Post by The Tronyx on 2009-07-19
If it's not being created by default I believe you may just need to create your own.

---

### Post by bhargava470 on 2009-07-19
I guess I should do that. Thanks [The Tronyx]("http://ubuntuforums.org/member.php?u=171935")

---

### Post by bhargava470 on 2009-07-19
I almost finished configuring the .cshrc file. But what I really want to have is this:

for example if I type cabextract in bash (which is not installed on my system) I get the following message:
```
cabextract
The program 'cabextract' is currently not installed.  You can install it by typing:
sudo apt-get install cabextract
bash: cabextract: command not found
```But if I do the same in tcsh it just shows 
```
cabextract
cabextract: Command not found.
```I want this feature. coz I can know for sure that I didnt spell the command wrongly.It is difficult for me to remember all the programs installed in the system. 

I'm not very good in scripting (still waking my first steps). So if any one can tell me how I can get this feature in the tcsh shell too.

Thanks.

---

