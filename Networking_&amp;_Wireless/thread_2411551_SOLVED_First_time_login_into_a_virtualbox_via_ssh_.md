---
title: "SOLVED First time login into a virtualbox via ssh : what is the password?"
date: 2019-01-31
forum: Networking &amp; Wireless
---

### Post by alreve on 2019-01-31
I have a virtualbox on a pc. Both are running kubuntu 17. I wish to talk to my virtualbox via a terminal on my real machine.

I installed ssh-client and ssh-server on both.

I found this post :
[https://ubuntuforums.org/showthread.php?t=2205941](https://ubuntuforums.org/showthread.php?t=2205941)

But it stops short. I have the same issue. 
The last questions are : 

Have you configured /etc/ssh/sshd_config?
Do you have an account on the server?
Are you using the password for the server account? (That's a common mistake)                 
Do you have an account on the server, with a password?                 

I looked at sshd_config and made 2 modifications
It was :
#PasswordAuthentification yes
 #PermitEmptyPasswords no
  Now it is:
PasswordAuthentification yes
PermitEmptyPasswords yes

Do you have an account on the server? I'm not sure. I have full access to the virtualbox, including root password.
I tried this password and the empty password. "Permission denied".

---

### Post by SeijiSensei on 2019-01-31
You need to have a user account on the virtual machine.  When you installed Kubuntu, you were asked to set up an account.  Did you set up the same account on both machines?

Ubuntu 17.x has reached [end-of-life]("https://www.ubuntu.com/about/release-cycle").  You should be using 18.04 which is a "long-term" release that will be supported until April of 2023.

Ubuntu has no "root password" as some other distros do.  To run commands with root privileges you need to use [sudo]("https://help.ubuntu.com/community/RootSudo").  The account you create at installation will have sudo privileges.

---

### Post by alreve on 2019-02-01
Sorry, I think I am using Kubuntu 18.4.

Setting up an account... Well, I gave a name to the machine when I installed Kubuntu. When I open a terminal in the virtual box, it opens on /home/<machine name>. Is this what you mean? And I have the sudo password. It is the same password as the one I use to unlock the screen.

I tried this sudo password, but it is not accepted.

Edit : Hey! You were right! The issue was the machine name! 
In the documentation I found, it said to type:
ssh -p 3022 vm@127.0.0.1
So I typed that. Then I was asked for a password so I got convinced it was a password issue. 
Replacing the "vm" by the name of the virtual machine and using the virtual machine's password solved the problem!

THANK YOU

---

