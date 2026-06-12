---
title: "Logitech Harmony One &amp; Concordance / Congruity?"
date: 2011-03-11
forum: New to Ubuntu
---

### Post by sobeitjedi on 2011-03-11
Hi.
 
I wish to update my Logitech Harmony One remote control with Ubuntu - is this possible? From doing a quick search I've seen that you need to install something called concordance so I've run
 
sudo apt-get install concordance
 
Not quite sure what that's done. 
 
So I then installed Congruity. This shows up in the Software Centre as a program that's installed.
 
That's as far as I've got. What else do I need to do to update & customise my remote?

---

### Post by sobeitjedi on 2011-03-15
Someone please help

---

### Post by jrial on 2011-06-17
The "sudo apt-get install congruity" line is something you type on the command line (in a terminal) in order to install congruity. If you're not familiar with the command line, it's the same as installing it via the software center.

You say that you already installed congruity, so all you need to do now is program your remote:

[LIST=1]
[*]Surf to the site [http://members.harmonyremote.com/](http://members.harmonyremote.com/) and skip the page that tells you there is a software update.
[*]If you don't already have an account, create one.
[*]Log in. It may give you the "Software Update Available" page again; just skip it.
[*]Configure your devices (TV, Amplifier, CD player, ...) and activities.
[*]When you're done, it will tell you to connect the remote and click next. Do this.
[*]The site will offer you an "EZHex" file; if your browser doesn't automatically open it with Congruity, tell it to do so:
[INDENT]From the "Open With" dropdown, if Congruity is not an option, pick "Other".
On the left hand side click on "File System".
In the right hand side go to "usr", then "bin" (it will take a while to list the contents of this folder) and doubleclick on "congruity" when the contents are loaded.[/INDENT]
[*]Click "Forward" in Congruity until the button changes to "Close". Close Congruity via the "Close" button.
[*]The site will show you a new screen after a couple of seconds, informing you that the communication with the remote was successful. Click "next".
[*]The site will do some work, and after a while offer you another EZHex file. Again, open with Congruity and click Forward on all screens and let Congruity do its thing.
[*]After Congruity is done, close it and disconnect your remote.
[/LIST]
At this point it's a good idea to keep the site open, and test your setup. Odds are you need to make some adjustments.

Hope this helps.

---

### Post by jean noel on 2011-10-14
Just got to this thread.Brilliant stuff. Need to test my remote to see if this is what I've been searching for so long. :D
Jean Noel

---

### Post by UncleBoxy on 2012-03-16
I just wanted to bump this and say that it worked for me, but I had to run congruity under sudo each time in order for it to connect to my remote (Logitech Harmony 600, but detected as a 700 - no big deal).

Navigated to the web site as per the above instructions.  After receiving Connectivity.EZHex, I ran

```
sudo congruity Connectivity.EZHex &
```After doing more stuff on the web site, it offered a 2nd Connectivity.EZHex file.  I saved this one as Connectivity.2.EZHex and then ran

```
sudo congruity Connectivity.2.EZHex &
```After doing more stuff still on the website, you'll finally get an Update.EZHex file.  I then ran this:

```
sudo congruity Update.EZHex &
```This is the one that updates the remote's firmware with your settings.

I'm honestly not sure if the 2 different Connectivity.EZHex files are needed since I did this several times without using sudo, so who knows.  Anyway, this finally worked for me, so hopefully it helps out someone else.

---

### Post by Elfy on 2012-03-16
Closed.

OPs been gone since last year.

---

