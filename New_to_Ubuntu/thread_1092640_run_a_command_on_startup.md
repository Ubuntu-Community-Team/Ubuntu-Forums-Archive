---
title: "run a command on startup"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by funkyali on 2009-03-10
Hi

I wanted to find out how/where I can place commands to run on startup as an example I want to run the following on startup.

```
sudo /opt/lampp/lampp start
```

Of course this will ask for a password so how can I run is as a root so I would need something equilivalent.

---

### Post by Master_Odin on 2009-03-10
Take a look at [this thread](http://ubuntuforums.org/showthread.php?p=2875632)

Or you could add the command as 
gksudo /opt/lampp/lampp start 

in the Sessions area (though you'll have to enter a password).

---

### Post by Locutus_of_Borg on 2009-03-10
sudo -i
echo "/opt/lampp/lampp start" >> /etc.conf.d/local.start

put anything in that file you want executed at boot as root

---

### Post by aaaantoine on 2009-03-10
> **Locutus_of_Borg said:**
> sudo -i
echo "/opt/lampp/lampp start" >> /etc**/**conf.d/local.start

put anything in that file you want executed at boot as root

Did I fix that for you?

---

### Post by Locutus_of_Borg on 2009-03-10
woops

good call


too used to tab completion to properly type anything these days ;p

---

### Post by funkyali on 2009-03-10
> **aaaantoine said:**
> Did I fix that for you?
Its not working this is what I typed

```
user@laptop:~$ sudo -i
root@laptop:~# echo "/opt/lampp/lampp start" >> /etc/conf.d/local.start
-bash: /etc/conf.d/local.start: No such file or directory
root@laptop:~# 

```

---

### Post by Master_Odin on 2009-03-10
> **funkyali said:**
> Its not working this is what I typed

```
user@laptop:~$ sudo -i
root@laptop:~# echo "/opt/lampp/lampp start" >> /etc/conf.d/local.start
-bash: /etc/conf.d/local.start: No such file or directory
root@laptop:~# 

```
I feel like you completely ignored my suggestion. :P
Go into terminal, type the command
sudo gedit /etc/rc.local

and add the following lines into the file:
/opt/lampp/lampp start
lomoco -m --sms

before exit 0

your localhost will now be started on startup (this is now I have mine set-up too! :o)

Also, I tried the other suggestion and got the same error as well since the file doesn't appear to exist on default <.<

---

### Post by Locutus_of_Borg on 2009-03-10
sorry, not using ubuntu here

its a part of sysvinit and i guess ubuntu uses upstart instead of traditional system v

---

### Post by t0p on 2009-03-10
Go to **System** > **Preferences** > **Sessions**, there's a facility there to set start-up programs.

---

### Post by bodhi.zazen on 2009-03-10
> **t0p said:**
> Go to **System** > **Preferences** > **Sessions**, there's a facility there to set start-up programs.

Those will be run when you log in.

To run at the time of booting, put the commands in /etc/rc.local as suggested earlier.

If you need to bypass the need to enter a password, take a look at expect.

---

### Post by funkyali on 2009-03-11
> **Master_Odin said:**
> I feel like you completely ignored my suggestion. :P
Go into terminal, type the command
sudo gedit /etc/rc.local

and add the following lines into the file:
/opt/lampp/lampp start
lomoco -m --sms

before exit 0

your localhost will now be started on startup (this is now I have mine set-up too! :o)

Also, I tried the other suggestion and got the same error as well since the file doesn't appear to exist on default <.<

Sorry I did read your post but that post you refered to just seemed to go over my head.

Thanks a million it is now starting my LAMP when I start up thanks a million. What is the this line for ```
lomoco -m --sms
```

---

### Post by Master_Odin on 2009-03-11
> **funkyali said:**
> Sorry I did read your post but that post you refered to just seemed to go over my head.

Thanks a million it is now starting my LAMP when I start up thanks a million. What is the this line for ```
lomoco -m --sms
```
Oops, sorry. That was one line too many! :P

lomoco is a package to manage USB logitech mice. So you if you don't have one, you don't need it. I have about 10 commands that are run in that file and the /opt/lampp/lampp start and well, haste makes fools of us all in the end. =/

---

