---
title: "Does removing &amp; replacing drive cause Boot Loop?"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by NunyaB on 2010-01-11
{  Re: Ubuntu 9.10, the honeymoon is over?, Logon boot loop }  

_Can some one tell me if this issue is being created by the drive being removed from the machine?_

OK, I think I have discovered what was causing the initial boot loop problem. I am not sure If I should start a brand new post or if anyone will see this.  As I said in my first post, I set up this system CENTRED around removable laptop drives in a ICY-Dock. This way I can swap out operating systems, versions , and configurations at will. I now think this is what is creating the boot loop. The new clean install worked great with no issues. Tested several restarts before & after upgrades, software installs. No problems. I cloned the drive and that one had no problems on restart. But I did notice on one try I was prompted for pw when I forgot to remove an external usb drive I was transferring files from. I removed it and back to no problems.  

Now here's the thing. I was working with other OS drives all weekend. Tonight I went back to the Ubuntu 9.10 drive. BOOT LOOP pw prompt! _Can some one tell me if this issue is being created by the drive being removed from the machine?_ If so I'm not sure I can rely on using Ubuntu until I can build a machine dedicated to just it. And that would not be nice... My first try at 9.10 lasted 2 months before the boot loop cycle corrupted the OS to non-functionality. 2 days this time before it starts. I can't be the only one who needs to remove the drive from the machine.  

Thanks in advance for all the help! NunyaB

---

### Post by NunyaB on 2010-01-12
OK, here's what I have found.  Every time I remove the drive and run another OS before reinstalling Ubuntu 9.10 drive I get prompted to password logon even though the drive was set up without pw logon.  If I reset instead of attempting the logon the pw prompt clears on next boot.

Also, starting the machine with a external USB drive attached (new one to installed Ubuntu 9.10 OS drive) gives the pw prompt.  I do not know why this is and no one has answered but maybe this will help some one in similar circumstances.  I have cloned 3 drives now and tested each, it's the case for each one.  I did find one additional drive in the batch that read as going bad ( even though new drive ) and that might have been the cause of my initial boot loop degradation.  

Guess Ubuntu 9.10 should have come with the splash screen as that scene in Lost Boys where grandpa says: " RULES!, we got some rules around here! "
1. Nobody touches the 2nd shelf in the fridge but me
2. If using KVM don't start Ubuntu without screen selected
3. If swapping HDs don't use pw logon just reset
4. make sure machine is exactly like it was when you did original install, nothing new!
5. ...
And we'll get along fine and you'll have the pleasant Ubuntu experience you thought you would.

If these conditions make sense to anyone who's been around Ubuntu awhile please let me know.  It's either that or I need to hang a gremlin no pest strip in my case.

Thanks Again for the help.  Especially to the posts about slowing disc burning down when cloning ISO.  That was a head slapping V8 moment.  :D

---

