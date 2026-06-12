---
title: "checkgmai hell!!"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by mbele3000 on 2009-03-05
I'm running 8.10 & have searched around and well I cant seem to fix checkgmail for all I've tried. Here is the error message I keep getting:

 CheckGmail uses Gtk2::Sexy for clickable URLs in mail messages
Please download and install from CPAN ([http://search.cpan.org](http://search.cpan.org)) if you want to use this feature ...

File does not exist:  at /usr/bin/checkgmail line 1353
Perl exited with active threads:
	1 running and unjoined
	0 finished and unjoined
	0 running and detached

 I went to the tombuntu site and the forums here went and uninstalled in treminal and with synaptic as well and nothing seems to work. I know with Ubuntu it's always something simple USUALLY!

---

### Post by billgoldberg on 2009-03-05
> **mbele3000 said:**
> I'm running 8.10 & have searched around and well I cant seem to fix checkgmail for all I've tried. Here is the error message I keep getting:

 CheckGmail uses Gtk2::Sexy for clickable URLs in mail messages
Please download and install from CPAN ([http://search.cpan.org](http://search.cpan.org)) if you want to use this feature ...

File does not exist:  at /usr/bin/checkgmail line 1353
Perl exited with active threads:
	1 running and unjoined
	0 finished and unjoined
	0 running and detached

 I went to the tombuntu site and the forums here went and uninstalled in treminal and with synaptic as well and nothing seems to work. I know with Ubuntu it's always something simple USUALLY!

Try to contact the guy who makes the app. 

An email address should be the official site.

--

Are you using the version from the Ubuntu repositories (if there is one) or the latest one?

If you are using the one from the repositories, try installing the latest one from the official website.

--

If you don't get it to work, you can get notified when you have a new gmail email using conky.

Google "conky gmail script".

---

### Post by mbele3000 on 2009-03-05
ok well I reinstalled GTK sexy (and it so is). Any way Im getting this error message

mycomp@me-desktop:~$ checkgmail

File does not exist:  at /usr/bin/checkgmail line 1353
Perl exited with active threads:
	1 running and unjoined
	0 finished and unjoined
	0 running and detached

 I forgot to say that this program was working and well I guess has been the 1st to "break" I guess. Which is a 1st for me with Ubuntu!  
 I went to this site 
  [http://marius.scurtescu.com/2007/06/25/installing_checkgmail_on_ubuntu](http://marius.scurtescu.com/2007/06/25/installing_checkgmail_on_ubuntu)
 Any suggestions?  BTW this is the site that distributes the program .

---

### Post by magic_balu on 2009-03-05
Had the same error. The problem was that the /.checkgmail/prefs.xml was completely empty. I renamed it and restarted checkgmail. At startup i had to reconfigure my preferences and the prefs.xml was regenerated.

---

### Post by kanikilu on 2009-03-05
This isn't really related, but I stopped using checkgmail in preference to mail-notification (in the repos).

---

### Post by mbele3000 on 2009-03-05
OK well it works when I run from terminal I get that same error message. BUT when I run it from Root it works as soon as I close the root window the program stops! So obviously it does work but only from root how do I correct this so that it works from the applications menu, instead of having to run it at root? I know that I'm more than likely gonna have to edit some scripts just not sure how. Any help is appreciated!

---

