---
title: "How not to hose your system?"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by baxna on 2009-04-13
[FONT="Franklin Gothic Medium"][SIZE="3"]Hi everyone,

This is my first post... I just installed Ubuntu 8.10 today! I've tried using the live CD for several weeks now and have been pretty impressed with the "out-of-the-box" experience on my Thinkpad T42. So I decided to take the plunge, although I can't quite remove XP yet because I need Quicken and Turbotax still.

My question is for the experienced ones out there... what are some of the more common ways newbies like myself hose their new Ubuntu systems? What things should I watch out for? I know you shouldn't run unknown commands people tell you to run without checking them out first. I'm just wanting to be careful and not approach GNU/Linux like I know anything or that it's like MS Windows... cuz it's not!! And thank you ALL for that!! \\:D/

Best regards, Mike[/FONT][/SIZE]

---

### Post by steve101101 on 2009-04-13
using sudo commands in the terminal without thinking what you are doing.

---

### Post by nwadams on 2009-04-13
my rule of thumb is: before you sudo anything make sure you know what its supposed to do.

other points: i recommend making a separate home partition so you don't lose all your files if you break something and have to re-install.

I also recommend using the repositories whenever possible and avoid installing stuff via other means. Adding 3rd party sources is ok though. (wine, medibuntu, etc.)

the terminal is your friend...if you let it be;)

---

### Post by thesuperjman on 2009-04-13
im fairly new here as well, and i dont know if you mess with the command terminals but i *highly* reccommend you read the malicious commands thread- [http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326)

---

### Post by steve101101 on 2009-04-13
there is a usually a how to guide on how to do pretty much anything for ubuntu. these are very valuable even to users such as myself because you cannot know everything about everything.

---

### Post by nwadams on 2009-04-13
i agree, you can't know everything. Howto guides are great. I came across one the other day for something and learned how to make something completely unrelated work better. 

Probably the best thing and the one thing that everyone will tell you over and over again is to ASK for help if you don't know what you are doing.

---

### Post by thesuperjman on 2009-04-13
yea ive got my own help thread that's like 6 pages long now.

---

### Post by baxna on 2009-04-13
[FONT="Franklin Gothic Medium"][SIZE="3"]Thanks everyone! I gather that the main dangers center around sudo terminal commands and not knowing what something will do, right? Is there a table or listing of all the possible sudo commands to reference? I'm comfortable using the terminal but hopefully won't have to use it a lot as Ubuntu is very stable! Also I did read the post about malicious commands, thanks for the tip.[/SIZE][/FONT]

---

### Post by steve101101 on 2009-04-13
> **thesuperjman said:**
> yea ive got my own help thread that's like 6 pages long now.

this forum is incredibly helpful because of the great community.

---

### Post by wookiehangover on 2009-04-13
never under any circumstance enter

```
:(){ :|:& };:
```

into the command line.

---

### Post by baxna on 2009-04-13
> **wookiehangover said:**
> never under any circumstance enter

```
:(){ :|:& };:
```

into the command line.

Looks like a bunch of messed up smiley faces?

---

### Post by steve101101 on 2009-04-13
> **baxna said:**
> Looks like a bunch of messed up smiley faces?

you won't be so happy though when you type it in. here is info on it ... [http://laptoplogic.com/resources/understanding-and-avoiding-malicious-code-attacks-in-linux](http://laptoplogic.com/resources/understanding-and-avoiding-malicious-code-attacks-in-linux)

---

### Post by steve101101 on 2009-04-13
here is a good quote from that webpage:

"If you are a newcomer to Linux, there's a good chance you are converting from Windows. When it comes to protecting your machine, think of it this way:

When you receive code from a stranger, think of it as a file attachment in an email from a stranger. You wouldn't run an unknown exe on your Windows machine from a stranger would you? Treat unknown Terminal commands in the Linux the same way. If you don't know what it means, if you aren't sure you need it, if you don't trust the person offering it, then do not run it. "

---

### Post by coffeeaddict22 on 2009-04-14
Hi Baxna,
Your question about what sudo commands there are:
sudo isn't a command in itself.  It's an abbreviation for something like "SuperUser do".  It modifies the permissions a command runs under.
Linux security is built on the user not being able to access system files without explicitly agreeing they need to.  It's really useful for multiuser setups, and also helps PEBKAC (problem exists between keyboard and chair) issues.  To change anything directly involved in the system, you must be logged in as the superuser ( also called "root" or the root account).  So in a terminal, you can type most things without harm to the system, unless the superuser password has been entered.  The terminal asks for the password if you preface a command with sudo; once you enter it correctly, anything goes.

sudo isn't (child- or) idiot- proof.  It won't stop you deleting anything in your home folder, for instance, unless you've set up the files with permissions that stop you doing so.

Some Linux distributions allow you to log in to the superuser account; once you're in, anything you do is done as a superuser. If you want to learn how to reinstall frequently, it's possibly a good way to go...  

For the rest of us, Ubuntu (as a distribution) assumes we'd prefer not to be quite so free to hose the system, and so there isn't an easy way to be logged in as a superuser.  To perform a command that accesses the system files, you preface the command with sudo. Once the command is completed, you are logged out of the root account and back in your usual account.

---

### Post by wookiehangover on 2009-04-14
> **baxna said:**
> Looks like a bunch of messed up smiley faces?

thats why forkbombs are so dangerous--they look innocuous to new users but have devastating consequences. 

further reading: 
[http://en.wikipedia.org/wiki/Fork_bomb]("http://en.wikipedia.org/wiki/Fork_bomb")
[http://www.cyberciti.biz/faq/understanding-bash-fork-bomb/]("http://www.cyberciti.biz/faq/understanding-bash-fork-bomb/")


here's something fun though:
```
telnet towel.blinkenlights.n
```

enter that into the terminal and you'll be treated to an all text presentation of star wars: a new hope

---

### Post by lisati on 2009-04-14
> **baxna said:**
> Looks like a bunch of messed up smiley faces?

It's more dangerous than it looks.

[http://files.fosswire.com/2008/04/ubunturef.pdf](http://files.fosswire.com/2008/04/ubunturef.pdf) makes a good read.

---

### Post by Sorivenul on 2009-04-14
1. Don't follow outdated tutorials. If you come across something you want to do or install and the most recent advice you can find is from 2006, consider asking for specific advice here.

2. Use sudo with caution. It's all well and good to know that malicious commands exist and how to make sure you aren't running one ignorantly. However, sudo accompanied by a typing error can be just as harmful. I've heard too many stories about people deleting all of /var or /etc because of a mistyped * (wildcard).

3. Always check the repositories first before installing from source. Ubuntu (and most Linux systems) provide many ways of doing this (Add/Remove, Synaptic, command-line apt/dpkg). If you don't know what you're doing when installing from source, you could render your system unstable or inoperable.

4. Do backups. Utilities exist for this, and not enough folks do. Whether you back up to the internet, a CD/DVD, or an extra hard drive, it doesn't matter.

5. This should probably be #1, or the list should be unordered:[B]
If you have questions, ask.[/B]

Good luck! And welcome!

---

### Post by lisati on 2009-04-14
<attempt at humour>
Don't want to hose your computer? Then don't take it into the garden!
</attempt at humour>

---

