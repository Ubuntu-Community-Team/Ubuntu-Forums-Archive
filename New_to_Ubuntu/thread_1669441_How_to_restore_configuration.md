---
title: "How to restore configuration?"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by Siramau on 2011-01-17
So, yesterday I went to boot up my computer and it hung at "Checking  battery state...". Unable to fix the problem, and requiring a usable  computer (but unwilling to give up), I installed Ubuntu from the LiveCD  into a new partition, and copied my home folder so I would have my  files. As much as I would rather restore my much-loved system, with all  of it's solved problems and tweaked, homey feel, I would be content to  restore my system config, applications, and app config.

I think for the most part I know how to find application configuration  files, once the applications are installed. So, there are two main  things I need help with:

1. What did I have installed?
I had a fairly large amount of software installed, applications and  more, a reasonable portion of it resulting from hours of troubleshooting  headaches. Is there some file that logs all packages installed? Even all applications? 'Cause there is no way I will remember all of them until I need them.

2. Where are system configuration files?
This is probably my most n00bish question here, but where are the files that contain system configuration information? Prefs like wallpaper, font size, panels, etc?

Thanks for any help!

---

### Post by Calais225 on 2011-01-17
I think this is a great question and would like the answer also.

I did investigate a program called Remastersys which is supposed to provide you with a dvd/cd of your program/settings/configuration in case you need to do what you want to  accomplish.

If you solve your issues, give that a look.

---

### Post by scradock on 2011-01-17
> **Siramau said:**
> So, yesterday I went to boot up my computer and it hung at "Checking  battery state...". Unable to fix the problem, and requiring a usable  computer (but unwilling to give up), I installed Ubuntu from the LiveCD  into a new partition, and copied my home folder so I would have my  files. As much as I would rather restore my much-loved system, with all  of it's solved problems and tweaked, homey feel, I would be content to  restore my system config, applications, and app config.

I think for the most part I know how to find application configuration  files, once the applications are installed. So, there are two main  things I need help with:

1. What did I have installed?
I had a fairly large amount of software installed, applications and  more, a reasonable portion of it resulting from hours of troubleshooting  headaches. Is there some file that logs all packages installed? Even all applications? 'Cause there is no way I will remember all of them until I need them.

2. Where are system configuration files?
This is probably my most n00bish question here, but where are the files that contain system configuration information? Prefs like wallpaper, font size, panels, etc?

Thanks for any help!
Great question! Basically, it depends what OS you were running.

If you were using Ubuntu, or most any other linux distro, anything you can fiddle with should have a hidden file (name starts with a period, such as .mozilla, for Firefox) in your own Home directory. Get access to the partition, from LiveCD or whatever, find the /home/NAME folder and copy ALL its contents. That will give you access to configuration data for a new install, etc.

If you were using any of the various Windows variants, on the other hand, all the config data is in a monstrous construct called the Registry. Different for every incarnation of Windows, very hard to copy or alter EXCEPT through the right Windows OS. In a Mac OS, I have no idea......

We may be able to help if you were using Ubuntu; if not, you should ask in a forum specializing in the OS in question.

---

### Post by Siramau on 2011-01-17
Okay, thanks. I was using Ubuntu, Maverick; I should have specified, sorry. Could you possibly provide more details? How does one show hidden files? Is this for system configuration, or specific applications?

---

### Post by akand074 on 2011-01-17
Your home folder has all your config files for all your applications (they are hidden, just press ctrl + H to make them visible). Copy and paste them all to your new home folder. I would suggest you put /home on a separate partition in the future when installing Ubuntu. That way you can reinstall Ubuntu many times without touching your data/config files.

---

### Post by Siramau on 2011-01-17
Great, thanks! That solves my application configuration problems. Now I just need to know if there's any log of installed software.

---

### Post by Siramau on 2011-01-17
Actually, I think I figured this out. A ctrl-f for "install" in the dpkg logs serves my purpose, although it's *annoying*. Anyone know of a better way?

Update:
Yeah, the dpkg logs do the job. If anyone ever has the same question, what I did was navigate to /var/log/ ,open all of my dpkg logs, including the archived ones, ctrl-f for "install", and skim through them, writing down any applications. Hopefully you can find a better way though, because this is long and tedious, and I only have logs from mid-November 'til now.

---

### Post by akand074 on 2011-01-18
> **Siramau said:**
> Actually, I think I figured this out. A ctrl-f for "install" in the dpkg logs serves my purpose, although it's *annoying*. Anyone know of a better way?

Update:
Yeah, the dpkg logs do the job. If anyone ever has the same question, what I did was navigate to /var/log/ ,open all of my dpkg logs, including the archived ones, ctrl-f for "install", and skim through them, writing down any applications. Hopefully you can find a better way though, because this is long and tedious, and I only have logs from mid-November 'til now.

If you ever plan on doing a clean install intentionally. You can also do [this]("http://ubuntuforums.org/showpost.php?p=8113316&postcount=3")

---

