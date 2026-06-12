---
title: "SSH, permissions, and other various questions..."
date: 2010-11-01
forum: New to Ubuntu
---

### Post by Wolf_22 on 2010-11-01
I hope you'll forgive me if these questions have already been asked, but I'm trying to properly setup SSH on a Kubuntu box and I'm having a difficult time understanding how various aspects work.

Allow me to start from the beginning: 

After having installed Kubuntu, I made sure that my LAMP was working by installing OpenSSH where I then tried to connect to the server itself from another computer in the same office. Fortunately, it worked. The thing that bugs me is that it takes me directly to the home/user directory. I guess it's supposed to do this by default (?), but what I would prefer it to do is have the SSH automatically log me into the "www" directory so that I can have instant access to my web projects. Should I just reconfigure the Apache httpd.conf file to designate my home/user directory as being my primary web documents directory?

...few more questions:

1.) When I log into the server, I log in as "john." I made this "john account" when I installed Linux, Ubuntu, Kubuntu (and everything else you can think up). What purpose, then, does having some obscure "root" account serve if I always log in as "john"? Isn't "john" root!? How am I supposed to know when something needs to be installed under the guise of "root" versus "john"?

2.) If I ever need important system information, such as the name and version of my installation of Ubuntu / Kubuntu, etc., where do I go for this? In XP et al, all you need to do is right click on "My 'Puter" and go to "Properties." In Linux, Ubuntu, Kubuntu...? 

3.) In the home/user directory, there is a single file called "GPG-KEY-DRBL". From what I understand, it pertains to "Pretty Good Privacy", ap pro po, it's something to do with key authentication. The thing, however, is that I make no use of key authentication with my SSH at the moment--only my username and password. For this reason, I decided to remove it from this folder. Should I now expect Satan's wrath for doing this or can I sleep soundly at night without worry of some horrible thing sneaking into my bedroom around midnight...?

4.) One last thing about the above file I removed... Before I did this, I tried to modify it's permissions--*just for the heck of it*--and the system wouldn't allow it, however, I can apparently move it to the trash without ruffling a single feather on a pixie's ***. What's up with that? Isn't that a bit *inconsistent*?

Sorry for the big post. This stuff is pretty frustrating but if I can someone around here with a bit more experience shed some light on the topic, I think I'll be alright. :)

---

### Post by alexandari on 2010-11-01
1. john isnt root. root is your god,and you are john. john is probably in the sudoers group (you have root rights) and you can use the command "sudo" to execute commands via the terminal under root
2. ```
 lsb_release -a 
``` 
or you can use **kinfocenter** in KDE
3.Yes,satan WILL come to your house...he probably is under your bed atm.
4.as I said,you need root rights to do that. use the "sudo" command in the terminal,and the thing you need to do after that. For example:
```
 sudo mv cool.tar.gz /usr/bin 
```

I suggest you take a look at some basic terminal commands,just use google :) good luck

---

### Post by papibe on 2010-11-01
> **Wolf_22 said:**
> 
2.) If I ever need important system information, such as the name and version of my installation of Ubuntu / Kubuntu, etc., where do I go for this? In XP et al, all you need to do is right click on "My 'Puter" and go to "Properties." In Linux, Ubuntu, Kubuntu...? 

There's not an exact equivalent to MyComputer -> Properties. The information and tools are separated in different places. Also it can be obtain using both the GUI and by using the command line.

**Closest thing in Ubuntu(gnome):**
GUI: 1. System -> System Monitor -> System Tab

Other ways:

**Ubuntu version**
GUI: 1. System -> About Ubuntu
CLI: lsb_release -a

**Kernel version**
CLI: uname -r

**RAM**
CLI: free -m

**Disk space**
GUI: System -> Administration -> Disk Utility
CLI: df -h

I hope it helps.

---

### Post by XeonBloomfield on 2010-11-01
To login by SSH to your server use command like this:
```
ssh -l <user_name> <server_address>
```

