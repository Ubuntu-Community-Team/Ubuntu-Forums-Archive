---
title: "errors in terminal"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by venicequeen7706 on 2009-12-20
I'm new to linux and I tried opening evloution from the gnome terminal and got a long list of problems, but it opened and worked ok anyway. I was wondering if someone could explain what all this stuff means and how i would go about learning to fix it on my own.


christopher@christopher-laptop:~$ evolution &
[3] 1971
christopher@christopher-laptop:~$ ** (evolution:1971): DEBUG: mailto URL command: evolution %s
** (evolution:1971): DEBUG: mailto URL program: evolution

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:1971): DEBUG: New Indicator: Inbox pop:
** (evolution:1971): DEBUG: New Inbox inidicator
** (evolution:1971): DEBUG: Number of email accounts: 1
** (evolution:1971): DEBUG: EI: SHELL STARTUP

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:1971): DEBUG: Evolution is focused

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:1971): DEBUG: EI: mail_read_notify
** (evolution:1971): DEBUG: Setting Inbox to 0 unread messages

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:1971): DEBUG: EI: mail_read_notify
** (evolution:1971): DEBUG: Setting Inbox to 0 unread messages

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:1971): DEBUG: Number of email accounts: 1

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:1971): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:1971): DEBUG: Number of email accounts: 1


 thanks for any help

---

### Post by Chesamo on 2009-12-20
That's debug information. For the most part, you can ignore that. Evolution accepts command-line switches in the form of a string (that's what "evolution %s" means), so your ampersand got sent to Evolution as an argument. Since the ampersand is a special character in C (and C++), Evolution got confused when it tried to process it. Remove the space between your command and the ampersand, and the debug information should stop showing up. Notice the difference between these two lines:```
$ evolution&
$ evolution &
```
The second line is wrong.

---

### Post by Mornedhel on 2009-12-20
> **Chesamo said:**
> That's debug information. For the most part, you can ignore that. Evolution accepts command-line switches in the form of a string (that's what "evolution %s" means), so your ampersand got sent to Evolution as an argument. Since the ampersand is a special character in C (and C++), Evolution got confused when it tried to process it. Remove the space between your command and the ampersand, and the debug information should stop showing up. Notice the difference between these two lines:```
$ evolution&
$ evolution &
```
The second line is wrong.

Sorry, you're just plain wrong. The ampersand would have been caught by the shell all the same, before it would have been sent to evolution as an argument. You can try this with other commands.

Both lines are correct and do the same thing. Debug information will not stop showing up unless there's an argument (such as --silent, or similar) he can pass to evolution, or he redirects all of evolution's output (at least stderr, possibly stdout as well) to somewhere else (a log file if he wants to keep it, /dev/null otherwise).

In any case, this output is normal and not a problem.

---

### Post by venicequeen7706 on 2009-12-22
thanks dude

---

### Post by t0p on 2009-12-22
> **Chesamo said:**
>  Notice the difference between these two lines:```
$ evolution&
$ evolution &
```The second line is wrong.


????

---

