---
title: "Need some help with script"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by CharlesA on 2009-12-15
Hi all,

I'm trying to create a script that'll run a bunch of commands so that I don't have to run them manually after a clean install.

Is there some trick to this?

Here's the script so far:

```
#Update system
sudo apt-get update && sudo apt-get upgrade
#Create group raid
sudo addgroup -gid 1004 raid
#Create user karen and add to group raid
sudo useradd karen -u 1001 -M -d /dev/null -s /dev/null -U -G raid
#Create user htpc and add to group raid
sudo useradd htpc -u 1002 -M -d /dev/null -s /dev/null -U -G raid
#Create user clone and add to group raid
sudo useradd clone -u 1003 -M -d /dev/null -s /dev/null -U -G raid
#Add charles to karen, clone, raid groups
sudo usermod -a -G karen,clone,raid charles
#Create /array and change owner and permissions
sudo mkdir /array && sudo chown charles:raid /array && sudo chmod 770 /array

```

This is what I get back after running the script:

```
charles@ubuntu:~$ ./script
E: Invalid operation update
E: Invalid operation upgrade
addgroup: To avoid problems, the username should consist oly of letters, digits, underscores, periods, at sighns and dashes, and not start with a dash (as defined by IEEE Std 1003.1-2001). For compatibility with Samba machine accounts $ is also supported at end of the username
useradd: group 'raid
' does not exist
useradd: group 'raid
' does not exist
useradd: group 'raid
' does not exist
usermod: user 'charles
' does not exist
chmod: cannot access '/array\r': No such file or directory
```

I checked each of the commands before throwing them into the shell script and they ran fine.

Is there something special I need to do to get them to work?

Thanks.

---

### Post by bodhi.zazen on 2009-12-15
I am not sure where the problem is , but I suggest a few things :

1. add a "shebang" at the top of the script :

```
#!/bin/bash
```

2. Rather then using sudo, simply write your commands and run the script with sudo ./script

3. Use the full path to commands

/usr/bin/apt-get rather then apt-get

---

### Post by CharlesA on 2009-12-16
> **bodhi.zazen said:**
> I am not sure where the problem is , but I suggest a few things :

1. add a "shebang" at the top of the script :

```
#!/bin/bash
```

2. Rather then using sudo, simply write your commands and run the script with sudo ./script

3. Use the full path to commands

/usr/bin/apt-get rather then apt-get

Thanks for the info. Good point about the full path, didn't even think about that. I'll make the changes and edit the post with the results.

EDIT: I modified the script like so:

```
#!/bin/sh

#Update system
/usr/bin/apt-get update && /usr/bin/apt-get upgrade
#Create group raid
/usr/sbin/addgroup -gid 1004 raid
#Create user karen and add to group raid
/usr/sbin/useradd karen -u 1001 -M -d /dev/null -s /dev/null -U -G raid
#Create user htpc and add to group raid
/usr/sbin/useradd htpc -u 1002 -M -d /dev/null -s /dev/null -U -G raid
#Create user clone and add to group raid
/usr/sbin/useradd clone -u 1003 -M -d /dev/null -s /dev/null -U -G raid
#Add charles to karen, clone, raid groups
/usr/sbin/usermod -a -G karen,clone,raid charles
#Create /array and change owner and permissions
/bin/mkdir /array && /bin/chown charles:raid /array && /bin/chmod 770 /array

```

Now when I run: ```
sudo ./script
```

it returns:
```
charles@ubuntu:~$sudo ./script
sudo: unable to execute ./script: No such file or directory
```

Same thing happens if I use the full path. I'm rather puzzled.

If I run it as root it returns:
```
bash: ./script: /bin/sh^M: bad interpreter: No such file or directory
```

I'm running 9.10 in VirtualBox, if that makes a difference.

Could it be that I am getting those errors since I am creating the file in Notepad on Windows and then transfering it over to Ubuntu in VBox?

I created a file in ubuntu with:

```
#!/bin/sh

#Update system
/usr/bin/apt-get update && /usr/bin/apt-get upgrade
```

And it looked like it ran. :o

---

### Post by cenzorrll on 2009-12-16
try making sure it's executable? (i know it's kind of like making sure the computer is plugged in, but it's caught me a few times)

---

### Post by CharlesA on 2009-12-16
> **cenzorrll said:**
> try making sure it's executable? (i know it's kind of like making sure the computer is plugged in, but it's caught me a few times)

It's executable. ;)

---

### Post by greg963 on 2009-12-16
> 
If I run it as root it returns:
Code:

bash: ./script: /bin/sh^M: bad interpreter: No such file or directory

I'm running 9.10 in VirtualBox, if that makes a difference.


What editor are you using? You are inserting windows newlines (CR+LF) instead of *nix newlines (LF)

---

### Post by CharlesA on 2009-12-16
> **greg963 said:**
> What editor are you using? You are inserting windows newlines (CR+LF) instead of *nix newlines (LF)

I am using Notepad :rolleyes: and ending the lines with just an <Enter>

Is there something special I need to do?

---

### Post by greg963 on 2009-12-16
Yes learn vi, know it, love it.

Or I suppose you could use some other linux editor
[http://en.wikipedia.org/wiki/Category:Linux_text_editors](http://en.wikipedia.org/wiki/Category:Linux_text_editors)

---

### Post by greg963 on 2009-12-16
BTY gedit is the default editor in ubuntu desktop, that would work too. Applications->Accessories->gedit

---

### Post by CharlesA on 2009-12-16
> **greg963 said:**
> BTY gedit is the default editor in ubuntu desktop, that would work too. Applications->Accessories->gedit

Thanks. I'm rewriting the script using gedit and I'll run it on the VM and see if it'll run correctly.

Thanks again.

*grumbles @ windows apps*

EDIT: It worked. Woot!

---

### Post by tacantara on 2009-12-16
I guess the following is superfluous, as you got it working...... 

I don't know if this will help, but I recently wrote a couple of small Bash scripts in gedit.  One script was designed to install the restricted extras package and the flash plugin (nonfree).  I ran into a problem executing the script with the commands on one line and separated by the double ampersand (&&), but rather than troubleshoot it, I went with a different approach and separated them with a semicolon:

```
sudo apt-get install ubuntu-restricted-extras ; sudo apt-get install flashplugin-nonfree
```This approach may be impractical if you have a bunch of commands to execute (such as you have), but it's worth looking at if all else fails.

Good luck getting that script running :)

---

