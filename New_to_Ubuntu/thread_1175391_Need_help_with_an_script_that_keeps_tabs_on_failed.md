---
title: "Need help with an script that keeps tabs on failed ssh login attempts"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by hovzio on 2009-06-01
hello :)

Some background; I have a desktop running an ssh server with firewall setting allowing ports open to the outside world. There are times when I check my logs and see that they are bombarded with login attempts. I wanted a way of being notified when this is happening so I wrote a bash script that will continuously check /var/log/auth.log and let me know when a failed login attemt has been made. For the popup I am using a program called popper, its a nice app using libnotify for a nice gnome integrated poppup. Compiled popper and its source are included in the tar bellow, author of popper is included in the readme. I put a screenshot in the tar.

To my bash script beobachter2.sh, to sum it up its an endless loop that  tails the last line of /var/log/auth.log and greps for certain occurances. 'ssh|failed login|succesfull login|etc' If one is found theres a poppup and its set as a variable, this variable is compared the next time around and if its the same it is skipped as to not repeat poppups for the same log entry. Now I have but a little pause in there, line 79. sleep 0.0 0.2 seconds. To my main question, IS this BAD for my hardware running this so often. The script does exactly what I wanted but I really think this may not be good for the drive or other components. I have it running every 0.2 seconds so no other entries can slip in there, like cron and so forth. Does anyone know of any alternatives? Any input appreciated :)

---

### Post by sanemanmad on 2009-06-01
You could install Denyhosts and use their built-in mail feature. You can then have it mailed to root@localhost

---

### Post by hovzio on 2009-06-01
> **sanemanmad said:**
> You could install Denyhosts and use their built-in mail feature. You can then have it mailed to root@localhost

Sounds cool, how does the mail part work. how would i check the mail? Does anybody know if the script i wrote is indeed "bad" for my hardware or is it fine running this loop every 0.2 seconds?

---

### Post by MrWES on 2009-06-01
> **hovzio said:**
> Sounds cool, how does the mail part work. how would i check the mail? Does anybody know if the script i wrote is indeed "bad" for my hardware or is it fine running this loop every 0.2 seconds?

I use DenyHosts on my server:
[http://ubuntuforums.org/showthread.php?t=450853]("http://ubuntuforums.org/showthread.php?t=450853")
I would also go with secure key logins only:
[http://www.mtu.net/~engstrom/ssh-agent.php]("http://www.mtu.net/~engstrom/ssh-agent.php")
In the denyhosts config you can turn on the feature to email root@localhost the failed attempts. Just make sure you have the following set in /etc/aliases
```
root:yourusernamehere
```
and you'll get root email concerning failed attempts, and you can read it with the command mail from the command line. I believe you can also setup Evolution to read system/root email.

Bill

---

### Post by hovzio on 2009-06-01
> **MrWES said:**
> I use DenyHosts on my server:
[http://ubuntuforums.org/showthread.php?t=450853]("http://ubuntuforums.org/showthread.php?t=450853")
I would also go with secure key logins only:
[http://www.mtu.net/~engstrom/ssh-agent.php]("http://www.mtu.net/~engstrom/ssh-agent.php")
In the denyhosts config you can turn on the feature to email root@localhost the failed attempts. Just make sure you have the following set in /etc/aliases
```
root:yourusernamehere
```
and you'll get root email concerning failed attempts, and you can read it with the command mail from the command line. I believe you can also setup Evolution to read system/root email.

Bill

Very cool, it works rather well. The only problem is that email to root@localhost is working. (that is with and without the alias set) It would be awesome to get this to work right. I guess I could set it up for my google account but I prefer the method mentioned above.

---

### Post by HermanAB on 2009-06-01
Wrong approach.  You are going to get millions of failed login notifications since these brute force attacks are very common.  It is best to just ignore it, or change the SSH port to something non standard to throw the script kiddies off.

---

### Post by Mornedhel on 2009-06-01
> **HermanAB said:**
> Wrong approach.  You are going to get millions of failed login notifications since these brute force attacks are very common.  It is best to just ignore it, or change the SSH port to something non standard to throw the script kiddies off.

I agree.

If you really want to know who tries to log on your system, write a nice sed/perl/whatever script to print a digest of what happened today, for instance (building from your grep in your shell script). There isn't anything you can do anyway on a failed attempt (what are you going to do, ping him back ?) and on a successful attempt, it's not like you can follow the script kiddy's progress through your system like in the movies : since he'll be brute forcing his way in, he'll be using a script, not by hand, and you wouldn't even have the time to pull the ethernet cable out.

As HermanAB says, you can A. ignore it B. change the port C. disallow connections from everyone but a few trusted IPs or blocks of IPs.

---

### Post by MrWES on 2009-06-01
> **HermanAB said:**
> Wrong approach.  You are going to get millions of failed login notifications since these brute force attacks are very common.  It is best to just ignore it, or change the SSH port to something non standard to throw the script kiddies off.


Very true, I only enabled the email notifications in the beginning to ensure everything was working and then I turned it off :)

Now if I feel the need to look, I just cat out /etc/hosts.deny

Bill

---

