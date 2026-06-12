---
title: "Crontab issue"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by spikoley on 2009-12-16
I am setting up a cron job and having an issue with the editor.  When I ran cron -e it ask what editor I wanted to use.  I selected 1.  After setting up the cron job I do not know how to exit.  How can I switch the editor to vim?  It doesn't give me the option to change the editor again.  This is on a Karmic Koala server.

---

### Post by spikoley on 2009-12-16
I found the answer in this [thread]("http://ubuntuforums.org/showthread.php?t=256778").

Solution 1:

> Type

export EDITOR=vim

in your terminal and append that line to your /home/YourUserName/.bashrc

Solution 2:

> Or, for a system-wide change, run "sudo update-alternatives --config editor" and pick vim.

---

