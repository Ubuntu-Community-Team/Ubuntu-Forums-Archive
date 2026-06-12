---
title: "Programs not behaving like they are suppose to, smuxi, firefox. Antivirus &amp; firewall"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by TruePurple on 2011-03-29
With firefox, I can't move the tabs around, other people with firefox and ubuntu can do this and I could do this in firefox under XP.

With smuxi, someone who has the exact same version of ubuntu (10.10 64bit) and smuxi, says they can use tab to autocomplete a chat name, but when I press tab, it just goes to a blank spot in the chat window itself.

I get the feeling both issues somehow involve ubuntu, but I can't be for sure.

*edit in*
Also firefox bookmarks are acting all funky in a manner difficult to describe. I can't assign bookmark pages to folders, and I can't move bookmarked pages into folders. This was also no trouble under XP.

Also, what free antivirus, antimalware, and firewall do you guys recommend for ubuntu? 

I would like something that is also capable of detecting windows viruses,(and maybe maleware too) since I plan to duel boot with win7 eventually, and it would be nice to be able to scan for viruses outside of windows, on behalf of windows (so I can treat ubuntu as a sort of extra safe, save mode)

---

### Post by eriktheblu on 2011-03-29
> **TruePurple said:**
> 
Also, what free antivirus, antimalware, and firewall do you guys recommend for ubuntu? 
None, but if you must Avast or AVG. There is not a whole lot of malware available for Linux currently, and regular updates are sufficiently prophylactic. Clam is available in the repositories, but it's performance is fairly weak.

> I would like something that is also capable of detecting windows viruses,(and maybe maleware too)That's about what you're going to get as the majority of viruses are Windows only.

Can't help with the other issues, but it may be helpful to identify which version of Ubuntu you are using, along with the versions of the other programs. Also, what addons are you using with Firefox?

---

### Post by An Sanct on 2011-03-29
What version of Firefox are you using?

I don't know "smuxi", but it might be that you are missing some setting(?).

For the Antivirus, [you have a few to choose from]("http://crenk.com/best-4-antivirus-software-for-your-ubuntu-os/"): AVG, KlamAV, Avast or F-prot, to name a few...

PS. Some more AVs are here on the [Ubuntu wiki]("https://help.ubuntu.com/community/Antivirus"), with links to the download pages....
PS2. There is also a beta for [Nod32 available for linux]("http://beta.eset.com/linux"), but it is commercial software.

---

### Post by TruePurple on 2011-03-29
Another issue came up, it seems there are certain aspects of the hotmail webpage (like email addresses out of edit mode) that refuse to copy with copy/paste.

> and regular are sufficiently prophylactic.Regular? Huh?

 > it may be helpful to identify which version of Ubuntu you are usingI did.

Firefox version is 3.6.16

Everything I have read, says that the tab thing is default in smuxi.

---

### Post by An Sanct on 2011-03-30
I just downloaded smuxi, to see where the problem might be...

Can you please check this setting, in the menu, click *File* and then *Preferences*, on the left select *Interface* and the *Input* tab, you should see a windows like attached.

Where my mouse pointer is, there is *Bash-Style Completion*, try changing that settings, as it should result in tab being "auto-complete".

PS. About the hotmail thing, if hotmail is made so, that it doesn't allow copying of the email, then that is *intended* to be so, and is the same on any OS.

---

### Post by Mark Phelps on 2011-03-30
> **TruePurple said:**
> I would like something that is also capable of detecting windows viruses,(and maybe maleware too) since I plan to duel boot with win7 eventually, and it would be nice to be able to scan for viruses outside of windows, on behalf of windows (so I can treat ubuntu as a sort of extra safe, save mode)

Actually, doing Windows virus scans and removal outside of Windows is really the best way to do it.

Recommend you go to the Kaspersky website and look for their Rescue CD.  This is a free download.  You burn it to CD, boot from that, and do virus scanning and repair OUTSIDE of Windows.

---

### Post by TruePurple on 2011-03-30
Thank you An Sanct for going through all that effort in trying to help me figure out this problem. 

I went there, I checked "bash style completion" no effect. So unless I need to restart smuxi, (and most programs tell you if that is required) that is not it.

[QUOTE=An Sanc]PS. About the hotmail thing, if hotmail is made so, that it doesn't  allow copying of the email, then that is *intended* to be so, and is the  same on any OS.     [/QUOTE]

Except there is no reason to forbid such copying, and more importantly I can copy the email address etc there just fine under win XP, so it is ubuntu or the ubuntu/linux version of firefox that is at fault.

