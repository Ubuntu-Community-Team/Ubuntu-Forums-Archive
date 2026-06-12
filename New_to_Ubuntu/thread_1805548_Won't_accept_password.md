---
title: "Won't accept password"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by sophie2cu2 on 2011-07-16
Hi,
I'm totally new to this and I just installed Wubi and now it wont let me log in. It keeps asking for a password. I know my password and I'm not likely to forget it. Can't get back on Linux. I was adjusting the settings to what I wanted when the computer rebooted and can't get back on Wubi since. What have I done wrong?
Thanks for your help,
Sophie

---

### Post by bcbc on 2011-07-16
Boot in recovery mode, drop to a root shell and change the password... enter:
```
passwd username
``` (replace username with your own)

You can confirm the username with
```
ls /home
```

PS there might be some other problem here. The fact that it rebooted in the middle of something indicates some issue. It might not be related to the password at all.
Before you change it, try dropping to a terminal from normal login CTRL+ALT+F1 and see if you can login normally.

---

### Post by Rubi1200 on 2011-07-16
Hi and welcome to the forums :)

Which password are you using; the Windows password or the one you created for Wubi at installation time?

edit: follow the advice posted by bcbc

---

### Post by sophie2cu2 on 2011-07-16
Hi all,
Thank you for your replies.
I'm using the password and user name Ubuntu asked me to specify during set-up
I'd love to do what bcbc suggests, but I haven't got the slightest idea what he means by dropping to a root shell. Sorry for being so dumb.
But thanks anyway.
S

---

### Post by dFlyer on 2011-07-16
First make sure the cap key is not on and try your password, if that doesn't work, turn on the cap key and type your password. One time after I installed I had the cap key on and it kept rejecting my password with it off. When I turn on the cap key and type the password it accepted it. If that is the case you can change it after you log in.

---

### Post by bcbc on 2011-07-16
> **sophie2cu2 said:**
> Hi all,
Thank you for your replies.
I'm using the password and user name Ubuntu asked me to specify during set-up
I'd love to do what bcbc suggests, but I haven't got the slightest idea what he means by dropping to a root shell. Sorry for being so dumb.
But thanks anyway.
S
When you boot select the second entry in the grub menu - it has (recovery mode) on the end. That will bring you to a menu, scroll down and select "root - drop to root shell prompt" [http://t1.gstatic.com/images?q=tbn:ANd9GcQDYwTDRsLmCbuG_cY4pdq4x-TpmT-3v2QzypAf349ImNk064dB](http://t1.gstatic.com/images?q=tbn:ANd9GcQDYwTDRsLmCbuG_cY4pdq4x-TpmT-3v2QzypAf349ImNk064dB)

---

### Post by sophie2cu2 on 2011-07-17
> **bcbc said:**
> Boot in recovery mode, drop to a root shell and change the password... enter:
```
passwd username
``` (replace username with your own)

You can confirm the username with
```
ls /home
```PS there might be some other problem here. The fact that it rebooted in the middle of something indicates some issue. It might not be related to the password at all.
Before you change it, try dropping to a terminal from normal login CTRL+ALT+F1 and see if you can login normally.

Hi Guys,
I want to thank you for all your help. The solution suggested by bcbc worked and Wubi is running fine now (even though it does seem a bit clunky - is that normal?). I'd love to know why it wouldn't accept my password in the first place. Now all I have to do is get past the long up-hill learning curve.
Many thanks,
Sophie

---

### Post by EthioJOB on 2012-01-28
> **Re: Won't accept password**
         Boot in recovery mode, drop to a root shell and change the password... enter:
     Code:
     passwd username 
 (replace username with your own)

You can confirm the username with
     Code:
     ls /home 
PS there might be some other problem here. The fact that it rebooted in the middle of something indicates some issue. It might not be related to the password at all.
Before you change it, try dropping to a terminal from normal login CTRL+ALT+F1 and see if you can login normally.     My concern here is that wouldn't this enable anyone to 'break' into your computer? If so, where's the security of Ubuntu? I mean, what would be the point of  installing it in organizations or so?

---

### Post by mcduck on 2012-01-28
> **EthioJOB said:**
> My concern here is that wouldn't this enable anyone to 'break' into your computer? If so, where's the security of Ubuntu? I mean, what would be the point of  installing it in organizations or so?

The security, as with every operating system, is in keeping unwanted people from gaining physical access to your computer.

Physical access is always same as full root access, there's nothing an operating system can do about it. Any user with access to a computer can always boot it using a live-CD or USB, or open the case and remove your hard drive(s), plug them to another machine and access your data that way. BIOS passwords and such are easily cleared so they don't make any difference. And of course there are many other ways how a person with physical access could get your files, or break your system in some other way.

The operating system's responsibility on security is of course limited to the times when the OS in question is running, they can't do anything to improve security when any other OS is used on the same machine or when it's powered off.

The only way to protect your files even in case of physical access is file system encryption. And even that might not be a perfect solution, or protect everything on your computer. (and it of course doesn't do anything when the system is already running and somebody gains access to it) So you really just have to keep unwanted people from accessing your computers, regardless of what operating system you use.

---

### Post by raja.genupula on 2012-01-28
> **EthioJOB said:**
> My concern here is that wouldn't this enable anyone to 'break' into your computer? If so, where's the security of Ubuntu? I mean, what would be the point of  installing it in organizations or so?
Good Question .
But what i am thinking is at the confidential areas they will appoint some camera's .

 
Hey one more thing we can put password for GRUB , may be it gonna help us to protect others from the user .

[http://www.makeuseof.com/tag/how-to-password-protect-grub-entries-linux/](http://www.makeuseof.com/tag/how-to-password-protect-grub-entries-linux/)

I think this will be the solution .

---

### Post by AnTonyWmM on 2012-12-05
Hi all!

I'm new to Ubuntu - just recently did a 12.04 install on HP dc7600 with pentium 4, 3.2ghz cpu and 3 gigs ram.

I'm liking it a lot so far, but I turned off the password to log in (it's a family compu so don't need to type that all the time).  When I went to install some software today and typed my password to authenticate, no go!  I know absolutely I have the correct password (I'd been using it all along before). Checked caps and all that.

Did the password reset in the root, but that said password change denied, parameter incorrect, something-or-other.

Tried booting from usb to mount the main drive and remove password in 'shadow' file, but it registered no password between the first two semicolons (where HELP said it should be). As if I already had removed it.  But entering no password as the next step in help says is to no avail either.

Anyway, I'm stumped at this point - could turning off the login password have done this to me?
Will I have to do a reinstall to fix the issue (and then leave the password on, though it's unhandy?)

Any insight will be appreciated.

Thanks!
Anthony

---

### Post by AnTonyWmM on 2012-12-07
Hi again!

I found another thread relating to this problem, and discovered why my root passwd reset didn't work: I needed to remount the root in read-write - apparently Ubuntu HELP hasn't been updated as to this more recent requirement.  For anyone who needs to do this, find a good how-to here:
[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

Still not sure why turning off password at login would initiate the problem, but I'm up and running again!

Anthony

---

### Post by AnTonyWmM on 2012-12-07
Hi again!

I found another thread relating to this problem, and discovered why my root passwd reset didn't work: I needed to remount the root in read-write - apparently Ubuntu HELP hasn't been updated as to this more recent requirement.  For anyone who needs to do this, find a good how-to here:[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

Still not sure why turning off password at login would initiate the problem, but I'm up and running again! 

Anthony

---

