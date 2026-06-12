---
title: "[SOLVED] Delete User"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by AvocadoNia on 2008-12-16
How do I remove 2 of the 3 users from my machine? I am using Intrepid 8.10. I know the names of the user names and the user passwords. I also know the root password. I am the sole owner and sole user of the machine.

This is what happened:
System>Administration>Users and Groups> Error Message

"The configuration could not be loaded You are not allowed to access the system configuration." [/B][/I]


I have successfully used "sudo" commands in safe mode and also in normal mode from a terminal. If you have any questions whose answers can help you help me please respond on this thread.

In the meantime I'll keep searching for the answer by looking at older threads.

---

### Post by taurus on 2008-12-16
What's the output when you run this from a terminal?

```
sudo apt-get update
```

Otherwise, you can delete a user from a terminal with

```
sudo userdel <username>
```

---

### Post by AvocadoNia on 2008-12-16
the output is as follows...



[sudo] password for ana:

---

### Post by AvocadoNia on 2008-12-16
The output for the second line of code kindly supplied yielded this...
sh: Syntax error: newline unexpected

The input was
sudo userdel <user>

and after I got the error message
the input was
sudo userdel <nia>

The two users that I want to delete are (1)user and (2)nia

I accessed the terminal form Applications>Accessories>Terminal

---

### Post by donkyhotay on 2008-12-16
> **AvocadoNia said:**
> the output is as follows...



[sudo] password for ana:

After putting in your password did apt-get update?

---

### Post by taurus on 2008-12-16
You're not supposed to include the < >.

```
sudo userdel user
sudo userdel nia
```

---

### Post by jerome1232 on 2008-12-16
you need to take out the "<>" symbols. Alot of people put those on the parts of the command that you need to change, you don't actually type them.

```
sudo userdel user
```

---

### Post by AvocadoNia on 2008-12-16
I opened a terminal and re-entered command "<" or ">" . I got no error message. Once I was asked for the ana password. I gave it. I closed the terminal. Thank you.

> **taurus said:**
> What's the output when you run this from a terminal?

```
sudo apt-get update
```

Otherwise, you can delete a user from a terminal with

```
sudo userdel <username>
```

> **taurus said:**
> You're not supposed to include the < >.

```
sudo userdel user
sudo userdel nia
```

---

### Post by AvocadoNia on 2008-12-16
The output was an update consisting of about 40 lines of text. The last 3 lines of which are as follows (approximately)...

