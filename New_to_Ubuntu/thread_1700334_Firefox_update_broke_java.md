---
title: "Firefox update broke java"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by Miljet on 2011-03-04
My wife installed updates this morning that included updating Firefox to version 3.6.14. When she tried  to access Pogo.com tonight, she got an error message that Firefox 3.6.14 has a bug that will not allow java to work. I haven't installed the updates yet and still have Firefox 3.6.13 which works.

I don't know how the bug affects other sites, but if you are a Pogo user, do NOT install the update yet.

---

### Post by mikewhatever on 2011-03-04
Mozilla has released version 3.6.15 addressing that issue.

[http://www.mozilla.com/en-US/firefox/3.6.15/releasenotes/](http://www.mozilla.com/en-US/firefox/3.6.15/releasenotes/)
```
What’s New in Firefox 3.6.15

Firefox 3.6.15 fixes the following issues found in previous versions of Firefox 3.6:

[B]Fixed an issue where some Java applets would fail to load in Firefox 3.6.14
[/B]
```

Hopefully Ubuntu devs will update shortly.

---

### Post by Miljet on 2011-03-04
Yes, a little further investigation turned up this link:
[https://support.mozilla.com/en-US/kb/pogo-and-other-java-pages-dont-work](https://support.mozilla.com/en-US/kb/pogo-and-other-java-pages-dont-work)

Apparently version 3.6.15 has been released by Mozilla but is not in the Ubuntu repositories yet. If it doesn't show up by tomorrow, I may have to refresh my memory on installing a tarball. Pogo.com is my wife's favorite site.

---

### Post by mikewhatever on 2011-03-04
With Firefox, there is nothing to install, just unpack and run it from the 'firefox' directory. Easy-peasy.

---

### Post by Penny N. Nickels on 2011-03-05
The update for Firefox 3.6.15 was in my updates this morning. I'm back to playing games at Pogo.com! :D

---

### Post by Miljet on 2011-03-05
> The update for Firefox 3.6.15 was in my updates this morning. I'm back to playing games at Pogo.com!

I just checked my updates and no such luck! But I am running 10.04 and assume that you are running 10.10?

> With Firefox, there is nothing to install, just unpack and run it from the 'firefox' directory. Easy-peasy.

Maybe easy-peasy for you, but nothing ever comes easy for me. I have extracted the files and found a file called run-mozilla.sh, which I assume to be the install script. But it refuses to run. And yes, I did make it executable first. I get the error message "run-mozilla.sh: Cannot execute."

---

### Post by asmoore82 on 2011-03-05
I'll have to concur with the "easy peasy" sentiment.

The .tar.gz you've downloaded for firefox isn't an installer —
it is the app iself. Just extract it were you want it and run the
"firefox" script that is inside of it.

Of course, "run-mozilla.sh" and "firefox-bin" are part of the voodoo that is required
for firefox to actually work, but the top-level "firefox" script does that for you.

---

### Post by mikewhatever on 2011-03-05
> **Miljet said:**
> I just checked my updates and no such luck! But I am running 10.04 and assume that you are running 10.10?
Shouldn't matter really, but you might not be using the same mirror.

> 
Maybe easy-peasy for you, but nothing ever comes easy for me. I have extracted the files and found a file called run-mozilla.sh, which I assume to be the install script. But it refuses to run. And yes, I did make it executable first. I get the error message "run-mozilla.sh: Cannot execute."

Once you unpack the tar ball, the folder named firefox will appear with ready to run binaries (all permissions set, nothing to install). Open a terminal window, cd into that folder (cd firefox), then run the firefox executable (./firefox).

_recap_
cd firefox
./firefox

You could create a GUI launcher, but that's probably an overkill for just one day or so. After updating, just delete the firefox folder, and it's gone.

By the way, I didn't get the 3.6.15 yet either.

---

### Post by Miljet on 2011-03-05
Thanks for the info. I've got her using Epiphany right now. She doesn't like it, but it works until I can get the Firefox issue sorted.

---

### Post by djeims on 2011-03-06
Hi.
Being a big RISK fan (pogo.com), I also have the same problem with the latest firefox update. I also don't know what to do with the extracted files from the tar.bz.whatever file.

Do I extract them into the /usr/lib/firefox directory? 
Do I extract them into the /etc/firefox directory?

You have to remember that you are in the beginner forum and sentiments like "easy peasy" arn't useful at all

---

### Post by djeims on 2011-03-06
I don't even have permission to extract, apparently

---

### Post by JohnE1 on 2011-03-06
> **mikewhatever said:**
> With Firefox, there is nothing to install, just unpack and run it from the 'firefox' directory. Easy-peasy.

That is dangerous advice to the unknowing, as witnessed by the follow-ups.

The danger is having 2 conflicting versions of Firefox files installed. After manually installing a 2nd but different version of a program on a system, who knows what files from what versions are located in what directories? Not to mention the dependency hell that can wreak havoc on the unsuspecting newbie.

When switching from programs maintained by Synaptic to manually maintaining them on your own, it is **always** best to **FIRST uninstall** the program(s) with Synaptic, **THEN install** the replacement program(s) manually. Also, it should be pointed out that once you replace a program manually, you are forever responsible for maintaining its updates; don't expect Synaptic to bail you out on that duty.

So, to the newbies, tread cautiously. I like the solution of one poster, installing an alternate program for a temporary solution. In this case, he installed Epiphany for his wife. No doubt, he used Synaptic for the install, and it will just as easily uninstall Epiphany when it's no longer needed (when Ubuntu finally releases the Firefox update in its repositories).

Firefox 3.6.15 has been out for several days now. I sure hope Ubuntu gets it out very soon for Ubuntu 10.10.

Anyone know if Red Hat has the Firefox update out there for Red Hat Enterprise Linux Server and for Fedora?

---

### Post by flyfishingphil on 2011-03-07
> **Miljet said:**
> My wife installed updates this morning that included updating Firefox to version 3.6.14. When she tried  to access Pogo.com tonight, she got an error message that Firefox 3.6.14 has a bug that will not allow java to work. I haven't installed the updates yet and still have Firefox 3.6.13 which works.

I don't know how the bug affects other sites, but if you are a Pogo user, do NOT install the update yet.
Just checked and the updates I had received did not include the Firefox update. If you have Firefox, and have not received the update to 3.6.15 try this easy method of finding it:
Click on System > Adminstration > Update Manager
When the Update Manager opens click on the "Check Updates" box.

This brought up the FF update to 3.6.15. Checked Pogo and no problems getting in. Simply do the "install updates" whe it appears.
(I'm not very good at this so I figure a simple method is great to hear about.)

---

