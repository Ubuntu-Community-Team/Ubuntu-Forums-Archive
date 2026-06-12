---
title: "Suddenly an Administrator"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by jda8818 on 2010-06-09
Fresh Install 10.04.  Checking "Users and Groups" I noticed my user type was "Custom".  

Added another user - generic desktop user (Wife).

Changed some group memberships - added Wife to 'audio' i think ...

And then my user type had changed to "Administrator"

Is this OK?  I love the proposition that as a generic (' or Custom") user malware etc won't have permission to modify files & otherwise wreak havoc.

I'm still prompted for password access to Synaptic, for instance, but my question is: Have I compromised security by somehow (inadvertently) becoming an administrator?

Thanks in advance for any comments or suggestions.

JA

---

### Post by Zemblan on 2010-06-09
Being an admistrator just means that you can use sudo to get 'root' access to change things. It doesn't mean that programs you run automatically have root privileges, they don't. The only way malware is going to be able to have sufficient access to change things outside your home directory is if you give it that permission.

---

### Post by jda8818 on 2010-06-09
Thanks Zemblan, I appreciate you reply!

Good, I'm glad I haven't compromised anything!  

I was able to use "sudo" as a "custom" user.

why, though, did i become an administrator?  I'm guessing that the difference between "Custom" and "Administrator" is membership in certain groups??

any idea which ones?  

Thanks again for all comments/advice ...

JA

---

### Post by doas777 on 2010-06-09
weird. was yours the first user account created (during install)?
usually this user is an Admin, as Zemblan described. 
the new users/groups tool is nice, but it still seems a little buggy in terms of reporting user membership summaries. if your membership changes while it is open, it will show as custom until the change is applied. after that, it more accurately display your status.

---

### Post by jda8818 on 2010-06-09
doas777:

Thanks for  your reply!

As I recall I was the only user configured during the install. and I have been type "Custom" since day 1.  Day 1 was about a week ago ...

Anyway, I always try to accept all the defaults during any installation.  I guess I'll not worry about it too much - if i should have been an administrator all along then i'm just catching up.

Do you know of any discussion/tutorial devoted to Linux users and groups?

Thanks again,

JA

---

### Post by louieb on 2010-06-09
Custom just means something from the default has changed - for example I installed the **zhs** shell and made it my default login shell - now my account shows up in users and groups as type Custom.

---

### Post by jda8818 on 2010-06-10
Hi Louieb:

I was "Custom" by default, and now that I've changed several things, I'm an administrator.

BTW, I was unable to get any sound via HDMI at first, so I ran an AlsaUpgrade script (which got me system sounds and Rhythmbox sound) and then created an /etc/asound.conf file that provided flash audio in Firefox.  I was able to get HDMI audio to work.  After adding another desktop user, that person has no HDMI audio.  The new user is at square one as far as HDMI audio is concerned.

I would have thought that the AlsaUpgrade and the /etc/asound.conf file would have had a global attect.

Do you think I should run the AlsaUpgrade script from the new users login?  The /etc/asound.conf file would apply to all users, wouldn't it?

Thank you in advance for all comments or suggestions!

JA

---

### Post by jda8818 on 2010-06-10
Never Mind!

Had to select HDMI Output in "Sound Preferences" (DUH)  All OK for both users!

Thanks to all,

JA

---