[QUOTE=Mark Phelps]
Actually, doing Windows virus scans and removal outside of Windows is really the best way to do it[/QUOTE]
Isn't doing in in ubuntu, "outside of windows"?

Are all the antivirus programs named so far, programs that run under ubuntu and scan for both linux and windows viruses at the same time and/or have a setting that enables/disables such?

---

### Post by An Sanct on 2011-03-30
> **TruePurple said:**
> 
Isn't doing in in ubuntu, "outside of windows"?

yes, that is "outside of windows", but slightly slower, then a dedicated scan (IMHO).

> **TruePurple said:**
> 
Are all the antivirus programs named so far, programs that run under ubuntu and scan for both linux and windows viruses at the same time
Yes.

> **TruePurple said:**
>   and/or have a setting that enables/disables such?

I would say **no**, because viruses/malware should be considered OS independent. Thus an AV under Linux has to detect malware/viruses, that don't affect Linux. If that is not so, IMHO its not an AV. 
But you can choose the partition/drive to scan (which more or less separates Windows from Linux)

---

### Post by TruePurple on 2011-03-30
> **An Sanct said:**
> 
I would say **no**, because viruses/malware should be considered OS independent.

How do you figure that, a windows virus/malware can't run on linux and visa versa, are you trying to claim any different?

---

### Post by An Sanct on 2011-03-30
Well, if you open it with wine, it can ... besides, there are also javascript/flash/pdf threats ...

Wine is great :) it also can run malware ;)

PS. If your windows partition is infected with something, there is a 0,00001% chance it will infect the ubuntu partition.

You would have to run it yourself, knowing, what you are doing and 100% ignoring security, then it is possible...

---

### Post by tgm4883 on 2011-03-30
> **An Sanct said:**
> What version of Firefox are you using?

I don't know "smuxi", but it might be that you are missing some setting(?).

For the Antivirus, [you have a few to choose from]("http://crenk.com/best-4-antivirus-software-for-your-ubuntu-os/"): AVG, KlamAV, Avast or F-prot, to name a few...

PS. Some more AVs are here on the [Ubuntu wiki]("https://help.ubuntu.com/community/Antivirus"), with links to the download pages....
PS2. There is also a beta for [Nod32 available for linux]("http://beta.eset.com/linux"), but it is commercial software.

Symantec also has a AV produce "Symantec Antivirus for Linux"

---

### Post by eriktheblu on 2011-03-30
From PM:
> [QUOTE=TruePurple][QUOTE=eriktheblu][QUOTE=TruePurple]In  [this thread]("http://ubuntuforums.org/showthread.php?p=10614156#post10614156"), what did you mean by "regular"? Please answer in the thread.
Regular *updates*. I was typing to fast.[/QUOTE]

You mean regular updates to ubunutu? How do I update ubuntu? It checks by itself automatically if you selected that during installation, right? So I don't need to do anything special to keep ubuntu updated?

Why would keeping ubuntu updated prevent any viruses? Is there a antivirus of some sort embeded into ubuntu?

What about a firewall?[/quote]
Regular updates to Ubuntu, yes. The update manager will download security patches and stability upgrades for all programs for which there are repositories. By default, a notifier will appear in your panel should any updates be available (click, hit the button in the new window, enter password, update).

Antivirus is treatment, where security updates are prevention. If a virus can exploit a security flaw, is it better to remove the virus, or to patch the flaw thereby rendering it impotent?

---

### Post by Perfect Storm on 2011-03-30
The linux anti-virus applications tend to give false positives when scanning your linux systems as they are build to scan Windows stuff.
Just be aware of that.

---

### Post by TruePurple on 2011-03-30
Seems perhaps I should have made two threads, so no one knows what might be going wrong with  the issues of things under ubuntu not working right?

[QUOTE=An Sanct]
Well, if you open it with wine, it can ... besides, there are also javascript/flash/pdf threats ...

Wine is great :smile: it also can run malware[/QUOTE]

But such infections can not escape the confines of said program, right?(unless also programmed to run under linux)

[QUOTE=An Sanct]You would have to run it yourself...[/QUOTE]
Run what yourself?

[QUOTE=An Sanct]
[quote=truepurple] have a setting that enables/disables [scanning for linux or windows viruses]?[/quote]
]I would say **no**, because viruses/malware should be considered OS  independent. Thus an AV under Linux has to detect malware/viruses, that  don't affect Linux. If that is not so, IMHO its not an AV. [/QUOTE]
Does a windows antvirus that doesn't scan for linux type viruses, any less of a antivirus for it?