Get 20:[http://us](http://us) archiive ubuntu.com intrepid updates multiverse Sources [803B]
Fetched 538kBb in 22s (23.9kB/s)
Reading package lists...Done

---

### Post by Kareeser on 2008-12-16
Reenter the commands ***WITHOUT*** the < or >

---

### Post by Paqman on 2008-12-16
Note that the command userdel won't remove the user's home folder. If you want to remove that and free up some space then i'd advise opening nautilus as root:
```
gksu nautilus
```

Close this session of Nautilus as soon as you are done removing the users folders.

You could also do this from the CLI with:
```
sudo rm -rf /home/*username*
```

However, be careful with this command, it's very powerful and can do a lot of damage if you accidentally hit the wrong folder.

---

### Post by AvocadoNia on 2008-12-16
> **Kareeser said:**
> Reenter the commands ***WITHOUT*** the < or >

Done. Thank you.

---

### Post by AvocadoNia on 2008-12-16
Thank you. Yes, by all (safe) means I want to remove all trace of "user" and "nia"

I am not clear on the instructions.

Should I open from recovery mode, inputting the root password,
then input the one line of code exactly as you gave it to access Nautilus?

How will I recognize the "folders" to delete? What will they be called?

If deletion of the correct folders is done at this step will I have any need for CLI ?

> **Paqman said:**
> Note that the command userdel won't remove the user's home folder. If you want to remove that and free up some space then i'd advise opening nautilus as root:
```
gksu nautilus
```

Close this session of Nautilus as soon as you are done removing the users folders.

You could also do this from the CLI with:
```
sudo rm -rf /home/*username*
```

However, be careful with this command, it's very powerful and can do a lot of damage if you accidentally hit the wrong folder.

---

### Post by jerome1232 on 2008-12-16
You can just boot as normal, the users home directories will be located at
/home/user
/home/nia

Functionally my commands are the same as the previous ones, I just added a -v switch so you can see what's being deleted. 

Check the command twice and be sure it's correct before you hit enter, deleting anything as the root user must be done with caution.

The commands:
```
sudo rm -rvf /home/user
sudo rm -rvf /home/nia
```

---

### Post by AvocadoNia on 2008-12-16
> **jerome1232 said:**
> You can just boot as normal, the users home directories will be located at
/home/user
/home/nia

Functionally my commands are the same as the previous ones, I just added a -v switch so you can see what's being deleted. 

Check the command twice and be sure it's correct before you hit enter, deleting anything as the root user must be done with caution.

The commands:
```
sudo rm -rvf /home/user
sudo rm -rvf /home/nia
```

1. Boot normally
2. Enter the two command lines...
sudo rm -rvf /home/user
sudo rm -rvf /home/nia
... into TERMINAL and when asked for a passowrd offer the ROOT PASSWORD.

I am not exactly clear as to where I enter the two command lines and knowing the  name of the place (if it is not Terminal), now to access that place.

...yeah...absolute beginner.

Thanks

---

### Post by taurus on 2008-12-16
Open a terminal, Applications -> Accessories -> Terminal, and enter one line at a time.  When you are done, there should not be those two directories in /home anymore.

```
ls -la /home
```

p.s.  It's not root password that you enter; it's your own password.

---

### Post by Paqman on 2008-12-16
> **AvocadoNia said:**
> 
Should I open from recovery mode, inputting the root password,
then input the one line of code exactly as you gave it to access Nautilus?


No, recovery mode isn't needed for simple admin tasks like this. For reference, recovery mode will (if you tell it) boot you into a command line with root privileges already, so you wouldn't need to use "sudo", and wouldn't be able to use graphical apps like Nautilus.

I should have been more specific about how to launch Nautilus as root, my mistake. You could either have opened a terminal, or simply hit Alt-F2 and entered the command. Alt-F2 has the advantage that you don't need to have the terminal window open as well.

---

### Post by AvocadoNia on 2008-12-16
This  is my "understanding", so to speak (lol):
I need to enter these two command lines...
sudo rm -rvf /home/user
sudo rm -rvf /home/nia

Do I need to do that from Nautilus as root user? If so, how do I oopen Nautilus as root user?

Thanks, I am offline until tomorrow. Thanks for your help. (I use my machine daily in my EFL classes that I teach.)

---

### Post by AvocadoNia on 2008-12-16
Thank you. So ALT + F2 gives me a window titled "Run Application". 

Is it there that I input the "gsk" command or is it there that I enter the two sudo commands with or without the term "sudo" leading the string...

Thank you very much.

---

### Post by jerome1232 on 2008-12-16
Okay I'll try and sum this up, you've been given two methods to remove those folders

Method 1) Command Line
A) Open a terminal; Click Applications -> Accessories -> Terminal or alt+f2 then type 'gnome terminal' without the quotes
B) Type the commands that have been given (or just copy paste)
```
sudo rm -rvf /home/user
sudo rm -rvf /home/nia
```
C) Your done

Method 2) Gui
A) Open Nautilus as root, press alt+f2 then type 'gksu nautilus'
B) Browse to /home and hold shift while deleting the folders 'user' and 'nia'
C) Your done


I hope that clears up some of the confusion for ya.

---

### Post by AvocadoNia on 2008-12-16
So this is the plan:
Applicatioms>Accessories>Terminal
sudo rm -rvf /home/user
sudo rm -rvf /home/nia

and if ever I am asked for a password give the non=root passwords "Sudo" is allowing me to act at root or as root for this specific operation so of course the put in my password not root password. Got it, yeah, that makes sense to me. Thanks so much

So in this route to a solution, I can ignore opening up Nautilus, is that correct? No gshk command anywhere at all, right?


> **taurus said:**
> Open a terminal, Applications -> Accessories -> Terminal, and enter one line at a time.  When you are done, there should not be those two directories in /home anymore. 

This will be handy code to verify that those home directories no longer exist. Thanks.

```
ls -la /home
```

p.s.  It's not root password that you enter; it's your own password.

---

### Post by Paqman on 2008-12-16
> **AvocadoNia said:**
> 
So in this route to a solution, I can ignore opening up Nautilus, is that correct? No gshk command anywhere at all, right?

Absolutely. All you're doing is deleting two folders. You can do it from the command line or from Nautilus, whichever you feel most comfortable doing. I mentioned the option of using Nautilus instead of the command line because (IMO) it's slightly safer and is easier to understand. 

For reference, if you do use the command line, this is what the commands actually mean:

**sudo** = take on root prileges, necessary as you don't own the folder.
**rm** = remove, aka delete.
**-r** = recursive, which means to also delete all the files and folder within the target
**v **= verbose, which means generate some output as it carries out the operation
**f** = use force, so nothing will stop this operation from completing
**/home/user** = the target folder

---

### Post by AvocadoNia on 2008-12-17
Thanks, Paqman. I opened up a terminal, input one line of code at a time and then closed the terminal. I checked for existing users, opening another terminal window and executing the ls -la /home command. Great."ana" is the sole user. Thanks, everyone. Mission accomplished.

---

### Post by AvocadoNia on 2008-12-17
Thanks, Paqman. I opened up a terminal, input one line of code at a time and then closed the terminal. I checked for existing users, opening another terminal window and executing the ls -la /home command. Great."ana" is the sole user. Thanks, everyone. Mission accomplished.

---

