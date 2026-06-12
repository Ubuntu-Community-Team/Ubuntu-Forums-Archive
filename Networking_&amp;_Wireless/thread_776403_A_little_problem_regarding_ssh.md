---
title: "A little problem regarding ssh"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by rksk16it on 2008-04-30
Hi friends,
i am facing a small problem, i think i have some misunderstood concepts, but let me explain the problem :

The situation :
I am using Ubuntu 8.04, I have 1 admin user and 2 normal users (without admin rights) on my PC. Its only me who use them, there are no other pppl who use them. Let me call the normal users : user1 and user2 (the actual names are different).
I use OpenSSH.

What i want :
I want to access the terminal of "user2" using SSH while i am in "user1", just to learn SSH :-)

What i did :
on "user1" i did following :
```
user1@my-desktop:~$ ssh-keygen
```
...it asked where to create the private key, i selected default location, then it asked the passphrase and i entered one, and this step was fine.

now..next command (on "user1") :
```
user1@my-desktop:~$ cp ~/.ssh/id_rsa.pub ~/id_rsa.pub
user1@my-desktop:~$ chmod ug+r ~/id_rsa.pub
```

now, next I logged in "user2"
```
user2@my-desktop:~$ mkdir ~/.ssh
user2@my-desktop:~$ cat ~/../user1/id_rsa.pub >> ~/.ssh/authorized_keys
user2@my-desktop:~$ chmod 700 ~/.ssh
user2@my-desktop:~$ chmod 600 ~/.ssh/authorized_keys
```

now, i logged out of "user2" and logged in from "user1"
then in "user1", no matter whatever i try in terminal i am unable to get myself authorized :(

i can tell what things i tried, but i think i am doing something stupid in previous steps, i'll be glad if anyone can help.

Thanks :)

---

### Post by kevdog on 2008-04-30
How are you trying to log in?? Whats the command line syntax?

---

### Post by rksk16it on 2008-05-01
I tried the following to login :

1. 1st attempt :
```
user1@my-desktop:~$ ssh user2@localhost
```

2. 2nd attempt :
```
user1@my-desktop:~$ ssh -o PreferredAuthentications=publickey user2@localhost
```

3. 3rd attempt :
```
user1@my-desktop:~$ ssh localhost
```

4. 4th attempt :
```
user1@my-desktop:~$ ssh -o PreferredAuthentications=publickey localhost
```

I was kinda desperate thats why i was trying all the combinations i can think of. Also, on the following line :
```
user1@my-desktop:~$ telnet localhost 22
```
i get the following :
```
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1
```

On all those attempts, a dialog box appears which says "The system wants to import the private key 'id_rsa' but it is locked", in it it asks for passwod...a tried all the things there...the passphrase, passwords of both users, admin password, but nothing works. Actually i dont really know the meaning of "importing" the private key (i just understood the authentication system, so i am a kindda newbie here).

After entering anything i like and clicking OK, it then asks for the password for user2@localhost in cases of Attempts 1 or 2 (according to above list of attemtps), and there also, whatever i give doesnt work, or in cases of other attemps (3 or 4), the authentication fails right away. :(

Thanks again for any help.

---

### Post by Monicker on 2008-05-01
I believe you need to specify the key to use.  Here is how I ssh from my desktop to my laptop using key authentication:


```
ssh -i ~/.ssh/keyname username@192.168.x.x
```

---

### Post by rksk16it on 2008-05-01
> **Monicker said:**
> I believe you need to specify the key to use.  Here is how I ssh from my desktop to my laptop using key authentication:


```
ssh -i ~/.ssh/keyname username@192.168.x.x
```

i tried that method too, it again opened that dialog box saying that the key "id_rsa" is locked and asked me to enter the password...nothing worked, then it asked about user2 password...but since password authentication is disabled, it didnt worked... :(

I would really like to know what to enter here (pls see the attached img).

Nothing, i really mean nothing seems to work there.... :(

---

### Post by Monicker on 2008-05-01
> **rksk16it said:**
> i tried that method too, it again opened that dialog box saying that the key "id_rsa" is locked and asked me to enter the password...nothing worked, then it asked about user2 password...but since password authentication is disabled, it didnt worked... :(

I would really like to know what to enter here (pls see the attached img).

Nothing, i really mean nothing seems to work there.... :(


It looks like the passphrase for private key, which you were prompted for when you created the key pair.

---

### Post by rksk16it on 2008-05-01
> **Monicker said:**
> It looks like the passphrase for private key, which you were prompted for when you created the key pair.

I also guessed that, but it doesnt work, thats what which is frustating me to no end. I also tried all the passwords which i know of all the users including admin user.

I guess I have to try this procedure from a different computer first (probably from a laptop which i am gonna buy soon :-)), i think its creating problems as both client and server are on same host and some configuration may be preventing localhost access....this may be a naive reason i know..but i am very frustated. :(

Thanks

---

### Post by rksk16it on 2008-05-02
A bump...
not really a bump, actually i narrowed down the original problem...

on user1 terminal i did :
```
user1@my-desktop:~$ rm -r .ssh    # removed all local ssh stuff.
user1@my-desktop:~$ ssh user1@localhost # attempted to login to same user.
```
and viola ! login successful ! (using password authentication ofc)
then i logged out of ssh and then logged out of user1 and then logged in user2, opened terminal and tried this :
```
user2@my-desktop:~$ rm -r .ssh
user2@my-desktop:~$ ssh user1@localhost # now atttempted to login to user1 from user2
```
and again using password authentication, login sucessful.
Now again, after logging out from ssh session but in user2 terminal, i did this :
```
user2@my-desktop:~$ rm -r .ssh
user2@my-desktop:~$ ssh user2@localhost # this time i tried to log into user2 from user2 itself
```
and strange enough login failed, it asked for password of user2 3 times, but even after entering correct password it failed :confused:...
then i went back to user1 terminal and tried this :
```
user1@my-desktop:~$ rm -r .ssh
user1@my-desktop:~$ ssh user2@localhost # trying to enter user2 from user1
```
strangely enough..login failed, with same situation as above failure..:confused:

also, before each attempt i cleaned the folder ~/gnome2/keyrings in both users.
So the situation is like i **cannot login into user2 from any user account** but i **can login into user1 from any user account** !!!

Thanks again for reading all the above stuff :) This problem is getting more and more amusing :P

---

### Post by kevdog on 2008-05-02
Can you list the permissions of the private key in both places?  Sounds like a file permissions problem to me!  Group, file ownership issue.

---

### Post by rksk16it on 2008-05-02
> **kevdog said:**
> Can you list the permissions of the private key in both places?  Sounds like a file permissions problem to me!  Group, file ownership issue.

well, as u can see, before each "trial" in all the above 4 cases, i removed the ".ssh" folder which has private keys, so i just tried with password authentication in above cases.

Also, one thing i forgot to mention in above posts, when i actually tried public-key based authentication, the results were exactly same, i can login into user1 using its public-key, but cant login into user2. :confused:

---

### Post by rksk16it on 2008-05-02
Heh...this problem, like most of the problems...turned out to be real simple thing...

i just checked /etc/ssh/sshd_config, and found that only the admin account and "user1" are there in "Allowed users" !! :lolflag:

Well, my problem is officialy solved, thanks to Kevdog and Monicker who took pains to reply to my posts. :)

:guitar:

---