And you will connect to your server - IP: "<server_address>" with user specified in "<user_name>".

---

### Post by papibe on 2010-11-01
> **Wolf_22 said:**
> 
1.) When I log into the server, I log in as "john." I made this "john account" when I installed Linux, Ubuntu, Kubuntu (and everything else you can think up). What purpose, then, does having some obscure "root" account serve if I always log in as "john"? Isn't "john" root!? How am I supposed to know when something needs to be installed under the guise of "root" versus "john"?


That confusion happens to all of us when first got into the Linux/Ubuntu environment. Mainly because the common sense is dictated by what we've learned using Windows.

There's no super-short-answer to explain you this. But you will have to believe me when I say: it is a far much secure system that what any version of Windows uses. Start by reading this: [Advantages and Disadvantages]("https://help.ubuntu.com/community/RootSudo").

Regards.

---

### Post by XeonBloomfield on 2010-11-01
@papibe:
I answered this one...

He want to use SSH connection to server... SSH command use system username by default. To login as another user you need to use "-l <user_name>" before server address (IP) and you will connect by this username.

---

### Post by sandyd on 2010-11-01
> **Wolf_22 said:**
> I hope you'll forgive me if these questions have already been asked, but I'm trying to properly setup SSH on a Kubuntu box and I'm having a difficult time understanding how various aspects work.

Allow me to start from the beginning: 

After having installed Kubuntu, I made sure that my LAMP was working by installing OpenSSH where I then tried to connect to the server itself from another computer in the same office. Fortunately, it worked. The thing that bugs me is that it takes me directly to the home/user directory. I guess it's supposed to do this by default (?), but what I would prefer it to do is have the SSH automatically log me into the "www" directory so that I can have instant access to my web projects. Should I just reconfigure the Apache httpd.conf file to designate my home/user directory as being my primary web documents directory?
[B]#if your cheap, you can just add this to the end of your .bashrc (or is it /bash_profile?
I don't remember which gets sourced for the gui and which one gets sourced for the terminal :rolleyes:

```

cd /var/www
```

[/B]

...few more questions:

1.) When I log into the server, I log in as "john." I made this "john account" when I installed Linux, Ubuntu, Kubuntu (and everything else you can think up). What purpose, then, does having some obscure "root" account serve if I always log in as "john"? Isn't "john" root!? How am I supposed to know when something needs to be installed under the guise of "root" versus "john"?
[B]No. John is a admin account, meaning that it can use sudo.
Root is obscured and not used directly because being root means you can do anything. including destroying your computer. its a saftey measure really, making you put sudo in front of your commands makes you give a second thought to what your running.

Installing stuff?
just use apt. It will set the permissions accordingly
[/B]

2.) If I ever need important system information, such as the name and version of my installation of Ubuntu / Kubuntu, etc., where do I go for this? In XP et al, all you need to do is right click on "My 'Puter" and go to "Properties." In Linux, Ubuntu, Kubuntu...? 

3.) In the home/user directory, there is a single file called "GPG-KEY-DRBL". From what I understand, it pertains to "Pretty Good Privacy", ap pro po, it's something to do with key authentication. The thing, however, is that I make no use of key authentication with my SSH at the moment--only my username and password. For this reason, I decided to remove it from this folder. Should I now expect Satan's wrath for doing this or can I sleep soundly at night without worry of some horrible thing sneaking into my bedroom around midnight...?

4.) One last thing about the above file I removed... Before I did this, I tried to modify it's permissions--*just for the heck of it*--and the system wouldn't allow it, however, I can apparently move it to the trash without ruffling a single feather on a pixie's ***. What's up with that? Isn't that a bit *inconsistent*?

Sorry for the big post. This stuff is pretty frustrating but if I can someone around here with a bit more experience shed some light on the topic, I think I'll be alright. :).

---

