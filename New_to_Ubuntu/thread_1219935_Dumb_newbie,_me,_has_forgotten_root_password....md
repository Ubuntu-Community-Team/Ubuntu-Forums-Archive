---
title: "Dumb newbie, me, has forgotten root password..."
date: 2009-07-22
forum: New to Ubuntu
---

### Post by johnnie j on 2009-07-22
is there any way I can recover this? I'd rather not have to re-install the OS.

---

### Post by HermanAB on 2009-07-22
Reboot, press Escape, select Single User (Safe) mode.  In console, type 'passwd'.

---

### Post by pro003 on 2009-07-22
If you forgot you password for your ubuntu system you can recover using the following steps

Turn your computer on.

Press ESC at the grub prompt.

Press e for edit.

Highlight the line that begins kernel ………, press e

Go to the very end of the line, add rw init=/bin/bash

press enter, then press b to boot your system.

Your system will boot up to a passwordless root shell.

Type in passwd username

Set your password.

Type in reboot

---

### Post by snowpine on 2009-07-22
There is no 'root password' in Ubuntu. You only need to remember one password, your user password. If you've forgotten that, see the post above.

---

### Post by johnnie j on 2009-07-22
Hi HermanAB and pro003,

Thanks for the fast responses. I have tried to do as you've suggested and when I start to type in the the new password, in single user mode, I am only able to type in one letter and I am not able to use that letter (password, I guess) to enter root mode, su, while in regular mode. Any further suggestions?

---

### Post by Penguin Guy on 2009-07-22
> **johnnie j said:**
> I am only able to type in one letter
When typing in a password in a terminal you should not see **anything** whatsoever. This is a common issue with new users - keep typing and press enter, all will be fine.

> **johnnie j said:**
> enter root mode
If you have followed the above steps correctly you should start off in root mode and should see a prompt something like this:
```
**root**@computer:~**#**
```
Rather than the normal prompt:
```
**you**@computer:~**$**
```

---

### Post by sisco311 on 2009-07-22
> **johnnie j said:**
> Hi HermanAB and pro003,

Thanks for the fast responses. I have tried to do as you've suggested and when I start to type in the the new password, in single user mode, I am only able to type in one letter and I am not able to use that letter (password, I guess) to enter root mode, su, while in regular mode. Any further suggestions?

if you have admin rights, then *sudo passwd root*

---

### Post by Linux000 on 2009-07-22
If you haven't changed it, the root password should be the same password as your account.

---

### Post by sisco311 on 2009-07-22
> **Linux000 said:**
> If you haven't changed it, the root password should be the same password as your account.

That's the default in Linux Mint, not in Ubuntu. ;)

---

### Post by sisco311 on 2009-07-22
I was able to reproduce this strange behavior.

When you are editing the kernel line you have to delete the *ro quiet splash*(at least the splash) options before you add *rw init=/bin/bash*.

---

### Post by johnnie j on 2009-07-22
sisco311,

That was exactly what I needed to do and thanks to all of you for responding.

With community support like this GNU/Linux will hopefully see a surge in growth over the next few years.

---

### Post by pro003 on 2009-07-23
> **sisco311 said:**
> That's the default in Linux Mint, not in Ubuntu. ;)

How come? There is only one password at the initial install of ubuntu and that is user's and root's password. I'd called that default behaviour.

---

### Post by sisco311 on 2009-07-23
> **pro003 said:**
> How come? There is only one password at the initial install of ubuntu and that is user's and root's password. I'd called that default behaviour.

The root account password is locked. The first user created is in the admin group, therefore is allowed to escalate privileges via sudo/gksu/policykit.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by pro003 on 2009-07-23
> **sisco311 said:**
> The root account password is locked. The first user created is in the admin group, therefore is allowed to escalate privileges via sudo/gksu/policykit.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

And when you type **gksu** or **sudo** before let's say "***rm -rf /***"you become what?

---

### Post by Paddy Landau on 2009-07-23
> **pro003 said:**
> And when you type **gksu** or **sudo** before let's say "***rm -rf /***"you become what?
You become horrified! :D

Seriously, I think that you might have missed the point.

Your password and root's password are different.

