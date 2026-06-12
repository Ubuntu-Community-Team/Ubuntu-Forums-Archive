---
title: "Wireshark and File Permissions"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by jeradaj on 2007-10-26
I have installed Ubuntu on a machine that will be used for nothing more than packet capturing (I work for a Telephone company selling VoIP and we need to continuously monitor the management traffic to have a record for troubleshooting user complaints). I'm using Wireshark running as root to capture the traffic that is being mirrored to a 2nd NIC on the machine. My plan was to have wireshark create a new file every 30 megs and dropped it into a specified folder. I then have FTP with the login pointed to that folder so I can simply FTP to the machine and download any file that I need to examine on my workstation. That is working fine; my problem is accessing the files that wireshark creates. Because it is running as root all of the files are created with root being the only user who can do much of anything with the files.

I could login manually and modify the permissions each time; but that is too much hassle. I want the process to be setup so all I have to do is FTP in and grab the appropriate file based on the timestamp of when the file was created.

Can anyone help? Did my description of what I want to do make sense?

---

### Post by kidders on 2007-10-27
Hi there,

How about **chgrp**-ing the directory you're storing your packet dumps in, and setting it's SGID bit? That way, assuming Wireshark's umask is loose enough, the files can be read by members of any group you designate.

There are other approaches, but that would be my first choice.

---

### Post by jeradaj on 2007-10-29
I'm afraid I don't know what an SGID bit is nor how to change it. Can you help with that?

Also, I'm not sure what you mean by wireshark's umask. Can you elaborate on that a bit?

---

### Post by kidders on 2007-10-29
Hey again,

They're pretty fundamental access control concepts, common to almost all operating systems. There's plenty of discussion of these (and similar) ideas around the web though, so if you've never seen them before, that's no problem. :-)

In brief, what I suggested in my last post was...[LIST]
[*]Imagine you have a group called "ftpusers" or something, and that Wireshark is dumping traffic to /var/tmp/wireshark, for the sake of example.
[*]Do **chgrp ftpusers /var/tmp/wireshark**, so that ftpusers becomes the directory's owning group.
[*]Do **chmod g+s /var/tmp/wireshark**, to set the directory's SGID bit, which will force the group associated with it on any new files created in it, regardless of who creates them.
[*]Then, provided Wireshark's environment's umask is at least 737, anything it creates will be automatically made group readable. A umask controls the permissions bits a file *doesn't* have.
[/LIST]

I hope that helps ... you'll find far more extensive (and better quality!) discussion of access control principles with a search engine though.

---

### Post by jeradaj on 2007-10-29
Thanks Kidders,
I think I can get it going based on that advice.

But just for the sake of asking, what would be the "normal" way of working with files created with wireshark/root that the normal login can't do anything with (because of the file permissions)?

---

### Post by jeradaj on 2007-10-29
Well, I thougt I could get it going; but no luck. I have made the user that is logging in via FTP the owner of the directory where the files are stored; plus ran the chmod g+s command but I still can't get the files VIA ftp unless I manually change the permissions on the file.

Any other thoughts on how I can set this up so I don't have to change the file permissions prior to being able to FTP the files?

---

### Post by kidders on 2007-10-29
> **jeradaj said:**
> But just for the sake of asking, what would be the "normal" way of working with files created with wireshark/root that the normal login can't do anything with (because of the file permissions)?If the problem is *permissions*, then there is no particular solution, since any user can freely alter the permissions of something he owns.

Ownership issues, on the other hand, are often best solved using the SGID bit.

> **jeradaj said:**
> Well, I thougt I could get it going; but no luck. I have made the user that is logging in via FTP the owner of the directory where the files are storedThe *user* that owns the files is irrelevant, and will always be the user Wireshark is running as. In your place, I would be most interested in the owning group.

---

### Post by jeradaj on 2007-10-29
Ok, then I can't get your current advice to work. Do you have any other suggestions?

---

### Post by kidders on 2007-10-29
Why did my suggestion fail, exactly? Could you describe the specific effect it had (or failed to have hehe) on files created by Wireshark? What do the current permissions on Wireshark's target directory look like?

---

### Post by jeradaj on 2007-10-30
When I go to the "Users and Groups" configuration window I don't have any type of "ftp" group whatsoever. I use the login of "administrator" to manage the machine as well as to login to the FTP server. There is a group "administrator" and user "administrator" is in the group. So, I assumed your suggestion of applying the chgrp command should work if I apply it for "administrator".

I'm attaching the commands that I have ran in a text document for you to examine. 

As you can see from the ls -la the new files that are being created still have very limited permissions for my user account.

---

### Post by kidders on 2007-10-30
Looks like you're there, except for the fact that Wireshark is being paranoid about the permissions it applies to files it creates. It seems to set them all "chmod 600", when "chmod 640" would be better. Ordinarily, applications obey their environment's umask when creating new files (which is why I suggested altering yours), but having tried it myself, it seems that Wireshark is hard-wired to ignore it. Unfortunately, short of altering its source code, there's no way to change that.

Wireshark has a long history of very serious bugs, which probably explains why it deliberately defeats attempts to make the files it creates automatically accessible by non-root users. I guess I should've checked that out before blindly suggesting the standard approach to this problem. Sorry.

Anyhow, long story short, it seems the answer to your o/p is "Wireshark is specifically designed not to let you".

---

### Post by jeradaj on 2007-10-30
Thanks for your help so far. But I guess I'm still stuck where I started.

Any suggestions?

---

### Post by kidders on 2007-10-30
Yeah. For "normal" applications, suggestions like the one I made would work quite well. Unfortunately, Wireshark essentially does this, when you save a file...[LIST]
[*]Touch the file.
[*]Override the environment umask by "chmod 600"-ing it.
[*]Override the file's owner, by "chown"-ing it.
[*]Append the saved data to the file.
[/LIST]So, it's been explicitly designed to defeat any attempt to make saved data accessible by anyone other than root.

The only alternative is to manually run "chmod g+r" on the files you want to access via FTP, I'm afraid ... although you *could* have cron do that for you on a regular basis, if you liked. In that case, assuming you set up a cron job that ran at 10-minute intervals (for the sake of argument), the worst case scenario would be that files would magically become accessible via FTP once they had existed for at least 10 minutes.

That approach would *certainly* work, but it's a bit hacky.

---

### Post by jeradaj on 2007-10-30
Thank you for your help kidders!

---

### Post by jeradaj on 2008-01-10
For anyone who may have read this and wants a "simple" solution I have come up with an eay solution.

I have create a cron job that will chmod the files every five minutes and apply the the necessary permissions. This allows me to access the files that I need.

---

### Post by kidders on 2008-01-10
Yep... that seems like the best option. Sorry it took so many posts to get you there. :-(

Wireshark has a long history of tremendous paranoia in the way it does things, motivated by a desire to try to make running such a dangerous application as safe as possible. That approach sure does make life difficult though!

---

