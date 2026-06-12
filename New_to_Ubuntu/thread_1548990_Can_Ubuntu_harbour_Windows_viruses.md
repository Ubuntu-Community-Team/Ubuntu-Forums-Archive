---
title: "Can Ubuntu harbour Windows viruses?"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by Uqunfu on 2010-08-09
I'm getting set to format the disk of my malware-ridden home laptop and reinstall Windows XP and Ubuntu on partitions.

Now, if I transfer some files I want to keep to USB, then port them onto the fresh Ubuntu, the Windows malware presumably won't have any effect.  But will the malware be lurking in Ubuntu, waiting to jump onto any media I use with it, and then infect other Windows setups I use?

---

### Post by Rubi1200 on 2010-08-09
> **Uqunfu said:**
> I'm getting set to format the disk of my malware-ridden home laptop and reinstall Windows XP and Ubuntu on partitions.

Now, if I transfer some files I want to keep to USB, then port them onto the fresh Ubuntu, the Windows malware presumably won't have any effect.  But will the malware be lurking in Ubuntu, waiting to jump onto any media I use with it, and then infect other Windows setups I use?
The answer is, theoretically, yes.

If those files came from an infected Windows machine they could lurk on Ubuntu until moved back to Windows where they would cause havoc.

The simple answer is don't take a chance like this. Unless these files are absolutely critical and cannot possibly be replaced or unless you are absolutely 110% sure they are not infected, I would say don't risk it.

---

### Post by Uqunfu on 2010-08-09
Thanks Rubi.  There's stuff I'd like to keep, but I'll have to sacrifice.

---

### Post by Tony Flury on 2010-08-09
> **Uqunfu said:**
> I'm getting set to format the disk of my malware-ridden home laptop and reinstall Windows XP and Ubuntu on partitions.

Now, if I transfer some files I want to keep to USB, then port them onto the fresh Ubuntu, the Windows malware presumably won't have any effect.  But will the malware be lurking in Ubuntu, waiting to jump onto any media I use with it, and then infect other Windows setups I use?

If you transfer infected files onto a Linux installation, and don't do anything to them - i.e. convert them, and then at somepoint move them back to a Windows installation, they will still have the ability to infect Windows. The malware wont run under Linux therefore wont be able to "jump" to any media - you would have to make a concious decision to move the files.

---

### Post by Uqunfu on 2010-08-09
> **Tony Flury said:**
> If you transfer infected files onto a Linux installation, and don't do anything to them - i.e. convert them, and then at somepoint move them back to a Windows installation, they will still have the ability to infect Windows. The malware wont run under Linux therefore wont be able to "jump" to any media - you would have to make a concious decision to move the files.

Right.  So if I transferred .doc and picture files there's no way the virus could hitch a ride?

---

### Post by mastablasta on 2010-08-09
yes it can. why not scan them with soem AV under Linux (they will detect windows viruses). There are a couple of them out there.

---

### Post by Rubi1200 on 2010-08-09
> **Uqunfu said:**
> Right.  So if I transferred .doc and picture files there's no way the virus could hitch a ride?
I am not sure if that is correct. Who knows what might be hiding in a seemingly innocent .doc file (e.g. a malicious macro).

I think what Tony Flury was saying is that if a file is infected with malware and you then consciously transfer it to a Windows box, then it will likely rear its ugly head again.

But since you are not sure if something is infected, better not to take a chance in my opinion.

---

### Post by Uqunfu on 2010-08-09
> **Rubi1200 said:**
> I am not sure if that is correct. Who knows what might be hiding in a seemingly innocent .doc file (e.g. a malicious macro)
That's what I feared.

---

### Post by TTGRULES on 2010-08-09
Why don't you just get an antivirus scanner... there are a lot of free good ones for linux and windows... just scan the files when you move them....

---

### Post by 3rdalbum on 2010-08-09
Viruses   are   not   biological   or   magical.   They   will   not   be   able   to   'jump'   to   any   media   unless   they   are   running,   which   they   won't   be   on  Ubuntu.   The   only   way   they   can affect   Windows   systems   again   is   if   you   put   an  infected   file   back   onto   a  Windows   machine   and   run it.

Viruses   only   really   reside   in  executables,   not   in   Word   docunebts   or   JPEGs.   If   in   doubt   you   could always   resave  the   documebts   on   Ubuntu   (Save   As...),   and   the   virus   will   not   be   in   the  new file.

---

### Post by Uqunfu on 2010-08-09
> **TTGRULES said:**
> Why don't you just get an antivirus scanner... there are a lot of free good ones for linux and windows... just scan the files when you move them....

The beastie I've got on there is invincible.  I've tried everything.  I didn't make the choice to format the HD easily!


> **3rdalbum said:**
> Viruses   only   really   reside   in  executables,   not   in   Word   docunebts   or   JPEGs.   If   in   doubt   you   could always   resave  the   documebts   on   Ubuntu   (Save   As...),   and   the   virus   will   not   be   in   the  new file.

My knowledge isn't great.  My understanding is that a simple script can hide in things like .doc and .gif files.  However, if I can resave things in a linux format I imagine that would purge anything that doesn't belong there.

---

### Post by dangerjunkie2002 on 2010-08-09
Hi,

There's some good advice here :)

As everyone says, Linux can "harbour" Windows viruses and malware, not in the sense that it can spread them but that it can store a file containing one and that file can subsequently be reintroduced to a Windows machine. Last year I also inadvertently spread a virus between 2 Windows machines on my USB thumb drive. Because I couldn't catch the virus on my Linux machine I'd not scanned for it or noticed it on my stick. It's a bit like being an asymptomatic carrier of a disease; I'd spread the digital clap to a couple of other people before I realised I had it. Be vigilant for "autorun" files suddenly appearing on your thumb drives.

There hardly any risk from copying media like photos and music from the infected drive. Dangerous items include anything executable (a program or parts of one) like EXE,COM,PIF,MSI,SCR,SYS,DLL and similar types. There is some risk in copying MS Office files as they can contain macros.

If absolutely must copy a file of one of the above types I would recommend uploading it for testing at virustotal.com before you do. This will feed it to a whole collection of antivirus products and give you a pretty decent certainly if it is infected or not.

I would also recommend you copy files consciously. Don't drag whole folders full without first looking inside to check there is nothing in there you didn't expect (like an exe file in your photos folder)

Important question: Are you sure the drive you're using to copy this media isn't infected with a boot-sector or autorun virus if it's been on the infected machine when it was running? Also make sure that every USB drive or thumb drive the owner of the Windows box has is clean. If it's not then you will leave, they will plug their thumb drive in and end up back in the same mess again.

Once you have got the files off the infected machine I recommend you download DBAN and totally erase the drive in it. Some boot-sector viruses can survive a reformat of the drive. If this happens the machine will be reinfected as soon as you build Windows on it.

Good luck,
Paul.

---

### Post by Uqunfu on 2010-08-09
Thanks Paul.  I'll nuke it with DBAN.

Cheers to everyone for the help.

---

### Post by beew on 2010-08-09
Actually, if you are transferring a file that has a windows virus in it. Would you be actually able to see it in Linux so that you can remove it by simply deleting it? Say you want to transfer a .rar file. You open it in  Linux and see a file with very strange name, --assuming you know what content to expect,---it would be a virus and you can simply delete it since it cannot hide or act up in Linux. Am I missing something?

---

### Post by dangerjunkie2002 on 2010-08-09
You're welcome. 

You don't need to waste time with any of the exotic modes in DBAN. The one pass writing zeros will be enough.

Cheers,
Paul.

---

