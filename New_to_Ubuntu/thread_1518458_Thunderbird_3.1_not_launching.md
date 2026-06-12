---
title: "Thunderbird 3.1 not launching"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by Norm24 on 2010-06-26
Been using the Mozilla build(installed thru Ubuntzilla) for a couple of years now.I upgraded to 3.1 yesterday and everything worked fine.Today it won't launch.When I click on the launcher the cursor starts turning and the usual notification in the bottom panel shows saying its starting and then nothing.

I've tried re-installing and that's a no go.

I've also tried removing it completely in terminal using:
```
sudo apt-get remove thunderbird-mozilla-build

```

And get this error message:
```
Errors were encountered while processing:
 thunderbird-mozilla-build
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've also tried removing it through synaptic and got this:
```
E: thunderbird-mozilla-build: subprocess installed post-removal script returned error exit status 2
```

I'm going assume its a bug in 3.1.If I could just completely remove the Mozilla version I could then install the Ubuntu version and move on.
Any help would be appreciated.

---

### Post by stmiller on 2010-06-26
Run this then try it again:

```
sudo apt-get clean
```

Most likely apt is having issues.

---

### Post by Norm24 on 2010-06-27
This is what I got after running clean,autoclean and autoremove:

```
dpkg-divert: mismatch on package
  when removing `diversion of /usr/bin/thunderbird to /usr/bin/thunderbird.ubuntu by thunderbird-mozilla-build'
  found `local diversion of /usr/bin/thunderbird to /usr/bin/thunderbird.ubuntu'
dpkg: error processing thunderbird-mozilla-build (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 thunderbird-mozilla-build
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by zerubbabel on 2010-06-27
After I did a clean install of 10.04 (amd64), I had similar problems getting Thunderbird 3.1 to run, and the problem seemed to be that it didn't want to inherit my old profile. I had to let it create a new profile and then copy my old "mail" subtree on top of the newly created profile. Then it worked fine.

---

### Post by Norm24 on 2010-06-27
I unfortunately have done something very stupid and manually deleted all files and folders with the word thunderbird.I can now install thunderbird without any conflicts...but when I try to launch it I get this error message:

```
Failed to execute child process "thunderbird" (No such file or directory)
```

Sometimes I really wish I could kick myself in the backside before I do something stupid!

---

### Post by Norm24 on 2010-06-28
Any clues guys as to how I can restore tbird?

---

### Post by Norm24 on 2010-06-30
Nuthin aye?

I guess its a full re-install of Ubuntu then.

---

### Post by Norm24 on 2010-07-01
Unbelievable.No one can truly help?

I really have to install the entire OS just to receive email?

---

### Post by Norm24 on 2010-07-06
C'mon!!!There's truly no one in the entire Ubuntu community that can help?I understand that most of the damage is my fault but really...NOBODY can help?I cannot install any email program without the same error messages.Thank goodness I still kept a dual boot with Windows...its been my only way of sending/receiving email.

I can't believe the only way to fix this is completely wipe the entire OS and start fresh.

---

### Post by lidex on 2010-07-07
Try this. Open this file for editing:
```
gksu gedit /var/lib/dpkg/status
```
Now find the entry for that package - I assume 'thunderbird-mozilla-build', beginning with 'Package:' and ending with space before next 'Package:'
Highlight and delete, then save file, close gedit.
Now:
```
sudo updatedb
locate thunderbird
```
Delete anything you find outside of your profile. I would suggest renaming and moving that. 
Next:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install thunderbird
```

---

### Post by Norm24 on 2010-07-07
> **lidex said:**
> Try this. Open this file for editing:
```
gksu gedit /var/lib/dpkg/status
```
Now find the entry for that package - I assume 'thunderbird-mozilla-build', beginning with 'Package:' and ending with space before next 'Package:'
Highlight and delete, then save file, close gedit.
Now:
```
sudo updatedb
locate thunderbird
```
Delete anything you find outside of your profile. I would suggest renaming and moving that. 
Next:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install thunderbird
```

When I try to launch I still get this error:
```
Failed to execute child process "thunderbird" (No such file or directory)
```

Thanks for the try.I really do appreciate your time and effort.

---

### Post by lidex on 2010-07-07
But you were able to install without error, correct?

---

### Post by Norm24 on 2010-07-08
> **lidex said:**
> But you were able to install without error, correct?

Yes.

---

### Post by AAccount on 2010-07-08
Did you try downloading thunderbird from the Mozilla website and using that like you would in M$ Windows?

[http://www.mozillamessaging.com/en-US/thunderbird/](http://www.mozillamessaging.com/en-US/thunderbird/)

I find the Ubuntu tends to be slow in updating firefox and thunderbird so I "installed" it like windows and have firefox & thunderbird check for updates by themself. It's easy to do

1 Install compatible 32 bit libraries:  "sudo apt-get install ia32-libs" (if you're using 64 bit)
2 Remove the Ubuntu's thunderbird "sudo apt-get remove thunderbird"
3 Assuming you downloaded the tar.bz2 package to Downloads, right click on it and choose extract here
4 Open a terminal and type "cd Downloads" and then "sudo mv thunderbird /usr/lib".
5 Now to launch thunderbird just run "/usr/lib/thunderbird/thunderbird".

---

### Post by Norm24 on 2010-07-08
> **AAccount said:**
> Did you try downloading thunderbird from the Mozilla website and using that like you would in M$ Windows?

[http://www.mozillamessaging.com/en-US/thunderbird/](http://www.mozillamessaging.com/en-US/thunderbird/)

I find the Ubuntu tends to be slow in updating firefox and thunderbird so I "installed" it like windows and have firefox & thunderbird check for updates by themself. It's easy to do

1 Install compatible 32 bit libraries:  "sudo apt-get install ia32-libs" (if you're using 64 bit)
2 Remove the Ubuntu's thunderbird "sudo apt-get remove thunderbird"
3 Assuming you downloaded the tar.bz2 package to Downloads, right click on it and choose extract here
4 Open a terminal and type "cd Downloads" and then "sudo mv thunderbird /usr/lib".
5 Now to launch thunderbird just run "/usr/lib/thunderbird/thunderbird".

Not for nothing but please read everything from the very 1st post before replying.

---

### Post by lidex on 2010-07-08
Have a look here:
[http://ubuntuforums.org/showthread.php?t=1524128&highlight=thunderbird]("http://ubuntuforums.org/showthread.php?t=1524128&highlight=thunderbird")

---

