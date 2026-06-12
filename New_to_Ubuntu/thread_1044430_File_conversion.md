---
title: "File conversion"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by MasterChief on 2009-01-19
I'm pretty new at using Ubuntu so bear with me please.

I've been converting .rpm files to .deb.

Was doing OK until I hit this: masterchief@cascadia:~$ sudo alien -k MySQL-server-4.0.25-0.i386.rpm
Warning: Skipping conversion of scripts in package MySQL-server: postinst preinst prerm
Warning: Use the --scripts parameter to include the scripts.

What does it mean exactly and how to I fix it?

I need to convert this file because there aren't any .deb files available in any repository for this old version of mysql.

---

### Post by Titan8990 on 2009-01-19
Typically, it is better to compile from source then convert RPMs to debs.

---

### Post by drubin on 2009-01-19
> **MasterChief said:**
> I'm pretty new at using Ubuntu so bear with me please.

I've been converting .rpm files to .deb.

Was doing OK until I hit this: masterchief@cascadia:~$ sudo alien -k MySQL-server-4.0.25-0.i386.rpm
Warning: Skipping conversion of scripts in package MySQL-server: postinst preinst prerm
Warning: Use the --scripts parameter to include the scripts.

What does it mean exactly and how to I fix it?

I need to convert this file because there aren't any .deb files available in any repository for this old version of mysql.

Is there a reason you would like to install an outdated version of any thing?

There is a reason it is on in the repos!

---

### Post by MasterChief on 2009-01-19
I'm going to be running a game server. And the game binaries are bound to mysql versions 4.0.20-0 to 4.0.25-0.

I was running the server on a regular PC using Fedora 9. I have a real server now and was having problems with F9 reading all the ram available. So switched to Ubuntu serer 8.04 LTS 32-bit. It has no problem reading all 8gb of ram.

Deb and source files are no longer available for these versions of mysql. They are available for 4.0.26-0 and newer, but won't work with the binaries.

---

### Post by drubin on 2009-01-19
> **MasterChief said:**
> I'm going to be running a game server. And the game binaries are bound to mysql versions 4.0.20-0 to 4.0.25-0.

I was running the server on a regular PC using Fedora 9. I have a real server now and was having problems with F9 reading all the ram available. So switched to Ubuntu serer 8.04 LTS 32-bit. It has no problem reading all 8gb of ram.

Deb and source files are no longer available for these versions of mysql. They are available for 4.0.26-0 and newer, but won't work with the binaries.

A much better solution would be trying to get the game server patched to work with the newer binaries... not much has changed in functionality and would not affect the runniing of the game. 

But as far as security fixes and bugs go.. You might as well open up your door and say here come in and find holes in my server.

---

### Post by MasterChief on 2009-01-19
I agree whole heartedly about the security and bug issues!:(

But we have no other recourse at this time.

Sometime between now and "spring" we are supposed to get new game code as it will be going open source.

But the new code was modified and re-optimized to run on Windows 2003 and using Oracle as the database!:mad:

So some of our talented programmers are going to try and get it working with newer versions of Linux and MySql. Getting the code might still be months away with possible months of conversion effort after that!

So in the meantime we run with what we have.

---

### Post by Titan8990 on 2009-01-19
What game is this?

---

### Post by drubin on 2009-01-19
> **MasterChief said:**
> I agree whole heartedly about the security and bug issues!:(

But we have no other recourse at this time.

I alone with many other members of this community would not be able to or willing to provide support to alien rpm -> .deb files.

Sorry but the amount of damage you can do to your system is not worth risking any thing. I will therefore not be able to help you.

Good luck with the up and coming  linux versions. :)

---

### Post by MasterChief on 2009-01-19
I can't tell you what game it is at this time...sorry!

Thanks for the best of luck drubin! I'll probably need it!

I've already run into warnings about alien converted files.

So guess it's back to F9 whether I want to or not.

---

### Post by Titan8990 on 2009-01-19
> I can't tell you what game it is at this time...sorry!

Is this code for "I am doing something illegal?"

---

### Post by drubin on 2009-01-19
> **MasterChief said:**
> I can't tell you what game it is at this time...sorry!

Thanks for the best of luck drubin! I'll probably need it!

I've already run into warnings about alien converted files.

So guess it's back to F9 whether I want to or not.

> **Titan8990 said:**
> Is this code for "I am doing something illegal?"

Either way. This isn't a place to ask vague questions. We can't help you if you do not want to let us.

I would suggest trying some where else or maybe installing a very out dated version of an RPM bassed distro like Fedroa 4 or something similar to have compatibility you require.

BTW they are on fedora 10 now. so you can see how outdated what you are asking is.

Another way would be to contact mysql dev team and ask them for a version. Else there are tones of paid mysql support teams with rather great reputations of doing "funky" things with mysql.

---

