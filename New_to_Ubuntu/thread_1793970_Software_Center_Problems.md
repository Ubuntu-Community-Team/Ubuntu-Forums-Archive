---
title: "Software Center Problems"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by Shen Anigans on 2011-06-30
I'm having a bit of a problem with both my Software Center.

Yesterday, I was going mad trying to install some simple software (Skype) from Software Center. The problem was that the install would not start, as it was "Waiting for other software managers to quit". I opened System Monitor and ended all the processes that even looked like a software manager. Still no luck. A friend recommended I just screw it all and update to Ubuntu 11.04 (I am currently on 10.04). So, I went to the downloader on the Ubuntu website, downloaded the darn thing, and two hours later, popped it all on a CD. Then I put the CD back into my computer, and waited for something interesting to happen. Synaptic Package Manager opens, and *it* says it cannot install. I spent the better part of my night searching these forums for up to date solutions, but nothing worked. I turned off the computer, and called it a night

Today, I tried downloading Skype again, <snip>. Lo and behold, it worked! Up until 54% that is. At 54%, Software Center said it was "Applying Changes". After an hour wait, I took the advice of my friend, and rebooted. Skype was gone from the Downloading queue, and was instead under Installed Software. I was happy. Skype works well. However, I now tried to install OpenJDK Java 6 Runtime, and now it's saying it's "Waiting for other software managers to quit". I am on the brink of taking a hammer and solving all my problems with this operating system the old fashioned way.

I know that's a lot to process (computer joke, haha) but I was wondering if anyone could help. I'm new, so if I've done anything taboo, please let me know.

UPDATE: I've managed to once again go crazy on System Monitor and get the download started on OpenJDK Java 6 Runtime. However, it is stuck on "Applying Changes" again. Why is this heppening?

---

### Post by amjjawad on 2011-06-30
Hello and Welcome :)

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

**Canonical partner repository** should be checked.
System > Administration > Synaptic > Settings > Repositories 

Reload and type "Skype" and it should be there.

---

### Post by Shen Anigans on 2011-06-30
Thanks for the link, however, for *all* of my downloads, I am getting stuck on "Applying Changes".

And when I go to open Synaptic, I get a "Unable to get an exclusive lock" error message.

---

### Post by amjjawad on 2011-06-30
> **Shen Anigans said:**
> Thanks for the link, however, for *all* of my downloads, I am getting stuck on "Applying Changes".

And when I go to open Synaptic, I get a "Unable to get an exclusive lock" error message.

Reboot your machine, Login, Open The Terminal and post the output of this command here and please wrap the text with "CODE" tags:

```
sudo apt-get clean
sudo apt-get update
```

---

### Post by Shen Anigans on 2011-06-30
When I did the clean, nothing happened.

When I did the update however, It works until an error pops up:

E: Some index files failed to download, they have been ignored, or old ones used instead.

I run sudo dpkg --configure -a, like it tells me.

Then, I get this:

```
Errors were encountered while processing:
 firefox
 firefox-gnome-support

```

I'm not even using Firefox, I'm using Chrome. What should I do from here?

---

### Post by amjjawad on 2011-06-30
> **Shen Anigans said:**
> When I did the clean, nothing happened.

When I did the update however, It works until an error pops up:

E: Some index files failed to download, they have been ignored, or old ones used instead.

I run sudo dpkg --configure -a, like it tells me.

Then, I get this:

```
Errors were encountered while processing:
 firefox
 firefox-gnome-support

```I'm not even using Firefox, I'm using Chrome. What should I do from here?

As I wrote previously, please post the output (the whole thing) of this command:

```
sudo apt-get update
```

and wrap up the text with "CODE" tags.

Thanks!

---

