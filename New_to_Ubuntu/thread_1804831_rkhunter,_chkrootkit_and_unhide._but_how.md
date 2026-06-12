---
title: "rkhunter, chkrootkit and unhide. but how?"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by Guy Secretan on 2011-07-15
i realise this makes me look like a clueless idiot but...

I've downloaded rkhunter, chkrootkit and unhide from the repository but i can't work out how i'm meant to run them.

i've been to their websites but it just reads like gibberish to me. i know i have to use the terminal but what exactly am i meant type? 

big cheers in advance for any help.

---

### Post by nomko on 2011-07-15
don't know about unhide, but the other 2 are command line programs. open a terminal and type in rkhunter or chkrootkit and press enter. you might get some feedback telling to run the program as root (if so, type sudo before rkhunter or chkrootkit) or you need to add some options.

---

### Post by Guy Secretan on 2011-07-15
big thanks but still really puzzled. everytime i type in a command, eg check, it says that no such command exists.

---

### Post by Guy Secretan on 2011-07-15
re rkhunter, it says when i open it in the terminal...

Current options are:
         --append-log                  Append to the logfile, do not overwrite
         --bindir <directory>...       Use the specified command directories
     -c, --check                       Check the local system
  --cs2, --color-set2                  Use the second color set for output
         --configfile <file>           Use the specified configuration file
         --cronjob                     Run as a cron job
                                       (implies -c, --sk and --nocolors options)
         --dbdir <directory>           Use the specified database directory
         --debug                       Debug mode
                                       (Do not use unless asked to do so)
         --disable <test>[,<test>...]

and a load more options.

anyway to get it to check for rootkits, i want the check option. but whatever i type it says its a bad command or something.

what should i type? i am assuming the answer is really obvious and i will look a moron but that's a price i'm prepared to pay...

---

### Post by alphacrucis2 on 2011-07-15
> **Guy Secretan said:**
> re rkhunter, it says when i open it in the terminal...

Current options are:
         --append-log                  Append to the logfile, do not overwrite
         --bindir <directory>...       Use the specified command directories
     -c, --check                       Check the local system
  --cs2, --color-set2                  Use the second color set for output
         --configfile <file>           Use the specified configuration file
         --cronjob                     Run as a cron job
                                       (implies -c, --sk and --nocolors options)
         --dbdir <directory>           Use the specified database directory
         --debug                       Debug mode
                                       (Do not use unless asked to do so)
         --disable <test>[,<test>...]

and a load more options.

anyway to get it to check for rootkits, i want the check option. but whatever i type it says its a bad command or something.

what should i type? i am assuming the answer is really obvious and i will look a moron but that's a price i'm prepared to pay...

```
chkrootkit -c
```

or

```
chkrootkit --check
```


From what I read above.

---

### Post by Guy Secretan on 2011-07-15
> **alphacrucis2 said:**
> ```
chkrootkit -c
```or

```
chkrootkit --check
```From what I read above.

thanks indeed. through trial and error i just stumbled on that. 

big thanks!

---

