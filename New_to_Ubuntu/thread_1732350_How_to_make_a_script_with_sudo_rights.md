---
title: "How to make a script with sudo rights"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by CaptainMark on 2011-04-18
In a terminal I can type 'sudo su' to drop to a root shell, i thought if i wanted to have a bash script that is capable of running commands with root access i would only have to add 'sudo su' to the start of the bash script but the effect this has if i run the script from a terminal is to open a root shell which will then do nothing until i quit as root and then the script will try and run the rest of the commands in the script without root access (so they dont run correctly)

How would I make a script that will allow root access?

Just some notes - 
Im not trying to create a script that bypasses the sudo password (so you dont need to list the reasons for sudo :))
Or trying to create a script that stores the sudo password in anyway
My script needs to be able to create symlinks outside of the home directory (thats why it needs sudo rights)

Thanks in advance 
Mark

---

### Post by coffeecat on 2011-04-18
You want a script that needs root privileges? One answer is to write it as though it has - don't use sudo anywhere - and launch it with:

```
sudo bash ./name_of_script.sh
```

Do that from an ordinary terminal; you don't need to sudo su to a root terminal.

---

### Post by deathadder on 2011-04-18
Can you edit the sudoers file you can use ln without providing a password?
```
CaptainMark ALL=(ALL) NOPASSWD: /bin/ln
```
Then you'd just be able to use "sudo ln" within the script.

---

### Post by Karlchen on 2011-04-18
Hi, deathadder.

Guess following your advice may be pretty convenient for most lazybones. But shouldn't you mention that doing so drops your Ubuntu back to the security level of something like Windows 95 or so? :frown:

Karl

---

### Post by HermanAB on 2011-04-18
Howdy,

Try Gksu and Beesu.

---

### Post by hakermania on 2011-04-18
> **Karlchen said:**
> Hi, deathadder.

Guess following your advice may be pretty convenient for most lazybones. But shouldn't you mention that doing so drops your Ubuntu back to the security level of something like Windows 95 or so? :frown:

Karl

I was thinking to post as well for this issue.....
Nevermind, running the script with sudo permissions would do the trick

---

### Post by deathadder on 2011-04-18
> **Karlchen said:**
> Guess following your advice may be pretty convenient for most lazybones. But shouldn't you mention that doing so drops your Ubuntu back to the security level of something like Windows 95 or so? :frown:
This is very true, I thought I had added a "You probably shouldn't do this" to the end of the post, oh well.

Although to be honest I have once or twice allowed NOPASSWD for a few commands on my machine like so:
```
me machine = NOPASSWD: /sbin/shutdown
```
Although as with all things posted on the internet you should make sure you understand what it's doing before entering a command. Including security concerns...

---

### Post by CaptainMark on 2011-04-18
It's a script that I intend on passing to friends who are complete terminal-phobes so I wanted it to be a simple case of double clicking the script, that's why I want to write the sudo part into the script rather than run the script with sudo rights

---

### Post by Zimmer on 2011-04-18
Why not just sudo the first command in the script?

Works for me and an rsync script I use. Not sure about the Symlinks, though.

That way when running the script the user is asked for the sudo password... 

any use ?

---

### Post by Paqman on 2011-04-18
If you include sudo commands in a script, they'll simply be prompted for their password when they run it. The sudo timeout will then allow all subsequent sudo commands in the script to be run without prompting.

---

### Post by deckoff on 2011-05-02
No matter what I tried to make a script  run with a sudo command inside, I fail. I run Natty 11.04.

Here is what I entered in sudo visudo 
```
%admin ALL=(ALL) NOPASSWD:/home/deckoff/Desktop/umountMBL
```

This is my actual script:

```
#! /bin/sh

sudo umount /media/MyBookLive
```

Any ideas?

---

### Post by idoitprone on 2011-05-02
[http://ubuntuforums.org/showthread.php?t=1729119](http://ubuntuforums.org/showthread.php?t=1729119) this thread may help?

---

### Post by ~Plue on 2011-05-02
> **deckoff said:**
> 
```
%admin ALL=(ALL) NOPASSWD:/home/deckoff/Desktop/umountMBL
```
That means you wouldn't need to enter the password for sudo with that script, not the contents within. And since the script would be run as root, there is no need to use sudo with umount```
sudo /home/deckoff/Desktop/umountMBL
```

---

