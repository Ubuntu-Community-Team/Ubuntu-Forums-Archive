---
title: "lost power while upgrading"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by nubimax on 2009-07-01
when downloading updates a clap of thunder from afternoon storm lost power now very few programs work I can get to terminal but have never used it every thing I get power manager failure. do I need to reload 8.04 or is there another solution.

computer Alaska, 1 g ram 40 g hd

---

### Post by DGortze380 on 2009-07-01
> **nubimax said:**
> when downloading updates a clap of thunder from afternoon storm lost power now very few programs work I can get to terminal but have never used it every thing I get power manager failure. do I need to reload 8.04 or is there another solution.

computer Alaska, 1 g ram 40 g hd

Were you downloading updates? or where you upgrading to a new version of Ubuntu?

Open a terminal and try this:

```

sudo apt-get update && sudo apt-get upgrade

```

If that errors out, you likely have to run 

```

sudo dpkg --configure -a

```

---

### Post by kansasnoob on 2009-07-01
I would go to terminal and run:

```
sudo dpkg-reconfigure -phigh -a
```

I've had that take a long time, but it may save you having to reinstall.

Then let us know what you end up with.

---

### Post by nubimax on 2009-07-01
terminal ask for password when I enter password it tells me sorry wrong password, as far as I know I only have the one.  I was down loading upgrades for 8.04 from upgrade manger.
M

---

### Post by DGortze380 on 2009-07-01
> **nubimax said:**
> terminal ask for password when I enter password it tells me sorry wrong password, as far as I know I only have the one.  I was down loading upgrades for 8.04 from upgrade manger.
M

Your password is your user accounts password, same one you use to log-in, same one you created when you installed.

It will not show on the screen as you type, type anyways, hit enter when you're done.

---

### Post by DGortze380 on 2009-07-01
> **nubimax said:**
> terminal ask for password when I enter password it tells me sorry wrong password, as far as I know I only have the one.  I was down loading upgrades for 8.04 from upgrade manger.
M

Upgrade and updates are two different things.

Were you downloading typical, daily UPDATES for 8.04?

Or where you trying to UPGRADE to 8.10?

Or where you UPGRADING to 8.04?

I don't quite understand what you're trying to explain...

---

### Post by nubimax on 2009-07-01
I was downloading updates (Iwent back to look) I am using the password that I sign in with. it now says 3 incorect attempts.  I am posting with my laptop, Toshiba Satellite L355-S7837 4 gig ram 250gig HDD
M

---

### Post by DGortze380 on 2009-07-01
> **nubimax said:**
> I was downloading updates (Iwent back to look) I am using the password that I sign in with. it now says 3 incorect attempts.  I am posting with my laptop, Toshiba Satellite L355-S7837 4 gig ram 250gig HDD
M

Do you have more than one user?

There's no reason for it to not take your password. Remember, they're case sensitive.

---

### Post by nubimax on 2009-07-01
There are no other users on that computer other then myself my wife has her own laptop and a net book that we use when traveling. There were a lot of updates, a 2 hr down load. I have had 8.04 for about 6 months but just got internet for it 2 days ago. 
M

---

### Post by DGortze380 on 2009-07-01
> **nubimax said:**
> There are no other users on that computer other then myself my wife has her own laptop and a net book that we use when traveling. There were a lot of updates, a 2 hr down load. I have had 8.04 for about 6 months but just got internet for it 2 days ago. 
M

Those two commands are the ones you need to start with, so you've got to figure out that password issue.

What happens if you do 

```

sudo touch /tmp/test.txt

```

You must have entered a password to do the updates, and it worked then.

I suppose the crash may have caused and issue with sudoers, there is something else we can try if you can't get that password to work.

---

### Post by nubimax on 2009-07-01
That let me in I got E:could not open lock file /var/lib/apt/lists/lock - 13 permision denied E: unable to lock the list directory
M

---

### Post by DGortze380 on 2009-07-02
> **nubimax said:**
> That let me in I got E:could not open lock file /var/lib/apt/lists/lock - 13 permision denied E: unable to lock the list directory
M

What did you enter that gave you that error?

Try 

```

sudo dpkg --configure -a

```

---

### Post by nubimax on 2009-07-02
to enter the terminal I used (sudo touch /tmp/test -txt) then I used (sudo apt-get update) that gave me the (could not unlock files message) then I ran (sudo dpkg-reconfigure -a) the computer reconfigured files for 14 minutes many of the files had errors.  This morning I turned on the computer and all I get is this message (kernal panic not syncing: vfs: unable to mount root fs on unknown -block(o,o) )
I have back ups on all files in this computer and my origanal iso disk for ubuntu 8.04.
M

---

### Post by DGortze380 on 2009-07-02
> **nubimax said:**
> to enter the terminal I used (sudo touch /tmp/test -txt) then I used (sudo apt-get update) that gave me the (could not unlock files message) then I ran (sudo dpkg-reconfigure -a) the computer reconfigured files for 14 minutes many of the files had errors.  This morning I turned on the computer and all I get is this message (kernal panic not syncing: vfs: unable to mount root fs on unknown -block(o,o) )
I have back ups on all files in this computer and my origanal iso disk for ubuntu 8.04.
M

If you have your backups, and an install disc, the simplest solution is to reinstall. Sounds like the power outage really hosed some system files.

If you prefer to keep working on a fix instead let me know... but at this point it will be difficult to get the system stable again, at least until we figure out which files have errors.

---

### Post by kansasnoob on 2009-07-02
It sounds like you got past the password problem but if not look here:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Regardless read that page about accessing Recovery Mode. Of course start up in recovery mode, and if needed fix the password problem as outlined there, otherwise just skip to "dpkg - Repair broken packages" as shown here:

[http://www.psychocats.net/ubuntu/images/resetpassword03.png](http://www.psychocats.net/ubuntu/images/resetpassword03.png)

Still no luck? Then start up in recovery mode again and select "root - Drop to root shell prompt". Then type:

```
sudo dpkg-reconfigure -phigh -a
```

---

### Post by nubimax on 2009-07-02
problems solved recovery mode has me up and running all my files still there many thanks to DGortze 380 and Kansasnoob for there help in this problem 
M

---

