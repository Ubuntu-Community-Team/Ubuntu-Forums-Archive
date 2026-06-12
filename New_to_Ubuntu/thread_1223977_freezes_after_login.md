---
title: "freezes after login"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by snitchard on 2009-07-26
Hello,
 
I installed Ubuntu using WUBI.exe about 3 days ago and all was going well and I was enjoying myself and then this morning I decided to use a different e-mail program so I uninstalled Evolution and everything that was associated with it and I must have accidentally uninstalled something important because after I rebooted I got the login screen and after I'm logged in I get a black screen and that's it the system just sits there.
 
So, I went into recovery mode and did everything in there and I noticed when I try to fix the 63 broken packages nothing happens, none of them download or install.  I wonder if they were to get fixed if that would solve my problem???
 
I'm a Windows user and was curious about Linux so that is why I used WUBI.exe to install Ubuntu.  I, unfortunately, don't think I'd ever be able to switch completely over to Ubuntu because I can only do a few tasks in Ubuntu that I can also do in Windows.  All of my other task have to be done in Windows or so it would seem and that is disappointing.  I do enjoy using Ubuntu but I think I'll check my e-mail "remotely" from Ubuntu meaning instead of using an e-mail client I'll just use a web based POP3 e-mail checking program.
 
Anyway, any help you can give me would be greatly appreciated.
 
Thanks

---

### Post by c0mput3r_n3rD on 2009-07-26
Boot into a root shell (in options at startup) and type:
```

sudo apt-get install upgrade

```And see if that fixes the dependencies that are missing.

EDIT: By the way, if you didn't want to Evolution you should have just ran:
```

sudo apt-get remove evolution

```

And what tasks do you not know how to do in Ubuntu that you can in Winblows?

---

### Post by snitchard on 2009-07-26
Hello,
 
Thanks for your reply.  I tried the commands you suggested and they did not work.  I'm honestly afraid of the command line so is there a way to uninstall programs from within the Ubuntu GUI?  I'm a computer tech and I know command lines in general are powerful tools, which is why I'm probably afraid of them.
 
As far as tasks go I'd be able to fully switch if I could find an office suite that has equivalents for M.S. Word, Excel, Power Point, Outlook, and Publisher as well as a general image editing program that can straighten, brighten, and sharpen my pictures but that is also user friendly.  I have this program that came with my Epson scanner that does all those things and my Epson copy utility would have to be duplicated my a Ubuntu program.  Also the features in Roxio's Easy Media creator for video editing.
 
Other than those high end things I just use my computer for web surfing and e-mail.
 
Any other suggestion?  I'd like to get it all back since it took me 3 days to get to where I was.
 
Thanks

---

### Post by zeroseven0183 on 2009-07-27
> **snitchard said:**
> Hello,
 
Thanks for your reply.  I tried the commands you suggested and they did not work.  I'm honestly afraid of the command line so is there a way to uninstall programs from within the Ubuntu GUI?  I'm a computer tech and I know command lines in general are powerful tools, which is why I'm probably afraid of them.
 
As far as tasks go I'd be able to fully switch if I could find an office suite that has equivalents for M.S. Word, Excel, Power Point, Outlook, and Publisher as well as a general image editing program that can straighten, brighten, and sharpen my pictures but that is also user friendly.  I have this program that came with my Epson scanner that does all those things and my Epson copy utility would have to be duplicated my a Ubuntu program.  Also the features in Roxio's Easy Media creator for video editing.
 
Other than those high end things I just use my computer for web surfing and e-mail.
 
Any other suggestion?  I'd like to get it all back since it took me 3 days to get to where I was.
 
Thanks


If you want a GUI for installing/uninstalling applications, access the Synaptic Package Manager via System > Administration.

Ubuntu has a pre-installed office suite in it, OpenOffice.org found in Applications > Office. It has an equivalent word processor, spreadsheet and presentation applications.

You'll do good with Evolution as your e-mail client. However, what's the problem all about again? And by the way, how did you uninstall it?

You can find almost everything you need in the repositories. You can also check out the equivalent software list here: [Linux software equivalent to Windows software]("http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software") or [Table of Equivalent Software]("http://www.libervis.com/wiki/index.php?title=Table_of_Equivalent_Software")

---

### Post by snitchard on 2009-07-27
Hello,

Thanks again for your reply.  I found a command dpkg --configure -a and tired it then tried thesudo apt-get install upgrade.  The computer did a lot of things, which looked promising.  I rebooted and everything was back to normal.  I had to use Synapic to uninstall Evolution and I learned to look at the dependences when uninstalling software and if it has anything to do with Ubuntu I leave it alone.

I'm conflicted as to whether I want to use Evolution or Thunderbird as my e-mail client.  Thunderbird is closer to M.S. Outlook Express but there are some annoyances I'll have to work around and live with.

I have been doing some research and the only thing that is going to be a pain is my video editing and Light scribe label making.  I looked into Lacie 4L but following the directions from a website I found doesn't work.  Everything in the software is grayed out and the software is not usable.  I wish Linux could just be point and click but I guess that is why it is free.  Even though I'm very experienced in Windows and fixing computers Linux is a whole new scary world.  Will I ever feel comfortable and confident???

Any suggestions or opinions are greatly appreciated.

Thanks

---

