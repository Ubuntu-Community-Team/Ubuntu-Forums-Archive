---
title: "rhythmbox through crontab"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by trikster_x on 2009-09-19
I am attempting to set up a simple alarm program using crontab and a couple extremely simple shell scripts to open rhythmbox and start playing files.  The problem I have is that when it comes time for crontab to do it's thing, nothing happens.  I have both scripts set up to output to a seperate log files.  The first script is simply the command "rhythmbox" to get rhythmbox to open.  When that tries to run, I get the error :

[CODE]cannot open display: 
Run 'rhythmbox --help' to see a full list of available command line options.[CODE]

The second script command is "rhythmbox-client --play-pause".  I have tried to get this to run through crontab with rhythmbox already open, but nothing happens.  I know both of the scripts work, so my question is why crontab can't run them?  It runs the other scripts I have made just fine.

---

### Post by KIAaze on 2009-09-19
This just worked for me:
```

XAUTHORITY=~/.Xauthority
DISPLAY=:0.0
58 19 * * * rhythmbox
59 19 * * * rhythmbox-client --play-pause

```

Here's more info if you want to use GUI apps through the root crontab:
[http://ubuntuforums.org/showthread.php?t=563687](http://ubuntuforums.org/showthread.php?t=563687) (note 3)
[http://ubuntuforums.org/showthread.php?t=1076486](http://ubuntuforums.org/showthread.php?t=1076486)
Related:
[http://www.faqs.org/docs/Linux-mini/Remote-X-Apps.html](http://www.faqs.org/docs/Linux-mini/Remote-X-Apps.html)
[http://ubuntuforums.org/showthread.php?t=699332](http://ubuntuforums.org/showthread.php?t=699332)

---

### Post by trikster_x on 2009-09-19
Thanks!  That did the trick.

---

