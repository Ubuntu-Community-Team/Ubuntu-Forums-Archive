---
title: "Which way to install Skype?"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by bw44 on 2009-02-16
I'd like to install the "right" version of Skype from the "right" source.  I've checked other threads on this forum and am still not clear which is the best approach.  I'm running Ubuntu 8.04. 

There seem to be three choices:


1. Download the version in deb package format for Ubuntu 8.04 from the Skype site (skype-debian_2.0.0.72-1_i386.deb). (size 14MB)

2. Download the Medibuntu version in deb package format (skype_2.0.0.72-0medibuntu1_i386.deb) (size 12MB)

3. Add the Skype repository (deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free) and use apt or Synaptic package manager to install it.


Maybe 2 and 3 above boil down to the same thing, but I'm not sure, since I have little experience with packages that don't come with Ubuntu out of the box.

Can anyone advise me on the preferred approach (for Skype, but also in general, where a choice like this is available)?

Thanks

bw44

---

### Post by swoody on 2009-02-16
Typically, it is better to install things that exist in the repositories, so option #2 or #3 would probably be your best bets. They are much easier to stay on top of updates in this way as well. I used the Medibuntu Repo to install Skype, which has worked beautifully so far. It's also useful to have those repos for all the great multimedia plugins that medibuntu offers:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

and here's how to add the Medibuntu Repositories. You can then use Synaptic/apt-get/whatever to install Skype:

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

---

### Post by T2manner on 2009-02-16
[This]("http://www.skype.com/go/getskype-linux-ubuntu") should help

---

### Post by linux_tech on 2009-02-16
2 Skype install docs that may help-
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype) 
[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Skype](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Skype)

---

### Post by Orion8 on 2009-02-16
I've installed at different times both the version in the repositories and the package from Skype's website.  There was no discernible difference that I could find, and the repository is much easier to install / uninstall from.

---

### Post by bw44 on 2009-02-16
> **woody86 said:**
> Typically, it is better to install things that exist in the repositories, so option #2 or #3 would probably be your best bets. They are much easier to stay on top of updates in this way as well. I used the Medibuntu Repo to install Skype, which has worked beautifully so far. It's also useful to have those repos for all the great multimedia plugins that medibuntu offers:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

and here's how to add the Medibuntu Repositories. You can then use Synaptic/apt-get/whatever to install Skype:

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)


Thanks very much for the benefit of your firsthand experience!  I'll go with adding the repository and installing that  way (my option #3).

I also checked ubuntu-freak's great multi-media how-to  that you give the url for. (I've been using it since day one! But he doesn't mention Skype in the how-to itself.)

Thanks to the other posters who have also responded already!

bw44

---

### Post by bw44 on 2009-02-16
> **Orion8 said:**
> I've installed at different times both the version in the repositories and the package from Skype's website.  There was no discernible difference that I could find, and the repository is much easier to install / uninstall from.

Thanks for confirming that it's easier to install/uninstall from the repo.  

Will this also mean that if Skype brings out a new version it will probably  find it's way into the repo and I'll get a message a new version is available?  This seems to work for Firefox and Thunderbird, but theyy're in a different repo.

Also, can you, or anyone,  tell me how to mark a thread "SOLVED"?  I thought you could do it from the dropdown menu "Thread Tools" but it doesn't seem to be there any more.

Thnx again.

---

### Post by swoody on 2009-02-17
> **bw44 said:**
> Thanks very much for the benefit of your firsthand experience!  I'll go with adding the repository and installing that  way (my option #3).

I also checked ubuntu-freak's great multi-media how-to  that you give the url for. (I've been using it since day one! But he doesn't mention Skype in the how-to itself.)

It's no problem :) I just mentioned that it might be easier to just add the Medibuntu Repository, as Skype is on that repo as well. So if you add that repo, you can install Skype and all the great multimedia stuff available through Medibuntu. Rather than having to add a separate repo for Skype alone.

---

### Post by swoody on 2009-02-17
> **bw44 said:**
> Also, can you, or anyone,  tell me how to mark a thread "SOLVED"?  I thought you could do it from the dropdown menu "Thread Tools" but it doesn't seem to be there any more.

Some of the functions of the website are disabled temporarily. There was some kind of problems with the Ubuntu servers, and they've removed the 'Thanks' and the 'Solved' abilities for a little while.

[http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714)

---

### Post by bw44 on 2009-02-17
> **woody86 said:**
> It's no problem :) I just mentioned that it might be easier to just add the Medibuntu Repository, as Skype is on that repo as well. So if you add that repo, you can install Skype and all the great multimedia stuff available through Medibuntu. Rather than having to add a separate repo for Skype alone.

