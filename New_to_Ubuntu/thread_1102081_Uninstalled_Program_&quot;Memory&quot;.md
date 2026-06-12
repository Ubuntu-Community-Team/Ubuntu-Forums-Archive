---
title: "Uninstalled Program &quot;Memory&quot;?"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by Mjsch on 2009-03-21
I am rather new to Linux in general, and I have learned much about linux since installing it about 6 months ago...

The first day I installed ubuntu, I also installed Thunderbird -- and proceeded to ruin my installation by replacing my user profile wrongly and causing a fatal error. So at a loss for a solution, and not having the time to screw with it - I just uninstalled it, and set up evolution. 

A few days ago (~3 months after uninstalling Thunderbird) I decided to give it another try. And just as before, I get the same fatal error that I caused by messing up my profile. So I opened up a "sudo nautilus" window, and navigated to the profiles folder, to see if it was the same problem.

Lo and behold, when I installed thunderbird anew, it still had my old profile from 3 months ago!!!!! How is this possible?

I was able to fix the problem, by just deleting the folder and letting thunderbird create a profile folder before replacing it, but: couldn't this be a security issue? if ubuntu retains program data after it has been uninstalled?
 
Is there a way to check what other uninstalled program "memory" that ubuntu is holding on me?

Thanks.

---

### Post by Bölvaður on 2009-03-21
> **Mjsch said:**
> 

Lo and behold, when I installed thunderbird anew, it still had my old profile from 3 months ago!!!!! How is this possible?


$ sudo apt-get purge thunderbird

*purge* in contrast to *remove* will delete the config files.
This is the same as *remove* vs *completely remove* in synaptic.


*added*
you can just go to your user's folder and either ctrl+h (in nautilus) or ls -A in terminal, and check the names of the hidden files (begins with a dot .)


this is the reason why I chose to have /data partition instead of /home partition.. to get rid of the config files. (yes deleting them would be easy also but maah... just as easy to just mount the /data partition)

---

### Post by yeats on 2009-03-21
> Lo and behold, when I installed thunderbird anew, it still had my old profile from 3 months ago!!!!! How is this possible?

Thunderbird, Firefox and all other xulrunner/Mozilla-based programs store your profile in a hidden folder in your home directory.  These "dot" directories are revealed by doing:

```
ls -a
```

There will be .mozilla (for Firefox) and .mozilla-thunderbird directories, and in each you will see a directory called *random string*.default - this is your user profile where all of your preferences (and in T-bird's case, emails) are stored.  Incidentally, these are portable, and this is a good way to replicate Firefox/Thunderbird profiles on other computers, in Windows, etc.

Apparently you moved this file, which is what caused the error you saw, but it was obviously not deleted, which is why you're still able to see it.

Mozilla programs keep this information by default, unless (as suggested in this thread) you purge the programs.  If all else fails, you can always just delete the .mozilla* directories to rid your station of this data.

---

### Post by Mjsch on 2009-03-21
New Question: I have copied my profile (from a Vista Machine if that matters) -- this time avoiding the fatal error -- and Ubuntu Tbird sees my account settings, etc... but it doesn't see my inbox and local folders. Could this be caused by extensions or something that are not compatible in linux? 

It has my account settings and everything, except for my email!

What's wrong?

Thanks

---

### Post by LowSky on 2009-03-21
inbox and local folders are downloaded directly to the machine, they wont be seen on other machine regardless of the same settings, only messages on the server can be downloaded, best option is to go into account and check "leave messages on server" option, or to set a date to when they can be erased.

---

### Post by 123456789123456789123456 on 2009-03-21
the only thing I can think of is that the folders from vista probably had NTFS permissions attached to them.  and those are sort of interfering with the programs ability to read them correctly.  Suggest you navigate to them, and see what ubuntu says the permissions are.  change them if need to using chmod, chown commands in terminal.

to see in terminal the permissions

ls -l

in case you are not sure of permissions, they will be something like
drw-rw-r--
first spaces ----, which would be drw- are for Owner, second group of 3 ---, rw-, are group owner, third is for everybody else.

if you want post your findings, it can help us, if you are confused about it.

---