sudo, gksu and gksudo allow you to run as root, temporarily, without knowing root's password. (You don't become root; you simply run as root.)

For example, if you create two accounts (say, pro003 and myfriend), both as administrators, you'll both have different passwords. Yet, you'll both be allowed to use sudo with your own passwords.

In Ubuntu, by design, you don't know root's password and you don't need to know.

---

### Post by pro003 on 2009-07-23
> **Paddy Landau said:**
> You become horrified! :D

Seriously, I think that you might have missed the point.

Your password and root's password are different.

sudo, gksu and gksudo allow you to run as root, temporarily, without knowing root's password. (You don't become root; you simply run as root.)

For example, if you create two accounts (say, pro003 and myfriend), both as administrators, you'll both have different passwords. Yet, you'll both be allowed to use sudo with your own passwords.

In Ubuntu, by design, you don't know root's password and you don't need to know.

But you can assign one, can't you? As a person who installed the system in 1st place you are in group of admin and that gives you a right to use sudo or gksu which is quite enough to gain powers of the superuser and do whatever you want. In sense of terms user is not a root, but can run as root because he's in the admin group by default, so this is a little confusing and we can argue about what's what all day long. The point is that when you install the system, you're neither a user nor a root, you are admin, and as one you can create other accounts, assign different passwords to admin, users or even root. From there we are going into area of administrating the system.
If you google you'll see that in many places root/admin term... So basically it's pretty much the same. 
Although a person should never become a root and login to x as one, that would be a catastrophe.

---

### Post by mcduck on 2009-07-23
> **pro003 said:**
> And when you type **gksu** or **sudo** before let's say "***rm -rf /***"you become what?

You become root, but not by using actual root password but your own instead.

If you try to use "su", or directly log in as root, it will fail because you don't have the root password.

Thus, root account is locked in the way that you can't log into it, but it still exists and is usable though "sudo".

What comes to the trick of editing the boot line in Grub, that's not really necessary. Just select the recovery mode from Grub menu, and when asked what to do choose the root shell option.

---

### Post by DarinB on 2009-07-23
thank you every one this is one of the best posts i have seen, when i learned red hat they told me if you lose your password you are headed for a reinstall
question on this if have a single user machine therefore single user me has admin rights but there is no root password and it is locked correct? if i for some reason forget that password as a the single user do i follow the same procedure as above by editing the kernel with rw init=/bin/bash. then enter in and change the user single user password, in users and groups properties????

---

### Post by sisco311 on 2009-07-23
> **DarinB said:**
> thank you every one this is one of the best posts i have seen, when i learned red hat they told me if you lose your password you are headed for a reinstall
question on this if have a single user machine therefore single user me has admin rights but there is no root password and it is locked correct? if i for some reason forget that password as a the single user do i follow the same procedure as above by editing the kernel with rw init=/bin/bash. then enter in and change the user single user password, in users and groups properties????

the sulogin shipped with Ubuntu is patched to handle disabled root account, you can boot in Recovery Mode (Single User Mode) without entering the root password. 

You have to edit the kernel line _only_ if you have a root password and forgot it. And, of course, your user is not in the sudoers.  

