---
title: "NO Ubuntu"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by bj218 on 2010-04-11
When I tried to go to Ubuntu this morning I got several screen shots the first read "could not update ICE authority file /home/bill/.ICE authority" another 1 said"create /home/bill/desktop & /home/bill/.nautilus" It also says I can let Nautilus
do it but it does not tell how to do that??

---

### Post by s_ø on 2010-04-11
Can you login to your system?
Then open a terminal - (press **Alt + F2** type **gnome-terminal**)
This command will list the ownership and permissions of the .ICEauthority file
```
ls -l ~/.ICEauthority
```
Can you please post the output here.

---

### Post by bj218 on 2010-04-12
NO maybe I need more detailed instructions

---

### Post by s_ø on 2010-04-12
No you cant login? or No you cant make the command work?
If you cant login you will need to boot from a livecd/usb.

---

### Post by Gone fishing on 2010-04-12
Have a look at this thread 

[http://ubuntuforums.org/showthread.php?t=1447544](http://ubuntuforums.org/showthread.php?t=1447544)

I'd open a terminal Alt Control F1 login and make sure you have ownership of your home directory something like 

sudo chown -R bill /home/bill

That should do it but if it doesn't look at page two of the thread above

---

### Post by bj218 on 2010-04-14
> **s_ø said:**
> No you cant login? or No you cant make the command work?
If you cant login you will need to boot from a livecd/usb.

This is what I got using my Ubuntu CD & going to terminal.

ubuntu@ubuntu:~$ sudo gnome-terminal 
root@ubuntu:~# ls -1 ~/.ICEauthority 
/home/ubuntu/.ICEauthority 
root@ubuntu:~#

now what do I do!!

---

### Post by dearingj on 2010-04-14
> **bj218 said:**
> This is what I got using my Ubuntu CD & going to terminal.

ubuntu@ubuntu:~$ sudo gnome-terminal 
root@ubuntu:~# ls -1 ~/.ICEauthority 
/home/ubuntu/.ICEauthority 
root@ubuntu:~#

now what do I do!!

That should be a lower-case L, not a number one. Easy mistake to make.

---

### Post by bj218 on 2010-04-14
This is what I got using my Ubuntu CD.

ubuntu@ubuntu:~$ sudo chown -R bill/home/bill 
chown: missing operand after `bill/home/bill' 
Try `chown --help' for more information. 
ubuntu@ubuntu:~$ sudo chown -R bill /home/bill 
chown: invalid user: `bill' 
ubuntu@ubuntu:~$

---

### Post by bj218 on 2010-04-14
Is this better?

ubuntu@ubuntu:~$ ls -l ~/.ICEauthority
-rw------- 1 ubuntu ubuntu 318 2010-04-14 18:29 /home/ubuntu/.ICEauthority
ubuntu@ubuntu:~$

Maybe I should just reinstall the program!!

---

### Post by dearingj on 2010-04-15
I forgot to mention, since you're booting from the live cd, you'll need to mount your Ubuntu hard drive partition (that should be as simple as clicking on it in the places menu) and modify the terminal command to look on that drive. Instead of pointing it at ~/.ICEauthority, you'll need to point it at /media/(some number)/home/bill/.ICEauthority

---

### Post by Gone fishing on 2010-04-15
You don't need to boot from a live CD.

When you see the error Alt Control F1 or F2 etc will give you a terminal where you can login.

Then sudo chown -R bill /home/bill

assuming the user name is bill!

---

### Post by Gone fishing on 2010-04-15
If the above doesn't work try deleting /etc/gdm/custom.conf you can do this at a terminal sudo rm -i /etc/gdm/custom.conf or use a live CD

If you look at this thread [http://ubuntuforums.org/showthread.php?t=1447544&page=2](http://ubuntuforums.org/showthread.php?t=1447544&page=2)  similar problem to yours you will see the problem can be solved

---

### Post by bj218 on 2010-04-15
I am getting my mouse hand operated on today so will proberly be out of service for a day or 2. On my next try I will to go to the proper 
partation ie where Ubuntu is installed.

---

### Post by bj218 on 2010-04-17
This is what I did today (4/17/10). At startup I clk on Ubuntu 9.10 & got the following 3 messages:
1."could not update ICEauthority" I clk close
2."there is a problem with the configuration server (/user/lib/libgconf2-4/gconf-sanity-check-2 exited with status256)" I clk close
3."Nautilus could not crsate the following required folders:/home/bill/desktop,/home/bill/.Nautilus. Before running Nautilus please create these folders or set permissions such that Nautilus can create them."Man would I love to let Nautilus do it if only I knew how!!
Next I typed "Ctrl Alt F1 this got me bill@bill-desktop:/$ I typed "sudo chown -R bill /home/bill" & I got "chown: cannot access`/home/bill':no such file or directory
I next typed Alt F2 this gave me bill-desktop login: which I did then @
bill@bill-desktop:/$ I typed "gnome-terminal" rtn this gave me the following "failed to parse argument:cannot open display.
What do I do now reinstall Ubuntu? It looks like
the word "bill" no longer exits!!I am going to 
reinstall Ubuntu to day 4/20 thanks to all for 
the help.

---

