---
title: "How to add a large number of new users?"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by allenbradley on 2009-07-24
Hey All. I have a central computer which I want to open up to access. I have students with Roll numbers like CE0XB0XX, where the X's are numerals. I want to add them as users to this computer, each with a home folder and permissions and all, and passwords as, say, the roll numbers again. While the single user is added using the Users and Groups functionality in Ubuntu, how do I do this for,say, 60 students?

Also, I've noticed that folders like Videos, Documents etc. do not get created immediately after creating a new user. You have to log out and log in as the new user for all your files to be completely set up. As i can't login each time as the new user, is there a workaround for this?

Thank you in advance :)

---

### Post by linuxguymarshall on 2009-07-24
You could write a BASH script to handle it with a loop that adds a number to each username. If you dont know how to do this then say so otherwise just do that.

---

### Post by bacil on 2009-07-24
you can do something like this 

```

cat listofusers.txt | xargs useradd -m

```

provided that each line of your listofusers.txt contais one usernamen

and -m will create home with its subdirectories only think i need to check is if you can create user without password and have them to change it on first login

---

### Post by t0p on 2009-07-24
> **bacil said:**
> i need to check is if you can create user without password and have them to change it on first login

I don't think so.  But the OP could use useradd with the --password flag, then specify a password that is the user's name or maybe just "password".  So long as the new user logs in and changes his password *immediately*, that shouldn't present too much of a security hole... hopefully...

OP: check out the useradd man page.  Type into the terminal

```
man useradd
```

---

### Post by allenbradley on 2009-07-24
Thank you linuxguymarshall and bacil and t0p, for the quick replies
@linuxguymarshall
I don't know bash scripting, so a little help would be appreciated
@bacil
I'll try that and post back.

---

### Post by frunns on 2009-07-24
This guide seems fairly straightforward.
[http://www.linuxconfig.org/Bash_scripting_Tutorial](http://www.linuxconfig.org/Bash_scripting_Tutorial)

Just ask if you have any specific questions. And I suppose you could generate a password and save along with the username as well actually.
[http://www.osix.net/modules/article/?id=570](http://www.osix.net/modules/article/?id=570)

But I suppose doing this too complex might take more time than just doing it manually. But wouldn't it totally be worth the effort?! =D (Well, over time it actually might be supposing you'll be doing this again...)

---

### Post by allenbradley on 2009-07-24
@bacil I created the file as you said with one username per line and I ran to command you posted. However, the command is not executed and the command useradd just displays the list of switches without executing it. What should I do?

@frunns Thanks for the links. I think that is a long term solution, which I'd probably use once I get to grips with Bash.

---

### Post by frunns on 2009-07-24
You ran it exactly as he wrote? As far as I can tell it should work. cat should send the content of the file to xargs which should send the usernames to adduser one by one...

---

### Post by decoherence on 2009-07-24
didn't work for me, either, but not because of flags.

```
cat listofusers.txt | sudo xargs useradd -m
```

you'll be prompted for your password (required to make a new user account)

note that when you type a password on the command line, nothing will appear. just type and hit enter.

---

### Post by Mornedhel on 2009-07-24
From the useradd man page :

```
useradd is a low level utility for adding users. On Debian,
administrators should usually use adduser(8) instead.

```

---

### Post by linuxguymarshall on 2009-07-24
Give me 15 -20 mins and I will get you a BASH script that should do  the trick.     I love BASH scripting

---

### Post by linuxguymarshall on 2009-07-24
It does not do **exactly** what you want but it should be a good starting point for you.

> #!bin/bash
clear
echo "How many users do you want to create?"
read num
clear
echo "What do you want the default password to be for every account?"
read pass
clear
let XXXXX=10000
until [ $numx -gt $num ]; do
		adduser CE0$XXXXX -p $pass	
        let numbx=numx+1
		let XXXXX=XXXXX+1
done

---

### Post by Mornedhel on 2009-07-24
linuxguymarshall: did you even test the script ?...

I predict it won't work.

---

### Post by linuxguymarshall on 2009-07-24
> **Mornedhel said:**
> linuxguymarshall: did you even test the script ?...

I predict it won't work.

that I did not. I am on a road trip only connecting to the internet by tethering my E70 through a Bluetooth connection and a Windows XP lappy so no BASH to test it out on

---

### Post by sisco311 on 2009-07-24
```
#!/bin/bash

cat /path/to/file/users | \
while read username; do
  # if the line is empty don't add user "" and don't chmod /home :)
  if [ "$username" ]; then        
    # add a new user with the same password as the username
    useradd -m -p $(mkpasswd -m sha-512 "$username") -s /bin/bash  $username
    # create private home for user
    chmod 0700 /home/"$username"
  fi
done

```

the script reads the user names from /path/to/file/users.

the user's password is the same as the user name.

---

### Post by allenbradley on 2009-07-24
You guys/girls are all awesome. Thank you for the replies. I'll try out the bash scripts now and let you know what happens.

@decoherens, frunns, mornedhel and bacil 

    No, the command doesn't seem to work. I had the input file like this :
```
listofusers.txt
allen
bradley
test
user
```

and used ```
cat listofusers.txt | sudo xargs useradd -m
```

and got this :
```
Usage: useradd [options] LOGIN

Options:
  -b, --base-dir BASE_DIR       base directory for the new user account
                                home directory
 .
 .
 .
  -U, --user-group              create a group with the same name as the user


```
I checked and the folders were not created.

@linuxguymarshall, mornedhel and sisco 311 I'll post the outputs of the respective bash scripts in a few minutes. 

Thanks again y'all!

---

### Post by allenbradley on 2009-07-24
@linuxguymarshall The script isn't working. Something about let: not found in line 14 and unexpected operator -gt and unknown option p and so on. 

@sisco311 The script works like a charm. Creates folders and the permissions are such that I can't cd into them unless I'm the user. 

Thanks a lot again. It truly helped. How do I add a SOLVED tag?

---