[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by jerome1232 on 2009-07-23
> **pro003 said:**
> And when you type **gksu** or **sudo** before let's say "***rm -rf /***"you become what?

actually nothing happens.

>        --preserve-root
              do not remove ‘/’ (default)


Now if you removed /* it's a different story.

---

### Post by shodai100 on 2009-07-23
just put in " sudo su ". Put in your password if it asks for it. Then put in " passwd ". You can then change your password.

---

### Post by pro003 on 2009-07-23
> **mcduck said:**
> You become root, but not by using actual root password but your own instead.

If you try to use "su", or directly log in as root, it will fail because you don't have the root password.

Thus, root account is locked in the way that you can't log into it, but it still exists and is usable though "sudo".

What comes to the trick of editing the boot line in Grub, that's not really necessary. Just select the recovery mode from Grub menu, and when asked what to do choose the root shell option.

well you're right about login directly as root, that's not possible, hence there you can log in in terminal by typing ***sudo -s*** or ***sudo -i***, enter your users password and you're **root@yourmachine:~#**

---

### Post by mcduck on 2009-07-23
> **pro003 said:**
> well you're right about login directly as root, that's not possible, hence there you can log in in terminal by typing ***sudo -s*** or ***sudo -i***, enter your users password and you're **root@yourmachine:~#**

Exactly like I said, the root account is there and accessible through sudo. :)

(by the way, use "sudo -i", not "sudo -s" or "sudo su". The first one loads root's environment variables correctly, others don't which can sometimes cause nasty side effects..).)

---

### Post by pro003 on 2009-07-24
> **mcduck said:**
> Exactly like I said, the root account is there and accessible through sudo. :)

(by the way, use "sudo -i", not "sudo -s" or "sudo su". The first one loads root's environment variables correctly, others don't which can sometimes cause nasty side effects..).)

thanks for advice, I hate nasty side effects ;)

---

### Post by geobz on 2009-07-28
I might be dumber....

I upgraded from ibex and when it restarted, i realized i couldn't remember my username. I know the password though. I used to boot up automatically without prompting for the username and password.

Would this thread answer my problems as well?

Thanks

---

### Post by sisco311 on 2009-07-28
Reboot in Recovery Mode and type:
```
ls /home
```
[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by pro003 on 2009-07-28
> **geobz said:**
> I might be dumber....

I upgraded from ibex and when it restarted, i realized i couldn't remember my username. I know the password though. I used to boot up automatically without prompting for the username and password.

Would this thread answer my problems as well?

Thanks

Or...

1. Turn your computer on.
2. Press ESC at the grub prompt.
3. Press e for edit.
4. Highlight the line that begins kernel ........., press e
5. Go to the very end of the line, add rw init=/bin/bash
6. press enter, then press b to boot your system.
7. Your system will boot up to a passwordless root shell.
8. Type in passwd <username>. Set your password.
9. Type in reboot.

---

### Post by sisco311 on 2009-07-28
> **pro003 said:**
> Or...

1. Turn your computer on.
2. Press ESC at the grub prompt.
3. Press e for edit.
4. Highlight the line that begins kernel ........., press e
5. Go to the very end of the line, add rw init=/bin/bash
6. press enter, then press b to boot your system.
7. Your system will boot up to a passwordless root shell.
8. Type in passwd <username>. Set your password.
9. Type in reboot.

Well, this method will NOT work.

1. In step 5. you have to delete the *ro quiet splash* boot options (at least the splash). The splash & init doesn't work together.

2. Even if you add the rw option sometimes the root ("/") partition is mounted ro, so you have to remount it rw:
```
mount -o remount,rw /
```

3. The reboot command will not work, you probably have to start some daemons. (Ctrl+Alt+Del works)

4. The hostname is not set.

5. Some commands will not work or will not work properly...

---

### Post by tarps87 on 2009-07-28
> **sisco311 said:**
> Reboot in Recovery Mode and type:
```
ls /home
```
[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

This will be the simplest as long as you have not changed your home directory name :)

> **pro003 said:**
> Or...

1. Turn your computer on.
2. Press ESC at the grub prompt.
3. Press e for edit.
4. Highlight the line that begins kernel ........., press e
5. Go to the very end of the line, add rw init=/bin/bash
6. press enter, then press b to boot your system.
7. Your system will boot up to a passwordless root shell.
8. Type in passwd <username>. Set your password.
9. Type in reboot.
 unfortunate there is a problem with step 8, "i realized i couldn't remember my username"

When you add a user in Ubuntu it automatic adds a group with you user name, once you have logged on in single user mode type
```
cat /etc/group
```
No see if you can spot your user name.
(you may need to use more if the output is too long)
```
cat /etc/group | more
```

About this would sudo/ root thing, if you look at the documentation for sudo it is very different to the root user. It gives you super user privileges only for the commands specified, it just happens that Ubuntu has a strange way off using it by allowing to to run all commands.

---

### Post by pro003 on 2009-07-28
Sorry sisco311, I just read thread all over again and realized that this is a different guy with a different problem that appears later and I misjudged the issue, and yes your absolutely right about checking the username with "ls /home" command.

I guess I need to get some sleep now, good night guys.

---

### Post by geobz on 2009-07-29
thanks sisco311. You totally saved me!

---

