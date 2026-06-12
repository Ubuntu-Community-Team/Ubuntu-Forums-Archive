---
title: "Running in root question."
date: 2011-03-09
forum: New to Ubuntu
---

### Post by SmiiiLee on 2011-03-09
Hi, I have been building and maintaining my own PC's for 15 years now, and working in IT related fields for 4. Until recently, the only thing I have used Linux for is running it from bootable CDs to recover files from FUBAR Windows installs. 

Lately, I have been experimenting at work using it for security testing. The more I use it the more it is growing on me. I decided to install it on my system to save the hassle of always having to have the disk in the drive. Now, I find myself booting up to Linux more often than I do Windows. 

My question is: If I am running in root on a machine that I also have loaded with Windows, is it possible for an attacker to mount my Windows drives?

My Windows install is on a separate drive which does not automatically mount when I boot Linux.

I am of the understanding that only mounted drives are at risk of being damaged by the user when running in root. That, I can deal with. If I accidentally run a bad command and blow away all my Linux data, it is a lesson learned to me. I don't keep anything important or work related there, so I reload and start over again.

If someone else gets into my machine, mounts my Windows drive, and blows away and/or steals anything from there; that is a completely different story and could possibly cost me my job. 

Is this something I have to worry about? 

I already know that our security is sub-par. If someone with the knowledge to do so plans on hacking us and stealing something they will. But, I also know that by entering the Linux security community online in my quest to learn I am going to come across a lot of other people who know way more about it than I do, and that not all of them are there to help. I just don't want to shoot myself in the foot by getting hacked while trying to learn how to prevent it from happening.

Also, if this is a risk that I have to worry about, does anyone have any suggestions of what I can do to minimize it?

Thanks in advance! Any advice is greatly appreciated! 

