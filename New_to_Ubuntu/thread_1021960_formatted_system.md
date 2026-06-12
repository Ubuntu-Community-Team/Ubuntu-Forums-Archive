---
title: "formatted system"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by phanipalagummi on 2008-12-26
To day i formatted my system to 8.10 from 8.04,because for the following problems.

my promt is like this in terminal
[HTML]I have no name!@dheera-desktop ~$ 
[/HTML]

and when i typed this
```
sudo fdisk -l
```
i got this

[HTML]sudo:uid 1000 does not exist in the passwd file[/HTML]

i dont know what happend exactly,finally my whole system got stuck,then i formatted my system,i tried to restart it but my hdd is not booting,
is my system got hacked,what exactly happend,i want to know please any one help me

---

### Post by northern lights on 2008-12-26
Your username was "I have no name!" before the troubles already or did it change without your input?

The latter'd be rather wicked indeed.

If you've formatted your hdd and reinstalled though, your system, even should you have gotten "hacked" (which I first off all highly doubt and further dislike the terminology for malicious breaching), would be clean again.

Can you describe the current situation in more detail?

You've tried to set up a new system, where does that fail?

---

### Post by hovzio on 2008-12-26
Hi, what do you mean, you formatted your system from 8.4 to 8.10? Did you upgrade to it or did you try installing intrepid from scratch. If you suspect that your system was breached (very unlikely but possible) then an upgrade probably wouldn't help much.

To the error after your  sudo command, this simply means the user is not part of the admin group. Did you create a new users and login under the new user? If so you may have not added the new user to the admins group. I would suggest firing up a live cd (intrepid) and doing  fresh install. (If this is not what you have already done.)

The above must not necesarrily be the case, if not it does sound rather awkward indeed, are you saying that your prompt just has no name in it or does it literaly say "has no name@~$..". That would be kinda freaky. If your username is just "not mentioned" you need to modify your $PS1 variable.

---

### Post by shankhs on 2008-12-26
phanipalagummi try doing one thing reboot anf login as root.I hope you know your root password change the passwd and username of the "I have no name!" account to the one you liked it.

Google if you dont know how to change username and passwd in fact to change passwd just type passwd <your account>

P.S. Please use the word "CRACK" for something that allegedly compromised the security of your system.

---

### Post by northern lights on 2008-12-26
> **shankhs said:**
> phanipalagummi try doing one thing reboot anf login as root.I hope you know your root password.The root account is disabled in Ubuntu by default. It is not very advisable to enable it either. I assume you mean a user account that is in the admin group.

> **shankhs said:**
> P.S. Please use the word "CRACK" for something that allegedly compromised the security of your system.
+1 for that one.

---

### Post by shankhs on 2008-12-28
> **northern lights said:**
> The root account is disabled in Ubuntu by default. It is not very advisable to enable it either. I assume you mean a user account that is in the admin group.


+1 for that one.
This is an interesting post.I wonder where the thread starter went I would like to hear more about his problem.
First of all northern_lights as much I know during installation only one user in admin group is added(ya later you can add more) so if anyones linux system is cracked either use sudo before every command or enable root login once (surely thats a risk ).
phanipalagummi is having a problem in his HDD try to check the integrity of HDD boot using live CD if you can start your HDD at all.
Tell us about your BIOS setting.
If its cracked then how come your HDD not booting even after clear format???
So its not cracked(not after you did a clean install unless you were using ubuntu image downloaded directly from ubuntu site not from any other malicious site) but something else...
Answer a few question:
1.From where you downloaded your image from?
2.Was you installation proper?
3.Do you have a dual boot?

---

### Post by shankhs on 2008-12-28
> **northern lights said:**
> The root account is disabled in Ubuntu by default. It is not very advisable to enable it either. I assume you mean a user account that is in the admin group.


+1 for that one.
This is an interesting post.I wonder where the thread starter went I would like to hear more about his problem.
First of all northern_lights as much I know during installation only one user in admin group is added(ya later you can add more) so if anyones linux system is cracked either use sudo before every command or enable root login once (surely thats a risk ).
phanipalagummi is having a problem in his HDD .try to check the integrity of HDD , boot using live CD if you can't start your HDD at all.
Google and you will get lots of apps in *nix that will check whether your HDD is correct or not.
Tell us about your BIOS setting.
If its cracked then how come your HDD not booting even after clear format???
So its not cracked(not after you did a clean install unless you were using ubuntu image downloaded directly from ubuntu site not from any other malicious site) but something else...
Answer a few question:
1.From where you downloaded your image from?
2.Was you installation proper?
3.Do you have a dual boot?

---

