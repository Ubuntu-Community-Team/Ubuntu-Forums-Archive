---
title: "Way To Re-install Ubuntu W/o  Deleting The Files too?"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by scootatheschool1990 on 2009-02-28
Ok. so i have a problem that hasn't been resolved. everytime i start my computer (ubuntu 8.10) there is no log-on screen. Instead of finding the fix to that, is there a comand that will let me wipe away ubuntu but keep all my files? Settings i don't care about because i believe they are the cause of my problems. 

it'd be nice to possible get my log on screen too because i can't even log on right now. ha ha

ANY Help would be lovely! I look forward to your responces
THANKS
~ scott

---

### Post by zzHanks on 2009-02-28
Hi.

I would boot up the LiveCD and copy the files to another hard drive. And do a clean install.

Note: I'm not an advanced user, so you might want to wait for another reply.

---

### Post by lordharsha on 2009-02-28
Unless your files are on a seperate partition, your only choice is to backup the data on an external device.
Although you mentioned you don't want a fix, could you tell me what happens when you boot up? Is there a blank screen, or a command line?

---

### Post by steveneddy on 2009-02-28
If you just want to reinstall the OS, just back up the /home directory and reinstall.

What did you do to make the GUI not come on at boot?

Do you get a test screen that asks you to log in?

What video cards do you have?

Do you have the correct video drivers installed for the video card that is installed in the PC?

Were you trying to install drivers that are not in the repos for your video card?

---

### Post by linuxisevolution on 2009-02-28
> **scootatheschool1990 said:**
> Ok. so i have a problem that hasn't been resolved. everytime i start my computer (ubuntu 8.10) there is no log-on screen. Instead of finding the fix to that, is there a comand that will let me wipe away ubuntu but keep all my files? Settings i don't care about because i believe they are the cause of my problems. 

it'd be nice to possible get my log on screen too because i can't even log on right now. ha ha

ANY Help would be lovely! I look forward to your responces
THANKS
~ scott

After the computer boots and you don't see a login screen you should see something like "login:$". Type your username and hit enter, and then type your password and hit enter. You will not be able to see them as you type. After that type sudo apt-get install ubuntu-desktop . After that is finnished restart the computer.

---

### Post by scootatheschool1990 on 2009-03-01
> **lordharsha said:**
> Is there a blank screen, or a command line?

yeah! there's just a blank screen but it has the curser and i can move it around. just no way to "log onto my account" i can press "cntrl alt F6" which gets me to the black and white screen where i can do Sudo's and what not. anything?

---

### Post by scootatheschool1990 on 2009-03-01
> **steveneddy said:**
> If you just want to reinstall the OS, just back up the /home directory and reinstall.

What did you do to make the GUI not come on at boot?

Do you get a test screen that asks you to log in?

What video cards do you have?

Do you have the correct video drivers installed for the video card that is installed in the PC?

Were you trying to install drivers that are not in the repos for your video card?

I know it's not the video card because i was doing the cube desktop (ifg what it's called) but i can see the screen and get to where i can write sudo's. any ideas?

---

### Post by scootatheschool1990 on 2009-03-01
> **linuxisevolution said:**
> After the computer boots and you don't see a login screen you should see something like "login:$". Type your username and hit enter, and then type your password and hit enter. You will not be able to see them as you type. After that type sudo apt-get install ubuntu-desktop . After that is finnished restart the computer.

ok. i'll see if that works " sudo apt-get install ubuntu-desktop"
thanks ill post a reply here in a second

---