(And yes, I know that as a noob to Linux I am probably jumping in way over my head by going straight for the security stuff. I don't care. That is just how I do things.)

---

### Post by 3177 on 2011-03-09
apparently you need to be careful

---

### Post by Sef on 2011-03-09
> My question is: If I am running in root on a machine that I also have loaded with Windows, is it possible for an attacker to mount my Windows drives?


Yes, it would be possible. If a cracker gets root access to your system, then they could mount Windows and remove data from it. Nothing is 100% secure. To make your system more secure, do not install, java, flash, and adobe. (Applies to all oses.)

---

### Post by 3177 on 2011-03-09
> **Sef said:**
> Yes, it would be possible. If a cracker gets root access to your system, then they could mount Windows and remove data from it. Nothing is 100% secure. To make your system more secure, do not install, java, flash, and adobe. (Applies to all oses.)

yes but wouldn't the person need a linux machine?
sounds like he's the only one on his network with a linux install.

---

### Post by teward on 2011-03-09
> **3177 said:**
> yes but wouldn't the person need a linux machine?
sounds like he's the only one on his network with a linux install.

NO.  This happened on one of my nets.  I ran a linux box that had a windows partition.  someone cracked root on my system on Windows, ssh'd AND sftp'd into the computer, got the data off of the mount point, and almost stole a TON of confidential data from me.  Problem was they got caught for a different issue, then got caught later (during the investigation into the first issue) for cracking root and stealing data.  Later when they were questioned, they said "It took a VERY long time, but i cracked it!"

---

### Post by 1clue on 2011-03-10
In a word, yes.

*Edit:*  Because I turned out to be post 6, the above means yes it's possible to be hacked.

Not only that, but it's possible to format your windows drive and put something else on it.  The fact that your Windows partition is on a drive you're not booted from means that fdisk (or any other partition or filesystem tool) can do whatever they want to do.  Heck, you could do it with **cat /dev/random >> /dev/sdb**, assuming that /dev/sdb is your windows partition.  10 seconds and your boot block is gone, a few more and chances are your Windows kernel is toasted.

Security, simplest to hardest:
[LIST=1]
[*]DO NOT RUN AS ROOT!
[*]Turn off unnecessary services.  Careful with this until you know for sure it's an unnecessary service.
[*]Use strong passwords on every account.
[*]Use a firewall appliance on your internet connection, and block everything coming in.
[*]Use the strongest possible encryption/security on any wireless network.
[*]Set up your DHCP server to only allow MAC addresses that are known to you.
[*]Read the security documentation on Ubuntu
[*]Read other security HOWTOs
[*]Pay attention to updates on your system, and READ the information on what each fix is for.
[*]Uninstall software you don't use.
[*]Search on security auditing and run one on your system.
[/LIST]

I've been running Linux since...Heck it was 1991 when I started being serious about UNIX and probably 1994 when I first messed with Linux.  I hardly ever use root, and then only for what I need to do as root.  Root is specifically for administering the system, and it has authorities which are just plain insane according to most home/business end-user machines.

I always run as a regular user.  I add myself to the sudoers file, which is automatically done for you in Ubuntu for the user created during installation.  I always put my files inside of the home directory.

FWIW, it's basically the same procedure you would use to secure a Windows box.

Most of this you can do without asking anything on a forum.  If you need to ask a question then do so in a specific way, and after you've done some initial research.  Ask a specific question about the service.

Everything somebody says to you, think your way through it and do some research to see if it's a sane approach.

---

### Post by 1clue on 2011-03-10
Sorry for double-posting.

One of the most compelling reasons to not run as root is to avoid doing stupendous damage by accident, *by yourself!*

You can accidentally mistype a command or drag your mouse to the wrong spot and cause the system to be unbootable and possibly unrecoverable.

A normal user is pretty safe in that the only thing they can trash are their own personal files.  As long as you stay away from root, you can't really hurt the system.

I can't say how many times in the early days I've thoroughly messed up my user account, created another user and went on from there.

It's possible that if you aren't careful with your system security, an intruder can gain root access even if you don't log in as root.  It's called a **root exploit**.

However, if you shut down your wireless to be the minimum of what you absolutely need, and you shut down your cable modem so nothing at all comes in (the default setting on most of them) and shut down anything you don't need on the system, there's really not much to exploit.

First you want defense in depth (the cable modem/firewall router being a separate host on the  network) and the security you add or configure on your linux box.

FWIW I think that Windows has the absolute worst security of any system I've known of since the Internet became public.  I won't use Windows specifically because it seems to be designed to transport malware no matter what you try to do to stop it.  You can secure Windows but it's a lot harder.

---

### Post by SmiiiLee on 2011-03-10
Hmm... thanks much for the responses. Sef's answer was the most relevant. I am not so much worried about losing data as I am of it being stolen. There are nightly back-ups so the most I could actually lose would be a few hours worth of work. 

I was expecting that answer before even asked. Common sense would tell me that if someone got root access they could do anything the root user can. I guess I was just hoping to be told that the drives not being mounted would somehow magically protect them from someone breaking in remotely and mounting them to steal information. 

@1clue - I am well aware of all of that. I am not sure that you even read the actual question or anything beyond the word root before answering. I am not in any way trying to secure the Linux portion of my box. All of the programs I am messing with are specifically meant for hacking, which I am using to find weaknesses in our system. They automatically change permissions and settings which require them to be run in root in order for them to work. I am aware that by doing so, the Linux portion of my box is wide open to threats, including myself being a noob to Linux.

I did a couple searches with no direct answer to my question. So, instead of spending hours sifting through answers to a bunch of other questions in order to find one relative to mine, I went somewhere and simply asked the specific question that I had. My question was answered in under 20 minutes so I am very satisfied with the results. :)

I have been and will continue to read all of the documentation and how-tos that I can find, but I wanted this one question answered ASAP.

Thanks all for your feedback! :)

Edit after seeing 1clue's second post: Did not mean to come across as a d!ck in my response to your post. I 100% agree that Windows has horrible security, which is why I am venturing into Linux. I am using it to find out firsthand just how bad our security is in order to patch it up as best I can. As I mentioned at the end of my original post, I know that I am jumping into the deep end by starting where I am with very little prior knowledge to Linux.

---

### Post by 1clue on 2011-03-10
No harm, no foul.

I DID read your entire post, and the following ones answering your post.  My responses were as much to them as to you, which is why it got so verbose.  There is a LOT of misinformation out there and a lot of assumptions made from that misinformation.  Somebody makes a tiny factual statement like, "Linux users don't have to worry about viruses" and a whole mythology builds up around it, amounting to an assumption that Linux is impervious to malware and intrusion, which could not be further from the truth.

I hate that.

Good luck and have fun.

---

### Post by dFlyer on 2011-03-10
Never run as root. What's so hard of su or sudo?

---

