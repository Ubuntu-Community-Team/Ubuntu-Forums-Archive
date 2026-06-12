---
title: "Where does tracker store its data?"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by Viva on 2009-06-15
Where is the tracker database stored?

---

### Post by MontelEdwards on 2009-07-14
what is the "tracker database"?

---

### Post by Viva on 2009-07-14
> **MontelEdwards said:**
> what is the "tracker database"?

The tracker desktop search stores all its contents in a database. The files are located in ~/.cache/tracker

---

### Post by MontelEdwards on 2009-07-14
oh, ok.
I really dont use the indexing feature, sorry

---

### Post by Stanwilliamsmusic on 2012-04-16
> **MontelEdwards said:**
> what is the "tracker database"?

[B]It Natty  ( 11.04) it is usually  in  
/home/YourUserName/.local/share/tracker/data/[/B]**tracker-store.journal** 

[B]

Inside your home folder  it you press  ctrl-H or click show hidden files.

Inside your Home folder it is or should be:

[SIZE=2].local/share/tracker/data 

[/SIZE][/B]**[SIZE=2].local/share/tracker/data/[/SIZE]****[SIZE=2]tracker-store.journal   [/SIZE]** <-- **full path**

[B][SIZE=2]
[/SIZE][SIZE=1][COLOR=Blue][COLOR=Black]It is a file named[/COLOR] [/COLOR][/SIZE][SIZE=2]      tracker-store.journal
It should be relatively large...

or if it isn't there, search your system for  a file named:  
    [COLOR=Black] [/COLOR][/SIZE][/B][COLOR=Black]**[SIZE=2]tracker-store.journal[/SIZE]**[/COLOR]

**My  tracker-control is no longer  standard issue ;)**

[B]________________________________________________

[SIZE=2]
In the terminal, if you type:      [/SIZE][SIZE=2][COLOR=Blue] [/COLOR][/SIZE][SIZE=2][COLOR=Blue][COLOR=Black]tracker-control --help [/COLOR][/COLOR][/SIZE][SIZE=2][COLOR=Black] [/COLOR][/SIZE][/B][B][SIZE=2]  
  
That should yield the following:[/SIZE]



tracker-control [OPTION...]  - Manage Tracker processes and data[/B]

[B]Help Options:
  -h, --help                       Show help options

Application Options:
  -k, --kill=APPS                  Use SIGKILL to stop all matching processes, either "store", "miners" or "all" may be used, no parameter equals "all"
  -t, --terminate=APPS             Use SIGTERM to stop all matching processes, either "store", "miners" or "all" may be used, no parameter equals "all"
  -r, --hard-reset                 Kill all Tracker processes and remove all databases
  -e, --soft-reset                 Same as --hard-reset but the backup & journal are restored after restart
  -c, --remove-config              Remove all configuration files so they are re-generated on next start
  -s, --start                      Starts miners (which indirectly starts tracker-store too)
  -m, --reindex-mime-type=MIME     Reindex files which match the mime type supplied (for new extractors), use -m MIME1 -m MIME2
  -V, --version                    Print version[/B]



[B]You can search for  ways to disable it if you wish.
 I dislike posting any code on the off chance that someone would inadvertently harm their computer and it would be my fault, as I am not qualified to do so.[/B]

**  On a perhaps somewhat related note: **
 [B]I also  got rid of Zeitgeist on this machine as  I don't particularly like  tracking or record keeping of that type  on principle alone, though I have no really sensitive data on here.

 For more regarding Zeitgeist see:
[/B][http://ubuntuforums.org/showthread.php?t=1773332](http://ubuntuforums.org/showthread.php?t=1773332)

---

