---
title: "Computer Janitor doesn't work, any alternative?"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by eilhart on 2011-03-15
Well, I'll uninstall it if I find an alternative. Any suggestions?

---

### Post by beew on 2011-03-15
Install bleachbit from the repo.

---

### Post by eilhart on 2011-03-15
> **beew said:**
> Install bleachbit from the repo.
Thanks. I'll try that.

---

### Post by 5149.5 on 2011-03-15
I like Ubuntu Tweak.

---

### Post by migrate from windows on 2011-03-15
I use Bleachbit as well as [COLOR=black]_ubuntu Tweak. _[/COLOR]The latter makes kernel removals, purging PPAs very easy.

---

### Post by eilhart on 2011-03-16
I installed Bleachbit and ran it as root. I wanted to clean Recent files when you enter Files and Folders. I checked document history but it didn't do that. There are also APT; clean, autoclean and autoremove options which I didn't try because I kinda got scared if they delete something important.
 
I'll try Ubuntu Tweak when I get home. Gotta head out for school. Thanks for all the replies.

---

### Post by beew on 2011-03-16
> **eilhart said:**
> I installed Bleachbit and ran it as root. I wanted to clean Recent files when you enter Files and Folders. I checked document history but it didn't do that. There are also APT; clean, autoclean and autoremove options which I didn't try because I kinda got scared if they delete something important.
 
I'll try Ubuntu Tweak when I get home. Gotta head out for school. Thanks for all the replies.

You can run bleachbit as root or as an ordinary user (there are two launchers). Since the document history belongs to the ordinary user, root doesn't change or erase it, you have to run bleachbit NOT as root (use the other launcher)

You run bleachbit as root to clean things that pertain to the whole system such as apt, while you run it as an ordinary user for things in your home directory (things like firefox cache, document history etc)

Ubuntu tweak is good too. Though purge ppa sometimes doesn't work. There is a command line tool that do that and you can install it from  the repo (just search for ppa. I don't remember whether it is called ppa-purge or purge-ppa :))

---

### Post by eilhart on 2011-03-16
I tried running regular Bleachbit too. It removed a file something like recent.xbl but I could see the recent files still. I restarted to be sure. They're still there.
 
Btw, sorry for being a complete noob but there is no Ubuntu Tweak in Ubuntu Software Center. I did a search in it. Nothing came up. Do you mean terminal by repository?
 
I also searched it in Synaptic Package Manager. Nada. Zip.

---

### Post by beew on 2011-03-16
> **eilhart said:**
> I tried running regular Bleachbit too. It removed a file something like recent.xbl but I could see the recent files still. I restarted to be sure. They're still there.
 
Btw, sorry for being a complete noob but there is no Ubuntu Tweak in Ubuntu Software Center. I did a search in it. Nothing came up. Do you mean terminal by repository?

When you run bleachbit the first time, you have to check the boxes for which files you want to erase. Did you check the box that says "recent documents" ?(for the non root launcher)

Also, I forgot to ask you which version of Ubuntu you are using. If it is 10.04 then the version of bleachbit is out of date, that one indeed didn't remove recent documents (this has  been fixed for a long time but the new versions didn't make it to the Ubuntu repo. so don't use LTS unless you use a lot of PPAs  If you only use Ubuntu's repo all the softwares have not had feature updates for a year ;)) If that is the case you should download a .deb file from bleachbit's website and install it (with a simple right click)

Ubuntu tweak is not in the Ubuntu repo, you can install it by adding its ppa to your sources list.  Open System > Administration > Synaptic Package Manager. Click on Settings > Other Software and then add and enter this in the box.
> **[B]ppa:tualatrix/pp**a[/B] Then close the dialogue box and click "reload" and you will find Ubuntu tweak in Synaptic and you can install, upgrade and remove it like other programs in the official repo.

---

### Post by eilhart on 2011-03-17
> **beew said:**
> When you run bleachbit the first time, you have to check the boxes for which files you want to erase. Did you check the box that says "recent documents" ?(for the non root launcher)
Yes, I did for the non root launcher. I'm using 10.10. I uninstalled Bleachbit and went to its home page. I downloaded it and opened it with Ubuntu Software Center. I think USC is using Synaptic Package Manager only it is more user friendly because when USC opened newly downloaded Bleachbit it said "there is an older version of this software in your system's repositories. install this only if you trust the source." Anyway, I installed it run the tool and checked several things under the system drop-down which I thought could be useful beside recent document history. Still no luck.  

I opened Synaptic for Ubuntu Tweak, though under settings there isn't "other software" option. There are Preferences, Repositories, Filters, Set Internal Option..., and Toolbar options. I tried all of them. Repositories->Other Software->Add Volume was the closest to your definition but when I did that it asked for a cd. I installed it through it's homepage again opened it with USC, it suggested that I enable Ubuntu Tweak in my repository, I accepted. Although I couldn't find an option to delete recent document history, I find it a very useful software.

---

### Post by beew on 2011-03-17
> **eilhart said:**
> Yes, I did for the non root launcher. I'm using 10.10. I uninstalled Bleachbit and went to its home page. I downloaded it and opened it with Ubuntu Software Center. I think USC is using Synaptic Package Manager only it is more user friendly because when USC opened newly downloaded Bleachbit it said "there is an older version of this software in your system's repositories. install this only if you trust the source." Anyway, I installed it run the tool and checked several things under the system drop-down which I thought could be useful beside recent document history. Still no luck.  

I opened Synaptic for Ubuntu Tweak, though under settings there isn't "other software" option. There are Preferences, Repositories, Filters, Set Internal Option..., and Toolbar options. I tried all of them. Repositories->Other Software->Add Volume was the closest to your definition but when I did that it asked for a cd. I installed it through it's homepage again opened it with USC, it suggested that I enable Ubuntu Tweak in my repository, I accepted. Although I couldn't find an option to delete recent document history, I find it a very useful software.

Which Ubuntu release are you running. I use bleachbit in  10.10 (from repo) and 10.04 (from website) and both clean recent documents fine (version 0.8 +)

To see the  "other software" tab you have to go to Settings > Repositories. Sorry for the mistake.

Synaptic is actually much better than the Software Center, way more flexible and a lot more options, it is also faster.  I don't use the SC.

---

### Post by eilhart on 2011-03-17
In my previous post, I told that I was using 10.10. Also, netbook remix version.

---

### Post by eilhart on 2011-03-18
Yesterday, I opened my session with Ubuntu Desktop Edition to check if recent document history was deleted there and it was deleted. I logged out and logged in to Ubuntu Netbook Edition from the side bar launcher I clicked "Files and Folders" and there it was again under "Recent" all the documents I've opened before. I guess deleting recent document history doesn't work for netbook edition yet. It's probably stored somewhere different than it is in desktop edition.
 
Btw, desktop edition is much easier to use than netbook edition I must say. The desktop is actually usable and there are menus at the top left unlike netbook edition.

---

