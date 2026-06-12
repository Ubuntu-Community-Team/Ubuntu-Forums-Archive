---
title: "Removing Program Leftovers"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by Vimmander on 2011-01-23
Hi there!  I was wondering....I tried out mutt (had to install  fetchmail, procmail, and msmtp), and I found that I wasn't really ready  for that kind of email management (I lost all my labels and stuff from  gmail too).  So, I went ahead and removed those programs via Synamptic,  then ran
```
sudo apt-get autoremove
```to get rid of any leftover junk.   Unfortunately, when testing out the "find" command, I found traces of  these programs.  The output of "find" for each one is below:

For mutt:
```
/etc/bash_completion.d/mutt
/usr/share/nano/mutt.nanorc
/usr/share/locale-langpack/en_GB/LC_MESSAGES/mutt.mo
/usr/share/dictionaries-common/mutt-ispell-init
/usr/share/vim/vim72/syntax/muttrc.vim
/usr/share/vim/vim72/ftplugin/muttrc.vim
/usr/share/app-install/desktop/mutter.desktop
/var/cache/apt/archives/mutt_1.5.20-7ubuntu1_i386.deb
```For fetchmail:
```
/usr/share/locale-langpack/en_GB/LC_MESSAGES/fetchmail.mo
/usr/share/vim/vim72/syntax/fetchmail.vim
/usr/share/vim/vim72/ftplugin/fetchmail.vim
/var/cache/apt/archives/fetchmail_6.3.9~rc2-4ubuntu5_i386.deb
/var/lib/update-rc.d/fetchmail
```For procmail:
```
/etc/exim4/conf.d/transport/30_exim4-config_procmail_pipe
/etc/exim4/conf.d/router/700_exim4-config_procmail
/usr/share/vim/vim72/syntax/procmail.vim
/usr/share/vim/vim72/ftplugin/procmail.vim
/usr/share/doc/bogofilter-common/examples/procmailrc.example
/var/cache/apt/archives/procmail_3.22-18ubuntu1_i386.deb
```For msmtp:
```
/var/cache/apt/archives/msmtp_1.4.19-1_i386.deb
```I've always depended on whatever OS I'm using to remove files like this  (I assume they're config fies?), but I guess these programs are an  exception to the rule.  Any suggestions on removing these without  obliterating my system?

---

### Post by JKyleOKC on 2011-01-23
Open Synaptic again, and in the lower left portion of the window click "Status" which will change the list of options in the upper left area. In that options area, if there's a "residual" entry as the last choice, click it. This will list all of the left-over configuration files that the system knows about. For each of them, click the checkbox and select "Mark for complete removal." When you have them all marked for complete removal, click "Apply" and you should be on the way to your desired result.

When you just "Mark for removal" in Synaptic, the system deliberately leaves the configuration files for the package in place so that you won't have to reconfigure it if you re-install the package. "Mark for complete removal" takes out the configuration files also, and the ones you've listed definitely appear to be such.

Hope this helps!

EDIT: You can run "sudo apt-get autoclean" to get rid of any leftovers in the apt-cache area, if Synaptic doesn't do that for you.

---

### Post by Vimmander on 2011-01-23
Synaptic did remove a bunch of residual packages, and autoclean removed two things that I didn't even know about
```
Del libfuse2 2.8.1-1.1ubuntu2.1 [141kB]
Del fuse-utils 2.8.1-1.1ubuntu2.1 [21.6kB]
```Other than that, those files are still there.  My main concern is my gmail password.  I had to use it in the muttrc and fetchmailrc files in order to use POP3 forwarding from my gmail account, and I don't know if it is also in the files that I can't seem to get rid of.  If it's not, then they're not really a big deal -- When 12.04 comes out, I'll just transfer my documents over and be done with those configs for good (fresh installs are always easier than upgrading, IMO)

---

### Post by SavageWolf on 2011-01-23
If someone has access to those files, your email is the least of your worries.

---

### Post by Elfy on 2011-01-23
If you're that worried - delete them. 

Either from a terminal or a root nautilus.

---

### Post by Vimmander on 2011-01-23
> **forestpiskie said:**
> If you're that worried - delete them.

That's what I wanted to do originally, but I always heard that deleting certain things manually was a bad idea.  Was I wrong?

Edit:  I went ahead and shredded the files after looking at a few of them.  I think they were just for those programs.

---

### Post by JKyleOKC on 2011-01-23
> **GrogTheDreamer said:**
> That's what I wanted to do originally, but I always heard that deleting certain things manually was a bad idea.  Was I wrong?It's a bad idea if you don't know what the files are, but in this case you had a pretty good idea that they were associated with packages that you had removed.

Just FYI, files with names that end in "rc" are almost always configuration files for the program of similar name, such as "muttrc" being a configuration file for "mutt." In most cases, such files are plain text files that you can view with any editor, to verify what they are, before deleting.

---

### Post by Vimmander on 2011-01-23
Well, after I did delete them, I ran rkhunter as I usually do once a month, and I got complaints about sshd and jetty not being in /etc/passwd, and about jetty not being in /etc/group.  I don't know how I rectified this (other than clearing out my /.ssh/authorized_users file on the servers I connect to for programming assignments), but those errors are gone.  The entries for those two programs, however, have not returned.  Where they important entries?  If so, can I get them back, or do I need to reinstall Ubuntu?  All I really wanted to do what restore my system to what it was like before I tried mutt, not trash the crap out of it :/

---

### Post by JKyleOKC on 2011-01-23
If they are not in /etc/passwd then they are user names that no longer exist on the system, and the one not in /etc/group is no longer a valid group name. Beyond that I have no idea what may have happened. I don't use any of the rootkit detectors, since by definition a really good rootkit cannot be detected by any of them. Instead, I rely on keeping my interface to the outside world as secure as possible, and being extremely careful about the web sites and emails that I deal with. And when I suspect I've been invaded (as happened last summer) I make sure I have backups of all my data, then do total reformatting of all hard drives and re-install everything from scratch.

The sshd user name, I believe, is created when you install the ssh server package on your machine. If you can still ssh into it from another box, things ought to be okay. Similarly for putty; if it still works, don't worry about it.

---

