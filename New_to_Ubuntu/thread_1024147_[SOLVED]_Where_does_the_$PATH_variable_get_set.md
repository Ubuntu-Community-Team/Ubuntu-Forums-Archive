---
title: "[SOLVED] Where does the $PATH variable get set?"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by baruch60610 on 2008-12-28
I made the mistake of installing Perl through the Perl Website instead of using synaptic.  The installation changed my perl path from /usr/bin/perl to /usr/local/bin/perl.  Now I've removed the unsanctioned Perl and want to use only the correct one, located at /usr/bin/perl.

So, where does the $PATH variable get set?  When I try to run Perl now, I get a message telling me that /usr/local/bin/perl doesn't exist, which is true.  So - how can I make my system revert to using /usr/bin/perl?  I know I can do an alias or something, but where does this naming of programs take place?

FWIW, I'm running Hardy with KDE, though I assume this wouldn't make a difference.

---

### Post by nhasian on 2008-12-28
look in /home/username/.bash_profile

---

### Post by baruch60610 on 2008-12-28
Hi, nhasian:

Thanks for the idea.  I don't have that file.  I'm not sure if I should just create it or what.  I'd actually prefer to just get to the place where that variable gets set, and change it there.

But I appreciate you trying to help.

---

### Post by nhasian on 2008-12-28
if you dont have ~/.bash_profile i'll bet you have  ~/.profile or ~/.bash_login :)

---

### Post by igknighted on 2008-12-28
Ubuntu changes it in /etc/environment

---

### Post by lswb on 2008-12-28
both /usr/bin and /usr/local/bin should already be on your path. Does the error message appear when you try running perl from a menu of some kind or from a perl script with a #!/usr/local/bin/perl first line?

Anyway, the systemwide initial path is set in /etc/environment and your user path can be set in ~/.bashrc but unless you have modified one or both of these I believe your problem lies elsewhere.

---

### Post by igknighted on 2008-12-28
re-reading your first post, I think you want update-alternatives, not $path.  What does the command 'update-alternatives --display perl' say?

---

### Post by baruch60610 on 2008-12-29
@igknighted, you were right about /etc/environment.  That contained the $PATH, except it was missing my /home/username/bin path.  However, that gets added in somewhere else, so it's no problem.

As for 'update-alternatives', it said there are no alternatives for perl.  Not surprising, since I deleted the version I had installed myself.  I had already checked for symbolic links by looking at the /usr/loca/bin/perl file (it was the binary itself, not a symbolic link).  I see that I could have saved myself some work by using 'update-alternatives'.  Maybe next time, if I remember it.

Anyway, for some reason, when I had the 'local' path preceding the 'usr/bin' path, when I invoked perl it gave me problems.

@lswb, you were also right about /etc/environment.  I suspect you're right about the problem lying elsewhere as well.  Swapping the two locations on the $PATH fixed the problem of invoking the wrong perl, but I'm not convinced there isn't some sort of link, file, or reference lurking out there somewhere, waiting to bite me.  My kluges usually come back to haunt me...

Thanks to all who helped me with this.

---

