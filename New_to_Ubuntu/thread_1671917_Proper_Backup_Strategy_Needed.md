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

### Post by Zill on 2011-01-20
> **ozark_hillbilly said:**
> I have just upgraded to 10.04 LTS and have a separate /HOME partition and all that good stuff. I have Simple Backup scheduled to do periodic backups of my /Home folder and /etc.
Excellent :-)
> **ozark_hillbilly said:**
> What is a good way to save all my program data NOT in the /HOME folder? Specifically programs I have downloaded through apt-get or Synaptic Pkg Mgr? Or is there a way to save a file that could go back out and re-download all these apps after I did a restore?
Post [#3]("http://ubuntuforums.org/showpost.php?p=5978600&postcount=3") in thread entitled["Existing Installed Applications When Reinstalling the OS?"]("http://ubuntuforums.org/showthread.php?p=5978600") may help...
> **ozark_hillbilly said:**
> P.S. Saving all my config data on browsers is a concern as well.
Do you just save the appropriate folder that has the browser run files in it or would everything be in the /HOME folder?
Browser data should be in hidden (dot) directories within your /home/username directory. eg.
```
~/.mozilla
```
Simple Backup generally saves these directories by default unless you have specifically excluded them.

---

### Post by ozark_hillbilly on 2011-01-20
Thanks Zill!

With your four posts I definitely got it. You runnin' that bean counter up or something?  

:^ )

---

### Post by Zill on 2011-01-20
> **ozark_hillbilly said:**
> Thanks Zill!

With your four posts I definitely got it. You runnin' that bean counter up or something?
Sorry about that - the forums seem to be quite flaky at the moment.  My post did not appear to have been accepted and so I tried re-sending with the same result - unfortunately, four identical posts then appeared later :-(

Computers! - don't ya just love 'em? ;-)

---