Well, duh, I already had the  Medibunu repo included ([http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free) under "Third-Party Software" in Synaptic, but thought I had to include *another* repo ([http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free) to get Skype.  So I can remove the Skype-specific one and still pick it up from Medibuntu, right?

Thanks for this, and also for clarifying in your next post about the "SOLVED" and "Thanks" functions being disabled.  I didn't visit the forums for a while, and when I came back a number of things had changed.  I thought you used to be able to search on multiple keywords and get only posts that had all the words, but if there's a way to do that I haven't been able to figure it out!

bw44

---

### Post by swoody on 2009-02-17
> **bw44 said:**
> Well, duh, I already had the  Medibunu repo included ([http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free) under "Third-Party Software" in Synaptic, but thought I had to include *another* repo ([http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free) to get Skype.  So I can remove the Skype-specific one and still pick it up from Medibuntu, right?

Thanks for this, and also for clarifying in your next post about the "SOLVED" and "Thanks" functions being disabled.  I didn't visit the forums for a while, and when I came back a number of things had changed.  I thought you used to be able to search on multiple keywords and get only posts that had all the words, but if there's a way to do that I haven't been able to figure it out!

Yup, with the Medibuntu Repo enabled, you should be able to install Skype already, and you can remove the Skype Repo since it's not needed.

You can type in search queries in this manner and have it find posts with multiple keywords:
> ubuntu + skype
Just put in a + sign between the terms you want to search for. Let me know if it works out for you :)

---

### Post by bw44 on 2009-02-17
> **woody86 said:**
> Yup, with the Medibuntu Repo enabled, you should be able to install Skype already, and you can remove the Skype Repo since it's not needed.

You can type in search queries in this manner and have it find posts with multiple keywords:

Just put in a + sign between the terms you want to search for. Let me know if it works out for you :)

Again, many thanks!  I had tried putting in ```
skype + install
``` but that found posts with "skype" OR "install".  It didn't occur to me that ```
skype+install
``` would change the search to AND. (What a difference a space makes!)

As for the Skype repo saga:  with the Skype repo installed and checked in the Synpatic third-party repo list, Synaptic showed that to be the origin of Skype.  I unchecked the Skype repo and re-loaded the repos and it showed the origin of Skype to be "Local/non-free".  I was going to mark it for re-installation and see if it would pick Skype up from the Medibuntu repo, but then I got cold feet.  Skype is all installed, configured, and working fine, so I'm reluctant to experiment for the sake of proving a point.  Maybe someone braver would like to try . . .

Cheers,

bw44

---

### Post by swoody on 2009-02-17
> **bw44 said:**
> As for the Skype repo saga:  with the Skype repo installed and checked in the Synpatic third-party repo list, Synaptic showed that to be the origin of Skype.  I unchecked the Skype repo and re-loaded the repos and it showed the origin of Skype to be "Local/non-free".  I was going to mark it for re-installation and see if it would pick Skype up from the Medibuntu repo, but then I got cold feet.  Skype is all installed, configured, and working fine, so I'm reluctant to experiment for the sake of proving a point.  Maybe someone braver would like to try 

You should be able to reinstall it, and it should pick it up from the Medibuntu Repo. The config files for programs will remain on your comp, so anything you setup or changed should remain the same as well. So there shouldn't be any worries about reinstalling it, you shouldn't notice any difference at all :)

---

### Post by Art3mis on 2009-02-17
I would just suggest you, use Wine to install skype

---

### Post by bw44 on 2009-02-17
> **woody86 said:**
> You should be able to reinstall it, and it should pick it up from the Medibuntu Repo. The config files for programs will remain on your comp, so anything you setup or changed should remain the same as well. So there shouldn't be any worries about reinstalling it, you shouldn't notice any difference at all :)

Yep, it worked as you said.  Two things for others to note, however:

1. After I removed  the Skype repo, marking Skype for re-installation, and applying it I got an error message (see attached image); so I had to select "Mark for Removal", apply it and then select Skype again for a fresh installation.

2. The version of Skype that was installed from their repo was 2.0.0.72-1, and the one from Medibuntu was 2.0.0.72-0, so I guess there has been an update that hasn't been vetted by Medibuntu yet.  But the earlier version seems to be working fine, and as you said, all the settings were OK.

Thanks for your help! :popcorn:

bw44

---

### Post by bw44 on 2009-02-17
> **Art3mis said:**
> I would just suggest you, use Wine to install skype

Well, if you noticed my previous post, the Linux version of Skype seems to be working fine for me.

Given I have a pretty slow old laptop and no experience with Wine, what would the advantage be of running the Windows version of Skype?  I have a dual-boot system with XP installed, and the Skype version 4 (for Windows) interface is quite different.  If I liked it better (which I don't) that might be a reason to run Skype with Wine I guess.

Thanks for your suggestion, even though I probably won't follow it. :)

bw44

---

### Post by SunnyRabbiera on 2009-02-17
There is no real advantage other then just giving skype a shot under wine, but skypes linux client I heard works quite well.

---

### Post by swoody on 2009-02-18
> **SunnyRabbiera said:**
> There is no real advantage other then just giving skype a shot under wine, but skypes linux client I heard works quite well.

Yup, Skype is one of the only 3 programs I have to have on Ubuntu, and I've NEVER had a problem or glitch at all! It's very nice :D

---

### Post by swoody on 2009-02-18
> **bw44 said:**
> Well, if you noticed my previous post, the Linux version of Skype seems to be working fine for me.

Given I have a pretty slow old laptop and no experience with Wine, what would the advantage be of running the Windows version of Skype?  I have a dual-boot system with XP installed, and the Skype version 4 (for Windows) interface is quite different.  If I liked it better (which I don't) that might be a reason to run Skype with Wine I guess.

I'm glad to hear everything's working well for you. Yeah, I wouldn't recommend using Wine to run anything unless it's something you absolutely NEED and can't find a replacement for in Ubuntu. I've not had a good record with running programs in Wine, and there seems to be much more overhead and problems associated with it.

---

