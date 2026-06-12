---
title: "bad firefox fonts...."
date: 2010-03-08
forum: New to Ubuntu
---

### Post by switch10 on 2010-03-08
My Firefox fonts are messed up in Ubuntu.  They were fine until I installed Kubuntu on another partition that shares my /home.  

I've gone to preferences>content in firefox and messed with the fonts, but it doesn't fix them.  

I have a backup of my .mozilla dir that I could restore, but how do I keep this from happening every time I boot in and out of Kubuntu and Ubuntu?

---

### Post by switch10 on 2010-03-08
OK I restored my .mozilla/firefox dir from backup, and it didn't fix the problem.  I guess I will just remove .mozilla, and reinstall firefox.  

I have to remember not to use firefox in Kubuntu...

---

### Post by switch10 on 2010-03-08
This sucks.  I have tried everything.  I cannot change the fonts at all, just the sizes.  I am about to do a complete reinstall of my OS to get my default fonts in Firefox back (I hope that works).  What is going on here?

I purged firefox, deleted the .mozilla/firefox directory, reinstalled, and the fonts are still the same.

Everything was fine, until I installed Kubuntu on another partition that shares my /home partition.

Any Ideas???

---

### Post by switch10 on 2010-03-08
Ok.  I am at a loss here.  A complete reinstall of the OS, other than /home did not fix the problem.  I completely deleted the ~/.mozilla directory as well.  Is there some other config file that firefox uses in /home?  

The font is so thin, practically unreadable.  I just want to restore the default firefox fonts.  they were perfect.

---

### Post by J_Stanton on 2010-03-08
try deleting ~/.fontconfig and see what happens. that's what happens when you have a /home partition sometimes. i just save individual .config files (not the whole /home) and save data to another drive. never had a problem.

---

### Post by switch10 on 2010-03-08
> **J_Stanton said:**
> try deleting ~/.fontconfig and see what happens. that's what happens when you have a /home partition sometimes. i just save individual .config files (not the whole /home) and save data to another drive. never had a problem.

thanks for the reply.  I deleted the .fontconfig dir as well, no luck.  I am switching to chrome on my desktop I guess...  I'm all out of ideas.

---

### Post by dwasifar on 2010-03-08
> **switch10 said:**
> My Firefox fonts are messed up in Ubuntu.

Can you define "messed up"?  What exactly is wrong with them?

---

### Post by switch10 on 2010-03-08
hmm I thought I included a screenshot in my first post, I guess it didn't go through.  The fonts are very thin and close together.  I can't tell if something is bold or not, over all very hard to read.  

This all happened after I installed Kubuntu on another partition, and shared my /home partition.  I've deleted everything that has to do with KDE out of my /home as well.  

Oh well, I guess I am a Google Chrome user now....

---

### Post by dwasifar on 2010-03-09
Did you by any chance install the Microsoft fonts at some point?  Look to see if you have ttf-mscorefonts-installer installed.  I find that Firefox looks crummy with the MS fonts, and it will use them for any page that specifies them - which is most pages - if you have them in your system.  I generally remove them because I have no use for them.

---

### Post by switch10 on 2010-03-09
> **dwasifar said:**
> Did you by any chance install the Microsoft fonts at some point?  Look to see if you have ttf-mscorefonts-installer installed.  I find that Firefox looks crummy with the MS fonts, and it will use them for any page that specifies them - which is most pages - if you have them in your system.  I generally remove them because I have no use for them.

yes msttcorefonts are installed.  But they always have been.  The problem started after Kubuntu made some changes in my /home folder.

Chrome isn't cutting it for me.  It is very good though.  I need firefox.  I am in the process of a reformat of my /home partition, and another reinstall of the OS.  That will fix it.

Its kind of funny I am reinstalling the entire OS because of some fonts :)   I never knew I could be annoyed by such a small detail.

---

### Post by nrb on 2010-05-12
This is a solution that I used in Ubuntu 10.04. 

The problem is not in the fonts in the computer or firefox or Kubuntu and the KDE destop still on the system. It is only in a configuration file ( a "dotfile", one that starts with a '.' so that you don't see it in a normal directory listing) that is in your home directory.  Kubuntu changes some settings in your account in one of the dotfiles. After I made the same mistake of opening kubuntu I also got the terrible fonts. Here is the fix:

I tried creating another couple of accounts (user1 and user2), opening user1 only in Ubuntu and user2 in Kubuntu and then Ubuntu. I then compared all configuration files with the command 'diff -r /home/user1/.[a-z]* /home/user2/.[a-z]* > /tmp/diffs.txt. THere were a lot of innocent differences but I could not find the "smoking gun".

So I logged back into my account, made a new directory dotfilies.bad and moved all of my dotfiles there with cp ~/.[a-z]* ~/dotfiles.bad. Then I copied the good dotfiles from user1 with 'sudo cp /home/user1/.[a-z]* ~' and then 'chown -R myaccountname ~/.[a-z]*. 

After logging out and logging back in the fonts were fixed but the desktop was like user1 and all of my prefs and other information was missing. Now was the time to start moving files back from dotfiles.bad. 

First remove the current file or directory and then move the originals back, for example, rm -rf ~/.mozilla and then mv dotfiles.bad/.mozilla ~.

The important ones that I moved back successfully were:
.mozilla
.evolution
.gconf
.ssh
and all of my special app specific ones like .subversion, etc.
I did >not< copy .kde or anything that had "font" in the name. 

After a logout and login everything was good.
Lots of work that could have been much easier if I had just found the single offending dotfile that had screwed up firefox and replaced only it. Ah, well, two hours wasted but at least everything is back to normal.

Funny. I didn't have the problem in some previous releases like 8.04LTS. But with this and any future releases I sure won't log into the KDE desktop again in my primary account. If I'm really curious about using KDE again then I'll make another account for a KDE desktop only. Looks like the two don't fully mix -- but then they weren't really designed to. Each has its own benefits and its own advocates. You can use them both on the same system, just not in the same account. You can also use some KDE apps on a Gnome desktop without problem. If you don't need the KDE desktop but do want some of the apps just install those apps and not the full KDE package. That is the safest route.

As a general rule if you do something that really seems to screw up the appearance of your desktop or an app try logging out and then logging in to another user account. If you don't see the problem there then the problem is in your home directory and probably in the dotfies. 

Good luck.

---

### Post by nrb on 2010-05-12
This was a repost in error. Looks like my preview turned into a post...

---

### Post by nrb on 2010-05-12
After all of the work that I talked about above I researched a bit further and found this link:
[http://www.kilobitspersecond.com/2009/04/17/ubuntu-font-hinting-you-a-cautionary-tale/](http://www.kilobitspersecond.com/2009/04/17/ubuntu-font-hinting-you-a-cautionary-tale/)

What was the real answer to the firefox problem? Just delete the ~/.fonts.conf file! That does it.

Lots easier than my previous  suggestions.:)

---

### Post by canario on 2011-05-24
> **nrb said:**
> After all of the work that I talked about above I researched a bit further and found this link:
[http://www.kilobitspersecond.com/2009/04/17/ubuntu-font-hinting-you-a-cautionary-tale/](http://www.kilobitspersecond.com/2009/04/17/ubuntu-font-hinting-you-a-cautionary-tale/)

What was the real answer to the firefox problem? Just delete the ~/.fonts.conf file! That does it.

Lots easier than my previous  suggestions.:)


Did the trick for me!! :D thx

---