A option to disable scanning for that which isn't a worry, (like windows viruses when its a program meant to run only in linux) would help save time scanning, since the larger the database to check against, the longer such scans take AFAIK. Do you know of any of them with such a feature?

[quote=eriktheblu]Antivirus is treatment, where security updates are prevention. If a  virus can exploit a security flaw, is it better to remove the virus, or  to patch the flaw thereby rendering it impotent?     [/quote]

A virus is a program designed to do something undesired and usually destructive to a persons computer. I suppose if a OS was absolutely perfect with it's security, a virus could do nothing, are you claiming that of ubuntu? If so, got any kind of proof/from what background or whatever do you come to this conclusion?

It seems to me one would want both good OS security and good virus protection. 

Does anyone else feel that antivirus and antimalware are pointless on a up to date ubuntu computer?

[QUOTE=       Artificial Intelligence]The linux anti-virus applications tend to give false positives when  scanning your linux systems as they are build to scan Windows stuff.[/QUOTE]

Well, which ones are designed to run on linux, rather then it being a afterthought?

[QUOTE=tgm4883]Symantec also has a AV produce "Symantec Antivirus for Linux"[/QUOTE]

Is that free? Is that designed to run on Linux? Or is it the kind of program Artificial Intelligence was talking about?

---

### Post by tgm4883 on 2011-03-30
> **Artificial Intelligence said:**
> The linux anti-virus applications tend to give false positives when scanning your linux systems as they are build to scan Windows stuff.
Just be aware of that.

Just because it detects a Windows file on Linux a threat doesn't make it a false positive. The file is still a threat, it is just located on a system that cannot run it.

> **TruePurple said:**
> Is that free? Is that designed to run on Linux? Or is it the kind of program Artificial Intelligence was talking about?

Not free. It is designed to run on Linux (I thought that was obvious by it's name as well as what I was responding to). Not sure what you mean by the last part, please see my above reply.

---

### Post by Perfect Storm on 2011-03-30
> Just because it detects a Windows file on Linux a threat doesn't make it a false positive. The file is still a threat, it is just located on a system that cannot run it.

That was not what I meant. The false positives comes when you're scanning your Linux systems and it reports linux files as infected.
I'll just make him aware of that, so he don't freak out ;)

---

### Post by eriktheblu on 2011-03-30
> **TruePurple said:**
> 
A virus is a program designed to do something undesired and usually destructive to a persons computer. I suppose if a OS was absolutely perfect with it's security, a virus could do nothing, are you claiming that of ubuntu?Not at all. Security patches are distributed all the time, which is testimony to the fact that there vulnerabilities. These flaws are often fixed shortly after they are discovered by the community. Security flaws in Windows are often not recognized (officially), delayed in reporting, and slow to be fixed; a current antivirus is more practical in this model.

> If so, got any kind of proof/from what background or whatever do you come to this conclusion?
Personal experience only:
Windows + no antivirus + user stupidity = malware
Windows + antivirus = little malware
Ubuntu + no antivirus = no malware

> It seems to me one would want both good OS security and good virus protection.Go for it. The benefit is more for Windows, but that doesn't mean it's not worthwhile.

> Does anyone else feel that antivirus and antimalware are pointless on a up to date ubuntu computer?Not pointless, just of significantly less value than on a Windows machine.

It's entirely up to you what your resources (time, money, system processing) are worth.

---

### Post by TruePurple on 2011-03-31
> **Artificial Intelligence said:**
> That was not what I meant. The false positives comes when you're scanning your Linux systems and it reports linux files as infected.
I'll just make him aware of that, so he don't freak out ;)

So which ones don't give such false positives? Any of those free? Any of those have a option on whether you want to scan for for either or both linux/windows infections?

---

### Post by Perfect Storm on 2011-03-31
The best way would be looking up the name of the virus then. There's a lot of anti-virus lists which explain what kind of virus it is etc. So if it's an Windows virus it have detected on a Linux file, you'll know it's false positive.

But the best defense on Linux/Ubuntu:
1) Strong Password
2) Use the official or trusted packages
3) Update regularly 
4) Clean the browser once in awhile

---

### Post by TruePurple on 2011-03-31
What do you mean by clean the browser? You mean delete cache? Not a good idea as flash games save game progress in cache, and I don't see how that would help me be more secure anyway.

Numbers 2 and 3, with autoupdate, won't both of them be covered?  Autoupdate will tell me if there is anything new, and I would assume it would only download official/trusted packages. If you mean other programs, I might add, how would I know if they are official and trusted or not?

So AI, you don't think I need antivirus/antimalware either? Would you please answer those questions I asked about this in my last post anyway?

