---
title: "Neither synaptic or apt-get work"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by chejose on 2006-12-20
I am trying to install Ubuntu for the first time, and am not able to install new programs. The browser works 100%... I am using it to send this.

Using synaptic, when it attempts to download new package information, the prograss bar just hangs there... a half hour with no movement.

If I try the apt-get update, it hangs at "security" as the example below. Again, half an hour with no movement.

jose@jose-desktop:~$ sudo apt-get update
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.

If I try to install a program with synaptic, the download progress bar just sits there with no movement (after half an hour). Finally the result is:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mozilla-thunderbird/mozilla-thunderbird_1.5.0.7-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mozilla-thunderbird/mozilla-thunderbird_1.5.0.7-0ubuntu1_i386.deb)
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out

If I attempt to install the program with apt-get, the result is:

jose@jose-desktop:~$ sudo apt-get install mozilla-thunderbird
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  mozilla-thunderbird-typeaheadfind mozilla-thunderbird-inspector
  mozilla-firefox mozilla-thunderbird-enigmail
The following NEW packages will be installed:
  mozilla-thunderbird
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.7MB of archives.
After unpacking 30.3MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  mozilla-thunderbird
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main mozilla-thunderbird 1.5.0.7-0ubuntu1
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mozilla-thunderbird/mozilla-thunderbird_1.5.0.7-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mozilla-thunderbird/mozilla-thunderbird_1.5.0.7-0ubuntu1_i386.deb)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Hopefully someone will recognize the problem and have a fix. But please spell it out in detail, since I am very new in linux.

---

### Post by maxamillion on 2006-12-20
It could be a number of things, it appears apt is mapping the mirror to 1.0.0.0 as the ip address, which is obviously very wrong. 

Try this ```
sudo aptitude install mozilla-thunderbird
```

aptitude tends to give more verbose output when something fails, post its output just like you did with the apt-get command and we can work from there.

---

### Post by chejose on 2006-12-20
OK... I did it, and the result is:

jose@jose-desktop:~$ sudo aptitude install mozilla-thunderbird
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  mozilla-thunderbird 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.7MB of archives. After unpacking 30.3MB will be used.
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  mozilla-thunderbird 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": yes
Writing extended state information... Done
0% [Connecting to archive.ubuntu.com (1.0.0.0)]

---

### Post by chejose on 2006-12-20
Sorry, I did not add the end:

 Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
jose@jose-desktop:~$

---

### Post by handy on 2006-12-20
Try [_**this how-to**_]("http://ubuntuforums.org/showthread.php?t=282034"), hopefuly it will solve your problems.

---

### Post by chejose on 2006-12-21
Well, I applied your solution... but I guess it is one step forward, and two back!!

Both synoptic and aptitude updates work now... they don't freeze. But both simply give a list of error 404, could not connect. Ping works fine.

But even stranger is that when I went to Firefox to write this, any page I try to open gets the same notice:

"Please use Internet Explorer to view this page", with a little Explorer icon below.

Now that is really hard to understand!!! Where in the world that would come from...

So I am writing from Windows again.

Hope you have some ideas as to "what now". I am beginning to feel like this:  ](*,) 

Thanks for your help so far...

---

### Post by handy on 2006-12-21
Any page?!

WOW :confused:

---

### Post by horsting on 2006-12-21
I un-install anon proxy and rebooted.  Then everything worked fine. you can do it through synaptic

---

