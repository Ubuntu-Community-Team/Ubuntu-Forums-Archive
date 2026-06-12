---
title: "using /dev/null"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by kaykav on 2010-10-22
hi again,
           I posted a question 5 mins ago. Cannot find it. so Ill post again.
             Being in /var/log diectory, I entered:
              less messages >/dev/null 2>&1    to dump all the messages. It did not work.  What could be wrong?     Thanks

---

### Post by JKyleOKC on 2010-10-22
Did you want to read the file, or to remove all its content?

The "less" program is a pager, to let you view the file's content one page at a time and scroll through it. There's no need at all to redirect its output anywhere.

Your "did not work" could mean lots of different things; you need to be much more specific about what you expected to happen, and what actually did happen. Only then will anyone be able to provide answers for you; without such detail, we can only guess...

If your intent was to remove all the content, you would probably have to reboot from a live CD so that the system did not have the file open before you could do so. You would also have to use "sudo" since your normal user account only has read permission to the log files and is not allowed to write to them. In any event redirecting output to /dev/null would not have any effect on the file content; it would only suppress all output from the file!

If the problem is that you did not see any output from the command, that would be because it did exactly what you told it to do: suppress all output.

---

### Post by kaykav on 2010-10-22
I wanted to remove all the messages from /var/log using /dev/null.
     I thought I could do that by creating an output using 'less'
then redirecting it to the 'null'file.  What did you mean rebooting with a cd?

---

### Post by ibuclaw on 2010-10-22
> **kaykav said:**
> I wanted to remove all the messages from /var/log using /dev/null.
     I thought I could do that by creating an output using 'less'
then redirecting it to the 'null'file.  What did you mean rebooting with a cd?

less reads files, not write to them.

To clear a contents of a file via command-line, you'd run:
```
>| /var/log/messages
```
Notice that the file that you want to write to is on the **right-hand side** of the file redirection operator ">", and not the left.

Regards
Iain

---

### Post by JKyleOKC on 2010-10-22
However, only user "syslog" (and of course root) has permission to write to the /var/log/messages file, and in addition only one process is permitted to have a file open for write actions at any specific time. Since the syslog driver keeps all of its files open for almost the entire time the system is running, trying to do a redirection to it will simply give a "permission denied" error.

To clear the file, you would have to shut down the system, then boot it from the Live CD or USB stick that you used to do the original install, selecting the "try without installing" option from its menu. This will load a separate copy of all the system files, allowing you to modify the set on your hard disk. Then you would have to become the root user, since redirection does not work as expected with "sudo", mount the original /var/log filesystem as an external folder, and only then would you be able to modify the content of /var/log/messages.

The "logrotate" utility that runs behind the scenes will move the current content of the file over to a backup copy, automatically. This normally happens once a week. The copy will be named "messages.1" in the /var/log directory. The previous messages.1 gets compressed to become messages.2.gz, and so on up to 5 weeks of backup copies in my case (which I think is probably the default setting). If you're running short of space, you can delete these backup copies without all the fuss: just do "sudo rm /var/log/messages.1" from a terminal window, followed by "sudo rm /var/log/messages.*.gz" to scrub out the compressed copies.

It's never a good idea to try to remove the current log files, since they are the primary means you have to find out what went wrong if your system crashes for any reason -- and also because absence of current logs is a strong indicator that your system has been invaded by a baddie, which can and does happen even with Linux (just not as often or as easily as with other systems). Clearing out the backup copies, however, is okay if you need the space.

You can also edit the logrotate files, in /etc, to change the interval at which cleanup occurs, and the number of backups to retain. However before changing things in /etc it's best to ask here, since you can easily make a system unusable by changing the wrong things there. It's like editing the registry in Windows: a good way to optimize things, but also quite risky for the inexperienced.

---

### Post by kaykav on 2010-10-22
Well with that bit of advice I guess Ill just leave it alone.
Asking questions can advise one as to what to-do, or not to-do. 
   thanks for your know-how......Rich

---