---

### Post by Perfect Storm on 2011-03-31
No, it's not needed. Only if you're running a server that communicates with Windows machines to protect them.

A virus is a malicious code that can replicate itself and spread automatically. To do this on Linux you have to set the Virus to be executable and you then have to execute the virus yourself. Furthermore if you want it to spread it systemwide you also need to execute it as superuser. That's why virus have very very poor conditions in a Linux System.

That's why I said previously; If you keep the 4 advise 'strong Password' etc. etc. then you are protected as good as you can.


> What do you mean by clean the browser? You mean delete cache?
Yes. And it's a good idea regardless which OS you use to get rid of data-mining, spyware etc. there's a few that are crossplatform but harmless. Other than that a lot of info, data etc. is gathering up and can have an impact of your browsers performance.

---

### Post by TruePurple on 2011-03-31
Numbers 2 and 3, with autoupdate, won't both of them be covered?   Autoupdate will tell me if there is anything new, and I would assume it  would only download official/trusted packages. If you mean other  programs, I might add, how would I know if they are official and trusted  or not?

Regarding clearing cache, how do I do that without losing saves?

---

### Post by Perfect Storm on 2011-03-31
Yes, Ubuntu will tell you when new packages are available, just make sure to install them when they are ;)

Ubuntu official repositories are enable by default, you can also enable Ubuntu Partners which also are safe.

outside packages and PPA's can be more trickier if you really need something that isn't in Ubuntu Software Center. But popular, well known sites are trustworthy and if you go to get something outside Ubuntu Software Center it should be those sites to check first.

eg.
[http://www.playdeb.net/welcome/](http://www.playdeb.net/welcome/)
[http://medibuntu.org/](http://medibuntu.org/)

When we talk by untrusted sites, I'm talking about a package you find on some obscure place or someone random person says/posted/uploaded; use this package, it do this and that. Such things you should be aware off.

---

### Post by TruePurple on 2011-03-31
Again I ask, how can I clear cache without deleting saves?

---

### Post by yeats on 2011-03-31
> **TruePurple said:**
> Again I ask, how can I clear cache without deleting saves?

Flash has its own cache, which can be managed here:

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html)

Deleting the browser cache should not affect flash programs.

---

### Post by TruePurple on 2011-04-02
One thing that came up is that what I have installed is vim-light, not vim-full, and vim light is much easier to use I am told.

I was told to use this command to get vim-full installed sudo apt-get install vim

But when I used it I got the following message

"WARNING: The following packages cannot be authenticated!
  vim-runtime vim
Install these packages without verification?"

Should I ignore this warning? Or is this one of the untrusted packages? If so, how do I get vim full?

 [http://www.gentoo.org/doc/en/vi-guide.xml](http://www.gentoo.org/doc/en/vi-guide.xml)

---

### Post by Perfect Storm on 2011-04-02
Try use nano instead if you want to use a CLI text editor, it's much easier to use if you're new.

---

### Post by TruePurple on 2011-04-02
Well I was told nano was more complicated, but either way, if I am going to have vim on this PC, I might as well have the better one. And someone might give me instructions that use Vim. Plus the question of what to trust in itself is important. So would you please answer my previous post anyway?

Furthermore, How do I get nano?

---

### Post by Perfect Storm on 2011-04-02
It's installed on Ubuntu by default.

Simple:
```
nano /path/file.name
```

or if you're going to edit some system files (outside your home directory);
```
sudo nano /path/file.name
```

---

### Post by TruePurple on 2011-04-02
> **TruePurple said:**
> One thing that came up is that what I have installed is vim-light, not vim-full, and vim light is much easier to use I am told.

I was told to use this command to get vim-full installed sudo apt-get install vim

But when I used it I got the following message

"WARNING: The following packages cannot be authenticated!
  vim-runtime vim
Install these packages without verification?"

Should I ignore this warning? Or is this one of the untrusted packages? If so, how do I get vim full?

 [http://www.gentoo.org/doc/en/vi-guide.xml](http://www.gentoo.org/doc/en/vi-guide.xml)

So what do you think of this issue?

P.S. Please pretend there is no such thing as "nano" for the moment.

---

### Post by Perfect Storm on 2011-04-02
Just ignore the error and say yes.


Have you added or edited your sourcelist?

---

### Post by TruePurple on 2011-04-02
I don't know.

---

### Post by TruePurple on 2011-04-03
Why do you ask AI? Something I should know?

---

### Post by Perfect Storm on 2011-04-03
I was just wondering why vim-runtime vim was not authenticated as the packages are from the official Ubuntu repositories.

---

