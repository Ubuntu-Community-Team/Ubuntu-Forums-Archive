---
title: "Creating a user that connot login"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by Jaymoid on 2006-10-26
Hi,

I want to create a user that cannot login; so that its account can be used to scp files to my home computer. can anybody please tell me how this can be acheived. Many thanks.
](*,) 
James

---

### Post by kidders on 2006-10-26
Hi there,

You could set a user's shell to something daft line /bin/false to prevent him from using a terminal, if you like.

---

### Post by whizbaby on 2006-10-26
put a # before the line with the username in /etc/shadow

---

### Post by kidders on 2006-10-27
This may be a totally ignorant question, but won't a '#' comment the line out?

---

### Post by whizbaby on 2006-10-27
Right, so the user cannot login. Wasn't this the goal?

---

### Post by whizbaby on 2006-10-27
What I don't understand is why you need a user without login to scp files...

---

### Post by kidders on 2006-10-27
It's fairly common to create users that can't log in (ntp, dhcp, syslog, etc.), which is not quite the same thing as *not* creating a user in the first place. You're right though ... this application of it does seem a little odd.

I'm not 100% certain SCP will even work for a user with no shell, though.

---

### Post by whizbaby on 2006-10-27
I'm pretty shure it won't work because 
*scp username@host:/path/file /destination*
will require you to type a password. With commented-out line in shadow this doesn't work and with no shell scp will not be able to login, too.
(BTW I'm aware that there are many users unable to login on the system, it was only difficult for me to see the relation to scp...).

So in conclusion:
As we showed you can easily make a user without login, but this makes no sense if you want to use the account with scp since you actually would have to login. So why is your homedir insufficient for that task, what is special?

EDIT:
it's hard to write 'host' + ':' + 'path' when
':' + 'p' = :p
(username@host:path/file)

---

### Post by Jaymoid on 2006-10-27
Hi, 

Thanks for all the responses, on an inital test, I commented out the user in /etc/shadow, and sure enough I couldnt log in as that user, but I could sudo su to that user which is perfectly as I wanted it... However the user doesnt have a shell now, so I'm not sure wether it would work, and because of the reason below I can't properly try it as its not my server.. I thought there would be some kind of switch in a config file somewhere that you could use to say something along the lines of:
login-enabled: false;

I havent treid scp'ing any files yet. But the reason why I wanted this was actually for a friend who has his own webserver and wanted to backup some files automagically...

On my friends webserver he would have one user that had the job of scp'ing backup files from the server to his home machine. This would be the only user on the system with a dsa key (so that it could copy files across with a blank passphrase) so only that user had access to his home machine. But to make it more secure he wanted this user not to be able to login, and therefore not gain access to his home machine. There are other users on the server so he didn't want them to be able to access his home machine without a password if they managed to get into this account.

I actually got the idea from here:
[http://ubuntuforums.org/showpost.php?p=366636&postcount=15](http://ubuntuforums.org/showpost.php?p=366636&postcount=15)

Cheers, if anyone has any other suggestions of disabling a user from logging in but still keeping the shell that would be appreciated.

ta.

---

### Post by kidders on 2006-10-27
> I thought there would be some kind of switch in a config file somewhere that you could use to say something along the lines of:
login-enabled: false;

That depends on what you mean by "log in". The usual thing to do is to set someone's shell to something that ... well ... isn't much use as a shell (eg /bin/false).

You see, there is a slight distinction here that you might be overlooking, in that just because a user can log in doesn't mean he can do very much. So, while a user with no shell can (technically) log in per se, he does not necessarily have free rein on your computer. In practice, an account you've created purely for the purpose of using SCP *does* need to be able to _log in_, but might not need a shell.

**Edit:** I imagine your SCP user will also need a home also (much like www-data has a home), for things to work as expected.

It is worth noting that, normally, the only way for someone to use the account on the web server to break into your friend's home PC is (a) to be root or (b) to know his password. Either would allow access to the private key. Even if this did happen though, how much damage could someone really do?

---

