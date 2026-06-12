---
title: "Auto-execute script"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by ChrisRChamberlain on 2009-10-06
Hi all

Ubuntu newbie so pls be gentle.

Need to execute the following script on startup and subsequently at say 15 minute intervals on a Ubuntu server.

```
wget -O - --http-user=Username --http-passwd=Password 'http://dynamic.zoneedit.com/auth/dynamic.html?host=www.mysite.com'
```

The code works just fine and updates the IP address at zoneedit.com if required.

If this should be considered to be a simple CRON application, what would the script look like, please?

TIA

---

### Post by Cheezespread on 2009-10-06
Cron can be used as you mentioned.

Save the code snippet of yours in a file in your home directory( **anywhere infact : Do remember the path )**:
eg: Check.sh . 
Path to the script :** /home/<user>/Check.sh**

**Now we edit the crontab file which holds the scheduled tasks.**

```
crontab -e 
```

**Enter this as your cron entry or the scheduled task.**
```
*/15 * * * *  /home/<user>/Check.sh 
```

or

```
0,15,30,45 * * * * /home/<user>/Check.sh
```

<user> - your user name
Please correct me if I am wrong.


[Have a look here if you want to know what the cron entries mean ]("http://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/")

---

### Post by ChrisRChamberlain on 2009-10-06
Cheezespread

Thanks for your reply.

Have created the script file as you suggested.

But when ```
crontab -e
```is entered in the terminal window, there is no editor called.

Instead ```
no crontab for chris - using an empty one
29
```comes up in the terminal window.

What's missing please?

---

### Post by fishy6969 on 2009-10-06
Sorry to jump in

> no crontab for chris - using an empty one


that's OK, this is the first time 'chris' has set up a cron job.

Does an editor (or a choice of which one to use) then appear?

---

### Post by ChrisRChamberlain on 2009-10-06
fishy6969

Thanks for your reply.

No editor or choice of editor appears, so you're left in the terminal window. :(

---

### Post by fishy6969 on 2009-10-06
Try running 'select-editor' from the terminal. It should give you a choice of editors installed on your system. Pick one and rerun crontab -e. Let me know what happens.

---

### Post by ChrisRChamberlain on 2009-10-06
That found it!.

Selected nano and entered ```
*/15 *
``` etc, etc, followed by path/filename.

So how do you now correctly save this file?

---

### Post by fishy6969 on 2009-10-06
Ctrl-X should do it. You won't be see a 'regular' file output name shown - just go with what it defaults to.

---

### Post by Cheezespread on 2009-10-06
As I remember , 
1.ctrl-O writes to the file
2.Press Enter
3.ctrl-x exits from nano.
The file would be saved and you can check your cron entry by using 

```
crontab -l 
```

This lists the crontab entries for the user present now.

---

### Post by ChrisRChamberlain on 2009-10-06
Ctrl+O to save - it seems odd coming from Windows.

Hopefully the script will now run at 15 minute intervals :)

Many thanks to Cheezespread and fishy6969 for your help.

---

### Post by Cheezespread on 2009-10-06
You are welcome. The details of how to save in nano are already listed at the bottom half of the editor when you do a " crontab -e " . You can just try a demo one to see if the cron entry works

---

### Post by ChrisRChamberlain on 2009-10-06
Unfortunately ```
crontab -l
```returns ```
no crontab for chris
```...so still missing something.

---

### Post by fishy6969 on 2009-10-06
Unusual.

When you exited nano did it give you the following message?

> crontab: installing new crontab


---

### Post by Cheezespread on 2009-10-06
1.ctrl-O writes to the file ( dont worry about the file name )
2.Press Enter ( saves the file to the name defaulated )
3.ctrl-x exits from nano.( gives you the terminal prompt )

As fishy6969 said , you should get a 

> crontab: installing new crontab  at the end of it.

---

### Post by Cheezespread on 2009-10-06
I will give you an example to check it.

Open a text editor from Applications > Accessories > Text Editor

Add the following lines to it.

```
#! /bin/sh
apt-cache search ap >> /home/<username>/Desktop/cronout.txt
```

Save the file as check.sh in your Desktop

In terminal change the permission to the file making it executable.

```
chmod u+x ~/Desktop/check.sh
```

Now to the cron part

```
crontab -e
```

select the editor

add this line ( if your time is 6:30 am )

```
32 6 * * * /home/<username>/Desktop/check.sh 
```

_If you are using nano_
Press Ctrl+O
Press Enter 
Press ctrl+X

```
crontab -l 
``` to list it .

<username> is your login name.
Change the time to 2 mins from the current time and wait. See if this works. The similar way , you can create your .sh file and the cron entry

---

### Post by ChrisRChamberlain on 2009-10-07
Thanks for the continuing support.

Reran crontab -e, (suspect did not use Enter in the editor), but anyway crontab -l now produces ```
*/15 * * * * /var/www/zoneedit.sh
``` and the file /var/www/zoneedit.sh exists c/w relevant code.

However the script either does not run or does not update zoneedit.com.

Will now follow Cheezespread's suggestion to determine if cron is running correctly

---

### Post by ChrisRChamberlain on 2009-10-07
Rightly or wrongly, decided on a little experiment before trying Cheezespread's suggestion.

Ran chmod on the file as he suggested, (may not have been necessary?).

Then changed permissions on the file to allow crontab to be the 'Open with' option.

Bingo, it works! :P

Again many thanks to Cheezespread and fishy6969 for your help and patience. :)

---

### Post by Cheezespread on 2009-10-07
Always a pleasure. Was wondering what could have gone wrong !

---

### Post by freak42 on 2009-10-07
now that it works and you gained experience, may I suggest the following:

[https://help.ubuntu.com/community/DynamicDNS#Using%20your%20Computer%20to%20perform%20Dynamic%20DNS%20Notification](https://help.ubuntu.com/community/DynamicDNS#Using%20your%20Computer%20to%20perform%20Dynamic%20DNS%20Notification)

btw some dyndamic dns web sites block you after a while if you update your ip information too often (meaning you update it but it hasn't changed)

hth

---

### Post by ChrisRChamberlain on 2009-10-07
freak42

Thanks for your reply, comments and link.

I already installed ddclient but was unable to get it working, hence this thread.

Unless there's some additional benefit in using ddclient or alternative, would prefer to use cron as it now works and there are other useful routines that might also be run.

Point taken about how often to update - before installing Ubuntu server was using similar setup with Windows checking zoneedit.com every 15 minutes without problem.

---

