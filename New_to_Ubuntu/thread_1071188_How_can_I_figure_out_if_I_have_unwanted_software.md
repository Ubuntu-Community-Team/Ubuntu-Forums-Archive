---
title: "How can I figure out if I have unwanted software?"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by kyalee on 2009-02-15
Okay, long story short, I found out that someone I share this computer with (he has his own profile) thought it was a good idea to open attachments sent to him in spam email. I explained to him that having a more secure OS does not give you the freedom to be a complete moron. He's convinced it's fine because it's not spam. He just somehow started getting emails from some random people--in Spanish (which he speaks, but not often)--about their lives and with large .ppt attachments included. I counter that it's strange spam, but still spam and probably malware intended to take advantage of saps like him.

Anyway. I was trying not to worry about it, but today when I was about to log off I got a message that there's an unknown program running and do I want to log off anyway. So now I'm a bit paranoid.

His profile is (thankfully) not admin level. Is it possible he managed to install something anyway? Is there any way to check for spyware/malware/viruses? Or am I just being totally paranoid?

---

### Post by abn91c on 2009-02-15
to start AVg makes a free linux version [http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl)

---

### Post by SunnyRabbiera on 2009-02-15
There is no addware/spyware/viruses for linux and its doubtful he could install anything harmful if he has no administration access.
But I would use the users and groups app in your master account and unlock it, select his account and click "properties"
after that go to the user privileges tab and make sure he has no administrative access.
Heck you may want to tweak things so he cant use the net without your permission, there are many tools for this too if you know where to look.

---

### Post by sandyd on 2009-02-15
> **kyalee said:**
> Okay, long story short, I found out that someone I share this computer with (he has his own profile) thought it was a good idea to open attachments sent to him in spam email. I explained to him that having a more secure OS does not give you the freedom to be a complete moron. He's convinced it's fine because it's not spam. He just somehow started getting emails from some random people--in Spanish (which he speaks, but not often)--about their lives and with large .ppt attachments included. I counter that it's strange spam, but still spam and probably malware intended to take advantage of saps like him.

Anyway. I was trying not to worry about it, but today when I was about to log off I got a message that there's an unknown program running and do I want to log off anyway. So now I'm a bit paranoid.

His profile is (thankfully) not admin level. Is it possible he managed to install something anyway? Is there any way to check for spyware/malware/viruses? Or am I just being totally paranoid?

its probably just something left over from what he was doing.
probably wouldn't do any damage anyways, because he doesn't have admin access.
the only stuff he could have installed are in his home directory and nin any other directory writable by him, which is not much...  . its not nice, but you can run though his root directory and see if theirs anything weird there. :)

---

### Post by kyalee on 2009-02-15
Yeah, I checked his user properties and he has no privileges to administer the system. So I'm probably okay.

Unfortunately, I can't go so far as to deny him net access. He, uh, pays the entire internet bill and if I had to pay it myself I'd be back to dial up because there's no way I can afford cable internet on my paycheck.

Any ideas what this unknown program is? Or how I can figure it out?

---

### Post by Shazaam on 2009-02-15
Check in System Monitor or run top (or htop if you have it installed) in terminal to see what is running.

---

### Post by Orion8 on 2009-02-15
Yeah, to see what is running I'd open System Monitor and then under "view" toggle the various options.

---

### Post by Vico Vicario on 2009-02-16
Also make sure your own directory has proper permissions. Unfortunately dirs are created with 755 permissions, so a malware could potentially change to your home dir and read files or write some if you have wrong permissions for your files.

Just 'cd /home' and 'chmod 750 $HOME'

V.

---

