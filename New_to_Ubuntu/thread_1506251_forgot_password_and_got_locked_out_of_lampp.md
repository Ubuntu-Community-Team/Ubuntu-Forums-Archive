---
title: "forgot password and got locked out of lampp"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by thorbs on 2010-06-10
Hi I forgot my password when I wanted to start lamp on my computer. I thought I remembered and typed wrong password twice. 
First I think I was completely locked out. Then I typed sudo mkdir /mnt/ubuntu and got to password. I typed my password, and was allowed again to used the terminal. But it still cant find any lampp commands. But when I type wheris lampp, it says lampp:

I also tried a command that was supposed to uninstall lampp; rm -rf /opt/lampp

but nothing seemed to happened I have tried to start lampp by just typing sudo /opt/lampp/lampp start, but it just says command not found.

So what should I do now in order to get a working lampp on my computer?

---

### Post by thorbs on 2010-06-10
I have to specify that the password I remembered was the one for ubuntu, which apparently is different from my lampp password.

Thanks for the help.

---

### Post by -Jeremy- on 2010-06-10
As far as I know lampp is just a package of separate programs so I don't think it's possible to try to run it the way you do. Instead try running them separately like so:

/etc/init.d/apache2 start
/etc/init.d/mysql start

etcetera...

On a related note: these daemons should run automatically on boot unless specified otherwise so I don't think you'll have to start them manually.

---

