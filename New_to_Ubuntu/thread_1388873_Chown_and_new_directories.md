---
title: "Chown and new directories"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by lawfultoad on 2010-01-23
Hello,
I have a directory with several sub-directories. I did a chown -R to ensure I'm the owner of everything. However, I have a process running under sudo that occasionally makes directories. These new directories are not accessible until I run chown again. 
 
I can guess that because I'm running the process using sudo that that is what is causing this problem. I'm just not sure how to work around it while letting the process run with sudo.
 
Is there a way to allow me to avoid having to constantly re-chown the parent directory to make the sub-directories accessible?
 
Thanks!

---

### Post by gnometorule on 2010-01-23
I'm a bit confused. You say that you have a 'process' running, which would imply you do some advanced scripting. If yes, all you need to do is add to the code, right after it creates a new directory, the command to chown it to what you would like it to be. If it's a 'process' (??) that you have no real control over or understanding of, but it creates, as the ROOT user, subdirectories (occasionally?), then I find that sorta fishy.

---

### Post by lawfultoad on 2010-01-23
It's just a hellanzb daemon.  It runs as sudo, if I chown -R the directory it downloads to and then it processes a file the directory it creates is inaccessible until I chown again.

---

### Post by gnometorule on 2010-01-23
Here's my suggestion: repost with subject 'question for hellanz users' or something like that, referring directly to hellanz.

I checked a sample config file for the application/daemon which you can google. It's written in python, which I don't speak, but it didn't seem to have a quick and easy way to address your need. Yes, if you run under root, directories created will be root absent further meddling through a script, or manually, after. So your best hope is that this can be configured from within the application, which another user might be familiar with.

---

