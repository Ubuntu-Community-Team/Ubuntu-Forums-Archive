---
title: "Which folders to copy? (new computer and upgrade)"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by hman469 on 2010-03-10
I have a new computer running 9.10 64 bit and I want to pull all my settings and files from my old computer running 8.04 32 bit, with out causing any problems with conflicting settings between the 32 and 64 bit systems.  I don't mind installing my applications and programs I want, but I was hoping to be able to save all my settings and such.  I have already copied my /home folder to an external hard drive, what else should I do?

Any help will be highly appreciated!  Thanks

---

### Post by diablo75 on 2010-03-10
It's best to come up with a list of the essential things you want.  Given that you've already made a copy of your home folder, it's safe to say "it's all in there", as far as personal settings and preferences go.  But I can't say whether or not you will encounter a compatability issue as things might be slightly different between versions of the software you used to use.  For example, pulse audio stores it's preferences in the home folder, and it would be better to leave the new version alone and not accidentally replace it with the old one.  So what I would do if I were you is go through your old home folder and look for things that seem familiar that you know you need/want and avoid the non-essential things or stuff you don't recognize.

My personal preference is to copy the old .mozilla folder into my new home folder, and tell it to Merge the contents when prompted.  Firefox will auto-import everything the next time you start it.  This includes bookmarks, stored passwords, history, shortcuts, bookmarks, etc.

A lot of programs that store settings in the home folder work in much the same way, but that doesn't mean it's the best way.  Evolution, for example, will let you merge your old .evolution folder like you do above for Firefox but it's better to do a backup from evolution so it exports everything out into one tar.gz file that you can import with the new evolution on the other system.

---

