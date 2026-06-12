---
title: "Thunderbird link to Browser"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by Don Bowen on 2010-04-05
When someone emails me a URL, I click on it, and instead of opening the Browser (FireFox), it gives me a little dialogue that says **"this link needs to be opened with an application."**

True. It does, and the application is FireFox.  It even gives you a "browse" button to locate an application, but how do you know where FireFox installed itself?

This makes me think of another question... is there a common folder (a la "ProgramFiles") where Ubuntu programs install themselves?  If so, what is the name/location of this folder?

thanks for reading,
D. Bowen

---

### Post by Uzi304 on 2010-04-05
Most programs install their executables in /usr/bin. So Firefox should be /usr/bin/firefox

---

### Post by r-senior on 2010-04-05
And you can confirm where a program is using:

$ which firefox
/usr/bin/firefox

Why bother? Well, it's true that most application type programs are in /usr/bin, but other programs aren't:

$ which grep
/bin/grep
$ which shutdown
/sbin/shutdown

If you are curious about such things:

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")

---

### Post by Michael Dooley on 2010-04-05
Please see [this]("http://ubuntuforums.org/showthread.php?t=1425738") thread.

---

### Post by uRock on 2010-04-05
Go to System> Preferences> Preferred Applications and make sure the Web Browser you want is selected. You may have to choose custom to get the "Open Link with Browser Default" highlighted.

---

### Post by Don Bowen on 2010-04-05
That fixed it for one user who logs on to this machine, but the other user (me) still can't click on a link in an email and have it load the browser and go to that link.  I'm sure I've messed up the setting on my account, but now I can't get that little dialogue box to come back to try to fix it.

I did click System, Preferences, Preferred Applications, and that setting seems correct.  It points to FireFox.

When I right-click the link in the email message, on of the menu choices is "open in browser", but that does nothing as well.

I'm guessing that it's a Thunderbird setting that's wrong.  One way to fix that is to remove thunderbird, and hunt down every folder of the same name and remove that.   

The other procedure that will fix it (probably) is to get out the installation CD, and remove and re-install Ubuntu 09.10!  That usually fixes most things but leaves me not knowing what caused the problem in the first place.

---

### Post by Don Bowen on 2010-04-05
OK..that fixed it.  I went to /home/don and deleted the .thunderbird folder.  This wiped out my individual account specs and made me start over fresh.  No need to re-install Ubuntu, and it solved the problem.

folders that begin with .  (like .thunderbird) are not visible without checking clicking view, and checking "show hidden files"...(in the Nautilus program)
 or I guess you could hit <CTRL><H>.  Most folks reading this already know that, but it's good to go over things you my THINK people already know.... for the sake of that one person who doesn't.

---

### Post by kellemes on 2010-04-06
> **Don Bowen said:**
> OK..that fixed it.  I went to /home/don and deleted the .thunderbird folder.  This wiped out my individual account specs and made me start over fresh.  No need to re-install Ubuntu, and it solved the problem.


Glad it works for you, but for those reading this thinking it will fix a relative minor browserlink-issue..
[SIZE="5"][COLOR="Red"]This will delete all your account-data[/COLOR][/SIZE] [SIZE="7"][COLOR="Red"]and emails!![/COLOR][/SIZE]

That's no fix for me.. I'd rather kill myself then lose all that ;-)

For some reason I've tried everything fixing the browserlink-issue!
Not working at all.. well.. forget it, it's not important.

---

### Post by lidex on 2010-04-06
You might try installing ubufox and make sure thunderbird-gnome-support (for gnome desktop) is installed as well:

```
sudo apt-get install --reinstall ubufox thunderbird-gnome-support
```

Yeah, and don't delete your profile, as kellemes points out.

---

### Post by Cavsfan on 2010-04-18
> **r-senior said:**
> And you can confirm where a program is using:

$ which firefox
/usr/bin/firefox

Why bother? Well, it's true that most application type programs are in /usr/bin, but other programs aren't:

$ which grep
/bin/grep
$ which shutdown
/sbin/shutdown

If you are curious about such things:

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)


Thanks r-senior! Now I know how to find where the executable is for anything! I saved  it too. 
I finally got Thunderbird to open the link when clicking on it instead of getting the popup.
Thanks again for sharing your knowledge!
By the way, Lucid Owns!

---

