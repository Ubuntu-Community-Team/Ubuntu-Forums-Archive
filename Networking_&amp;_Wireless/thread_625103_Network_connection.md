---
title: "Network connection"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by yarivabr on 2007-11-27
Hello,

I'm new in linux.
I installed Ubuntu on my private computer at home.
I have 2 questions:
1) What is the default password for the administrator the root ?
2) I have on this computer also Widows OS. I'm connected to the internet with it.
I don't know how to connect also my Linux to the net.


Thanks

---

### Post by konig12 on 2007-11-27
1)  In ubuntu when you want to run command as root you should use the sudo command on the command line.  For example, if you wanted to edit a file owned by root you would do this:
```

sudo nano someRootFile.txt

```
if you absolutely need a root shell you can use sudo to do a su as follows:
```

sudo su

```
This will give you a root shell.

2) If the computer is a desktop computer connected with a wired connection it should automatically configure the internet connection for you.  if you have to use a specific ip adress or some other advanced configurations, you can select "Manual configuration" by clicking on the network manager in the top right corner of the screen.  Wireless configurations are also simple using the network manager.  If you want to connect to a wireless network, click on the network manager and select the desired network.  You will be prompted for a password if the network is encrypted.

Hope that clears up your questions.  If not Ill try to explain thins better.

---

### Post by yarivabr on 2007-11-27
When I tried to su root : I was asked to enter a password.
Wheich I don't know, because when I Installed ubuntu, I wasn't asked for admin user and password:(

---

### Post by konig12 on 2007-11-27
There is not actually an administrator password, but instead you will be able to use your user password to sudo when logged into your account.  try using the password for your username when sudo prompts for the password.

---

### Post by RPG405 on 2007-11-27
Run the command: sudo passwd

to change the root password. Otherwise, when doing sudo, you always use the user's password.

---

