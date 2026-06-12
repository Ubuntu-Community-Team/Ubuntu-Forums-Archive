---
title: "Proper Backup Strategy Needed"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2011-01-20
I have just upgraded to 10.04 LTS and have a separate /HOME partition and all that good stuff. I have Simple Backup scheduled to do periodic backups of my /Home folder and /etc.

What is a good way to save all my program data NOT in the /HOME folder? Specifically programs I have downloaded through apt-get or Synaptic Pkg Mgr? Or is there a way to save a file that could go back out and re-download all these apps after I did a restore?

I just want to cover my bases now that everything is square and working right. If I'm leaving anything out please let me know OR if there is a good tutorial that answers these questions direct me to that area of the forums.

Thanks,

An Ole Fart Coming Up to Speed

P.S. Saving all my config data on browsers is a concern as well.
Do you just save the appropriate folder that has the browser run files in it or would everything be in the /HOME folder?

---

### Post by ajgreeny on 2011-01-20
For your downloaded packages backup **/var/cache/apt/archives**, or you can try aptoncd, which does the same thing for you, but makes an iso file of all packages, which you can either keep as an iso, or burn to CD.  I never bothered with the CD, I just used the iso file when I needed to restore packages to the cache.

As fort all your browser data, bookmarks, email addresses, etc etc, they are all in hidden folders in your /home partition, eg ~/.mozilla for firefox and ~/.thunderbird for thunderbird.  To see them hit Ctrl+H in nautilus.

I don't use simple backup, (g)rsync is my tool, and I have no idea if it backs up hidden files & folders by default, so check that and make sure you do have them included.  Incidentally I have never bothered with /etc, though I know some users do it as the normal.

---

### Post by gordintoronto on 2011-01-20
Remastersys lets you create an ISO which includes all your programs.

Most programs save their configuration details in a hidden folder in /home, such as .nautilus and you can set nautilus to show hidden folders.

---

### Post by gordintoronto on 2011-01-20
Remastersys lets you create an ISO which includes all your programs.

Most programs save their configuration details in a hidden folder in /home, such as .nautilus and you can set nautilus to show hidden folders.

---

