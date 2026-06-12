---
title: "synaptic - error"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by kimikrishna on 2009-01-02
```
Failed to run /usr/sbin/synaptic as user root.

Unable to copy the user's Xauthorization file.
```

I get this error message whenever i open sypatic..

---

### Post by kimikrishna on 2009-01-02
and sypantic is not opening for me..!

how do i get rid of this error ?

---

### Post by Michael.Godawski on 2009-01-02
hi, 

try to restart the machine first. Is the error still occurring?

If yes we will see further.

---

### Post by kimikrishna on 2009-01-02
I restarted.

it still occurs........ :( :( :(

---

### Post by balaknair on 2009-01-02
Did you change file permissions or your user name?

Could you copy paste the following command into a terminal(Applications menu> Accessories> Terminal) and post the output here

ls -l $HOME/.Xauthority

---

### Post by kimikrishna on 2009-01-02
***_I did NOT change any settings... _***
> 
-rw------- 1 gokulakrishna gokulakrishna 117 2009-01-02 09:34 /home/gokulakrishna/.Xauthority

this is what i got

---

### Post by abhiroopb on 2009-01-02
open a terminal and enter the following:

```

sudo chown gokulakrishna .Xauthority

```

---

### Post by balaknair on 2009-01-02
Hmmm...
That seems OK.

gokulakrishna would be your username, and you have read-write permissions on the .Xauthority file.

So from the .Xauthority file I don't see any reason for the error.

Hit Alt+F2--> type ***gksudo synaptic*** , enter your password(for the user gokulakrishna) and see if you're getting this error.

---

### Post by kimikrishna on 2009-01-03
I do not know what is the magic that occured..

my synaptic started working fine ... 

SOLVED >>>>>>> [by magic ;) ]

---

### Post by kimikrishna on 2009-01-04
whoaaaaaaaaaa !! 

[size=7]this started again........[/size]

> help me with a *permanent* solution to solve the sypatic problem.....

---

### Post by kimikrishna on 2009-01-04
> **balaknair said:**
> Hmmm...
That seems OK.

gokulakrishna would be your username, and you have read-write permissions on the .Xauthority file.

So from the .Xauthority file I don't see any reason for the error.

Hit Alt+F2--> type ***gksudo synaptic*** , enter your password(for the user gokulakrishna) and see if you're getting this error.
I tried this too..

I am still getting the same........ :( :confused::confused::confused:

***_> I WANT A PERMANENT SOLUTION FOR THIS SYPATIC PROBLEM_***

---

### Post by kimikrishna on 2009-01-04
will anyone reply me ? :( :( :(

---

### Post by balaknair on 2009-01-06
Sorry for the delay in posting.
Was shifting to a new house, no internet connection for the last two days.

When you get this error, use this command in terminal
```
*ls -l $HOME/.Xauthority*

```
If in the output you see *root root* instead of *gokulakrishna gokulakrishna* it might be a GDM bug(which I believe was only in the GDM in older versions of Ubuntu; what version of Ubuntu are you using?), where it seems some malfunctioning app transfers ownership of the file to root. This usually seems to happen when the system is not properly shut down or when ctrl-alt-backspace is used to force restart the GUI. Have you installed any apps from sources other than the Ubuntu repositories? Or have you had any app crashing or had to 'kill' or 'force quit' any program?

Solution:
What abhiroopb suggested-
In a terminal
```
*sudo chown gokulakrishna .Xauthority*
```

If you're using an older version of Ubuntu, might I suggest switching to a newer version?

---

### Post by kimikrishna on 2009-01-06
oooooo

I am very new user..

I requested a cd and got it....

then will it be the latest one ??? my ubuntu is 810

---

### Post by balaknair on 2009-01-08
Yes, Ubuntu 8.10 is the latest version.

Do you still have trouble with Synaptic, Xauthority?
Does *ls -l $HOME/.Xauthority* show *root root* instead of *gokulakrishna gokulakrishna*?

---

### Post by chargrims on 2009-01-09
Hi there,

I am also having the same problem with 8.10 and having trouble finding a solution.

I had not changed any permissions before getting the message. Using your above command it is my own username shown, not root.

A reboot solves the problem every time, but it occurs again within an hour or so. Also when it happens I get a message in Thunderbird saying 'unable to write temporary file' when trying to send an email.

Sorry if this is highjacking the thread, not posted here before but thought I best post to an existing thread on the topic!

---

### Post by balaknair on 2009-01-09
> Unable to copy the user's Xauthorization file.


As far as I know, this happens in the following situations:

1) After messing around with user or file permissions(chmod, setting up a new 'root' account, setting NOPASSWD options etc.)

2) A bug in older versions of GDM where it failed to reset .Xauthority
(you'd see *root root* instead of [I]username username
[/I])
3) Your hard drive may be full(I should have thought of that before; sorry :oops: )

Since we've eliminated 1) and 2), I think the trouble might well be 3).

You might have run out of space on the Ubuntu partition.
Use Disk Usage Analyzer(Applications menu> Accessories> Disk Usage Analyzer) to check how much free space is available.

If it shows your drive to be full or close to full, delete any unnecessary files from your /home folder or clear the apt-get cache(all files downloaded by Synaptic and the Update Manager are stored here as a backup).
To clear the apt-get cache, type in a terminal
```
sudo apt-get clean
```

---

### Post by kimikrishna on 2009-01-20
I do not know... 

restarting [when i get this] solves my problem..

but it periodically starts... !

---

### Post by kimikrishna on 2009-01-20
it shows gokulakrishna only,, not raot user 

i think that i have low disk space

and i have a question regarding expanding disk size [unanswered] 

you may want to see this..

```
[http://ubuntuforums.org/showthread.php?t=1033020](http://ubuntuforums.org/showthread.php?t=1033020)
```

---

### Post by balaknair on 2009-01-20
I'm afraid I don't know much about LVPM, and in your thread it doesn't give any clue as to what files you're trying to rename and which ones give you the error. I assume it's the root.virtual.disk. The first thing I suggest you do is run a chkdsk from within Windows(Right-click on the C:\ drive icon(or whichever drive Wubi is installed on) in My Computer--> Tools--> Disk checking). You might have to reboot. 

You could also try booting into the LiveCD, navigating to the folder where the file is, and copying/renaming it.

You could check this thread though
[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

As for the synaptic problem, did you try what I mentioned in the previous post?
Use Disk Usage Analyzer to see how much free space you have on your disk and which files/folders are taking up the most space.

---

### Post by grouchyolddude on 2009-01-20
okay .. I'm getting the same error when trying to run synaptic, simple backup, ect. anything requiring Admin.' access ...."I think".
It just started today. I backed up and updated yesterday. 
I tried to restore the backup, but I get the xauthorizatioon error.. 
> -rw------- 1 o o 414 2009-01-19 14:00 /home/o/.Xauthority
 
return from the ls -l $HOME/.Xauthority command in terminal.
I also "think" that is correct?? 
over 40 G on the hd according to "disk usage analyzer"..
Any solutions?? 
THANKS

edit:
another new strange error that may be related
> There is not enough room on the disk to save /tmp/Hwxr3FmF.wmv.part.

when trying to open email attachments.
  I'm getting the email error mentioned previously too.

---

### Post by balaknair on 2009-01-20
@grouchyolddude

Looks like you're running out of space on the hard drive or on your root partition(/).

To get a better idea how much space is being used and how much you've got left in GBs/Mbs, type in a terminal *df -h*


To regain space:
1) Empty Trash
2) *sudo apt-get autoremove* to remove unneeded or deprecated packages
*sudo apt-get clean* to regain some space on your hard drive by deleting the update manager's cache
3) Empty the /tmp folder(this requires exiting the GUI to safely do so without messing things up). At system startup, select Recovery mode from the menu--> it gets you to a Recovery screen--> Drop to Root Shell Prompt--> type in *rm -rf /tmp/**  and then *reboot*
**Be very careful when using root and even more careful with commands like rm -rf**

4) Ubuntu installs quite a few language packs in a default install. Deleting some of these can free up some space. Use localepurge to remove unused language packs.
*sudo apt-get install localepurge*
You will now get a configuration screen asking which ones you want to keep.
Choose the language packs you want, and localepurge will remove the rest.

---

### Post by balaknair on 2009-01-20
Just found this at [http://www.ubuntugeek.com/bleachbit-cleans-unnecessary-files-to-free-disk-space-and-maintain-privacy.html](http://www.ubuntugeek.com/bleachbit-cleans-unnecessary-files-to-free-disk-space-and-maintain-privacy.html)

It's got an illustrated guide on how to use it as well on the page linked above.

---

### Post by grouchyolddude on 2009-01-20
hanks! I'll give it a shot.
I'll report back on the results

---

### Post by balaknair on 2009-01-20
OK

All the best

---

