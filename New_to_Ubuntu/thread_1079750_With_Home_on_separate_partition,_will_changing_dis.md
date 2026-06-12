---
title: "With Home on separate partition, will changing distros keep personal settings?"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by cyan on 2009-02-24
I have my home directory on a separate partition. If I choose to change to a new distro (say, from Easy Peasy to vanilla Ubuntu or EEEbuntu), will all my settings transfer? Or will they only transfer if I reinstall the same flavor I was using before?

Presumably, I will still have access to my documents, photos, etc. but I wonder how the settings for Firefox and Open Office, for example, work when you reinstall a new distro.

Thanks for the help!

---

### Post by snova on 2009-02-24
> **cyan said:**
> I have my home directory on a separate partition. If I choose to change to a new distro (say, from Easy Peasy to vanilla Ubuntu or EEEbuntu), will all my settings transfer?

Yes. They're all stored in your home directory.

I imagine if the distro has different versions of some software, a few settings could go awry... but it's only a thought, not very likely.

---

### Post by cyan on 2009-02-24
That makes sense. Thank you for the help!

---

### Post by lukjad on 2009-02-24
cyan, I have kept the same /home folder for quite a few upgrades now. While it's true that it usually works, there are a few things you need to remember. If you don't start off fresh, then you miss out on any new changes that were made during the last upgrade. Also, I've personally experianced problems in some programs when I upgraded and the versions were not the same. Also, if you have any shortcuts or quick launchers, they may be broken. 

My rule of thumb is this: Keep everything, but only put back what you need, one folder at a time. That way, if and when problems arise, you will be able to know right away what caused them.

---

### Post by cyan on 2009-02-24
Excellent advice, thank you. Does the rule of only adding back what you need also apply to settings? And if so, how does one "add back" only some settings and not others?

---

### Post by ptn107 on 2009-02-24
It is not advised to be using the same home folders between different distributions.  GNOME in particular complains when two different versions of itself use ~/.gconf, ~/.gconf.d, and ~/.gnome2.  (ex. Debian or Fedora and Ubuntu)

---

### Post by cyan on 2009-02-24
PTS107, I see your point. But just to be clear, are you talking about two separate installed distros pointing to the same /Home?

The case I am looking at is where a new install would wipe out the old one. So I would only ever have one distro pointing to one /Home partition.

---

### Post by lukjad on 2009-02-25
> **cyan said:**
> Excellent advice, thank you. Does the rule of only adding back what you need also apply to settings? And if so, how does one "add back" only some settings and not others?

How you "add back" the settings is like so. Assuming your username is *cyan*, you would copy all the hidden files in your /home/cyan/ folder. So things like **.wesnoth** and **.openoffice.org2** are where the settings are held. (To view hidden files, navigate to your /home/cyan/ folder in Nautilus and press Ctrl+H.) So, when you install the new distro, you will then paste them back into the new /home/cyan/ folder. Is is suggested that your new username be the same as the last one to minimize the possible problems. It also should be noted that there most likely will be some problems by using the same setting and hidden files. If you were to keep the same home folder with all the settings, there would be some pretty big problems. So, just test them out, one at a time. Hope this helps. :D

---

### Post by llamabr on 2009-02-25
I've had the same /home directory for 10 years, through 5 different distributions, and hundreds of installs.

You'll very often want to go through and rm your dot files, as new features will make settings in them obsolete.  And between distros, things will break .gnome settings.

But otherwise, all of your files and things will be just fine in there.

Do a backup before you proceed, of anything you can't afford to lose.

---

### Post by handy on 2009-02-25
I don't know, but I surely would be looking at this comprehensive how-to on the subject, an effort to educate myself as to how things work in the /home arena:

*_[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)_*

---

### Post by cyan on 2009-02-25
Thanks, everyone! Good advice and suggestions. A couple of questions arise from the info I'm gaining.

First, when I copy the /Home directory (as I do using sbackup to backup my files to an FTP site), do the hidden files in that directory get copied as well? Or do I need to tell sbackup to specifically include hidden files?

Second, I want to make sure I understand the advice about bringing in /Home files as needed after a new install. Are some of you saying that I shouldn't just install a new distro and point to the old /Home on a separate partition? That instead, I should do a completely new install with a brand new /Home directory and then copy my old /Home files as needed?

If I am understanding this correctly, keeping the old /Home and just pointing to it from the new install is doable it just might require more tweaking (or cause more hiccups) than if I simply copy the files I need back to a fresh /Home.

Am I understanding that right?

Thanks again for all the help and advice!

---

