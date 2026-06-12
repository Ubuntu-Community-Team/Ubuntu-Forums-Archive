---
title: "Transfering Files/Settings Into Thunderbird or Evolution - From TB XP Files"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by powerfade1 on 2009-08-20
[B]ALL PROBLEMS SOLVED NOW.  THANKS EVERYONE!

[/B]
Yes, another Thunderbird/Evolution question, but I think this one is different.

I've wiped my hard drive installed 9.04 64 bit and will be virtual boxing XP for certain programs.  I backed up all files from XP on an external drive.

I found my Thunderbird (XP) file folder and copied that to my Ubuntu desktop.  I can't figure out how to copy or import them into Linux Thunderbird, but I can do one file at a time with the Evolution import tool.

So, what are my options?  The easier the better, but if I have to do it one file at a time, I'll do that.

Thanks for the help!

---

### Post by philinux on 2009-08-20
I think I remember doing this way back. I just went into the .thunderbird profile folder on ubuntu deleted anything there and dropped in my windows TB profile.

Someone else may clarify the method.

[edit] [http://users.telenet.be/mydotcom/howto/linux/migration01.htm](http://users.telenet.be/mydotcom/howto/linux/migration01.htm)
scroll down to the TB bit.

---

### Post by LewRockwell on 2009-08-20
wow, that has been a few moons ago

we used the export and then import function, repectively

unless we're mistaken and we didn't...hmmm....

.

---

### Post by Moop on 2009-08-20
> **philinux said:**
> I think I remember doing this way back. I just went into the .thunderbird profile folder on ubuntu deleted anything there and dropped in my windows TB profile.

Someone else may clarify the method.

[edit] [http://users.telenet.be/mydotcom/howto/linux/migration01.htm](http://users.telenet.be/mydotcom/howto/linux/migration01.htm)
scroll down to the TB bit.

That's what always works for me. Your Ubuntu Thunderbird profile is in home. Click on Places-Home, then click on view and enable viewing of hidden folders. Open up the .mozilla-thunderbird folder, delete everything and replace it with your contents from the XP profile.

---

### Post by cariboo on 2009-08-20
What I find even easier is just drop the whole XXXXXX-default directory in ~/.mozilla-thunderbird and edit profile.ini to point to the new default directory.

---

### Post by powerfade1 on 2009-08-20
> **philinux said:**
> I think I remember doing this way back. I just went into the .thunderbird profile folder on ubuntu deleted anything there and dropped in my windows TB profile.

Someone else may clarify the method.

[edit] [http://users.telenet.be/mydotcom/howto/linux/migration01.htm](http://users.telenet.be/mydotcom/howto/linux/migration01.htm)
scroll down to the TB bit.

[B]EMERGENCY HELP PLEASE!

I purged/deleted Evolution, reinstalled ekiga and rebooted.  Now I only have access to files!  My desktop is now lacking the top and bottom toolbars.  I happened to have something on the desktop that opened Firefox so I could write this.  How do I get Ubuntu back to normal??

Please help, asap!  :(:confused:[/B]

---

### Post by oldfred on 2009-08-20
I think evolution is part of gnome so by uninstalling it you uninstalled too much.
try reinstalling the desktop - should only reinstall missing bits:
control alt f2      to get to command line
sudo apt-get update && sudo apt-get install ubuntu-desktop
sudo aptitude install ubuntu-desktop

---

### Post by powerfade1 on 2009-08-20
> **oldfred said:**
> I think evolution is part of gnome so by uninstalling it you uninstalled too much.
try reinstalling the desktop - should only reinstall missing bits:
control alt f2      to get to command line
sudo apt-get update && sudo apt-get install ubuntu-desktop
sudo aptitude install ubuntu-desktop

Thank you, oldfred, that worked.  But now Thunderbird isn't working.  Error message:

Thunderbird is already running...you must close TB or restart your system.  I restarted and it didn't work, and I can't find a process that looks like it's from TB.  Can you tell me which one it might be?

---

### Post by oldfred on 2009-08-20
Thunderbird writes a file to say it is open. you can delete that. The file is .parentlock in your profile.

The profile is %/.mozilla-thunderbird/ -randomdigits-  .default.

Use file brower to open your home folder and under view show hidden files. Then you should be able to see .mozilla-thunderbird and your profile directory which is a bunch of digits.

---

### Post by powerfade1 on 2009-08-20
> **oldfred said:**
> Thunderbird writes a file to say it is open. you can delete that. The file is .parentlock in your profile.

The profile is %/.mozilla-thunderbird/ -randomdigits-  .default.

Use file brower to open your home folder and under view show hidden files. Then you should be able to see .mozilla-thunderbird and your profile directory which is a bunch of digits.

I deleted .parentlock, rebooted, and the same error appears.  Could it be something else?

---

### Post by oldfred on 2009-08-20
.parentlock I thought was the main issue. They also discuss a lock file that I do not see on my system but I am using Ubuntu but my profile is in a FAT32 partition to share with windows.

Mozilla has additional possible reasons:
[http://kb.mozillazine.org/Profile_in_use](http://kb.mozillazine.org/Profile_in_use)

---

### Post by powerfade1 on 2009-08-21
> **Moop said:**
> That's what always works for me. Your Ubuntu Thunderbird profile is in home. Click on Places-Home, then click on view and enable viewing of hidden folders. Open up the .mozilla-thunderbird folder, delete everything and replace it with your contents from the XP profile.

Ok, got the switch working, and realized I confused a '1' with an 'l' when typing the new default into the .ini file.  One more question:[B]

1. How do I move my new ISP settings and identities to the old XP settings folder?  Which file(s) is it in?

[/B]Thanks everyone!

---

### Post by oldfred on 2009-08-21
I always copy the entire profile. If you do not have a lot of saved emails it copies easier. I usually back it up, houseclean old emails and then copy. 
I actually have both thunderbird and firefox in a shared partition for use by XP and Ubuntu, but copy the profile to a portable when ever we travel and copy it back when we return.

---

### Post by powerfade1 on 2009-08-21
> **oldfred said:**
> I always copy the entire profile. If you do not have a lot of saved emails it copies easier. I usually back it up, houseclean old emails and then copy. 
I actually have both thunderbird and firefox in a shared partition for use by XP and Ubuntu, but copy the profile to a portable when ever we travel and copy it back when we return.

Interesting.  I did the entire .default file, but would still like some recent emails from the old mail file.  Settings I simply entered anew.  I wonder if there is a way to transfer individual emails from one to the other.

---

### Post by oldfred on 2009-08-21
Using the profile manager you can load different profiles. I have not copied emails from one to another. 
We started the portable's thunderbird when we were using the main house computer and a few emails downloaded into the portable. We emailed them back to ourselves and quickly closed before it could download them, and they came back on the main computer.

---

### Post by powerfade1 on 2009-08-21
I figured it out.  I've been changing the names of the folders in the old XP mail folder by adding a '1' before the .net then copied them into the new mail folder.  Most emails are there now but I've got some rearranging to do.

Thanks everyone for your help!

---

