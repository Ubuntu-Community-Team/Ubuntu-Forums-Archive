---
title: "I messed up - need help importing into Thunderbird"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by anewguy on 2009-04-19
Okay, I did something REALLY stupid.  I sold the computer I had been using, which was dual-boot Windows XP and Ubuntu.  In my haste to get things off the old machine before reloading Windows to it, I only saved my email folders and my address book (it's wab).  Now, after I no longer have access to Windows, I find that I was to have exported the address book as cvf, not kept as wab, since Thunderbird won't import a wab that I have found.

So, to help an idiot out, can someone tell me if there is a way and point me to some sort of how-to's for the following:

- with only Linux being available, convert wab to cvf so I can import it into Thunderbird

- with only Linux being available, some way to get my email folders (Outlook Express) imported into Thunderbird?

Sorry for being such an idiot - even I know better and know I should have looked first - I just assumed it would work like an idiot in my haste.

Thanks for any help!

dave :)

---

### Post by cybergalvez on 2009-04-19
you might have to find a friend with a windows computer to help you out, or borrow a friends XP disk, and intall it uner virtual box, do your export and then dump the windows install

---

### Post by -kg- on 2009-04-20
While apparently there is nothing available in the Repos, I did find a few converters through Google, including this one:

[http://unix.freshmeat.net/projects/libwab]("http://unix.freshmeat.net/projects/libwab")

Unfortunately, it comes in tar.gz form (no .deb that I could find), so you'll have to take extra steps to install it, but you might google something like "convert wab to ldif linux" (without the quotes) and see what else you can find.

You might find something that has been put in .deb format, possibly with a Repo and Public Key so that you can download it, install it, and check for dependencies and conflicts through Synaptic or Aptitude.

As far as your email folders, I can only suggest you try to import them through Thunderbird itself.  If it doesn't give you the option, I would suggest going over to the Mozilla help forum and seeing if you can find out there.

I've been very lucky, since in my early internet days I started out with Netscape (which preceded Mozilla Firefox and Thunderbird), and when I switched from Netscape, all my files, ABs, and all exported and imported without a hitch.

---

### Post by anewguy on 2009-04-20
Thanks for the help  - I'll check all those out, and possibly see if I can install Outlook in wine as that would help.

As far as Netscape, yeah I go back before them even.  I wish I had stuck with their products, but I remember 1 release that I just had a heck of a time with - I can't remember the number, but I think it was when they switched or whatever to gecko or something - maybe back about communicator version 6 or something.  It's been so long I really just don't remember now.

It would have made things a lot easier for me now that I've done something stupid!!  :)

Thanks again! 

Dave :)

---

### Post by anewguy on 2009-04-20
The libwab program worked great - did exacty what I needed!

Thanks!

Dave :)

---

### Post by -kg- on 2009-04-21
Glad I could help.

):P

---

